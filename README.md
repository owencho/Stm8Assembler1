# Stm8Assembler
## Introduction
This is STM8Assembler which convert STM8 assembly language into STM8 machine code.
The main function for this STM8Assmbler is `getInstruction()` function which return the machine mode when user pass in the assembly language code into the function.
The tokenizer that used inside this STM8 Assembler to retrieve the instruction and operand token is based on the TokenizerSkeleton [2].
The format of the machine code is based on [1] which is STM8 datasheet PM0044.pdf file that has all the instruction details. 

## Requirement
The following software need to be installed on your PC
1. Ceedling 
2. MSYS32/64
3. Ruby
4. Git
5. Cosmic STM8 Software Development tools ([Software Link](https://www.cosmic-software.com/stm8.php))


## How to clone the file from GitHUB
Stm8Assembler can be cloned by issuing the command below with GitBash.
```
git clone https://github.com/owencho/Stm8Assembler
```
Or you can download through STM8Assembler GitHub webpage 

![clonepic](https://github.com/owencho/Stm8Assembler/blob/master/Resources/images/cloneImage.PNG)


## Updating the STM8Assembler
If **STM8Assembler** has updates , the repository can be updated by issuing the command below with GitBash.
```
cd Stm8Assembler  // if you are not inside the project folder
git fetch         // to fetch the STM8Assembler update from the source 
git pull          // to pull the update from the source
```
Remember to **clobber and rebuild the project** by using the command below after update.
```
ceedling clobber          // clobber / clean all generated file
ceedling                  // Build the STM8Assembler project
```
## Testing the program
You can test STM8Assembler by issuing  `ceedling test:all ` command on GitBash.


## STM8 Instruction set
![instructionsettable](https://github.com/owencho/Stm8Assembler/blob/master/Resources/images/STM8InsSet.PNG) 

Note: Each different instruction group have different source file, header file and test file in this repository.


## Note
1. For instruction that is relative jump or relative call function
  - It **DOES NOT support word jump** eg `JRNE loop` , the word jump label are not supported \
    and it **ONLY support value jump** eg `JRNE $15`
    
  - The output machine code value for the address part will be value of `destination hex value + machine code length` \
    instead of value with `Program Counter + destination hex value`.

2. There is an extra instruction named *interrupt instruction* which does not belong to any instruction group are now placed under 
**Interrupt Management** instruction group.

3. There is an CustomAssert test file which test the `TEST_ASSERT_EQUAL_MACHINECODE(expectedMcode,mcode)` function.
This function compares the difference between the expected machine code and the generated machine code which returned by the `getInstruction( ) `function. \
This is CustomAssert test file is disabled default during the test and it required to manually remove the x from this file name `test\xtest_CustomAssert.c` to conduct the test.

   
    

















## Appendix
1. https://www.st.com/content/ccc/resource/technical/document/programming_manual/43/24/13/9a/89/df/45/ed/CD00161709.pdf/files/CD00161709.pdf/jcr:content/translations/en.CD00161709.pdf
2. https://github.com/chaosAD/TokenizerSkeleton

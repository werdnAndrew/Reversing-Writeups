# Microcorruption Level #1 - New Orleans
This is the first level without having your hands held.
As soon as you start the challenge you are greeted with the following info popup:

![](New_Orleans_Images/New_Orleans_Info.png)

#### First Steps
Quickly scrolling through the disassembly window we see a couple functions that stand out: create_password and check_password.
Without spending too much looking through them, lets set a breakpoint at main.
Enter 'c' into the Debugger Console to continue to the breakpoint.

The first instruction in the main function adds the hex value 'ff9c' to the sp register (sp was 4400) resulting in the value '439c' being placed in it.
The next instruction then calls 'create_password'.

#### <create_password>

![](New_Orleans_Images/create_password.png)

The first instruction moves the hex value '2500' into r15. The next instruction is 'mov.b'. After consulting reseaching online for the MSP430 instruction set, we can see that 'mov.b' moves a byte into the specified location. In this case the specified location is the value in r15 plus an offset. The offset is 0x0 and r15 = 2400, so the instrucation places the value '75' at address '2400'. The following instructions increment the offset by one and add their value to that location. After all the 'mov.b' instructions the memory address '2400' looks like this:  

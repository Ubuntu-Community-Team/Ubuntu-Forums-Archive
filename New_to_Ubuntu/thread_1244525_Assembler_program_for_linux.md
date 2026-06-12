---
title: "Assembler program for linux"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by nikhilbhardwaj on 2009-08-19
hello

i have a paper this semester in college 
it has to do with microprocessors and assembly language
the recommended book is bary b brey microprocessor programming and interlacing

it recommends using Microsoft Assembler 
so will i need to go back to windows or is there an equivalent for linux
please note that the program should work identically as MASM does
ie there shouldn't be any difference in the assembly language code

please guide me so that i can find a program that works for me.

---

### Post by michy99 on 2009-08-19
You might try running MASM in Wine. You could also check out this:

[http://www.japheth.de/JWasm.html](http://www.japheth.de/JWasm.html)

I don't know anything about it, just something google turned up.

---

### Post by Nepherte on 2009-08-19
For mips you can always use spim: [http://www.nepherte.be/spim-on-linux/](http://www.nepherte.be/spim-on-linux/)

---

### Post by nikhilbhardwaj on 2009-08-19
i don't know anything about it either
i'll need to learn how to use it to compile and run programs on it

---

### Post by lkraemer on 2009-08-19
nikhilbhardwaj,
Man, I wish I were in your shoes......Those were the good ole days.....
(I worked for a C programmer who wrote some code to toggle the Numlock
key state and it was 32K in size.  I told him that was good, but I could
it in less than 10 bytes.  He laughed!  I wrote my code and it was only
8 bytes!)

Give this a try as it will work good.  Use Synaptics to install Dosbox.
Once Dosbox is installed it should create an Icon in the following Menu:
APPLICATIONS -> SYSTEM TOOLS -> Dosbox
It it doesn't right click on APPLICATIONS and add the Menu item to
SYSTEM TOOLS for Dosbox.  (It will add the correct Icon.)

Create a folder/Subdirectory named C: at your /home/user/
Copy your masm Folder/Subdirectory to /home/user/C:
So, now you have all the MASM files located in /home/user/C:/masm
Now Double Left Click on the Dosbox Icon, and read the info, and
look around.

The following commands can be used in dosbox
intro
intro mount
intro cdrom
intro special
help
help /all

Along with a lot of special commands that are shown on their help screens.

Now to run MASM do the following in the Dosbox window:
mount c ~/C:
C:
cd masm
masm /zi yoursource.asm

(NOTE: Once mounted you don't need to repeat the mount command, just
cd to the folder you need to access.)

To UNMOUNT C: use the following command:
mount -u c

Typically you run masm /zi Source.asm to make the OBJECT modules,
then LINK the OBJ Modules with Libraries needed to build your EXE.
Then for some code you can do a EXE2COM to make a *.COM file which
will be smaller.

This method of using Dosbox might not like relocatable code where you
are compiling for TSR's etc (Terminate & Stay Resident) were Multiple
passes are used.  I haven't tried that with Dosbox.  But, for your class
I'd bet it will work fine.

Check out A86 and D86 (Assembler and Disassembler) which were in the
Public Domain.  There was also Turbo Assembler that was put out by
Borland which had a really good Integrated Environment (IDE).  You could
single step through the code, and look at all the variables, etc.
You just had to compile with /debug information and then debug your
code at the Source level.  I don't know if MASM, TASM, A86, and D86
are still available.  Maybe a GOOGLE Search will find some versions
that you can use.  I wonder if MASM will be furnished for your class?

Typical Commands:
;Assemble with: (Where progname was TD3286.asm)
;                MASM /zi progname;
;                LINK progname;
;                EXE2COM TD3286.EXE TD3286.COM
;                Erase TD3286.EXE
;

 
lkraemer

---

### Post by zerhacke on 2009-08-19
Natively, Linux and most of the other Unices use NASM, the Netwide Assembler.  It's in the repositories.

---

### Post by lkraemer on 2009-08-20
Here is another thread on using MASM!
[http://ubuntuforums.org/showthread.php?t=1114850](http://ubuntuforums.org/showthread.php?t=1114850)


lkraemer

---

### Post by nikhilbhardwaj on 2009-08-21
many many thanks to you lkraemer 
and everyone else who posted here to help me out

---

### Post by markbuntu on 2009-08-21
Ahhh...I remember writing assembler on a punchcard machine....

then we got real terminals...

WhooHoo!!!!

You kids these days got it so easy.

---


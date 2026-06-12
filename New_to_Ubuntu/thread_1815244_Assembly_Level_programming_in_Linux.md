---
title: "Assembly Level programming in Linux"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-07-30
In my college, in the micro processor lab we use 8086 trainer kit for the programming the microprocessor  ! Is it possible to execute the Assembly Level programming in  my pc installed with linux? Is the 8086 micro processor code are compatible with my intel micro processor? 

Thank you!

---

### Post by Redblade20XX on 2011-07-30
Honestly with assembly you can't really execute any code in a pc because it's really abstract conceptualization of the pc itself. i.e it's just really move the value of one register to another to accomplish a task in higher level programming. There once was a program in the repository for MIPS32 but I think it has been removed due to depreciation.

---

### Post by anewguy on 2011-07-31
If you want to execute it, you could try loading wine and running it in there.

There are also other emulators around, such as fake86, to allow running DOS apps, etc., in emulation.

Just what types of things are they having you do with assembler?  The answer to that can help point us in a direction to try to help.  God forbid they are doing any GUI type programming in assembler - that's more than a little bit difficult.  If the trainer is to teach you about registers, shifting, etc., perhaps reading and writing from ports, then one of the emulators might help.

I've looked for a 8086 assembler training software for linux but haven't found some sort of package for that.

fake86 is supposed (I've never used it) to provide an emulated 8086 so you presumably could run the programs there.  They are supposed to have a debian package for download that should work for ubuntu.  See: [http://fake86.rubbermallet.org/]("http://fake86.rubbermallet.org/")

If you need an assembler for 8086, that's another matter.  If you could explain more what the trainer is/does perhaps we can try to find something comprable in Uuntu/linux.

dave ;)

---

### Post by anewguy on 2011-07-31
> **Redblade20XX said:**
> Honestly with assembly you can't really execute any code in a pc because it's really abstract conceptualization of the pc itself. i.e it's just really move the value of one register to another to accomplish a task in higher level programming. There once was a program in the repository for MIPS32 but I think it has been removed due to depreciation.
Assembler isn't an abstraction layer - it is the low level access to the CPU - registers, yes, but also everything else you can do from port read/write to who knows what.  You CAN run the output of an assembler on a PC if it's output is for the processor in the PC.  What you don't want to do is try to run an assembly program in Windows without really knowing what you are doing.  We used to do all kinds of things in assembly even with Windows - even simple things like grabbing the keyboard interrupt so we could test key strokes and generate a different output as needed for such things as RAD and CAP tools that needed keystrokes specific to a certain terminal type.  It's more a matter of what you want to do or what you are learning.  Sometimes learning with assembly is the best way to understand a CPU, so that you can then go on to discreet microprocessor controllers, etc..  While many of these now support C or simple C++ as well as Basic, learning the hardware via an assembler is a great way to know exactly what is happening, the timing cycles, etc., needed to do low-level signal aquisition, data collection (interrupt driven I/O), etc., etc..  The assembler available, what it's exact linking, etc., are also dependant on the OS - you can't really just write up some 8086 code, assemble and link it, and expect it to run anywhere.  There are always those little "hooks" that need to be observed.

---

### Post by Redblade20XX on 2011-07-31
> **anewguy said:**
> Assembler isn't an abstraction layer - it is the low level access to the CPU - registers, yes, but also everything else you can do from port read/write to who knows what.  You CAN run the output of an assembler on a PC if it's output is for the processor in the PC.  What you don't want to do is try to run an assembly program in Windows without really knowing what you are doing.  We used to do all kinds of things in assembly even with Windows - even simple things like grabbing the keyboard interrupt so we could test key strokes and generate a different output as needed for such things as RAD and CAP tools that needed keystrokes specific to a certain terminal type.  It's more a matter of what you want to do or what you are learning.  Sometimes learning with assembly is the best way to understand a CPU, so that you can then go on to discreet microprocessor controllers, etc..  While many of these now support C or simple C++ as well as Basic, learning the hardware via an assembler is a great way to know exactly what is happening, the timing cycles, etc., needed to do low-level signal aquisition, data collection (interrupt driven I/O), etc., etc..  The assembler available, what it's exact linking, etc., are also dependant on the OS - you can't really just write up some 8086 code, assemble and link it, and expect it to run anywhere.  There are always those little &quot;hooks&quot; that need to be observed.

 lol nowhere did I say that assembly is an abstraction layer. It's an "abstract" concept dealing with the inner workings for the pc. Most people probably will never deal with it directly unless they're an engineer designing the cpu.

---

### Post by anewguy on 2011-07-31
Sorry - I misread your post! ;)  Indeed, being the ex-engineering type, I know that most people would never look at it or have a clue what to do, and really that's what today's OS's are all about - isolating the programmer and the user from the underlying hardware.  It does, however, have it's uses outside of CPU design - it's still very critical in cases where timing is essential so that signals aren't missed, etc..

  Keep in mind that 40 years ago a lot of corporate information systems where still all in assembler.  At that time, not all programming languages (in particular things like COBOL) did not have terminal interfacing built-ins yet.  So a lot of that was done in assembler (and yep - I worked back then ;) ).  Also, if you were a systems programmer and administrator as I was, you had to deal with the systems' instruction set, addressing, etc., all the time.  I've been out of the business and the working world since 1996, so I know not only have things migrated to client/server and away from large proprietary mainframes but that the OS is more isolated away from the programmer and user today.  However, todays' OS's, including Linux itself, still use assembler.  It's far from anything from anyone designing a CPU.  In fact, a lot of CPU design is actually done by computers today - the engineers play a HUGE part, but none the less the computer does a lot of it.

So, while the OP needs it to go along the their class, I agree that most people today would never use it, and to be honest, it's really kind of a shame.  There's nothing quite like controlling/interfacing to each piece of hardware.  Accessing address and data busses, instructions to each piece of hardware, etc., gives you a more in-depth knowledge of what a computer really is than most people are exposed to today. Back when we had to write our own floppy disk drivers, hard disk drivers, printer drivers, etc., you learned things that also help today in debugging problems.  But will the average or even above-average user see or use it today?  No, definitely not.

So, sorry I misread you post, but it's also important for people to understand that assembler still plays very keen parts in things today.  It's far and away anything than just something engineers use to design CPU's.

Sorry I misread your post, but things like > It's an "abstract" concept dealing with the inner workings for the pc are extremely inaccurate.  Short of hand-assembled machine code you toggle into memory, it is THE way, and not an abstract concept, to interface with the hardware - something sorely missing in today's courses.

Dave ;)

---

### Post by nipennem on 2011-07-31
> **1991sudarshan said:**
> In my college, in the micro processor lab we use 8086 trainer kit for the programming the microprocessor  ! Is it possible to execute the Assembly Level programming in  my pc installed with linux? Is the 8086 micro processor code are compatible with my intel micro processor? 

Thank you!

If only you would use [Google]("http://www.google.com/search?q=8086+emulator"), you would probably find what you're looking for. There are a number of 8086 emulators available which will show you exactly what happens on the processor, and which may even emulate some simple peripherals typically found on microprocessor demo boards...

---


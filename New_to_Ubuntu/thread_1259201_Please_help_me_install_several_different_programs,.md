---
title: "Please help me install several different programs, I do not know how to compile/run t"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by ftgibson on 2009-09-06
I have searched the world over and thought I'd found true love but Ubuntu wouldn't help so thwep he was gone! (HeeHaw, and Amie aka ftgibson).

I have several different (extremely important) programs relating to seismology downloaded to my Ubuntu computer. I have extracted some, etc. but as for any help on actually making any of the programs run, I am evidently in the dark.

 Any advice anyone could give to me would be greatly appreciated! My Linux guru and mentor was killed in an accident last year and he never got to tell me how to make  an installed program "run".


Thank you to anyone that can please help me.

Amie :(

---

### Post by 3rdalbum on 2009-09-06
Do the programs give any instructions on how to install and run them? Without a set of instructions, or being there looking over your shoulder, we have no idea how these are meant to be run. We don't know if they need to be compiled, and if so with what build system; we don't know if they are meant to be put into your filesystem, we don't know if there's an installer script to run, etc.

If they provide usage or install instructions, have a go at following them, if you get stuck reply with the step you are having trouble with, and whether you're getting any error messages, and we'll do our best.

---

### Post by ftgibson on 2009-09-06
This is exactly what one of the main programs that I need operating (Read me) file says:


    The hypoinverse source files in this directory are for both VAX VMS version 5.4 and sun unix 4.1 systems.  When a file exists with only a .for extension, the same file compiles under either system.  When there is both a .f and .for version, the .for is for VMS and the .f is for unix.  If present, the mem_dump.for and mem_eq_update.for subroutines and mem_record.inc and mem_structure.inc files are exceptions to this rule.  They are vax only routines for reading CUSP mem files and are unused in the unix version of the program.  These routines in turn depend on other cusp subroutines that are not here but must be present on your vax system.
   
  The hybeg subroutine contains the string defining the path to the standard startup command file that hypoinverse runs when you type the ini command.  That is, of course, very system dependent and you will need to change it for your system.
   
  The unix makefile is the one I used to build the program on a different sun computer.  The file libfs.a is a library built with the "ar -c -arch" command.  These are subroutines I use with many different programs.  The sources for these subroutines are in the subsdir directory.  I use the same conventions of .f (unix only) and .for (VMS or both) file extensions.
   
  The VAX link command I use on our VAX system is in the file hypVAX.com.
  


   I hated even asking a question because I always get the feeling and by also reading others posts, that people who are not experts in Linux are somewhat made a whipping post. 

 I just honestly need help and I did not see any other threads similar to my topic so I just posted. After  reading all the forums for the past two hours, I decided to take a leap and see if I could get anyone to help.


Please help me if you can,
ftgibson

---

### Post by 3rdalbum on 2009-09-06
Whoa. That makes my head spin, without helping me to understand how the software is installed. That's more like developer's documentation; is there not a file called "INSTALL" in that directory? (usually contains installation instructions).

I'm guessing that the reference to a Makefile means that you have to compile the software from source.

Can you navigate a terminal to the program's directory and run the following commands:

```
./configure
make
sudo make install
```

If you don't know how to navigate a terminal into the directory, then install the "nautilus-open-terminal" package, log out and back in again, navigate the **file browser** to the program's directory, right-click in some empty space and choose "Open In Terminal".

---

### Post by mlentink on 2009-09-06
From reading the instructions, I am doubtful whether this stuff will run at all on Ubuntu. 
You can forget about all the VAX/VMS routines. Completely different architecture and operating system.
The UNIX parts might be made to run, but you need to keep in mind that even though Linux looks a lot like UNIX, it isn't exactly the same animal. The software, as it is written now, might make calls to API's that do exist on Sun Unix, but not on Linux.

I am not a programmer, but I'm pretty sure that without more info from the authors on how to adapt and compile this stuff on Linux, you're in for a challenge

---

### Post by 3rdalbum on 2009-09-06
> **mlentink said:**
> From reading the instructions, I am doubtful whether this stuff will run at all on Ubuntu.

So am I, but I'm hoping that the description in the README is hopelessly outdated and that there is in fact Linux support.

---

### Post by ftgibson on 2009-09-06
> **3rdalbum said:**
> So am I, but I'm hoping that the description in the README is hopelessly outdated and that there is in fact Linux support.


  Do you think it would be possible for me to install something like belenix_0.7 on a different machine and the program might work?  The programs are all earthquake location programs that were written with Unix and Solaris platforms.

I appreciate all the posts and thoughts to try to help me figure how to get these working!

I am in a pickle! ](*,)

Thanks,
Amie aka ftgibson

---

### Post by 3rdalbum on 2009-09-06
Your best shot might be to install OpenSolaris (if I remember correctly, Belenix is an OpenSolaris distro from back before OS was a distribution too).

I have heard that the kernel API for Solaris is so stable that you can install 10-year-old Solaris drivers on OpenSolaris. Perhaps the userspace libraries have similar stability.

I take it you haven't had any luck in compiling these programs on Linux?

---

### Post by mlentink on 2009-09-06
> **3rdalbum said:**
> your best shot might be to install opensolaris 
+1

---

### Post by ftgibson on 2009-09-06
I have tried everything.  The files do not seem to have a ./configure option etc. Where would I get opensolaris?  

Thanks,
Amie

---

### Post by mlentink on 2009-09-06
here: [http://opensolaris.org/os/downloads/](http://opensolaris.org/os/downloads/)

---


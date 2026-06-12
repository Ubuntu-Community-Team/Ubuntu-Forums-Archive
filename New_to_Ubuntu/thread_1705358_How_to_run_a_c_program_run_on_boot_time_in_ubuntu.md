---
title: "How to run a c program run on boot time in ubuntu"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by muhammed irshad on 2011-03-12
I want a c program which copies a file from one location to another to  run at boot time that is before operating system starts.......Any body  please help.....Actually i was planning to create a software which backups the system  files in ubuntu....As a part of my mini project......And i need c  program to run on boot time while restoring the os files...That is why i  am seeking help..I need only how to make my c object file to execute on  boot time...

---

### Post by turtle153 on 2011-03-12
You can put it in **System > Preferences > Startup Applications** to make it run when you login.

---

### Post by thameera on 2011-03-12
Compile the program. Then put the command which you use to run the object file in the Startup Applications.

---

### Post by muhammed irshad on 2011-03-12
@turtle and thameera ...I am not looking for running it while logging in ....I want it to run on boot time..

---

### Post by agnes on 2011-03-12
Make a script that invokes the program. Put the script, example name "myscript", in /etc/init.d
Make sure to give it executable permissions. Then type "update-rc.d myscript defaults".
[More info]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by muhammed irshad on 2011-03-12
I need a reply related to boot loaded module.....Because i need  this for to replace the root file system with another 1....So i think init.d wont do...Can any1 post related to boot loaded module..

---

### Post by wep940 on 2011-03-12
Ubuntu is going to have to boot to some degree before you can do this, and that is going to use the root file system. What you want to do sounds like a pre-boot procedure, and I think the only way you can do that is with a different boot loader and and some sort of "mini OS" to run your program. That's if you want to replace the files as you have stated. If you want to just copy them for backup, you can do that in any of the ways already suggested.
 
EDIT: The reason I say mini-OS is that most "C" programs, unless you have gone so far as to write your own hard disk drivers using the BIOS, programs rely on libraries specific to the operating system to perform any I/O. You may be better off adding another OS, such as a different variant of Linux that is very small, to have added to the grub menu. Then you could select it to boot, autorun your backup/replace program and auto reboot. Then the grub menu would return again and you could just select boot Ubuntu.

---

### Post by muhammed irshad on 2011-03-13
Can i replace the root file system by using a kernel module with another 1 on booting time ....By adding those program in a kernel loaded module......

---

### Post by wep940 on 2011-03-13
You're not going to be able to replace the root file system during boot. The root file system is where it finds grub, the kernel image, the kernel modules to load, etc. That means that the entire root tree is going to busy during boot and you can't just replace it.
 
So, do you really want to replace the entire root file system?  Why?  If you're doing that, why not just have another installation you can boot from the grub menu?

---

### Post by muhammed irshad on 2011-03-13
@wep940
Thank you very much for your reply..
I need this because i am planning to create a backup for the root directory as a part of my mini project...
I can backup root directory to a hard disk during run time.....But when we need to restore the root directory it wont do during run time because like you said it will be busy...
So i thought it can be restored by creating a c program to restore the root directory from hard disk to the existing root  and add that into kernel module and it can be done during boot time....So can you please advice me to achieve this in any other way...please...

---

### Post by grahammechanical on 2011-03-13
I admit that I do not know what you are talking about. I am ignorant about this subject. May add a comment?

When I boot from a Ubuntu live CD I notice that a type of Linux loads first and from that Ubuntu loads. I think that it is called isolinux or something like that. Perhaps you could modify the booting method of a live CD to do what you want.

It is just a crazy idea. 

Regards.

---

### Post by wep940 on 2011-03-13
I didn't know that - does it do it on a normal boot from hard disk? I always thought ISOLinux *was* Ubuntu booting.
 
EDIT:  Just did a quick search on the net - looks like ISOLinux is only for booting from the CD.

---

### Post by CaptainMark on 2011-03-13
it sounds like your mini project is a bit of a redundant idea, there are plenty of ways to back up the entire root file system, all of which would need you to boot the os first, why does it have to be before boot, you can backup the entire / file system to anohter harddrive or any location while it is being used, also why use C again seems uneccesary, i would use a bash seen as c would only have to pass arguments to bash

---

### Post by wep940 on 2011-03-14
For some reason the OP seems to be interested in REPLACING the root file system prior to boot, if I've read the thread correctly.  It escapes me as to why someone would want to do this.

---


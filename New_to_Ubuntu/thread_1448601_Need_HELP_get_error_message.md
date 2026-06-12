---
title: "Need HELP get error message"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by sketchme on 2010-04-06
I get an error message on my computer when I start up: NTLDR is missing 
can someone explain this to me and how to get past it. I tried reinstalling ubuntu and I still get it. I am using netbook remix

---

### Post by zeroseven0183 on 2010-04-06
NTLDR is a Windows file. So if you have the Windows bootable disc then you can do what's mentioned here [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

> 
**Windows XP users**       
[LIST=1]
[*]Insert the Windows XP bootable CD into the computer.
[*]When prompted to press any key to boot from the CD,  press any key.
[*]Once in the Windows XP setup menu press the "R" key  to repair Windows.
[*]Log into your Windows installation by pressing the  "1" key and pressing enter.
[*]You will then be prompted for your administrator  password, enter that password.
[*]Copy the below two files to the [root]("http://www.computerhope.com/jargon/r/root.htm") directory  of the primary hard disk. In the below example we are copying these  files from the CD-ROM drive letter, which in this case is "e." This  letter may be different on your computer.

copy e:\i386\ntldr c:\
copy  e:\i386\ntdetect.com c:\
[*]Once both of these files have been successfully  copied, remove the CD from the computer and reboot.
[/LIST]


---

### Post by sketchme on 2010-04-06
ok I used windows 7 I will try the start up disc... I dont get it I completely erased windows in my drive

---

### Post by zeroseven0183 on 2010-04-06
Alright. You didn't mention that you deleted Windows 7 already. How many partitions do you have?

---

### Post by sketchme on 2010-04-06
Idk I think one or two can't remember just did the standard install

---

### Post by zeroseven0183 on 2010-04-06
How did you install UNR? Because as far as I remember, if you do the "standard" install, it will wipe out all what's in the drive including your Windows 7.
Installing GParted will help us through this process. Unless others have a better or easier solution.

---

### Post by sketchme on 2010-04-06
i thought it would too erase everything, like I said I installed it again with no help

---

### Post by zeroseven0183 on 2010-04-06
When you boot your machine, do you see the Grub menu? The one with the operating systems list?

---

### Post by sketchme on 2010-04-06
um just dell boot icon, I can go into boot menu thats it

---

### Post by zeroseven0183 on 2010-04-06
What do you see in the boot menu? Is there an entry for Windows 7 or something?

EDIT: I'm thinking that's a recovery partition issue.

---

### Post by lidex on 2010-04-08
I think you wiped out windows but not the mbr, so windows bootloader is still in charge. What you need to do is install grub to the mbr.

Try this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---


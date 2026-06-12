---
title: "Total noob that needs help"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Joey Barclay on 2010-10-19
Im completely new to Ubuntu and Linux. I duel booted my computer a couple months ago.
I updated my Ubuntu 10.04 to 10.10 and everything went fine until Ubuntu told my computer to reboot. I got what I think is called a splash screen and my computer froze( I waited about 15 minutes) I then flipped the power switch on the back. When I turned it on all seemed normal windows was there to pick and so was Ubuntu. Windows booted up just fine and normal but when i try to go into Ubuntu instead of letting me pick how I go into it (example: safe mode generic 12.345.21 kernel It looked similar to this ) It just shows a couple of lines of text in the top left corner that say file cannot be found. My computer then reboots. Like I said im a complete noob and I used the windows installer. Can I fix my computer without having to reinstall Ubuntu? I think the missing menu is the grub. Can anyone give me strait forward directions for fixing my computer?

---

### Post by Joey Barclay on 2010-10-20
I just noticed this error flashed right before it reboots
(hd0,0): NTFS5: No wubildr
(hd0,1): NTFS5 
Error file not found
Error file not found

---

### Post by bcbc on 2010-10-20
You may have corrupted the root.disk when you did a hard shutdown. Wubi is very susceptible to this.


Boot windows, go to my computer, right click your drive, Properties, Tools, Check disk for errors, Fix automatically. You probably will have to reboot to do this.

Then check for the file c:\ubuntu\disks\root.disk (change drive if necessary). It's possible that it gets moved to hidden folder FOUND.000 when you run check disk. If so, move it back to c:\ubuntu\disks\.

In the future, if you need to force shutdown, use ALT-SysRq + R-S-U-B

---

### Post by mastablasta on 2010-10-20
wubi is not propper dual boot and it is not a good idea to upgrade the os in wubi as it might not be supported. wubi is ment more to test out the system.
 
Unfortunatell Canonical moved/removed the site explaining the fix for this. :-(
 
if you are on wubi and dont' have any important data in linux, i suggest booting into windows. removing wubi and if you want to use Ubuntu via wubi install the new ubuntu version again (clean install).
 
But you should consider a propper dual boot as it is easy to make and these issues don't exist there.

---

### Post by bcbc on 2010-10-20
Another thing with the wubi upgrade to 10.10 - it is known to corrupt the wubildr, so copy c:\ubuntu\winboot\wubildr file over c:\wubildr 

(you can backup c:\wubildr first if you like as it's good practice).

---

### Post by Joey Barclay on 2010-10-20
Thank you for your suggestions I will try them as soon as I have access to my computer. I wouldn't mind installing Ubuntu the right way but I don't have a good understanding of partitions. It was my understanding that the windows installer did everything correctly. I doubt I will be able to install Ubuntu the correct way:(

---

### Post by bcbc on 2010-10-20
> **Joey Barclay said:**
> Thank you for your suggestions I will try them as soon as I have access to my computer. I wouldn't mind installing Ubuntu the right way but I don't have a good understanding of partitions. It was my understanding that the windows installer did everything correctly. I doubt I will be able to install Ubuntu the correct way:(

Wubi is designed with you in mind. When you're more comfortable with partitioning you can migrate to a direct install. Don't worry about the negative comments you sometimes see about wubi on the forums - some people are offended by wubi for some reason (perhaps the association with windows). Yes it has some issues, but it's pretty cool really. It's a proper dual boot, just uses a virtual disk. As long as you take precautions like backing up the root.disk before major changes/upgrades, you shouldn't have any issues. 

I recommend backing up all important data whatever OS you use. Even "true" ubuntu has been known to have a few issues ;)

---

### Post by Joey Barclay on 2010-10-20
> **bcbc said:**
> Wubi is designed with you in mind. When you're more comfortable with partitioning you can migrate to a direct install. Don't worry about the negative comments you sometimes see about wubi on the forums - some people are offended by wubi for some reason (perhaps the association with windows). Yes it has some issues, but it's pretty cool really. It's a proper dual boot, just uses a virtual disk. As long as you take precautions like backing up the root.disk before major changes/upgrades, you shouldn't have any issues. 

I recommend backing up all important data whatever OS you use. Even "true" ubuntu has been known to have a few issues ;)

Thanks I am from the Android hacking world and know that there are several 1 click hacks but the long ones are always preferred by the experts. My android phone actually inspired me to get Ubuntu due to its customization and Linux kernel

---

### Post by mastablasta on 2010-10-20
> **bcbc said:**
> Wubi is designed with you in mind. When you're more comfortable with partitioning you can migrate to a direct install. Don't worry about the negative comments you sometimes see about wubi on the forums - some people are offended by wubi for some reason (perhaps the association with windows). Yes it has some issues, but it's pretty cool really. It's a proper dual boot, just uses a virtual disk. As long as you take precautions like backing up the root.disk before major changes/upgrades, you shouldn't have any issues. 
 
I recommend backing up all important data whatever OS you use. Even "true" ubuntu has been known to have a few issues ;)
 
all this is true. except it is a dual boot just not "side by side" but more within windows (due to using a virtual disk). 
 
take it slow. there is no rush. 
 
i hope you manage to fix it and then explore the side by side boot. partitioning is not that hard. but precaution steps have to be taken to avoid any possible data loss. and once it is done you will be able to have 2 systems running on separate parts of disk independent of eachother.

---

### Post by Joey Barclay on 2010-10-20
this time when i pressed ubuntu it come up with the grub but i dont know what to do. it says GNU GRUB version 1.98+20100804-5ubuntu3 minimal Bash-like editing is supported. For the first word, TAB lists possoble command completions. Anywhere else TAb lists possible device or file completions. what the heck do i do at this screen please reply quickly to help me turn off my computer or fix ubuntu as it is 2 in the morning right now for me :confused:

---

### Post by mastablasta on 2010-10-20
> **Joey Barclay said:**
> this time when i pressed ubuntu it come up with the grub but i dont know what to do. it says GNU GRUB version 1.98+20100804-5ubuntu3 minimal Bash-like editing is supported. For the first word, TAB lists possoble command completions. Anywhere else TAb lists possible device or file completions. what the heck do i do at this screen please reply quickly to help me turn off my computer or fix ubuntu as it is 2 in the morning right now for me :confused:
 
```
sudo shutdown -h now 
``` to turn off the computer
 
otherwise the easiest way would be to reinstall.

---

### Post by Joey Barclay on 2010-10-20
> **mastablasta said:**
> ```
sudo shutdown -h now 
``` to turn off the computer
 
otherwise the easiest way would be to reinstall.

When i did that i get unknown command "sudo"

---

### Post by SuaSwe on 2010-10-20
Are you at a # prompt or a $ prompt? Maybe try just 'shutdown -h now'. :)

---

### Post by Joey Barclay on 2010-10-20
> **SuaSwe said:**
> Are you at a # prompt or a $ prompt? Maybe try just 'shutdown -h now'. :)

I don't think i am in a terminal. im at a grub> _

---

### Post by Joey Barclay on 2010-10-20
Should i use the halt command will that turn it off?

---

### Post by Joey Barclay on 2010-10-20
I looked online and saw that contrl alt del will reboot the computer. night

---

### Post by SuaSwe on 2010-10-20
Sorry, didn't realise you were at the grub prompt! Night night. ;)

---

### Post by bcbc on 2010-10-20
Did you confirm that the root.disk is there? Look in c:\ubuntu\disks\ folder and make sure.

Also, did you copy c:\ubuntu\winboot\wubildr to c:\wubildr ?

Please confirm. 

If both of those are done, I can give you commands to manually boot the wubi install, but it's better to just get try and get it fixed.

PS If you need to copy data off your root.disk you can use a program called [ext2read]("http://ext2read.blogspot.com/") (it can give read-only access - just download, run and point it at the root.disk).
Just bear in mind, if you decide to uninstall/reinstall, the root.disk will be deleted - so make sure you get your data first.

---

### Post by Joey Barclay on 2010-10-20
> **bcbc said:**
> Did you confirm that the root.disk is there? Look in c:\ubuntu\disks\ folder and make sure.

Also, did you copy c:\ubuntu\winboot\wubildr to c:\wubildr ?

Please confirm. 

If both of those are done, I can give you commands to manually boot the wubi install, but it's better to just get try and get it fixed.

PS If you need to copy data off your root.disk you can use a program called [ext2read]("http://ext2read.blogspot.com/") (it can give read-only access - just download, run and point it at the root.disk).
Just bear in mind, if you decide to uninstall/reinstall, the root.disk will be deleted - so make sure you get your data first.

root.disk was there I haven't copied wubildr yet I will do that next.
edit I noticed that the two files are different sizes the one that was already in C was 113 kb but the one in the folders is only 87kb

---

### Post by Joey Barclay on 2010-10-20
It works now thank you very much. Im not sure if I should start a new thread but ever since I installed Ubuntu all the sounds are extremely quite. I can barely hear sounds and all of my volume settings are maxed out. They also show that they are maxed out when I type alsamixer in the terminal.

---

### Post by bcbc on 2010-10-21
> **Joey Barclay said:**
> It works now thank you very much. Im not sure if I should start a new thread but ever since I installed Ubuntu all the sounds are extremely quite. I can barely hear sounds and all of my volume settings are maxed out. They also show that they are maxed out when I type alsamixer in the terminal.

Great. You're welcome.

I don't know much about the sound problems with maverick - I've noticed a few posts but not followed them so I suggest a new thread.

---


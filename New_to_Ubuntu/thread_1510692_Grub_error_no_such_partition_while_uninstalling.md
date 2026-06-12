---
title: "Grub error no such partition while uninstalling"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Shadeslader on 2010-06-15
I installed ubuntu 10 a few weeks ago to mess around on, booted it a few times but never used it since. So i uninstalled today, i used wubi to uninstall, it went fine then later on when i boot my pc it loads grub 2 displaying error : no such partition, i searched around a bit and found out that since after i used wubi to uninstall i mistakenly thought i was done with it so i deleted the partition little did i know ubuntu made a partition inside of my partition or something so after i finally got both partitions deleted and resized my main partition. I booted my pc and got the error i said before and the answer i found was that i deleted the config and the grub install when i formatted, the number one way to fix it is by boot cd, well i don't have one. im stuck in grub rescue with no way out.

so i need the commands to use in grub 2 to either uninstall it or to change it to boot windows 7(so i can repair MBR) i need some files for my business that i have stored on there within the next hour or so otherwise im having to reinstall windows 7 so i can get to them. 

Any help is appreciated

---

### Post by Chesamo on 2010-06-15
I would suggest using [RiP Linx](http://rip.7bf.de/current/) and running the grubconfig program. It'll help you replace GRUB.

---

### Post by Shadeslader on 2010-06-15
tried what you suggested but it attempts to boot and gives me could not find kernel image : menu.c32

---

### Post by garvinrick4 on 2010-06-15
If you used WUBI install and used ADD and Remove programs in Windows to uninstall you most likely left part of the wubi in the Windows bootmanager called bcd. There is a uninstall in the folder in Ubuntu Wubi right next to Users in C: drive with a uninstall in the folder to use. But if the folder is gone its gone.
  Now you have to see if you can get your boot back together. Here you go. Copied and pasted from a thread found on Ubuntu Forums.
                          <!--         @page { margin: 0.79in }         P { margin-bottom: 0.08in }     -->       

 How to restore the Windows Vista or 7 bootloader  
 

 To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.  
 If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7.  
 When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." 
 

 On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.  
 Then click on "Command prompt". From there, type in the folowing:  
 

 Code:  
 

 bootrec.exe /fixboot  
 

 Code:  
 

 bootrec.exe /fixmbr  
 

 Now close the two windows and click "Restart."  
 

 Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader. 
 __________________

---

### Post by garvinrick4 on 2010-06-15
Once you can boot Windows go to command line and 

```
bcdedit
```

```
bcdedit delete {the indentifier # with wubildr with these brackets}
```

To explain it better find the one that says something close to wubildr in it and
that is the one you want to delete so just copy and paste or type in the identifier # with the brackets after delete. You will see what I mean if it is still there.

---

### Post by Shadeslader on 2010-06-15
thanks first post works i downloaded a win 7 recovery cd and mounted it to a usb, and ran it everything worked but now i have to re activate windows because it says its not genuine -_-

but thanks problem solved

---


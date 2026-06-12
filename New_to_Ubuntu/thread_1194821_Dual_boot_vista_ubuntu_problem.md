---
title: "Dual boot vista ubuntu problem"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by CdM-newb on 2009-06-23
I cannot boot to ubuntu, because EasyBSD says at the booting: Looking for hd 0,0; ext2 (something like that) and it reboots. Vista boots normally. I tried editing boot/grub/menu.lst but I cannot save it because I am on live cd.. Any help would be appreciated..

I really miss ubuntu..

CDM

---

### Post by frup on 2009-06-23
if you want to edit the your real /boot/grub/menu.lst you need to mount the drive.

You can also use chroot to do some pretty effective things.

---

### Post by CdM-newb on 2009-06-23
a) How do i get chroot? 

b) How do i mount the disk? I think it was mounted but i couldn't save because I didn't have permissions..

Thanks for all help!

---

### Post by frup on 2009-06-23
Chroot is a terminal command that changes where user space sees / as. If you don't understand what that means don't worry, I don't exactly :P. Practically speaking, using chroot allows you to use the LiveCD environment on the drive better. I'm just trying to think if this works with the GUI though, the only thing I've really used chroot for was resetting user passwords and I've always just ctrl alt f1'd and used the terminal to do it.

In a terminal you go chroot /dev/sdba1 for example I believe. see type man chroot in terminal for a manual.

As for the mounting, yeah you need root/administrator permissions to edit files which aren't in the home directory. Try doing gksudo gedit /boot/grub/menu.lst

This should allow you to save. Or you can use nano if you want to stay in the terminal.

---

### Post by CdM-newb on 2009-06-23
ok i edited it and saved (TNX!) but it only boots vista, not a trace of ubuntu.. How could i overwrite vista's boot data?

---

### Post by kingzleshe on 2009-06-23
get  grud4dos from internet on vista
 
Extract grud4dos put grldr and menu.lst in C:/
 
you are windows vista not windows xp so you must create a new NOTEPAD  Name change boot.ini
 
write "C:\grldr=linux boot" in boot.ini
 
use NOTEPAD open menu.lst write correct vmlinuz and initrd path

General like this 
 
root (hd0,n) 
kernel /boot/vmlinuz ro root=LABEL=/ 
initrd /boot/initrd.img 
Boot
 

 
if your kernel change

configfile (hd0,n)/grub/menu.lst

---

### Post by CdM-newb on 2009-06-23
> **kingzleshe said:**
> get  grud4dos from internet on vista
 
Extract grud4dos put grldr and menu.lst in C:/
 
you are windows vista not windows xp so you must create a new NOTEPAD  Name change boot.ini
 
write "C:\grldr=linux boot" in boot.ini
 
use NOTEPAD open menu.lst write correct vmlinuz and initrd path

General like this 
 
root (hd0,n) 
kernel /boot/vmlinuz ro root=LABEL=/ 
initrd /boot/initrd.img 
Boot
 

 
if your kernel change

configfile (hd0,n)/grub/menu.lst

Do you mean GRUB4DOS or GRUD4DOS?

---

### Post by kingzleshe on 2009-06-23
GRUB4DOS
 
sorry -_-

---

### Post by CdM-newb on 2009-06-23
> **kingzleshe said:**
> GRUB4DOS
 
sorry -_-

ok no problem :D so i have this installed, but I can't see a menu.lst so i created it myself. Is 
root (hd0,n) 
kernel /boot/vmlinuz ro root=LABEL=/ 
initrd /boot/initrd.img 
Boot
all there is supposed to say?

also, I am experiencing problems using grub4dos? What should the file name be and I cant select any hard drives.. Sorry for wasting your time :S

---

### Post by kingzleshe on 2009-06-23
I forgot to say  do all these things before use DOS what format your disk mbr
 
C:/format mbr
 
because your Grub is still here.but have something woring with you Grub to boot ubuntu so we can format mbr to delete Grub and vista take over boot task,this like you had never install linux as you don't have live CD that Grub can't be Reinstall.  only way use grub4dos let vista guide boot your ubuntu

---

### Post by sadaruwan12 on 2009-06-23
Some thing similar to this has been discussed earlier as well try this thread this might help you.

[http://ubuntuforums.org/showthread.php?t=1111107&highlight=restoring+GRUB]("http://ubuntuforums.org/showthread.php?t=1111107&highlight=restoring+GRUB")

---

### Post by CdM-newb on 2009-07-09
OK Ubuntu is running great but how do I create dual boot with vista (black edition 2009) using grub? Previously I used EasyBCD but it didn't run out :(.. I would need step by step tutorials please :P

:popcorn:

---

### Post by CdM-newb on 2009-07-14
OK... after some work I have put vista in menu.lst but when I select vista it says NTLDR is missing. press alt+ ctrl+ del to restart. How do I restore NTLDR without vista overwriting MBR? Thanks for your help

---

### Post by _Rosco_ on 2009-07-17
Hey there...

This one can be real tricky to solve but there's a step by step solution on the website below that i've had success with.

This error appears when NTLDR's attributes have been altered or there is another problem with NTLDR.

To try the most common solution for this, read the following article:

PS:  NTLDR is missing.  Press CTRL+ALT+DEL to restart.
[http://www.proposedsolution.com/solutions/ps0013.php](http://www.proposedsolution.com/solutions/ps0013.php)

If the above does not fix it you may need to follow the Windows Boot Troubleshooting Guide on that site.

Hope this all helps.

___________________
Rosco

---

### Post by CdM-newb on 2009-07-26
OK THANKS EVERYBODY FOR THE HELP!! I finally had success, in the end I had to use my vista installation dvd and then everything worked as a charm!

---


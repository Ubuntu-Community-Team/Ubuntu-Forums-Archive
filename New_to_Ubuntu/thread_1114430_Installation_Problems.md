---
title: "Installation Problems"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by feral1939 on 2009-04-02
Hi,  I have previously posted my problem with trying to install Ubuntu 8.10 unsuccessfully on my dual HDD Vista computer.  I now have tried to install versions 8.04 and 8.10 on 2 separate occasions and while the installation process has been completed without any dramas, on both occasions (I deleted one B4 trying the other), the dual boot which has been installed does not work on boot-up,the computer boots straight into Vista. The partitions are shown on my D drive on my partition software but not on the Vista piechart for this drive,the partitions are there but only in disk capacities. It seems to me that the installation(s) have disappeared into cyberspace and I am at a loss as to how to get Ubuntu to work and would greatly appreciate some help. Thanks.

---

### Post by pieisgood4589 on 2009-04-02
Does it display the GRUB bootloader, or skip over it?

---

### Post by feral1939 on 2009-04-02
> **pieisgood4589 said:**
> Does it display the GRUB bootloader, or skip over it?

Hi, Thanks for your quick reply.  I watched the progress of the installation and saw that the Grub bootloader was being installed. I hope that this is what you were asking. Thanks.

---

### Post by presence1960 on 2009-04-02
> **feral1939 said:**
> Hi,  I have previously posted my problem with trying to install Ubuntu 8.10 unsuccessfully on my dual HDD Vista computer.  I now have tried to install versions 8.04 and 8.10 on 2 separate occasions and while the installation process has been completed without any dramas, on both occasions (I deleted one B4 trying the other), the dual boot which has been installed does not work on boot-up,the computer boots straight into Vista. The partitions are shown on my D drive on my partition software but not on the Vista piechart for this drive,the partitions are there but only in disk capacities. It seems to me that the installation(s) have disappeared into cyberspace and I am at a loss as to how to get Ubuntu to work and would greatly appreciate some help. Thanks.

Did you install Ubuntu to a different HDD than Vista is installed on? If so you can go into BIOS and set the Ubuntu HDD to boot before the Vista HDD. When I first went to Ubuntu I installed Ubuntu on my second drive and put Grub there. I couldn't get a GRUB menu until I switched the boot priority order in BIOS. Then I got Grub but couldn't get Windows to boot. I had to edit the Windows entry in menu.lst to include map lines. First switch your HDD boot order in BIOS and see if that brings up GRUB. If that works then you can move on to editing your windows entry in menu.lst

P.S. Windows can't natively read Linux partitions.

---

### Post by feral1939 on 2009-04-03
> **presence1960 said:**
> Did you install Ubuntu to a different HDD than Vista is installed on? If so you can go into BIOS and set the Ubuntu HDD to boot before the Vista HDD. When I first went to Ubuntu I installed Ubuntu on my second drive and put Grub there. I couldn't get a GRUB menu until I switched the boot priority order in BIOS. Then I got Grub but couldn't get Windows to boot. I had to edit the Windows entry in menu.lst to include map lines. First switch your HDD boot order in BIOS and see if that brings up GRUB. If that works then you can move on to editing your windows entry in menu.lst

P.S. Windows can't natively read Linux partitions.

Ubuntu was installed on the HDD without Vista - I went into my BIOS and changed the boot order as you suggested but I didn't get Grub when I restarted.  I am at a bit of a loss to know where to go from here and would gladly welcome any suggestions.

---

### Post by jcm1107 on 2009-04-03
when you boot your system up does it say loading grub boot loader, or a similar message? if so hit esc if not then you need to boot from your Ubuntu cd.

---

### Post by feral1939 on 2009-04-03
> **jcm1107 said:**
> when you boot your system up does it say loading grub boot loader, or a similar message? if so hit esc if not then you need to boot from your Ubuntu cd.
No, all I get is the usual bootup into Vista without any other "message".

---

### Post by jcm1107 on 2009-04-03
> **feral1939 said:**
> No, all I get is the usual bootup into Vista without any other "message".

then you need to insert your Ubuntu installation cd and reboot and make sure your system is set to boot from cd drive.

---

### Post by jcm1107 on 2009-04-03
after you do that it should give you the option to recover. If not then I am not sure, because I am new to this too.

---

### Post by jcm1107 on 2009-04-03
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
check out this website after you get into Ubuntu!
let me know if it works for you. This will walk you through getting windows to boot.

---

### Post by feral1939 on 2009-04-03
> **jcm1107 said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
check out this website after you get into Ubuntu!
let me know if it works for you. This will walk you through getting windows to boot.
Thanks but I don't have any problem with Windows - my problem is that after installing Ubuntu and restarting the computer (after removing the disk) it boots into windows without any Ubuntu dual boot windows or any other refrence to Ubuntu.

---

### Post by jcm1107 on 2009-04-03
if the autostart manager does not do it chec out the post grub boot error 18. [http://ubuntuforums.org/showthread.php?t=1111541&highlight=edit+grub](http://ubuntuforums.org/showthread.php?t=1111541&highlight=edit+grub) 

magzee gives detailed insturuction on editing the menu.lst file

---

### Post by jcm1107 on 2009-04-03
ok thats different than my problem, I couldn't get to windows. Ubuntu started automatically.

---

### Post by presence1960 on 2009-04-03
> **feral1939 said:**
> Ubuntu was installed on the HDD without Vista - I went into my BIOS and changed the boot order as you suggested but I didn't get Grub when I restarted.  I am at a bit of a loss to know where to go from here and would gladly welcome any suggestions.

OK, try reinstalling grub using the Live CD. Boot into live CD & follow this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

For #7 I would install grub to the MBR of the HDD set to boot first (Ubuntu). If this works getting the GRUB menu you may still have to edit your menu.lst file to get Vista to boot. But that is a simple matter. Do this first and we'll go from there.

---

### Post by feral1939 on 2009-04-03
> **presence1960 said:**
> OK, try reinstalling grub using the Live CD. Boot into live CD & follow this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

For #7 I would install grub to the MBR of the HDD set to boot first (Ubuntu). If this works getting the GRUB menu you may still have to edit your menu.lst file to get Vista to boot. But that is a simple matter. Do this first and we'll go from there.
Thanks for all your help everyone.  I have finally got Ubuntu up and working. Cheers.

---

### Post by presence1960 on 2009-04-03
No problem, we are glad you are up & running. Remember to return the favor in kind to someone else looking for help!

P.S. you might want to edit the title of your thread to include [solved].

---


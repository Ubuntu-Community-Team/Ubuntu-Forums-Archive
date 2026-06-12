---
title: "Help install Ubuntu on my 2nd HDD"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by coolranch on 2009-06-27
Hello, I have 2 HDD. One that contains my Windows Vista setup on a 500gb drive. 
My other is ATA which is 80gb. which is ran off my VIA VT6421 IDE raid controller. (originally got that card for my xbox 360) now I use it to connect my non Sata drives. 
Anyways I turn off my computer unplug the Sata drive that contains Vista boot up Ubuntu from the CD Rom drive. And install Ubuntu onto my 80GB hard drive. After I install it, says to take out the cd and restart so I do. The computer starts back up still with the Sata Drive unpluged and It goes to a scree with Intel (r) Boot Agent PXE base code Pxe - 2.1 build 085 and something about a Mac Address and ... / (that spins)  so I am confused. Turned off the computer put back in the CD Ubuntu loads and I can see in the drive area that it sees my HDD 80gb with Ubuntu installed onto it.   

SO I turned off computer again, pressed F2 to load into BioS and I was looking for boot order or some sign of the HDD but where it shows for Hard disk drives says None and boot options there were 4 2 which were my CD drives, 1 that was for a Floppy drive whcih i dont have and 1 other with a bunch of wierd letters and numbers i figured it was for my VIA VT6421 card so i put that to load first and still nothing changed. I can not figure out why It will not load Ubuntu when it is the only HDD connected. If i plug back up the Vista Drive it just loads into windows vista.

Here is the Card that i'm using [http://tekgems.com/Products/la-pci22-vt6421a.htm](http://tekgems.com/Products/la-pci22-vt6421a.htm)

here is little info on my computer

Windows Vista Home Premium
System: Gateway
Model Gm5626
Processor:  Intel(R) Pentium(R) Dual CPU E2180 @ 2.00 Ghz 2.00Ghz
Memory(RAM)  4.00GB
System Type:    32-BiT OS


Thanks for any help.

---

### Post by LewRockwell on 2009-06-27
> **coolranch said:**
> Hello, I have 2 HDD. One that contains my Windows Vista setup on a 500gb drive. 
My other is ATA which is 80gb. which is ran off my VIA VT6421 IDE raid controller. (originally got that card for my xbox 360) now I use it to connect my non Sata drives.
Anyways I turn off my computer unplug the Sata drive that contains Vista boot up Ubuntu from the CD Rom drive. And install Ubuntu onto my 80GB hard drive. After I install it, says to take out the cd and restart so I do. The computer starts back up still with the Sata Drive unpluged and It goes to a screen with Intel (r) Boot Agent PXE base code Pxe - 2.1 build 085 and something about a Mac Address and ... / (that spins)  so I am confused. Turned off the computer put back in the CD Ubuntu loads and I can see in the drive area that it sees my HDD 80gb with Ubuntu installed onto it.

the "spinner" was telling you that the install was finishing up after you rebooted(so you probably caused a fault/halt in the finalizing of the install)

> **coolranch said:**
> 
SO I turned off computer again, pressed F2 to load into BioS and I was looking for boot order or some sign of the HDD but where it shows for Hard disk drives says None

BIOS will "see" bootable devices directly connected to the motherboard like hard drives, optical drives, USB drives, and/or network cards(for network booting)

your 80GB drive is connected via your controller card which the BIOS probably isn't negotiating

> **coolranch said:**
> 
and boot options there were 4 2 which were my CD drives, 1 that was for a Floppy drive whcih i dont have and 1 other with a bunch of wierd letters and numbers i figured it was for my VIA VT6421 card so i put that to load first and still nothing changed. I can not figure out why It will not load Ubuntu when it is the only HDD connected. If i plug back up the Vista Drive it just loads into windows vista.

I think you'll need to reinstall and let it finish thoroughly after the reboot

.

---

### Post by -kg- on 2009-06-27
I'm a bit confused by your description and your setup, but I am assuming that you are wanting to dual-boot Vista and Ubuntu.

Since you are unable to boot to your ATA (hooked to a RAID controller card for a non-SATA drive?) hard drive, and since you want to dual boot anyway, you will need to install Ubuntu to your secondary hard drive _with your Vista drive connected._  Since you are only able to boot to the drive with Vista installed on it (assumably it is a SATA card that is bootable by your system), and since you want to dual-boot you will need GRUB (the Grand Unified Boot Loader) installed on that drive.

You should be able to install GRUB on the drive using the instructions on the following page:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck]("http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck")

<edit> Beat to it again.  Yes, reinstallation is another (and probably easier) way to do it, especially since it's a fresh install, anyway.  Just make sure that this time you leave your Vista drive connected so that GRUB can install into the MBR of that drive.

---

### Post by coolranch on 2009-07-01
Sorry for the late replay, been away. Anyways  

I did the reinstall with both drives hooked up and did a full install onto the 83 gb HDD not to touch my Vista 500 gb drive.

SO did that restarted the computer and it loads and I get this ...

Grub loading stage 1.5
grub loading, please wait ... Error 21

so then the only thing i could do was restart.

unhooked the 83 gb HDD and tried to just load back into vista same thing.

Hooked back up the 83 GB HDD and loaded back into Ubuntu Via the CD

and now im talking to you guys from the cd live and i can not load back into my vista im lost any help?

---

### Post by cjv8888 on 2009-07-01
Have you tried changing the boot order of the HDs in the BIOS ?

---

### Post by coolranch on 2009-07-01
So in my BioS it lists my 500gb HDD as my only HDD.

This is really tickin me off. Is there a way i can just restore the original boot so I can atleast get back into Vista

---

### Post by cjv8888 on 2009-07-01
To get back into Vista, you can put the Vista rescue disk in and do a fixmbr or whatever it is in Vista.

But before you do that, we can try to find Grub and create a dual boot.
Try opening a terminal in the live CD and type:

```
sudo grub
```

then 

```
find /boot/grub/stage1
```

---

### Post by coolranch on 2009-07-01
ok i did what you said and it says...

(hd1,0)








**Restoring the Master Boot Record**

 In order to stop the computer from looking for the option to boot Ubuntu on startup, the Master Boot Record (MBR) must be reset to its original condition.
 
[LIST]
[*]A user should restart the computer, booting first from CD. To boot from CD instead of the hard drive, a user needs to access the BIOS settings, in the same way done to [first install Ubuntu]("http://computersoftware.suite101.com/article.cfm/dualboot_ubuntu_on_vista").
[*]With BIOS settings properly reset, insert the Vista Recovery Disk into the CD drive and press a key, when prompted, to boot the recovery manager.
[*]A user needs to select a language, time, currency, and input method to continue.
[*]On the next screen, rather than clicking the large "Install Now," a user should look below for the option "Repair your computer."
[*]Clicking on the Microsoft Windows Vista drive (most likely drive C) will allow a user to access system recovery options. Then, opening Command Prompt will give a user the opportunity to type in this line:
[/LIST]
Bootrec.exe /FixMbr
[LEFT][COLOR=#000000]
[http://computersoftware.suite101.com/article.cfm/undo_ubuntu_dualboot_for_vista#ixzz0K0YSIsR6&D](http://computersoftware.suite101.com/article.cfm/undo_ubuntu_dualboot_for_vista#ixzz0K0YSIsR6&D)
[/COLOR][/LEFT]

---

### Post by cjv8888 on 2009-07-01
try typing into the terminal the following, line by line

```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```

---

### Post by coolranch on 2009-07-01
Ok did that

---

### Post by cjv8888 on 2009-07-01
Have you tried re-booting to see if you can boot into Ubuntu and Vista?

---

### Post by coolranch on 2009-07-01
No was waiting to see if i needed to do anything else. I will do that right now.

---

### Post by coolranch on 2009-07-01
ok so went to a mac adress followed by ... / ( that spun) then it said " no boot filename recieved"


Grub loading Error 21

---

### Post by coolranch on 2009-07-01
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa38ec07c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1315    10562706    7  HPFS/NTFS
/dev/sda2   *        1316       60802   477820928    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb3a2b3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9598    77095903+  83  Linux
/dev/sdb2            9599       10011     3317422+   5  Extended
/dev/sdb5            9599       10011     3317391   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# 



if this helps idk.

---

### Post by cjv8888 on 2009-07-01
Hmmm, I think the problem is due to the VIA VT6421 IDE raid controller and the BIOS not recognising the existence of the IDE drive.  Have you tried going into the BIOS to see if you can find the drive there anywhere?


Perhaps someone more experienced in the use of these raid controller can come along to guide you.

If not, you can always fixmbr with the Vista rescue disk  and get back into Vista for now.

---

### Post by coolranch on 2009-07-01
ya i have looked i dont think my BiOS recognises it im going to try and get it back to just vista. Thanks anyways.

---

### Post by presence1960 on 2009-07-01
> **cjv8888 said:**
> Hmmm, I think the problem is due to the VIA VT6421 IDE raid controller and the BIOS not recognising the existence of the IDE drive.  Have you tried going into the BIOS to see if you can find the drive there anywhere?


Perhaps someone more experienced in the use of these raid controller can come along to guide you.

If not, you can always fixmbr with the Vista rescue disk  and get back into Vista for now.

I know this isn't what you are looking to hear, but why don't you plug the hard drive into the IDE socket on the motherboard and you won't have this problem. Then BIOS will detect the drive,. probably as long as you have it into that card you may continue to have this problem. If you only have one IDE socket on your mobo then invest a few bucks on a dual hook up cable and put you Ubuntu hard disk as master & assuming your optical drive is IDE as slave.

---

### Post by coolranch on 2009-07-01
Just thought i'd let you know that i got back into vista with the  restore MBR from vista cd.

Also it seems that I only have 1 slot on my mobo for that type of connector which is connected to my 2 dvd rw drives. I will look into something for it to try and get this duel bootingl. it has been a long night lol I was worried that I wouldnt make it back into vista. Ubuntu is just somethign new that I wanted to pick up and if i need spend a few bucks no problem. Anyways thanks for the help everyone.  

o.h ps
 
once i get this  working is it possible to duel boot and have 2 OS running at the same time? on same monitor or on 2 monitors idk. I guess Ill search the internet or something. haha anyways thanks again have a good night / day w.e :)

---

### Post by presence1960 on 2009-07-01
> **coolranch said:**
> Just thought i'd let you know that i got back into vista with the  restore MBR from vista cd.

Also it seems that I only have 1 slot on my mobo for that type of connector which is connected to my 2 dvd rw drives. I will look into something for it to try and get this duel bootingl. it has been a long night lol I was worried that I wouldnt make it back into vista. Ubuntu is just somethign new that I wanted to pick up and if i need spend a few bucks no problem. Anyways thanks for the help everyone.  

o.h ps
 
once i get this  working is it possible to duel boot and have 2 OS running at the same time? on same monitor or on 2 monitors idk. I guess Ill search the internet or something. haha anyways thanks again have a good night / day w.e :)

why don't you switch the hard disk as I said and put the one DVD-RW drive into the controller card. That will cost $0.

---

### Post by raymondh on 2009-07-01
> **coolranch said:**
>  
once i get this  working is it possible to duel boot and have 2 OS running at the same time? 

Virtualization

---

### Post by cjv8888 on 2009-07-01
Yes, as Presence1960 suggests, you can put 1 of the DVD drives into the raid controller and put the IDE HD directly into the MB.  If there is boot error, just post back and it should be reasonably easy to get the dual boot going.;)

---

### Post by coolranch on 2009-08-18
Sorry about the long wait, been real busy, anyways just thought I would let everyone know that I did get it to work finally by swapping the dvd drives and connecting the HDD to mobo. Thanks again for the help.

---

### Post by presence1960 on 2009-08-18
> **coolranch said:**
> Sorry about the long wait, been real busy, anyways just thought I would let everyone know that I did get it to work finally by swapping the dvd drives and connecting the HDD to mobo. Thanks again for the help.

Glad you got it working! Enjoy ubuntu.

---


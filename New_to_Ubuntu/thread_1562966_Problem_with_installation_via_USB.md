---
title: "Problem with installation via USB"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by Valeralol on 2010-08-28
Hello all,I'm new for Linux andd Ubuntu.Today I downloaded last Ubuntu 10 dist and trying to burn it on my flash(i have no dvd drive =( )using programm in documentation (Universal USB Installer).But while booting error happens.I tried several else programms but the result was the same.I never face with booting via USB before.Can you recommend me some utilities or programms?

---

### Post by USB_NL on 2010-08-28
I think you must be more specific.
what are the problems exacly?

---

### Post by Valeralol on 2010-08-28
I can't install Ubuntu)Installer doesn't load after POST.

---

### Post by USB_NL on 2010-08-28
what are you using now Windows xp?

---

### Post by USB_NL on 2010-08-28
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

This site i used the first time for usb do you know it?

---

### Post by USB_NL on 2010-08-28
Here is the official 1 2 3 step guide
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by USB_NL on 2010-08-28
> **USB_NL said:**
> Here is the official 1 2 3 step guide
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Click on SHOW ME at step 2 have seen that?

---

### Post by USB_NL on 2010-08-28
That universal USB installer is for windows ok so i asume you have that

do you know that you also need to look at your BIOS at start up and enable booting from USB ?

or

select bootmenu if possible 

that depends on your PC

---

### Post by Valeralol on 2010-08-28
BIOS USB Booting is enabled.
All that you have written i have done.

---

### Post by USB_NL on 2010-08-28
sometimes a boot stops in the textinterface then try 

```
startx
```

to start the x windows server (the graphical interface)

---

### Post by Valeralol on 2010-08-28
After BIOS' POST there is a "Boot Error" Mesage.This is my main problem.I can't even reach some shell or interface.

---

### Post by SteveNorman on 2010-08-28
did you get to this screen at all?


[http://www.tuxation.com/tutorials/linux-dualboot/step0.png](http://www.tuxation.com/tutorials/linux-dualboot/step0.png)

---

### Post by Valeralol on 2010-08-28
No(As I've alreadt writen I have an error after the BIOS' test.Ubuntu loader even doesn't appear.

---

### Post by SteveNorman on 2010-08-28
clear your usb stick, reformat and start over from square one. also you may have to redownload ubuntu again.

---

### Post by Valeralol on 2010-08-28
Okay,I'll try it.

---

### Post by SteveNorman on 2010-08-28
to check that you have a good download of ubuntu do this
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

---

### Post by Valeralol on 2010-08-28
Sometimes another mistake occurs.After BIOS' tests next screen appears: "SYSLINUX 3.86 2010-04-1 EBIOS.....
         No DEFAULT or UI configuration derective found!
         boot: "
Also i noticed that on my USB boot flash all volume concentrated in one file "filesystem.squashfs" (~670MB) Is it OK?

---

### Post by SteveNorman on 2010-08-28
i think the filesystem.squashfs is just a format for read only files. I think the problem is somewhere in the process of copying the os to the usb stick. what process are you using to load yous usb stick? I use a utility called unetbooten

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

your error message is unfamiliar to me btw

---

### Post by Valeralol on 2010-08-29
I have redownloaded disrt(ubuntu desktop),reformated flash drive.All is the same.It's seems i have to forget about using Ubuntu =)

---

### Post by SteveNorman on 2010-08-29
wat computer? if it is an aspire one or eee try kuki linux. built just for those machines.


[http://www.kuki.me/](http://www.kuki.me/)

---

### Post by xutre on 2010-09-03
Sometimes I find that the USB is not made bootable properly by syslinux. Also, first check that the fat partition on the usb has the "bootable" flag set. Some fat filesystems work better than others eg the usual fat32 (vfat) works most times, but if not, try fat16 (older format). The quickest way that I've found to create a bootable USB when I've had problems with some USB drives (note, some USB flashdisks just do not boot, period (see below)), is to download puppylinux (currently lupe5.01, I think), find a PC you can burn to a cd so that you can boot from that cd, use the puppy installer to install puppy to the usb, and follow the detailed prompts. After that, I boot from the flashdrive into puppy to verify that it is indeed, bootable. Then I delete all the puppy installed files, and use unetbootin, to prepare the ubuntu bootable flashdrive. Thereafter, it works every time I update the version. I've now learned to only buy good flashdrives with lifetime warrantys eg Transcend, Kingston, etc.

---


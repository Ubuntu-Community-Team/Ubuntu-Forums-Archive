---
title: "absolute a newbie - couldn't install"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by joelee2000 on 2010-06-20
I downloaded 32-bit Ubuntu Desktop Edition, the file name is "ubuntu-10.04-desktop-i386.iso" and burned it to a CD, but my desktop doesn't restart from that CD, I checked the files in the root directory, there are 5 of them:
autorun.inf
md5sum.txt
README.diskdefines
ubuntu
wubi.exe

I don't see any bootup files like: IO.sys or MSDOS.sys etc. did I do anything wrong?

Thanks

Tony

---

### Post by Temposs on 2010-06-20
Did you set your BIOS boot order so that the CD-ROM boots before the hard drive?

---

### Post by Ariakkas on 2010-06-20
2 things off the top of my head....

did you burn the iso as an image? you need to specifically burn it as an image to make it bootable.

second, you may have to change the boot order of your pc to having it look to the cdrom to boot

---

### Post by JK3mp on 2010-06-20
If your able to open & view files u may not have burned it as an image. Burn it as an image and if it still boots windows I would check your boot menu in BIOS (Hit F10 or F12 or w/e on start, varys from diffrent MOBO manufacturers)

---

### Post by Ariakkas on 2010-06-20
in case you dont know how to burn an image, some burner software wont do it. in windows i use infrarecorder.

google it, download it, open it.

click on the actions pull down, select burn image.

navigate to the iso you downloaded, and select it.

often times i leave the burn speed at max, but it can cause problems sometimes. ymmv

when it is done, pop it in or reboot and it should work

---

### Post by joelee2000 on 2010-06-20
Thanks guys for answering my questions.
I believe I burned the CD as image, and set BIOS to boot from CD too.

I googled my problem, and stumbled across this site:
[http://cdimage.ubuntu.com/daily-live/20100620/](http://cdimage.ubuntu.com/daily-live/20100620/)

I downloaded another file "maverick-desktop-i386.iso" and this time it boots, but after 3-4 minutes, I got some messages:

--------------------------------------------------------------
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

--------------------------------------------------------------

Now I am totally lost :)

---

### Post by oldos2er on 2010-06-20
Maverick is alpha software, which I wouldn't recommend to someone new to Linux.

Did you check md5sum on the 10.04 disk you burned? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---


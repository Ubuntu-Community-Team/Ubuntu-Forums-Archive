---
title: "GRUB errors!"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by linuxdualbooter on 2009-06-16
Ok, I recently deleted the ubuntu partition and GRUB because I needed more disk space and because GRUB wouldn't load Vista.
I expected Vista to load automatically because it's the only OS on the computer. However, when I loaded it, It showed GRUB error 22, which I have faced down before.
But this time I'm stuck between a wall and a hard place: error 22 or error 12. Please Help!

---

### Post by gn2 on 2009-06-16
You have removed the partition which contains the files Grub needs to boot the installed operating systems.

You need to reinstate the Vista bootloader, this can be done with a Vista Recovery CD which you can download from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

### Post by linuxdualbooter on 2009-06-16
Is there anyway to extract the files w/out burning the CD? I'm using the ubuntu LiveCD but it only has 8.04.

EDIT: Could I use the Recovery partition that the computer came with?
EDIT2: Do I boot on the DVD?

---

### Post by gn2 on 2009-06-16
The simplest way to fix your problem is to create a bootable CD from the download I linked to earlier.
This is done in the same way as creating a Linux Live CD, i.e. burn as image using the likes of ImgBurn in Windows or Brasero in Ubuntu.
The downloadable Vista recovery CD is capable of reinstalling the Vista bootloader on the hard drive's MBR, overwriting the remnants of Grub.

Your hard drive recovery partition can only re-install the entire OS and you will lose everything that's on it if you do.

Another way to fix it is to just re-install Ubuntu but if you want to get some space back do it into a smaller partition than you had previously, 5gb should be enough.

---

### Post by linuxdualbooter on 2009-06-16
OK, I burned the Image. Now what? 
Do I boot into it?

EDIT: I seem to not be albe to boot into the DVD.

---

### Post by linuxdualbooter on 2009-06-16
> **gn2 said:**
> 
Another way to fix it is to just re-install Ubuntu but if you want to get some space back do it into a smaller partition than you had previously, 5gb should be enough.

That's where the other part comes in. If I get GRUB back, and I try to load Vista, it'll show error 12.

---

### Post by Steelmourne on 2009-06-17
When you boot the dvd a menu should be brought up with an option to restore the MBR, assuming your BIOS is set to boot from the dvd drive.

---

### Post by Gone fishing on 2009-06-17
Start up on the Vista install disk and go to the repair console
and type Bootrec.exe /FixMbr.

That will remove grub from the mbr and return it to standard.

However, the idea of choosing to use vista .... ughh

---

### Post by gn2 on 2009-06-17
> **linuxdualbooter said:**
> That's where the other part comes in. If I get GRUB back, and I try to load Vista, it'll show error 12.

In which case if you don't have a Vista Installation DVD, you'll need the Vista Recovery CD I linked to previously so that you can run fixboot.

---

### Post by sahabcse on 2009-06-17
For Fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by linuxdualbooter on 2009-06-19
OK. I tried to boot from the CD, but it turns out I didn't burn anything onto it. So, I tried to download it onto my laptop to burn onto a CD. But for some reason, it says I'm connected onto the internet, but when I try to load the page, it says I'm NOT connected. Still, I'm booting of a .Live CD.
I'll be back in a sec. I'm gonna reinstall ubuntu.

EDIT: Apparently, the partioner on the LiveCD doesn't work, so I can't create a ubuntu partition....
this sucks...........

---

### Post by linuxdualbooter on 2009-06-19
> **Gone fishing said:**
> Start up on the Vista install disk and go to the repair console
and type Bootrec.exe /FixMbr.

That will remove grub from the mbr and return it to standard.

However, the idea of choosing to use vista .... ughh

Sorry, I have a lot of old files that I still need. I can access from LiveCD, but somethings don't appear.

---


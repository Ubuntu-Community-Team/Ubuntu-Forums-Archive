---
title: "problem installing ubuntu server"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Warpedflash on 2009-10-27
i have having problems installing ubuntu on the following machiine

Transmeta Crusoe CPU 500 MHz
60GB HDD
64MB ram (soldered/not upgradeable)

i can boot the installer and pick language/keymap
scanning my hardware
scanning CD-ROM
loads additioonal components
But at the stage "retreiveing partman base" it goes nuts and teh console starts flashing black tehn white over and over! any ideas?

the CD Drive is a usb one is that matters...
thanks,
Warpedflash

---

### Post by yeats on 2009-10-27
> But at the stage "retreiveing partman base" it goes nuts and teh console starts flashing black tehn white over and over! any ideas?

When you downloaded the disk image, did you check it with [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?  Have you run the "Check CD for Defects" tool from the installation CD menu?

---

### Post by Warpedflash on 2009-10-27
> **chrissharp123 said:**
> When you downloaded the disk image, did you check it with [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?  Have you run the "Check CD for Defects" tool from the installation CD menu?

yea i ran teh check and it passed. i think its running out of ram so i am using puppy linux to set up a swap partition

---

### Post by yeats on 2009-10-28
> 64MB ram 

Funny - when I read that, I saw "64 bit" instead.  Yes - the RAM is the problem :-).

---

### Post by egalvan on 2009-10-28
Go to this page.

[http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.04](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs/9.04)

It starts out with this...

[I]Ubuntu 9.04 Server Edition (Jaunty Jackalope)

Ubuntu Server Edition is meant to run on any Intel or AMD x86, AMD_64, EM_64T processors.
 [COLOR="Red"]It requires a minimum of 192Mb of RAM [/COLOR]and 1Gb of disk space.
 Depending on your needs, you might manage with less than this.
 However, most users risk being frustrated if they ignore these suggestions. [/I]


Note that 8.04 Server requires less at 128MB, so maybe this would be a better fit.

In this day and age, it's very difficult to find Linux distro that will run well in 64M.
Sad.

Even Puppy is only happy once you give it 256MB



There is one called TinyCore Linux, that is an 11MB download.
Give a look. 11MB doesn't take long :o

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

or try their smallest offering...
[I]Also offered is Micro Core a 6 MB image that is the console based engine of Tiny Core.
 CLI versions of Tiny Core's program allows the same functionality of Tiny Core's extensions only starting with a console based system.[/I]

---


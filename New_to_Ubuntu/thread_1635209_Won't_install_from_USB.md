---
title: "Won't install from USB"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Katana24 on 2010-12-01
Hi - i just finished creating a bootable USB drive with Ubuntu on it. When I put it into my desktop computer i can try Ubuntu fine - except the fact that I cannot connect to my wireless network even though the password is correct! but when I click on "Install Ubuntu" it fails. 

It gets to the stage where I create a username and password - and tells me that there may be something wrong with the CD/DVD drive (cant be because the computer doesn't have a CD/DVD drive) or the hard drive is faulty. So does this mean I have to buy a new hard drive?

Unet gave me an option of scanning the disc for errors - which i did and it said there was one if this helps.

Anyone?

---

### Post by sikander3786 on 2010-12-01
> Unet gave me an option of scanning the disc for errors - which i did and it said there was one if this helps.

Do you mean to say that there is an error on the installation media i.e, USB in this case?

Anyways, I would recommend to check the MD5SUM of downloaded image at first.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn it to a usb again. Format the USB (FAT32) and try unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Please let us know about your progress :-)

---

### Post by Katana24 on 2010-12-01
Hello - i ran the appropriate command on my mac on the downloaded version of the Ubuntu and I checked the Ubuntu website which said this:

 59d15a16ce90c8ee97fa7c211b7673a8 
    ubuntu-10.10-desktop-i386.iso 



The hash number that I got back was: 



openssl md5 ubuntu.iso
MD5(ubuntu.iso)= [COLOR=Red]2541e9a65e8062e7fb7751b8894a74bd[/COLOR]


[COLOR=Black]I actually though that maybe one number or something would be wrong, clearly not. I also checked it against the other numbers too and it didn't match any of those numbers either. 
[/COLOR]


As regards to the reformatting issue - would that be needed?  Its already formatted to FAT-32, why reformat it? I'm going to re-download the same version of Ubuntu and run the same code in the terminal. 



I'll keep you posted :D

---

### Post by NCLI on 2010-12-01
> **Katana24 said:**
> Hello - i ran the appropriate command on my mac on the downloaded version of the Ubuntu and I checked the Ubuntu website which said this:

 59d15a16ce90c8ee97fa7c211b7673a8 
    ubuntu-10.10-desktop-i386.iso 



The hash number that I got back was: 



openssl md5 ubuntu.iso
MD5(ubuntu.iso)= [COLOR=Red]2541e9a65e8062e7fb7751b8894a74bd[/COLOR]


[COLOR=Black]I actually though that maybe one number or something would be wrong, clearly not. I also checked it against the other numbers too and it didn't match any of those numbers either. 
[/COLOR]


As regards to the reformatting issue - would that be needed?  Its already formatted to FAT-32, why reformat it? I'm going to re-download the same version of Ubuntu and run the same code in the terminal. 



I'll keep you posted :D
If the md5 doesn't match, it means that your download has been corrupted somehow. Try downloading the iso again :)

---

### Post by Katana24 on 2010-12-01
Hello -  i sorted the problem - my version was corrupted and not its working 
Cheers guys

---


---
title: "Not able to install ubuntu with my flash drive"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by 1ktmeadows on 2011-08-11
Im trying to install ubuntu 11.04 onto my other laptop but my laptop cd/dvd drive isn't working so Im trying to install Ubuntu with a flash drive. I have done all of theses steps 
1. downloaded Ubuntu 11.04 
2. Burned it to a disc
3. Formated my 2GB flash drive 
4. Went to 'usb-creator' on Ubuntu disc and run executable file
and I selected 'discarded on shutdown, 
5. Then I click on MAKE START UP DISK
6. Once completed, I put the flash drive  into my laptop and then I booted from USB
After I do all of those steps right after the toshiba logo shows my computer only shows " SYSLINUX 3.82 2009-06-09 EBIOS Copyright (Cc) 1994-2009 H. Peter Anvin et al" and it does not do anything else, it just stays there on my screen. Im not sure what to do, can anyone help me. What did I do wrong

---

### Post by fslezak on 2011-08-11
Try pressing any key :P
Or the RETURN key.

Also, check your MD5 for the ISO. Maybe the ISO is corrupt. Run in terminal:

```
 md5 
```After the MD5 command, drag and drop your ISO file into the Terminal, then press Return.

Compare the result with these codes:
Alternate:
     ```
AMD64: 8468300a61ea1e3b7607f46f7643b57a
i386: e6a29ce3dccb0ab12332036dcff7d9e4
```Desktop:
     ```
AMD64: 7de611b50c283c1755b4007a4feb0379
i386: 8b1085bed498b82ef1485ef19074c281
```Server:
     ```
AMD64: 355ca2417522cb4a77e0295bf45c5cd5
i386: b1a479c6593a90029414d201cb83a9cc
```Sorry for the length, but every letter counts!!!

---

### Post by Hakunka-Matata on 2011-08-11
For burning .iso to USB, I've found unetbootin to be very reliable.  Since 11.04, while the program is unpacking file #11, it takes a long time, maybe a minute or more, don't worry, if you're watching it do it's thing, just wait.
 Download link in my signature:  

to check the md5sum (in this example the downloaded .iso is in my Downloads directory, hence the cd command to start with)

```
das@Backoffice-10:~$ cd Downloads
das@Backoffice-10:~/Downloads$ md5sum  ubuntu-11.04-alternate-i386.iso
e6a29ce3dccb0ab12332036dcff7d9e4  ubuntu-11.04-alternate-i386.iso
das@Backoffice-10:~/Downloads$ 


```check the hash generated against your downloads hash, which can be found @ [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

**EDIT:  **I just checked the unetbootin download and find they have a new version, which is not marked 'executable' by default.  So after downloading the file you must right-cliq on it, select 'properties', 'permissions', then tick the "Allow executing file as program" box.

---

### Post by 1ktmeadows on 2011-08-12
I want to first say thank you for writing back, The thing is that Im trying to install ubuntu 11.04 onto my Windows 7 laptop. So do I follow these instructions under the command prompt in Windows. I have also tried [http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/) instructions, I got to the screen where I can install ubuntu but when I install it to the hard drive I still get an error. It will start to load and then numbers starting going down the screen and the alot of information will start going down the screen and then it stops and those nothing. When looking at the words there is something saying that it can not find something in the root. Im not sure what that means and Im not sure what to do.

---

### Post by Hakunka-Matata on 2011-08-12
Maybe your Ubuntu usb stick is good, you may have a partition issue if Windows 7 was pre-installed on your laptop.  The commands I list are to be used in an Ubuntu terminal, yes.  Can you run Ubuntu by selecting "try Ubuntu without installing" from your usb LiveCD?  Do you get a menu if you boot from the USB?

---

### Post by 1ktmeadows on 2011-08-12
Yes, they are install from usb, install to hard drive, install from hard disk, and help. Thats what I get when I turn on the computer with the usb.

---

### Post by Hakunka-Matata on 2011-08-12
you don't get a "try Ubuntu without installing" option"?

---

### Post by wojox on 2011-08-12
> **Hakunka-Matata said:**
> For burning .iso to USB, I've found unetbootin to be very reliable.

Yes. Unetbootin even lets you great persistence.

---

### Post by 1ktmeadows on 2011-08-12
Ok I will try buying a new flash drive because i read that sandisk flash drive have issues with ubuntu 11.04 and i will try Unetbootin and see what happens. Me and my dad have been trying to get ubuntu onto my newer computer. We have spent six hours trying to get ubuntu 11.04 onto my windows 7 laptop, we tried everything that we can think of. So Im wondering if anyone can give me detailed instructions on installing ubuntu 11.04 onto a windows 7 laptop without a cd drive, if possible?

---

### Post by robgraves on 2011-08-12
> **1ktmeadows said:**
> Ok I will try buying a new flash drive because i read that sandisk flash drive have issues with ubuntu 11.04 and i will try Unetbootin and see what happens. Me and my dad have been trying to get ubuntu onto my newer computer. We have spent six hours trying to get ubuntu 11.04 onto my windows 7 laptop, we tried everything that we can think of. So Im wondering if anyone can give me detailed instructions on installing ubuntu 11.04 onto a windows 7 laptop without a cd drive, if possible?

are you trying to install it as a dual boot, both windows and ubuntu, or overtop of windows?

if it's on a laptop then you probably only have one hard drive, so if you're dual booting you will have to shrink the windows partition, i also would advise using unetbootin downloade it here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) , you will also need to download ubuntu, you can actually do this from within unetbootin OR from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) to get the .iso file which is an image which can be burned to a cd or to a USB using unetbootin, once you have the ubuntu iso and unetbootin installed, you can plug in your usb stick and run unetbootin and select from image and select where your iso file is located and the drive that your USB stick is and let it put the image on the USb as a bootable USB, to shrink the windows partition you have to go into windows and click on Start and then type in disk management, and open the disk management program in windows and then click on the c:\ drive and right click and select shrink volume, however i should add you should clean up any unneccesary files and do a disk defragment before doing this and back up any important data, windows will then allow you to shrink it's partition and free up some space, you will also have to go into BIOS when you reboot and make sure that the USB drive is set BEFORE the hard drive in the boot order.

---


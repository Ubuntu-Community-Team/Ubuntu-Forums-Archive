---
title: "ubuntu on a 512mb flash drive"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by gridd on 2010-04-20
hi is there an ubuntu image that would fit onto a 512mb flash drive and how would i do it to run on win 7 without a full install,
thanks

---

### Post by -humanaut- on 2010-04-20
Thats to small, you need atleast 1gb for most SSD's the iso images are bigger than the capacity alone

---

### Post by e4uforums on 2010-04-20
By default, no.  However, the beauty of open source software is you can modify it to suit your needs.

This thread here walks you through "remastering" your own Ubuntu.  If you stripped out additional software you may be able to get an image down under 500MB.

[http://ubuntuforums.org/showthread.php?t=869659](http://ubuntuforums.org/showthread.php?t=869659)

---

### Post by gridd on 2010-04-20
ok I have obtained a 4gb flash drive I'm afraid I'm nowhere near the level of stripping down programs yet.
and I wouldnt want to lose out anyway.

do I need to format the drive at all I've only got windows 7 at the moment.

---

### Post by achase79 on 2010-04-20
[unetbootin.sourceforge.net]("unetbootin.sourceforge.net")
this should give you the correct program to set it up and answer most of your questions

---

### Post by Sef on 2010-04-20
>  do I need to format the drive at all I've only got windows 7 at the  moment.If you run it as a live usb, no.  

If you want to install it, then yes, you would need to format it the hard disk.

What do you want to do?

Note: If you have not run the live usb, then run it first for a while.  Make sure that Ubuntu works with your system.

[> ]("http://unetbootin.sourceforge.com/")[unetbootin.sourceforge.com]("http://unetbootin.sourceforge.com/")
this should give you the correct program to set it up and answer most of  your questions

First, find out if the OP wants to install it or run it as a live usb.

---

### Post by RedRat on 2010-04-20
I have a question in regard to trying to load Ubuntu on a usb drive that is 16GB. I run 8.04 and when I try to start usb-creator and point to the iso file on my hard drive, the program just sits there and does not appear to do anything. Is this a fault of the usb-creator program? It is in 8.04 repos and latest version. Does the program have to sit and cogitate for some time?

---

### Post by dwarfolo on 2010-04-20
I've managed to use the usb-creator tool under System->Administration on a SD flash card (8GB). It booted Live a netbook and installed Karmic on a laptop.

---

### Post by gridd on 2010-04-20
> **achase79 said:**
> [unetbootin.sourceforge.net]("unetbootin.sourceforge.net")
this should give you the correct program to set it up and answer most of your questions

thanks for that, before I go I've copied an iso live 8.10 HH base but the windows f2 boot sequence will not boot it gives 7 options 3 or 4 for usb

but none of them work usb 2 generic
---------------------usb ffd
---------------------usb key
---------------------usb cd/dvd

which one should work?

---

### Post by chrisxuk on 2010-04-20
> **gridd said:**
> ok I have obtained a 4gb flash drive I'm afraid I'm nowhere near the level of stripping down programs yet.
and I wouldnt want to lose out anyway.

do I need to format the drive at all I've only got windows 7 at the moment.

Have a go at running a live CD. You get the option to do so when you boot the pen drive. 

If you didn't know, booting to a Live CD would allow you to try out an alternate operating systems without making changes to the computer’s existing OS, hard drives or files.

---

### Post by WinterRain on 2010-04-20
> **RedRat said:**
> I have a question in regard to trying to load Ubuntu on a usb drive that is 16GB. I run 8.04 and when I try to start usb-creator and point to the iso file on my hard drive, the program just sits there and does not appear to do anything. Is this a fault of the usb-creator program? It is in 8.04 repos and latest version. Does the program have to sit and cogitate for some time?

Usually, you will see 2 listings for your usb drive. Try highlighting the other choice and see if it makes a difference.

---

### Post by linuxman94 on 2010-04-20
Use unetbootin to make  your drive able to boot Ubuntu.

1. Download the program at [unetbootin.sourceforge.net]("unetbootin.sourceforge.net")

2. Make sure your USB drive is blank and run the program. Select the option for disk image and direct it to the ISO you downloaded.

3. Select USB drive and choose your USB drive letter then click OK.  When it is done, reboot and use the USB key option.

---

### Post by RedRat on 2010-04-20
> **linuxman94 said:**
> Use unetbootin to make  your drive able to boot Ubuntu.

1. Download the program at [unetbootin.sourceforge.net]("http://unetbootin.sourceforge.net")

2. Make sure your USB drive is blank and run the program. Select the option for disk image and direct it to the ISO you downloaded.

3. Select USB drive and choose your USB drive letter then click OK.  When it is done, reboot and use the USB key option.

OK, I think part of my problem is that this usb drive is a Maxell, which is Linux compatible, but it appears to have three files that are locked, I think it is a locked partition that contains its own file browser. I have not been able to change the permissions from within Ubuntu. any suggestions??

I even tried "sudo nautilus" and still could not change the files. Clearly there are two partitions on the thumb drive. The small one contains the file browser, an icon, and an autorun.inf file. These and the partition are all locked.

---

### Post by linuxman94 on 2010-04-21
Open gparted (system -> administration -> Gparted) and select your flash drive from the drop down menu in the upper left-hand corner.  Use gparted to delete both partitions and create a new one with the FAT32 file format.  Click apply and then try unetbootin again after it is finished.

---

### Post by RedRat on 2010-04-22
> **linuxman94 said:**
> Open gparted (system -> administration -> Gparted) and select your flash drive from the drop down menu in the upper left-hand corner.  Use gparted to delete both partitions and create a new one with the FAT32 file format.  Click apply and then try unetbootin again after it is finished.
OK I started gparted and it only shows the 15.15GB Fat32 partition, it does not show the other files or what I think to be a hidden partition, small one. Gparted claims that it cannot read the files on that large partition. I was able to load the Lucid Lynx daily build the other day onto the drive using the Windows version of the program on my XP system. I will see if this is bootable on a laptop.

OK checked it and was able to boot from usb flash drive. So it looks OK.

---


---
title: "Issues with the BIOS"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Dondarrion on 2010-10-17
I recently got a PC running Windows XP from my grandparents, and decided that I wanted Ubuntu on it. Using a mac, I downloaded the .iso file and put it onto a USB drive. The computer I'm trying to install Ubuntu onto has an ASUS A7V8X-X motherboard, so I pressed DEL to get to the Setup Utility.

I went to BOOT and moved the Removable Device option to number one in the boot order. This gives me two option, USB FDD or USB ZIP. I've tried both, neither one opens up the Ubuntu installer when I restart. 

This computer does not have a CD drive (I think I could scrounge one up though.) Should I do this and put the .iso on a CD, or is there something else I can do.

Thanks for any help.

---

### Post by GabrielYYZ on 2010-10-17
that .iso file is an image file, you need to use a program to burn an image to cd and select that .iso file as the image you want to burn, that'll do it. 

i'm not really familiar with usb thingies, but i assume the procedure with them is similar. you need to burn the image, not just copy it in the drive or cd.

edit:

here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) 

in step 2, select usb stick and click show me how.

---

### Post by spikoley on 2010-10-17
The .iso will not boot if you just put it on a USB drive.  Follow the directions in step 2 to make it bootable.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by amjjawad on 2010-10-17
> **Dondarrion said:**
> I went to BOOT and moved the Removable Device option to number one in the boot order. This gives me two option, USB FDD or USB ZIP. I've tried both, neither one opens up the Ubuntu installer when I restart. 

It should say **USB HDD** otherwise, you'll not be able to boot from your USB Flash Disk/Pendrive.

> 
This computer does not have a CD drive (I think I could scrounge one up though.) Should I do this and put the .iso on a CD, or is there something else I can do.

Thanks for any help.

You need a CD-ROM Driver or DVD-ROM Driver ... any optical driver that could read CD-ROM.
Then, you need to BURN the .iso file NOT just copy and paste it or burn it as a data file.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Read: Burn your CD or create a USB drive

---

### Post by Dondarrion on 2010-10-17
Thanks for the help.

@spikoley
> 
The .iso will not boot if you just put it on a USB drive. Follow the directions in step 2 to make it bootable.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


What does it mean by "Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)"

What is my target.img?



If I can't get that to work, i'll just find a CD-Drive somewhere and burn a CD.

---

### Post by spikoley on 2010-10-17
I have never created a bootable USB drive on a Mac, but I believe it is referring to where you want to save the file.  Try running the command below.  Make sure you change the *~/path/to/ubuntu.iso* to the location of the download.

```
hdiutil convert -format UDRW -o ~/Desktop/ubuntu.img ~/path/to/ubuntu.iso
```

My concern is usually with Unix based operating systems the target location is last, but that is the documented command.  Try it and let us know how it goes.

Edit:  This [GUI]("http://docwhat.org/2008/06/os-x-make-an-iso/") way might work.

---

### Post by oldfred on 2010-10-18
While my BIOS showed lots of USB choices, the flash drive was listed under hard drives. 

I was not able to boot from any of the USB choices, found my USB would boot in my portable and plugged it back into my system. Did not work. I happen to be changing hard drives to boot from and there it was.

---

### Post by spikoley on 2010-10-18
OK, it sounds like the USB drive works.  What brand and model of computer are you having troubles booting into?

---


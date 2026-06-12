---
title: "can't get Ubuntu started on net-book"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Hal Story on 2009-07-12
can't boot Ubuntu - netbook jumps to XP
HP 1000 series netbook. Downloaded image, downloaded program to copy image to thumb drive, formatted thumb drive to remove old data, used recommended program to copy image to thumb drive, told netbook BIOS to give priority to thumb drive, inserted thumb drive, cold boot, and VOILA!  Windows XP! I must have done something wrong, but what? Any ideas?  Desperate to get started - could I boot from an SD card?

---

### Post by twright on 2009-07-12
> **Hal Story said:**
> can't boot Ubuntu - netbook jumps to XP
HP 1000 series netbook. Downloaded image, downloaded program to copy image to thumb drive, formatted thumb drive to remove old data, used recommended program to copy image to thumb drive, told netbook BIOS to give priority to thumb drive, inserted thumb drive, cold boot, and VOILA!  Windows XP! I must have done something wrong, but what? Any ideas?  Desperate to get started - could I boot from an SD card?
Hi,
I doubt the situation would be any different with a SD card as they work the same way. First have you checked that files are actually being created on the USB stick and did you format it as fat32/vfat (not ntfs). If you have then the problem is probably how you are booting it, rather than changing the setting in the bios can you try pressing escape, delete, f12 or whichever key your bios specifies to bring up a boot device menu and select your USB stick.

Good luck and welcome to Ubuntu :-)

---

### Post by Flying caveman on 2009-07-12
I would say you need to use the dd command to put your .img on your usb drive.  Sorry I don't know how to do that in Windows, and it won't allow you to dual boot if thats what you want.  

You could download the Ubuntu .iso and use Unetbootin for Windows to make your usb stick bootable.  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by LewRockwell on 2009-07-12
I wanted to point out something that others might have overlooked with reference to using thumb drives

Unlike a burnt(and uneditable/unchangable) piece of optical media(CD/DVD), thumb drive contents are not so protected...

Yes, I know the standard excuse and shreik is that the netbook has no optical drive(yes, I know this...I have them also)

cd-rom drives out of old computers are dime a dozen and you can hardly give them away around here...so I know there is no need to spend money on one...

all you need is one of these(or something similar to enable your netbook to utilize optical media)...and you'll be good to go!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

[http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

so...for the ultimate in the secure knowledge of uncorrupted data...optical media is the way to go...

.

---

### Post by Flying caveman on 2009-07-12
also read: [http://ubuntuforums.org/showthread.php?t=1045239](http://ubuntuforums.org/showthread.php?t=1045239)

maybe useful.

---

### Post by Hal Story on 2009-07-18
The best I have managed is "BOOT ERROR". I got that by transferring the image file to the target machine (HP mini with 16 GB solid state mass storage) and execuring the copy to the USB stick from the target machine. Until I did that, the HP simply ignored the USB stick memory. Have I selected the wrong image file?  Which one is right for the HP mini?

---

### Post by Hal Story on 2009-07-19
> **twright said:**
> Hi,
I doubt the situation would be any different with a SD card as they work the same way. First have you checked that files are actually being created on the USB stick and did you format it as fat32/vfat (not ntfs). If you have then the problem is probably how you are booting it, rather than changing the setting in the bios can you try pressing escape, delete, f12 or whichever key your bios specifies to bring up a boot device menu and select your USB stick.

Good luck and welcome to Ubuntu :-)

I tried to make the USB on my desktop computer to no avail. Then I moved the image and image writer to the HP mini and tried again. Now I get "BOOT ERROR" for my troubles. Could I have downloaded the wrong image file? I read about the HP mini coming from HP with Ubuntu pre-installed. There should be a variation which will work!

---

### Post by 3rdalbum on 2009-07-19
Try Unetbootin instead of the inbuilt Ubuntu tool. My netbook wouldn't boot from the drive until I used Unetbootin.

---


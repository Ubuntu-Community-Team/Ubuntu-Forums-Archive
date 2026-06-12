---
title: "Help me get Ubuntu on my computer, please"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by j2the242 on 2010-01-29
Hello everyone,

So about a year back I had ubuntu and xp running as a dual boot on my Asus eeepc 1000hd. I had nothing but problems, so I deleted ubuntu. But I cant remember how I got ubuntu on here in the first place.

I dont have a optical drive, or a floppy drive, and Ive tried every method with a usb flashdrive but I cannot get ubuntu to work, I cant even get my computer to boot from the usb.

When I installed ubuntu last year I didnt have a usb flashdrive and I got it on here, but I cant find any resources on how to do that again.

How do I install ubuntu on my eee pc 1000hd without a cd drive, floppy drive, or usb?

I appreciate your help in advance, and I look forward to being done with any microsoft software.....and being free from it for the rest of my life.

Ubuntu, kubuntu, or xubuntu.....dont care which one, whatever is the easiest to do.

---

### Post by gabo.cr on 2010-01-29
You can try Wubi:
[http://wubi-installer.org/](http://wubi-installer.org/)

I don't really like Wubi, but it seems to be the best option for you.
;)

---

### Post by Merk42 on 2010-01-29
You should be able to install via USB on an EEEPC, are you sure you're doing it correctly? (make note of step 3 on the second page)
[http://www.associatedcontent.com/article/1758422/how_to_install_eeebuntu_on_your_eee.html](http://www.associatedcontent.com/article/1758422/how_to_install_eeebuntu_on_your_eee.html)

(don't mind that it's called eeebuntu, the instructions are similar regardless)

If you don't have a CD drive, then WUBI is your only option, like gabo.cr I'm not a fan of it as it doesn't perform as well as a natural install.

---

### Post by j2the242 on 2010-01-29
What do you mean when you said "it doesnt perform as well", when talking about wubi? Does the install process not perform as well, or does the OS not perform as well after installed?

---

### Post by Rex Bouwense on 2010-01-29
I too have an ASUS EeePC.  Mine is a 1000H and it came with XP installed.  I have subsequently installed Ubuntu on the whole drive.  You can do it with a flash drive but you must tap the F2 key to change the booting order when you boot.  You can also boot from a CD that is plugged into a USB port. I know this because I have done both.  This of course assumes that you have Ubuntu or Ubuntu Remix on the flash drive which is another question.

---

### Post by knurledflanges on 2010-01-29
> **j2the242 said:**
> I appreciate your help in advance, and I look forward to being done with any microsoft software.....and being free from it for the rest of my life.


If you want to dump Windows completely, don't use wubi, as this installs Ubuntu within Windows and transferring the wubi install to its own partition and getting rid of Windows is not a newb task. I just went through all this.

---

### Post by egalvan on 2010-01-29
I would suggest this page...

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)


This is another very useful site

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Merk42 on 2010-01-29
> **j2the242 said:**
> What do you mean when you said "it doesnt perform as well", when talking about wubi? Does the install process not perform as well, or does the OS not perform as well after installed?

It doesn't perform as well, also like knurledflanges says, WUBI REQUIRES Windows to still be installed.  Nuke Windows and Ubuntu goes with it.

So again, look into UNetbootin and whatever key you need to press to boot from the USB with your particular model.

As for the Ubuntu Netbook Remix that egalvan posted, the only difference with that versus standard Ubuntu is the interface.

---

### Post by Shpongle on 2010-01-29
what you could do since you have no optical drive is download the iso and run it in a virtual machine such as virtual box!, then if you still wanna properly install , use the virtual machine to make a usb image and boot and install from that!

---

### Post by Shpongle on 2010-01-29
what you could do since you have no optical drive is download the iso and run it in a virtual machine such as virtual box!, then if you still wanna properly install , use the virtual machine to make a usb image and boot and install from that!. [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by j2the242 on 2010-01-29
Ok so I downloaded the ubuntu iso image and used 7-zip to unzip the files (unetbootin says that there isnt an application file to store the information, and it wasted 2 hours of my time). Then I saved it to my usbb drive and rebooted. When I select 'boot from usb' I get a black screen with a blinking white line on the top, Ive  tried it 3 times, every time its the safe thing.

What does that mean?

---

### Post by Merk42 on 2010-01-29
> **j2the242 said:**
> Ok so I downloaded the ubuntu iso image and used 7-zip to unzip the files (unetbootin says that there isnt an application file to store the information, and it wasted 2 hours of my time). Then I saved it to my usbb drive and rebooted. When I select 'boot from usb' I get a black screen with a blinking white line on the top, Ive  tried it 3 times, every time its the safe thing.

What does that mean?

Well first off, [check the md5 sum of the iso](https://help.ubuntu.com/community/HowToMD5SUM)

I've never used Unetbootin, but when I used a USB to install Windows I had to do certain things to the filesystem to say it's bootable.

Did you use Unetbootin at all? I don't quite understand the error you're getting with it. I'm guessing if you just dragged the extracted files to teh drive, it didn't make it bootable and therefore caused the blinking white line.

---

### Post by egalvan on 2010-01-29
> **j2the242 said:**
> Ok so I downloaded the ubuntu iso image and used 7-zip to unzip the files
 (unetbootin says that there isnt an application file to store the information, and it wasted 2 hours of my time). 

WHAT ubuntu iso image did you download and **from where**?

Regular ubuntu iso's** do not** get "un-zipped".
They must be burned to cd as an image,
or used by unetbootin directly.
(one can also mount the iso as a file-system)

> Then** I saved it to my usbb drive and rebooted.**
 When I select 'boot from usb' I get a black screen with a blinking white line on the top
, Ive  tried it 3 times, every time its the safe thing.

What does that mean?


WHAT did you "save to the usb drive"? the ubuntu iso?

---

### Post by j2the242 on 2010-01-30
I was finally able to use unetbootin to unzip the iso (that I downloaded from ubuntu.com.....ubuntu netbook remix....also tried kubuntu netbook....and easy peassy......) all of them went through netbootin, at seperate times after deleting the drive of course, and all of them went on a usb and a flash. I was able to boot from the flash, and I was able to boot from the USB....but every time,, with every method, and every OS all I got was a black screen with a blinking white dot.

---

### Post by ppb1701 on 2010-01-30
on my 1000he if i boot from a flashdrive i have to go into bios boot options and toggle the hard drive to point to the usb stick.

---


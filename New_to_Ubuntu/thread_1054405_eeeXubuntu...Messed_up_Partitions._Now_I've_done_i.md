---
title: "eeeXubuntu...Messed up Partitions. Now I've done it..."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by thescree on 2009-01-29
Hey all.

I'm fairly new to the whole eeeXubuntu thing. I've used ubuntu before, and I was sick of the eee interface so I wanted to use a faster, or at least a cooler looking build.

So I tried to install eeeXubuntu on my 2g surf. I read all the forums here about the problems people were having and decided to run it without the localization. I tried to set my 512 card as the swap and my main HD as the main drive...

Well of course when it was installing the files, it crapped out. I'm not sure how, but I looked at my machine and it cut out of the install. I rebooted and took the USB drive out (which has the live eeeXubuntu install on it) and I get a message saying "error 22". I know this is a grub error but I don't know how to fix it.

The old Xandros won't boot up and I have no idea if I can fix the partition problem (which is what error 22 seems to be).

Can someone help me?

---

### Post by ibizatunes on 2009-01-29
[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

boot to you live usb and you can recover GRUB there


[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Is a good url

PS you may want to use eeebunutu, if you have 2gb of ram
that is up to you

[http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by thescree on 2009-01-29
Unfortunatley this got to the point where my USB drive wasn't even usable. I'm currently re-building the live version of eeexubuntu onto the usb drive so I can recover grub.

EDIT:

I got the live thumbdrive working. Went into terminal and typed
sudo grub

I get the command prompt with 

grub>

I type

find /boot/grub/stage1

and I get "error 15: file not found"

Am I screwed?

---

### Post by thescree on 2009-01-29
bump...please help!

---

### Post by cardinals_fan on 2009-01-29
You need to figure out what the correct partition is.  Can you post the output of "fdisk -l"?

---

### Post by caljohnsmith on 2009-01-29
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by oyroy on 2009-01-29
Ive had problems with GRUB when installing from USB-Pen as well. Seems GRUB includes the USB-Pen into everything, and when you try to boot without a USB-Pen connected GRUB gives an error so you cant boot the machine. Probably a way to manually fix GRUB, but when I've installed eeeXubuntu/Ubuntu-eee/eeeBuntu (Ive used em all :D) from an SD-card instead of USB-Pen everything runs smooth.

Prob not the best way to deal with a problem, but from me it was the easiest by far.
Ohh, and btw, from experience with Eee 700 Surf 2GB. (This might have changed), I would suggest beeing offline when installing it (Not activate wlan when running the live installer) as for me the installation always failed because it was downloading OpenOffice and loads of other stuff, which filled my 2GB-drive and crashed the installation. I fixed that by installing offline, so it only got the bare minimum of packages, then sorting out and removing what I didnt want, then upgraded the system later. That might fix your problem as well, if it crashed mid-way or towards the end.

---

### Post by thescree on 2009-01-29
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

I would, but nothing is currently on the desktop. The only way I can get Xubunutu working is off the pen drive live.

---

### Post by caljohnsmith on 2009-01-29
> **thescree said:**
> I would, but nothing is currently on the desktop. The only way I can get Xubunutu working is off the pen drive live.
That's fine, you can run the script from your pen drive live. :)

---

### Post by thescree on 2009-01-29
Okay, let me get back on live and see where we are...

---

### Post by thescree on 2009-01-29
Now I'm having problems even booting Xubuntu. I'm either getting Error 22 before it loads, or it sits on the loading screen with the bar going back and forth.

---

### Post by thescree on 2009-01-30
I've gotten back to the install screen, but now when i try to install, I get this message:

[Errno 5] Input/output error

---

### Post by thescree on 2009-01-30
I just tried it again, and this time I got up to about 80% before the installer quit again. I simply look at the thing and it's not giving me an error message or anything, it simply just stopped.
No rhyme or reason...someone want to explain that one? 
:(

---

### Post by thescree on 2009-01-30
More bad news. Since I only have one flashdrive I decided to load the Super Grub Disk onto the USB drive. Without the usb drive booting, I get ERROR 15.
With booting up the Super Grub Disk, I get an error as well:

Loading Boot Sector...MEMDISK: Failed to load new boot sector.

And then nothing...silence. I'm about to give up and sell this thing for beans to someone who can actually fix it. I've had it up to the ears with dicking around with Linux....

---

### Post by oyroy on 2009-01-30
Reffering to my earlier post, are you online when you are installing eeeXubuntu? If you are, try disable wifi before you install, else the installer might crash because the disk gets full. Are you using much space for swap? You need as much of the 2GB as possible for the install, so try to keep as much avaliable as possible.

---

### Post by thescree on 2009-01-30
> **oyroy said:**
> Reffering to my earlier post, are you online when you are installing eeeXubuntu? If you are, try disable wifi before you install, else the installer might crash because the disk gets full. Are you using much space for swap? You need as much of the 2GB as possible for the install, so try to keep as much avaliable as possible.


I am not online when installing (I don't have wifi at my house). As far as the swap goes, I tried to use my SD card for that, but I get an error saying the installer can't create a file system on the main drive.

I may be partitioning wrong when manually setting it. I tried to make my hard drive and ext3 system with "/" as its mount point, and set the SD card as "swap".

(Yeah, I'm pretty new to this...)

---

### Post by thescree on 2009-01-30
> **thescree said:**
> I am not online when installing (I don't have wifi at my house). As far as the swap goes, I tried to use my SD card for that, but I get an error saying the installer can't create a file system on the main drive.

I may be partitioning wrong when manually setting it. I tried to make my hard drive and ext3 system with "/" as its mount point, and set the SD card as "swap".

(Yeah, I'm pretty new to this...)
bump

---


---
title: "Questions about installing Ubuntu 10.10"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by IVIurdoc on 2010-10-25
I am currently in the process of creating recovery discs and personal data backups for a worse case scenario and just had a few questions regarding Ubuntu. I will list some of the hardware I am using, I'm installing on a Sony Vaio currently running Windows 7 Home Premium 64 bit. I think I am going to install the 32 bit version of Ubuntu since I have heard there are less bugs, etc. and there isn't much notice in performance between 32 and 64bit.  I am running a Intel Pentium T4400 2.2 GHz processor, a Mobile Intel Graphics accelerator 4500M, with 4GB of ram. I was wondering if there might be any incompatibility and if the install will also search for and install drivers automatically and if not is there a way to back them up or easily find them online. What are a few tips or important pieces of information I should know when changing operating systems? I think that's about it. Any help is greatly appreciated!

---

### Post by bioterror on 2010-10-25
> **IVIurdoc said:**
> I am currently in the process of creating recovery discs and personal data backups for a worse case scenario and just had a few questions regarding Ubuntu. I will list some of the hardware I am using, I'm installing on a Sony Vaio currently running Windows 7 Home Premium 64 bit. I think I am going to install the 32 bit version of Ubuntu since I have heard there are less bugs, etc. and there isn't much notice in performance between 32 and 64bit.  I am running a Intel Pentium T4400 2.2 GHz processor, a Mobile Intel Graphics accelerator 4500M, with 4GB of ram. I was wondering if there might be any incompatibility and if the install will also search for and install drivers automatically and if not is there a way to back them up or easily find them online. What are a few tips or important pieces of information I should know when changing operating systems? I think that's about it. Any help is greatly appreciated!

Hi, you should absolutely run 64bit Ubuntu to get every drop of your RAM used for the system.

I suggest you to make a bootable USB stick with Unetbootin [unetbootin.sf.net]("unetbootin.sf.net") and check if everything works okay. Then you can just click Install icon on the desktop and let the intaller handle the rest if you're satisfied what the Live environment had to offer to you.

---

### Post by ArgusVision on 2010-10-25
I don't believe there are any incompatibilities with the hardware you've listed. What is your wireless card though? There are a few of those that have issues.

---

### Post by ArgusVision on 2010-10-25
You said Pentium right? Those aren't 64-bit (If I recall correctly). Stick with the 32 as it will work.
Drivers etc are downloadable.

---

### Post by sikander3786 on 2010-10-25
Hi and Welcome to the community :popcorn:

If you install 32-bit Ubuntu, you will later need to install PAE-Kernel in order to support the 4 GB RAM you've got.

I feel it would be better to install 64-bit. No real boost in performance but still some notable difference is always there.

You might not need to install any extra drivers except your Wireless card. Boot into a Live CD and test all your hardware before installation.

Regarding tips,

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by bioterror on 2010-10-25
> **ArgusVision said:**
> You said Pentium right? Those aren't 64-bit (If I recall correctly). Stick with the 32 as it will work.
Drivers etc are downloadable.

T4400 is a 64bit CPU [http://ark.intel.com/Product.aspx?id=40739]("http://ark.intel.com/Product.aspx?id=40739")

---

### Post by ArgusVision on 2010-10-25
> **bioterror said:**
> T4400 is a 64bit CPU [http://ark.intel.com/Product.aspx?id=40739]("http://ark.intel.com/Product.aspx?id=40739")

I stand corrected.

---

### Post by IVIurdoc on 2010-10-25
You guys know more about my hardware than I do lol, I'm not exactly tech savy but I'm working on it. How do I create a Live CD to test it out. Do I just download Ubuntu and put it on a CD/DVD or what? My wireless card is an Atheros AR9285. Also I just thought of another question I have a Canon MP495 series printer with built in WiFi how good is Ubuntu with connectivity to wireless printers? Is it just a matter of using Wine to install the files or will I need to do anything special. I hope I'm not getting in over my head with all this. Is there any difference as to a learning curve or such between 64 bit and 32 bit. I would like to use 64 bit so I can get the full potential out of my processor and RAM but without any added difficulty of use. Once again thanks for all the replies.

---

### Post by beew on 2010-10-25
> **sikander3786 said:**
> Hi and Welcome to the community :popcorn:

If you install 32-bit Ubuntu, you will later need to install PAE-Kernel in order to support the 4 GB RAM you've got.

I feel it would be better to install 64-bit. No real boost in performance but still some notable difference is always there.

You might not need to install any extra drivers except your Wireless card. Boot into a Live CD and test all your hardware before installation.

Regarding tips,

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Isn't the PAE-Kernel already installed?

If there is no real boost in performance I don't see why 64 bit is preferred. I can see some potential problems such as drivers and software compatibility. It is true that many software that run in 32 bits can run in 64 bits but they are optimized for 32 bits.

Canonical suggests that 64 bit should not be used on a work system. Now I know some64 bit advocates disagree, but I would take the words of Canonical any day since they put the system together and would know all about the ins and outs.

---

### Post by bioterror on 2010-10-25
> **IVIurdoc said:**
> You guys know more about my hardware than I do lol, I'm not exactly tech savy but I'm working on it. How do I create a Live CD to test it out. Do I just download Ubuntu and put it on a CD/DVD or what? My wireless card is an Atheros AR9285. Also I just thought of another question I have a Canon MP495 series printer with built in WiFi how good is Ubuntu with connectivity to wireless printers? Is it just a matter of using Wine to install the files or will I need to do anything special. I hope I'm not getting in over my head with all this. Is there any difference as to a learning curve or such between 64 bit and 32 bit. I would like to use 64 bit so I can get the full potential out of my processor and RAM but without any added difficulty of use. Once again thanks for all the replies.

I've been running 64bit Ubuntu on my desktop and I haven't encountered any problems with it.

About your printer, check this one out [http://ubuntuforums.org/showthread.php?t=1602839]("http://ubuntuforums.org/showthread.php?t=1602839")

And what comes to the WLan, you might look this too [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

Small tweakings for your evenings, and you can surely experience some Ubuntu joy ;)

---

### Post by sikander3786 on 2010-10-25
> Isn't the PAE-Kernel already installed?

Here is a statement from

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

> Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

I have seen many cases where PAE Kernel didn't got installed automatically and therefore needed to be enabled manually.

> If there is no real boost in performance I don't see why 64 bit is preferred. I can see some potential problems such as drivers and software compatibility. It is true that many software that run in 32 bits can run in 64 bits but they are optimized for 32 bits.

There is a boost in performance regarding compressing, video encoding etc but that is not something a normal desktop cares about. 32-bit vs 64-bit is a vastly debateable topic. I will refrain from it or the thread is going to be moved to Recurring Discussions :-)

> Canonical suggests that 64 bit should not be used on a work system

Well that is a statement that in my opinion really needs to be modified to something else.

I am myself using 64-bit since the last 2 years and never had any problems regarding drivers, flash, java or anything else.

---

### Post by beew on 2010-10-25
> **IVIurdoc said:**
> You guys know more about my hardware than I do lol, I'm not exactly tech savy but I'm working on it. How do I create a Live CD to test it out. Do I just download Ubuntu and put it on a CD/DVD or what? My wireless card is an Atheros AR9285. Also I just thought of another question I have a Canon MP495 series printer with built in WiFi how good is Ubuntu with connectivity to wireless printers? Is it just a matter of using Wine to install the files or will I need to do anything special. I hope I'm not getting in over my head with all this. Is there any difference as to a learning curve or such between 64 bit and 32 bit. I would like to use 64 bit so I can get the full potential out of my processor and RAM but without any added difficulty of use. Once again thanks for all the replies.

Instead of a live CD I recommend a live usb with persistence if your BIOS supports booting from usb (most newer computers do)  because it is much faster and you can save your settings, which can be convenient if you need to restart at some point.

To create a live usb in Windows (your current OS), you can use the universal usb creator
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

Instead of 10.04 you can download the 10.10 iso, I think the universal usb creator would support it, otherwise you can use LiLi
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

After you create the live usb, boot into it and see if wireless etc work.

---

### Post by akand074 on 2010-10-25
I'd be so surprised if you had any driver issues. I would install the 64 bit if I were you. Despite what you might hear, there are no "64bit bugs", at least that you would notice. You get to use all your RAM right out of the box, and 64 bit is exponentially more effective at handling information with RAM. I mean, you won't likely notice much difference in every day use, but might as well take advantage of it, the 32bit libraries are installed as well so you can still run programs in 32 bit if that's all they support. 

Either way though, you shouldn't have any problems with Ubuntu's compatibility with your system.

---

### Post by IVIurdoc on 2010-10-25
How do I create the Live CD to boot Ubuntu so that I can preview/test it before doing a full install?

---

### Post by ArgusVision on 2010-10-25
After you download, you'll need to use a disk burning software like Roxio, Nero, DeepBurner, etc. that supports burning .iso images to disk. Using the built-in windows cd maker or making a "data" CD won't work, as it needs to be bootable.

---

### Post by ArgusVision on 2010-10-25
If you don't currently have one of these, DeepBurner is free (as in no cost) from [www.download.com](www.download.com).

EDIT: It's hosted by cnet and will redirect you as such.

---

### Post by IVIurdoc on 2010-10-25
Thanks for the link and thanks everyone for all the help. I don't even have Ubuntu installed yet and I already like it because of this friendly help.

---

### Post by beew on 2010-10-25
> **ArgusVision said:**
> After you download, you'll need to use a disk burning software like Roxio, Nero, DeepBurner, etc. that supports burning .iso images to disk. Using the built-in windows cd maker or making a "data" CD won't work, as it needs to be bootable.

If OP can boot from usb a live usb is much better and easier to create(download Lili or the universal usb creator from my links above). A live CD is not only slow, but pretty useless if you want to test your system on installation, internet auto connection etc because you lose all settings on reboot. 

"Burning a live CD" is almost like "get a floppy" to my ears. :)

---

### Post by ArgusVision on 2010-10-25
Glad to hear it, and to be a part of it. :)

---


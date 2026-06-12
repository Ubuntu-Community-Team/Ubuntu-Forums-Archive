---
title: "USB-Stick Ubuntu issues."
date: 2010-08-21
forum: New to Ubuntu
---

### Post by MarionNette on 2010-08-21
Hey there! I am completely new to the realms of Linuxia and I need some advice for the start ;)

I have installed the latest Ubuntu on a 16 gb USB stick (installed like on a harddrive, not live mode!) and plan to use this as alternative to my Windows that suffers from bluescreenitis. However I have some Problems:

1. I am annoyed by repetitively having to enter my password when changing things on the system. After logging in I want to be able to do what I want without having to reenter my password. How can I configure this?

2. The Ubuntu, run from USB-Stick used as Live CD ran quite smoothly, but I couldnt get it persistent and didnt want do live with the limitations of the live mode. So I installed Ubuntu directly on the Stick. It does what  want, but I have certain performance Problems. Eg, when i type in a URL it sometime takes seconds to display what I have typed. Or the menues pop up delayed. Not so nice. Is there a way to fix it? My PC is a Turion 64 Laptop with 2 gb ram, so hardwarewise it shouldn't be a problem. No fancy effects activated.

3. I activated this encryption option on installation, but now I am not so sure if I need it. Is there a way to deactivate it?

Kudos in advance for any help!

---

### Post by mörgæs on 2010-08-21
> **MarionNette said:**
> Hey there! I am completely new to the realms of Linuxia and I need some advice for the start ;)

I have installed the latest Ubuntu on a 16 gb USB stick (installed like on a harddrive, not live mode!) and plan to use this as alternative to my Windows that suffers from bluescreenitis. However I have some Problems:

1. I am annoyed by repetitively having to enter my password when changing things on the system. After logging in I want to be able to do what I want without having to reenter my password. How can I configure this?

This is a security feature. If a process is trying to do something potentially harmfull, Ubuntu wants the confirmation that it is intended.

> **MarionNette said:**
> 
2. The Ubuntu, run from USB-Stick used as Live CD ran quite smoothly, but I couldnt get it persistent and didnt want do live with the limitations of the live mode. So I installed Ubuntu directly on the Stick. It does what  want, but I have certain performance Problems. Eg, when i type in a URL it sometime takes seconds to display what I have typed. Or the menues pop up delayed. Not so nice. Is there a way to fix it? My PC is a Turion 64 Laptop with 2 gb ram, so hardwarewise it shouldn't be a problem. No fancy effects activated.

Running from a USB stick is never as fast as running from the hard drive. If you have some space on the hard drive, you could defrag Windows a couple of times, open some space for Ubuntu and install Ubuntu next to Windows.

---

### Post by MarionNette on 2010-08-21
Thank you for your reply.

>  			 		 	 	 This is a security feature. If a process is trying to do something  potentially harmfull, Ubuntu wants the confirmation that it is  intended.

Well, can it be deactivated anyway?

> Running from a USB stick is never as fast as running from the hard  drive. If you have some space on the hard drive, you could defrag  Windows a couple of times, open some space for Ubuntu and install Ubuntu  next to Windows.

If the lags are caused by the fact, that I run Ubuntu on a USB-Stick, then why did'nt I have these lags, when I used ubuntu in live mode? Also the lags dont happen in situations, when there should be data loaded from the stick. I want to keep my Ubuntu on the Stick, I find the Idea of having a pocket-OS convenient.

---

### Post by oldfred on 2010-08-21
USB is a little slower and then encryption with LVM is a little slower. The combination may be part of the problem. I installed without encryption and did not notice much difference, but have not used it much as I wanted it just as a backup.

Standard full install to flash or SSD, info on settings:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by C.S.Cameron on 2010-08-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MarionNette on 2010-08-21
Thank you, Oldfred, I really have the Impression, that the tweaks really helped to Improve the speed. :) 

And thank you to, Cameron. I will think about it.

---

### Post by MarionNette on 2010-08-22
How ever, I still have strange Lags from time to time, mostly when surfing, what I am actually doing most of the time. The Window even greys out for 1-3 Seconds.

---

### Post by mörgæs on 2010-08-22
The grey windows indicates a heavy processor load. Which process is causing this?

---

### Post by MarionNette on 2010-08-22
The CPU-Usage Peak seems to be mostly when firefox is loading a page, or sometimes too when I type into a search-field, like the one of google.

---

### Post by mörgæs on 2010-08-22
If Firefox makes trouble, then this might help:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---


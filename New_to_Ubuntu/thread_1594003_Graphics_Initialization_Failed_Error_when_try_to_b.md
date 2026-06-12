---
title: "Graphics Initialization Failed Error when try to boot from usb"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by lstagner on 2010-10-11
Hey Everybody,

I just bought a Toshiba NB255-N250 netbook and I want to set it up as a dual boot like my Desktop. I downloaded Ubuntu 10.10 Netbook and loaded on a SanDisk 4 Gb flash drive using the latest USB Universal installer. When I booted from the USB I get the following message.

graphics initialization failed
Error setting up gfxboot
boot: 

I get this error with both the Netbook and Desktop editions.
I check the USB on another system and it worked fine.
 
Here are the specs for my computer:
[http://laptops-specs.blogspot.com/2010/06/toshiba-mini-notebook-nb255-n250.html](http://laptops-specs.blogspot.com/2010/06/toshiba-mini-notebook-nb255-n250.html)

If I were to hazard a guess as to the reason I would say that the graphics card I have is not yet supported.

---

### Post by jayhoytt on 2010-10-14
I am having the exact same issue with the Toshiba NB255-245.

---

### Post by jayhoytt on 2010-10-17
Perusing other threads on this forum, I encountered the following solution for the problem above:

Upon encountering the error, simply type "help". Installer proceeds to load as expected.

---

### Post by Jacob111 on 2010-10-25
Oh, well that's stupid.  I've been fighting with this for weeks.  Why did it take me so long to find this?  Thanks a TON.

---

### Post by John Q (be) on 2010-11-02
Hi guys;

I was installing 10.10 on an old (read really OLD) IBM.
First I've used the on-board GFX and got the same error.

Changing the GFX to a PCI GFX card solved my problem instantaneously...

Maybe this in not related to the USB problem however I wanted to share this with you all.

John

---

### Post by JohnM1 on 2010-11-13
> **jayhoytt said:**
> 
Upon encountering the error, simply type "help". Installer proceeds to load as expected.

Thanks, I had the same problem booting from an external USB CDROM

Typing "help" solves the problem, and allows me to boot the CD.

---

### Post by Mudmanc4 on 2010-11-19
Installing 10.1 from internal optical drive produces the same results on dell | D810 , typed help and the options screen comes up , but obviously the wmi driver has not been installed because none of the f keys function.  I have not found a solution as of yet. Over writing all data right now  ( clearing it ) since i had suse installed. 

workin on it

[EDIT: I had a bad download iso , of my own doing - [Solution : check your download size and or just re download the iso and get a fresh image ]

---

### Post by beercz on 2010-12-21
Hi Guys - I had exactly the same problem on my son's Toshiba NB250 netbook.

Typing 'help' at the boot prompt worked!

I would never have thought of that.

Thanks again.

---

### Post by microsafe17 on 2011-02-25
I had the same issue and typing help also fixed me, thanks for the fix. My machine was a Toshiba NB305 booting from a USB drive.

---

### Post by Hamid_1978 on 2011-07-08
I'm still didn't succeed to install the Ubuntu on my Micro client server. After typing "help" a screen appears with some installation steps. After a while everything turns black and nothing happends. What els can i do?

Thanks!

---

### Post by ethanthesweet on 2011-09-01
mkay well im getting this with the cd version. i have an old hp pavilion dv9000  and even when i type help it will bring  up the splash page, then it will go black and stay black. ive even tried waiting for over an hour

---

### Post by smleimberg on 2012-06-13
After getting the gfxboot error, typing "help" at the boot prompt brought me to the "HELP INDEX" where I just hit enter to boot.

iso: Xubuntu 12.04 Alternate i386

---

### Post by oldos2er on 2012-06-13
smleimberg, please start a new thread; this one's two years old.

---


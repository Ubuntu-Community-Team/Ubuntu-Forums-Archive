---
title: "Old laptop won't boot Live Ubuntu usb"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Baylynx on 2010-08-06
[FONT=Times New Roman][SIZE=3]I have an older laptop - Compaq 2103us. The Boot Menu doesn’t offer an option to boot from a USB drive. I tried to create a Live Ubuntu CD, but I get I/O write errors on the internal cd drive and several attempts failed. Instead I created Live Ubuntu on a usb stick drive (2gb Sandisk Cruzer) and in Setup Mode selected Removable Devices to boot first… but no luck.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]On another forum someone suggested the following:[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3][COLOR=purple]**>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>**[/COLOR][/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman][COLOR=black][FONT=Arial][COLOR=purple]**You could save all the work and just use UNetBootin. It worked perfectly on my old systems which did not have USB boot.**[/COLOR][/FONT][/COLOR][/FONT][/SIZE][FONT=Times New Roman]
 
[SIZE=3][COLOR=black][FONT=Arial][COLOR=purple]**1. Go to windows or linux and install the OS image on the USB key using Unetbootin.**[/COLOR][/FONT][/COLOR][/SIZE][COLOR=black]
**[SIZE=3][FONT=Arial][COLOR=black]2. Shut down the system and turn it back on with the USB key plugged in.[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=Arial][COLOR=black]3. Quickly jump to the BIOS by pressing the appropriate key.[/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=Arial][COLOR=black]4. The USB key will now be listed under Hard Drives or Removable Devices![/COLOR][/FONT][/SIZE]**
**[SIZE=3][FONT=Arial][COLOR=black]5. Setup the BIOS to boot from the USB key and your done.[/COLOR][/FONT][/SIZE]**[/COLOR]
[/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=purple]**>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>**[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Do you recommend this? If so, I would like to try this method, but can someone provide more details... specifically, what is meant by installing "OS image on the USB key" ???[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Also... will these instructions to **Put PLoP on a Floppy Disk **work with an *[COLOR=black][FONT=Arial]**external floppy drive?**[/FONT][/COLOR]* I have one, but will need to travel to another location to pick it up, but I’m unsure it will work as BIOS may not recognize that either. [/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Thanks.[/SIZE][/FONT]

---

### Post by Elmer Fudd on 2010-08-06
Are you talking about the "Boot Menu" in the BIOS Setup?

Forgive me for proposing the obvious...
If you are having problems with your CD writer and you have access to another computer (someone elses if not your own) the quickest fix here would be to create a new LiveCD on that computer. Of course, if your CD is bad, you might be SOL anyway.

The USB method that you are asking about does work, but not if your BIOS won't allow booting from USB. You can check for the latest BIOS available for your laptop to see if that capability has been added.

---

### Post by Baylynx on 2010-08-06
> **Elmer Fudd said:**
> Are you talking about the "Boot Menu" in the BIOS Setup?
 
Yes, that's what I was referring to.
 
> **Elmer Fudd said:**
> If you are having problems with your CD writer and you have access to another computer (someone elses if not your own) the quickest fix here would be to create a new LiveCD on that computer. Of course, if your CD is bad, you might be SOL anyway.
 
I strongly suspect my CD drive is bad.
 
> **Elmer Fudd said:**
> The USB method that you are asking about does work, but not if your BIOS won't allow booting from USB.
 
Someone suggested that Unetbootin also gives you an option to emulate a hdd so your USB will boot. Anyone know how to do this?
 
> **Elmer Fudd said:**
> You can check for the latest BIOS available for your laptop to see if that capability has been added.
 
I'll check with HP.
 
Thanks.

---

### Post by Rex Bouwense on 2010-08-06
I have an old Dell Inspiron 1000 that didn't want to boot from a flash drive but I discovered that it considered the flash drive another hard drive.  I just configured the BIOS boot order to boot from that "hard drive" before it booted from the real hard drive.  It installed.  At the time, I also had a bad CD/DVD drive so I was in a similar situation.

---

### Post by snowpine on 2010-08-06
Hi Baylynx, curious if you have read [the Ubuntu system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")?

> The Recommended Minimum System Requirements, here, should allow even an inexperienced user to easily install a usable system with enough room to be comfortable. A good "rule of thumb" is that machines that could run Xp, Vista, Win7 or x86 OS X will almost always be a lot faster with Ubuntu. Simply try Ubuntu Cd as a LiveCd first to check the hardware works.

Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

If your computer is very old, you might be better off with Xubuntu.

Either way, you will need to find a way to boot the Live CD/USB. :)

---

### Post by Linux000 on 2010-08-06
If all else fails, and you have 6 weeks to wait(I'm not that patient) you can try this [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
Also, I have used SmartBootManager to boot on older computers, I don't know if it would work in your case though.

---

### Post by Baylynx on 2010-08-07
> **Rex Bouwense said:**
>  but I discovered that it considered the flash drive another hard drive. I just configured the BIOS boot order to boot from that "hard drive" before it booted from the real hard drive. It installed.
 
Interestingly enough... Setup Mode confirms only one local hard drive [C:]. However, the system configuration utility sees the following:
 
 
[LEFT][SIZE=3][FONT=Times New Roman]**[SIZE=3][FONT=Times New Roman]Local Disk (non-partitioned) FUJITSU MHV2060AH[/FONT][/SIZE]**[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3][C:] Capacity - 55.88 GB[/SIZE][/FONT][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]Used: 16.54 GB[/FONT][/SIZE][/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]Free: 39.34 GB[/FONT][/SIZE][/FONT][/SIZE][SIZE=3][FONT=Times New Roman]
[/FONT][/SIZE]**[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]Local Disk (non-partitioned) SanDisk U3 Cruzer Micro USB Device[/SIZE][/FONT][/SIZE][/FONT]**
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3][J:] Capacity - 1.90 GB[/SIZE][/FONT][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman][FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]Used: 334.41 MB[/SIZE][/FONT][/LEFT]
[SIZE=3][FONT=Times New Roman]Free: 1.57 GB[/FONT][/SIZE]
 
[/SIZE][/FONT][/FONT][/SIZE][/FONT][/SIZE]
I find this discrepancy very strange. Sooo, how did you configure the BIOS to see two local hard drives?
 
> **Rex Bouwense said:**
>  At the time, I also had a bad CD/DVD drive so I was in a similar situation.
 
Funny thing... huh?

---

### Post by Rex Bouwense on 2010-08-07
I didn't do anything to cause it to see two hard drives.  Before the splash I pressed F2 (I think) to get into set up.  I went to boot order and arranged the order the way I wanted.  Of course since the CD/DVD drive was a no-go at the time and it had not previously recognized the flash drive as a bootable drive, I noticed that there was a plus before hard drive.  I clicked on it to open it and discovered that it had my hard drive and then my flash drive.  I simply reversed the order so the flash drive would boot first.  I thought that it was odd at the time but it booted and I installed Ubuntu on my old Dell.  I have no idea why but it would be something to check if the computer will not boot from a flash drive and a CD drive is "not available."  By the way I now have a working CD/DVD drive in the Dell and a plug and play USB CD/DVD drive for my netbook.

---


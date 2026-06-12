---
title: "Rescatux on USB not bootable"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by actt2 on 2011-02-11
Downloaded and installed Ubuntu 10.4, updates upgraded it to 10.10. Had dual boot with Windows Vista working. Last Ubuntu update choked the system on reboot. It would boot as far as the version select menu (didn't show up) and then recyle itself back to start.
 
I installed Unetbootin and had a GUI with GRUB. While fooling around in the commands, I think I instructed Windows to "fix" the MBR and now I have lost my access to the partition with Ubuntu.
 
Downloaded Rescatux and extracted it onto a USB 2 gig flash drive. According to the instructions, one reboot is all that should be required to again have GRUB at my disposal. My boot order is USB, CD, HD. The computer will not boot up in the USB. Any hints as to how I can get my computer to recognize the flash drive?
 
Kinda panicking here.....have had Ubuntu long enough to transfer everything over and can't really afford to lose anything. From what I read, the fix should be easy enough if I can ever get access to GRUB again.
 
What am I overlooking with this USB thing? I'm a newbie.

---

### Post by robsoles on 2011-02-12
Welcome to UF!

It sounds like you might have simply copied the files onto the USB stick and never actually made it bootable.

Look: [http://www.techdrivein.com/2011/01/create-bootable-live-usb-drives-of.html](http://www.techdrivein.com/2011/01/create-bootable-live-usb-drives-of.html)

Any good?

---

### Post by tednix on 2011-02-12
Actt2's post got me worried because I had read that rescutux was supposed to be the answer to most GRUB problems.
I've downloaded the program and first tried to burn it to USB stick with StartUp Disc Creator and got an error.  I then used UNetbootin and the burn completed as it should.  However when I tried to boot form the USB nothing happened.  Could it be because my GRUB is intact?
Any way I will have to try burning a CD when I have more time.

---

### Post by robsoles on 2011-02-12
> **tednix said:**
> Actt2's post got me worried because I had read that rescutux was supposed to be the answer to most GRUB problems.
I've downloaded the program and first tried to burn it to USB stick with StartUp Disc Creator and got an error.  I then used UNetbootin and the burn completed as it should.  However when I tried to boot form the USB nothing happened.  Could it be because my GRUB is intact?
Any way I will have to try burning a CD when I have more time.

Sounds like either your BIOS is not set to try USB devices for booting first **or** the image file you downloaded was perhaps corrupt.

If when you say "nothing happened" you mean that it booted your desktop (or failed to boot it in the same way that made you get rescatux) then it is likely to be the BIOS settings - otherwise if the failure was pretty much entirely different then it is likely the corruption issue.

---

### Post by tednix on 2011-02-12
I checked the boot order and USB was first.  What I meant was that a normal GRUB selection screen came up which indicated to me that Rescutux did not boot first,  Next step is to find and run the checksum numbers.
Have you gotten Rescutux to boot from a USB stick?

---

### Post by robsoles on 2011-02-12
I apologise to have to say that of half a dozen systems that 'suddenly wouldn't boot' I have managed to get them flying again without referring to rescatux.

I've been working from experience of dealing with bootable disc images etc.

Trying to Google for rescatux behaviour I gain the impression that the rescatux image should boot and offer some options regardless of the state of your grub installation status - I imagine I can find the time later today: I will grab the ISO off the internet and burn it straight to a blank disc (no spare USB stick to do it to!) and boot a couple of systems here from it before saying too much more about it :roll:

---

### Post by tednix on 2011-02-12
I used a copy of Rescatux that I had dl several days ago and tried to burn an iso cd but Brasero would not recognize the file.
So I dl a second copy tonight and now Brasero managed to make the CD which works fine in both my laptop and netbook.  Next I tried UNetbootin to make a USB image but could not get that to boot in my netbook.  I have yet to try it on the laptop.

---

### Post by actt2 on 2011-02-12
When the Rescatux extraction was finished, I have folders .disk, isolinux, live, BOOT, and others.  The file in the BOOT folder is "Bootable Noemulation.img"
 
I'll do some reading on the link you provided and see what I did wrong.  Hope it's as simple as that.
I appreciate the help.

---

### Post by uRock on 2011-02-13
Rescatux has their own forums as well, which may be a great resource for this type of problem. [http://www.supergrubdisk.org/forum/](http://www.supergrubdisk.org/forum/)

Documentation [http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

---

### Post by robsoles on 2011-02-13
> **actt2 said:**
> When the Rescatux extraction was finished, I have folders .disk, isolinux, live, BOOT, and others.  The file in the BOOT folder is "Bootable Noemulation.img"
 
I'll do some reading on the link you provided and see what I did wrong.  Hope it's as simple as that.
I appreciate the help.

It really does sound like you are using the archive-manager to extract the contents  of the ISO file onto your USB stick and that's just not going to work - no bootloader on the USB's MBR (simile), no partition marked as bootable on it either; no chance to boot.

If you have an operable Ubuntu desktop then look in 'System'->'Administration' for 'Startup Disk Creator' if it's there then have a poke and fiddle with it and see if you can make yourself a bootable stick using the ISO with that - failing that the 'unetbootin' that the page at my link carries on about works in Windows and Ubuntu, see if you can do it with that.


I tried the latest rescatux from [http://www.supergrubdisk.org/category/download/rescatuxdownloads/](http://www.supergrubdisk.org/category/download/rescatuxdownloads/). It is functional as a LiveCD, appears capable of booting from that  single CD for 32 bit or 64 bit session, and also appears to have some  righteous tools for recovering a system - can't wait till one of my  users has a borked start up again :)

---

### Post by tednix on 2011-02-13
Got my UNetbootin install of Rescatux to a USB stick to work on my laptop.  I'm not sure why it's not booting on my netbook.

My USB stick contains the following folders: doc, isolinux, live and ubninit.  
It also contains 3 text files and ldlinux.sys, menu.c32, ubnkern and syslinux.cfg.

---

### Post by actt2 on 2011-02-16
I did a frugal install of Ubuntu in C: and then used Gpart to partition and prep the USB drive.  Then went to Startup Disk Creator in Ubuntu to create a startup from Rescatux.iso which I have downloaded on a CD.  The process goes to 47% at which time it stops with an error message saying can't continue.  Soooo.......  reformatted the USB, blanked the CD.........starting over.  Not sure what's wrong as I can't decipher the error message.  (all that hexadecimal jibberish).
Still struggling with it.  Have ordered a LiveCD with Ubuntu 10.10 but don't expect to get that for a few weeks if their predictions are correct.

---

### Post by robsoles on 2011-02-16
Sorry to hear it's still being a struggle to you, this may be indicating failed Hdd controller in your computer or failing USB drive or something of that nature.

You might have better luck making a rescatux bootable USB using a friend's (or Library) computer perhaps?

---


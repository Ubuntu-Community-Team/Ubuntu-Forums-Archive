---
title: "Dell Inspiron 910 - Trying to figure 8.10 install"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by freykatt on 2009-02-22
Hi all, just received this mini w/atom. Hooked up external cdrw.  Will not go "live". My question = How to set bios to boot to usb external cdrw.  I have tried in bios to set but, cannot figure out to "save" setting. everytime I try to set, the cdrw flashes, but puutor still boots to xp.  It does (grub?) come for choice, but does not boot to 8.10.  8gb flash drive , no hD.  500mb mem. 




t

---

### Post by ikonia on 2009-02-22
I think you need to be clear here.

1.) the bios needs to have a boot order of USB first, then you need to read our BIOS manual for how to save

2.) your USB device should be a CDrom, which you say it is, and it should contain a valid Ubuntu 8.10 CDrom.

3.) what is the 8GB usb device you meation, I'd advise you to only have one USB device in while trying to boot from USB. 

4.) if the CDrom boots you should say a graphical screen with the ubuntu logo on.

---

### Post by freykatt on 2009-02-22
Thanks Ikonia, bios -= I clicked on usb first, but no way to save the setting.  However, one will see the boot up trying to load, but it does not load.  at prompt type help for more options, nothing worked.  I will search for the Bios report.  8gb is the atom flash drive - no real HD.

May I should just go ahead and uninstall xp first, but would love to at least try the Live Ubuntu.   Thanks for your reply.

---

### Post by sandyd on 2009-02-22
> **ikonia said:**
> I think you need to be clear here.

1.) the bios needs to have a boot order of USB first, then you need to read our BIOS manual for how to save

2.) your USB device should be a CDrom, which you say it is, and it should contain a valid Ubuntu 8.10 CDrom.

3.) what is the 8GB usb device you meation, I'd advise you to only have one USB device in while trying to boot from USB. 

4.) if the CDrom boots you should say a graphical screen with the ubuntu logo on.

ikona, heres what i think hes saying

he has NO HARD DISK
hes booting from a USB CD ROM
and he wants to install ubuntu to his FLASH DRIVE

correct?

try this
unplug the usb drive
stick the usb connector of the external cdrom to where the usb drive was plugged in before
stick the usb drive into the slot that the cdrom was plugged into a few seconds ago.

---

### Post by sandyd on 2009-02-22
> **freykatt said:**
> Thanks Ikonia, bios -= I clicked on usb first, but no way to save the setting.  However, one will see the boot up trying to load, but it does not load.  at prompt type help for more options, nothing worked.  I will search for the Bios report.  8gb is the atom flash drive - no real HD.

May I should just go ahead and uninstall xp first, but would love to at least try the Live Ubuntu.   Thanks for your reply.
whatdo you mean it can't save

---

### Post by freykatt on 2009-02-22
Dell Inspiron 900, 8gb internal drive of somekind, 500mb mem.,I downloaded drivers for my old Buslink USB CDRW to insert my Ubuntu 8.10 Live disk.  The Bios shows a USB and a Removable storage unit.  First tried to change bio to USB boot first - no worki., secondly - tried the removable storage unit - no worki, still boots to xp.  I don't remember how, but one time I clicked on cdrw, right clicked on Ubuntu, a window opens with three choices. One to install, another for I believe "live" and the third choice - something about some kind of help?, when I clicked on it , it on reboot gives me a grub menu and I chose ubuntu.  It proceded to try to load, but stalls and tells me to type in "help" for a list of commands, nothing workis.  end of line.

---

### Post by ikonia on 2009-02-25
you need to speak to and discuss this with your hardware vendor.

---

### Post by notwen on 2009-02-25
The Dell Mini 9s come w/ a Solid State Drive, not a Hard Disk Drive.  The Minis ship w/ a 4GB, 8GB and 16GB SSD.  I believe they're saying they want to install to their 8GB SSD.

I have a Mini and I can't recall any difficulty changing my boot order in BIOS, but once I'm home I'll see if there was any certain trick to save changes you've made in BIOS.  =]

---

### Post by freykatt on 2009-02-25
Hi all, thanks for the replies.  Yes, 8gb SSD, not HD. I finally figured out how to "save" the Bios change.  Now then, all I want to do is dump xp and load Ubuntu or a derivitive of same.  As I mentioned, I finally was able to (supposedly) load ubuntu 8.10 as grub pops up, but will not, after showing the logo and progress screen, load. On one try, a pop up states that not enough room on the drive.  I believe it would be a lot simpler if done with a thumb drive, but being really dumb about working with thumb drives and the reading about how to on thumb drives, still haven't been able to do the thumb drive thing.  Will get this thing figures one day.   Thanks to all.         Dick

---

### Post by notwen on 2009-02-25
Download [Unetbootin]("http://unetbootin.sourceforge.net/").  It can download the latest Ubuntu image and a couple of other major distro releases and install it onto a USB flash drive.  You can then proceed to use the Ubuntu installer to resize your XP partition/remove it/whatever you wish to do and then install Ubuntu.  I personally have a 16GB SSD on my Mini 9 and am still stressed for room, I've added in a 16gb SDHC card to use for storage.  Post if you have any issues and/or questions.  =]

---


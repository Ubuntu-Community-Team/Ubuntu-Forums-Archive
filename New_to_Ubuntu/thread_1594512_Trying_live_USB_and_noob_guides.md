---
title: "Trying live USB and noob guides"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by BKbroila on 2010-10-12
Before installing ubuntu, I'd like to at least try it. So I've got the ISO on a live USB, but wanted to ask here whether there was anything I should be wary of while trying it out. Is there anything during the process that I should try (Wine, anything else)?

A technical question: if I change the boot order in BIOS so that it boots from USB first, do I have to restart my computer, or will it restart it by itself and look at USB? I've got the ISO on the main directory of my USB drive with several other folders; would that be a problem, or can I leave everything else on there?

And lastly, I've read tons of guides or first-timers and newbies, but if there are others, I'd be happy to read them. Any links to guides, documentation would be great!
Thanks!

---

### Post by celticbhoy on 2010-10-12
First things first,

Have you made a usb startup disk, or just copied the iso onto a usb drive?

---

### Post by Hippytaff on 2010-10-12
You might already have read this but it's worth posting - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 
also I had problems with 10.10 usb live, and from the posts I've read so have other people - in the end it was easier to burn a live cd (ie burn the iso to cd) and try it that way.
 
when you change the boot order to usb it should just restart automatically and look for a bootable usb before your hard drive.

---

### Post by C.S.Cameron on 2010-10-12
I downloaded the iso, checked it's MD5SUM, burnt it to CD, booted the CD and then used Startup Disk Creator on the CD to install it to flash drive.
Ubuntu runs better from USB than from CD.

---

### Post by celticbhoy on 2010-10-12
Ok, was just checking. If you set your boos to boot from Usb first, then when you save & exit it should boot from your USB without problem. 
As for things to be wary of, nothing really.  What to try, well that depends what you use your PC for.

---

### Post by BKbroila on 2010-10-12
Quick question: I'm confusing myself over this: when running the usb-creator.exe file, I should point to the ISO file on the USB drive, correct? I'm doing so, and nothing is showing up in the 'Make Startup Disk' window's ISO selection pane.

---

### Post by celticbhoy on 2010-10-12
> **BKbroila said:**
> Quick question: I'm confusing myself over this: when running the usb-creator.exe file, I should point to the ISO file on the USB drive, correct? I'm doing so, and nothing is showing up in the 'Make Startup Disk' window's ISO selection pane.

copy all the files you have on your usb disk to your hard drive.
then run the usb-creator.exe and point to the iso file on the hard drive, then you should be able to create the usb startup disk

---

### Post by admiralspark on 2010-10-12
When 'burning' an ISO to usb, you should probably use UNetbootin. It's graphical and seems to work with just about every linux release (I've had one no-go and 16 working so far). Do not place the iso ON the usb, place it in a folder on the computer.

---

### Post by BKbroila on 2010-10-12
Sorry, but for some reason, this isn't working... I feel like an idiot.
I've got my USB cleaned out except for the installer.exe file. I've run it tried pointing to the .iso file on my desktop, but it doesn't come up in the installer...
Do I need Virtual CloneDrive right now? Could that be the problem?

---


---
title: "Hi I'm in a lot of trouble - Natty 11.04 purple screen"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Digitonin on 2011-06-11
I got a new system recently and decided to instead of opting for the Windows route, go for Natty 11.04 and try and get it working.

However, after fiddling with the propitiatory drivers to get WoW working with my video card, I rebooted and hung on a purple screen.

I keep hanging on this blasted purple screen - currently posting on a Win7 laptop as the desktop is COMPLETELY inaccessable.

It's extremely important that I get 1 file from the hard disk onto a usb pen drive, so my question;

How do I fix the purple screen issue? Or, even better;
How do I use the terminal to access my hard drive and transfer the file across.

My current knowledge is slim so I appreciate all the help!

---

### Post by VOT Productions on 2011-06-11
Try a live CD.

What is your video card?

---

### Post by WannabeFantasma on 2011-06-11
Try using a live dvd, boot up and try to locate the file and copy it to a USB drive?

---

### Post by sanderd17 on 2011-06-11
If you just want to save your files, a live CD is the best option, and that almost always works (unless you really removed it).

Repairing Ubuntu will be more difficult. I've never heard someone hanging on the purple screen. Could you hit the 'e' in the grub menu (where you choose your OS) and remove the words "quiet splash" and press ctrl+x to boot. Than you will see the terminal output of the boot, look where it hangs. (maybe take a picture of it).

---

### Post by Digitonin on 2011-06-11
Hi,

Video card is an ATI Radeon HD 5500.

I've booted up a LiveCD and am on the problem computer now, not sure how to access the files from here, any tips?

---

### Post by WannabeFantasma on 2011-06-11
just go to the map on the "bar" (not sure how it's called)
(the upper most icon)

and "mount" the drive where the file is located and search it

---

### Post by Digitonin on 2011-06-11
Nailed it.

Thanks guys! Really appreciate it! ;)

---

### Post by VOT Productions on 2011-06-11
Go to recovery mode in GRUB, and then use the "resume" option. Then do sudo apt-get install fglrx (This is the ATI driver)

---


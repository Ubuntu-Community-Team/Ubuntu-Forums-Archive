---
title: "Kernel Panic"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by RayleenCourtney on 2010-07-01
I was in the middle of an upgrade to Ubuntu 10.04 when my laptop was powered off. On trying to power it back on, I get the message:

*[ 0.709641] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)*

Is this something I will have to have fixed professionally, or is there a process I can undertake?

---

### Post by k3lt01 on 2010-07-01
If you are able to install via a LiveCD that will be your best option in my opinion. Are you able to? if you are you will need to back up your /home directory first as 10.04 has a different file system type as standard than does 8.04. This is just to mak sur you don't lose vital information and settings

Let us know and we can walk you through it if you need to.

---

### Post by RayleenCourtney on 2010-07-01
Well the good news is that I purchased the laptop just today with Ubuntu 8.04 already on it-- so I don't have any personal files to speak of on it. Phew!

Since I can't access my operating system at all any more, I would love a walk-through of installing via a LiveCD! \\:D/

---

### Post by da burger on 2010-07-01
This is a pretty easy task but it does take some time. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) <-that page walks you thgough it. If you have anyother questions just ask. 
 
This page (and the site as a whole) will be helpfull as well -> [http://psychocats.net/ubuntu/getting](http://psychocats.net/ubuntu/getting)
 
NB Just so you know that page is for downloading 10.04. Some people still prefer 8.04 and it is still supported but the recomendation is that you get 10.04

---

### Post by RayleenCourtney on 2010-07-01
I've got a CD already, I'm just not sure how to go about installing it when I can't access Ubuntu. It won't run automatically, either-- when I put it in and turn on my computer, I get an "Error reading boot cd" message... followed by two columns with various numbers in them that say "data" and "prog" at the top of them.

I may be in over my head here.

---

### Post by k3lt01 on 2010-07-01
The psychocats page is a really good resource.

Have you got another PC you can test the CD on? If you have it will help us discount a faulty CD.

Is the CD clean? I wouldn't normally advise this but if you have a very soft cloth dampen it, just damp not dripping wet, and give the CD a wipe.

---

### Post by 2edgesword on 2010-07-01
**If the computer is already attempting to boot from the CD then this procedure is probably not the answer to your issue...**
 
Your computer may not be set to automatically run/boot from the CD.
 
You can switch boot priority by turning on the system and hitting the "Esc" key as soon as you hear the computer go on. That should open up a screen that shows your current bios settings and somewhere on the screen there should be an option to move around and change particular bios settings including the boot priority. Usually the default setting is to boot from the hard drive but you can reset it to boot from a CD.
 
You'll have to follow the instructions on the screen for which keys to hit in order to select which aspect of the bios you want to change and how to change the setting.
 
Once you make the change you have to save it and reboot the system. Again, there should be instructions on the screen for saving the new settings.
 
When the computer reboots it should boot from the CD and then just follow the step by step instructions for installation.
 
BTW, if hitting the "Esc" key doesn't get you into the bios options screen try looking up the correct function key by doing a Google search using the make/model of computer and the words "changing boot priority". Sometimes other function keys are used (F2, F8, etc.) for getting you into the system bios.

---

### Post by RayleenCourtney on 2010-07-01
Yes, I've tried from two different discs (one belonging to a friend). Neither one of them work-- though, I don't get the error message from my friend's disc, just the same "Kernel Panic" message after I select 10.04 from the boot menu.


2edgesword- It is set up to boot from a cd before the hard drive, but still just isn't responding to either of these discs.

---

### Post by k3lt01 on 2010-07-01
Rayleen, does your computer allow booting from a USB device? If it does that may be a better way to install as you may have other issues.

Could you give us some information about your computer. Make, model, motherboard, memory, cpu etc?

---

### Post by RayleenCourtney on 2010-07-01
I don't think it does, but I could be wrong. My options in the boot menu are:
Internal HDD
CD/DVD/CD-RW Drive
Cardbus NIC
Onoard NIC
BIOS Setup
Diagnostics

The laptop is a Dell Latitude 110L, Pentium(r) M Processor 1.70 GHz, Total memory is 512 MB

---

### Post by k3lt01 on 2010-07-01
ok, the only thing I can suggest at the moment then is that you download a new iso image on another PC and burn it to a disk. If you do this make sure you burn it at the slowest speed available as it helps to stop burning errors. I would also suggest that you choose the "Alternate" CD option as your memory while being enough is getting on the low side for using a LiveCD.

---

### Post by k3lt01 on 2010-07-06
How did you go with this Rayleen?

---

### Post by RayleenCourtney on 2010-07-06
Oh my goodness, I have kept meaning to log in here and update you. =)
I used a program called Darik's Nuke & Boot to just wipe the computer of all it's data and then was able to boot using the Ubuntu disc and install it. I guess I'll never know what the problem was-- but I am so very glad it is fixed. Lucky for me, it was a new-to-me refurbished laptop and I had absolutely no personal files on it whatsoever.

Thank you SOOOO MUCH for your help on this! This forum is amazing. I'm sure I'll be back. =)

---


---
title: "No audio in ubuntu"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by mustis81 on 2010-12-25
When i enter the command line "lspci -v | less" in terminal it doesnt show any sound card installed but when i switch to windows ( i have ubuntu dual booted ) audio works just fine. The output of the command is as follows:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 33
Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
I/O ports at 4050 [size=8]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
Subsystem: Hewlett-Packard Company Device 1425
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at d4406100 (64-bit, non-prefetchable) [size=16]
:

When i checked for sound devices in windows it said i have Realtek High Definition Audio Speakers. The driver name is RTKVHD64.sys if that helps too. Thank you in advance for any advice offered!

---

### Post by kesman on 2010-12-25
Please do
```
lspci > lspci.txt
```
and attach the lspci.txt file it creates to your reply. Maybe it's hidden somewhere :P

---

### Post by mastablasta on 2010-12-25
also which ubuntu are you running (10.04 or 10.10)?

---

### Post by mustis81 on 2010-12-25
lspci > lspci.txt doesnt do anything when i enter it into terminal (im assuming thats what you meant). It just goes to the next blank line.

Im using version 10.04

---

### Post by tushar maroo on 2010-12-25
install **alsamixer** with** graphical interface** from the **ubuntu software centre.**.......and** see **is there **anything muted or not**.......i think it will help you out.......it **worked for me.**:popcorn:
Please remember to mark the thread "solved" if we have success helping you out. This helps people to look for help later on.

---

### Post by mustis81 on 2010-12-25
Nope, alsamixer said nothing was muted. It did say that both card and chip were pulse audio. I dont know if that helps or not. From the info in my first post does it look like ubuntu is detecting my soundcard?

---

### Post by mustis81 on 2010-12-26
Just found out that i get audio when i plug headphones in. Anyone know how to get ubuntu to recognize my speakers?

---

### Post by kesman on 2010-12-27
Seems like it is if you get sound with the headphones.
Type alsamixer in terminal and browse through everything to see if they are muted. Note that you have to press TAB to view all channels.


> **mustis81 said:**
> lspci > lspci.txt doesnt do anything when i enter it into terminal (im assuming thats what you meant). It just goes to the next blank line.
It's not supposed to print out anything. It creates a file called lspci.txt to the current directory, usually /home/username if you didn't change it.

---

### Post by mastablasta on 2010-12-27
> **mustis81 said:**
> 
Im using version 10.04

if you are still having problems with no sound or sound &card dissaperang after a while you can upgrade the drivers (ALSA) following this guide: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

or there is also a script for the upgrade if you hate copy pasting the commands.

make sure that after upgarde you lock all the ALSA packages in synapticso they don't get *downgraded* by system updates.

---


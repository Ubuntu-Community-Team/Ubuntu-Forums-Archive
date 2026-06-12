---
title: "slow boot up time w/ 10.04"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by cd91780 on 2010-05-08
Hi everyone
I have just clean installed 10.04 netbook version on my toshiba nb205. The boot up time is almost 10 minutes. Can someone help with an answer/fix? Thank you in advance.

---

### Post by Pratheek on 2010-05-08
Hey, 

What's ur RAM size ??? is it something like 1 GB ??

---

### Post by sadaruwan12 on 2010-05-08
Please, Stat your system spec so w can have a better idea.

---

### Post by cd91780 on 2010-05-08
Hello, thanks for the replies.

Here's the specs of my netbook.  I  tried the update manager but it says not all updates can be installed.


Intel Atom N280 1.66GHz Processor
1GB DDR2 RAM
160 GB Hard Drive
5800 mAh 6-Cell Battery
Processor, Memory, and Motherboard
Hardware Platform: PC
Processor: 1.66 GHz Intel Core Solo
System Bus Speed: 667
Number of Processors: 1
RAM: 1000 MB
RAM Type: DDR2 SDRAM
Hard Drive
Size: 160 GB
Type: Serial ATA

---

### Post by BT1 on 2010-05-08
> **cd91780 said:**
> Hello, thanks for the replies.

Here's the specs of my netbook.  I  tried the update manager but it says not all updates can be installed.


Intel Atom N280 1.66GHz Processor
1GB DDR2 RAM
160 GB Hard Drive
5800 mAh 6-Cell Battery
Processor, Memory, and Motherboard
Hardware Platform: PC
Processor: 1.66 GHz Intel Core Solo
System Bus Speed: 667
Number of Processors: 1
RAM: 1000 MB
RAM Type: DDR2 SDRAM
Hard Drive
Size: 160 GB
Type: Serial ATA

The Intel Atom N280 1.66GHz processor is a single core? I have the N270 1.6 and it has two logical CPUs (dual-core-ish). My netbook is older than yours I suppose, but its an acer yet I don't have the start-up issues you have. I have Lubuntu, Ubuntu, Xubuntu, and the Netbook edition installed on different partitions and it still doesn't lag on start-up like what you explain. Perhaps bad install? Did you mess with the boot settings or something?

Try this though, go to the Ubuntu Software Center and download these two programs (just start typing the first four letters in the search):

BootUp-Manager
StartUp-Manager

Then mess with the settings a bit to see if it speeds up the boot process. I personally disable Bluetooth, Scanner, Cups (printing), Hardware and Software Auto Update Search (this is because I can manually do it once a week to save start up time). 

That's just a few tweaks you can try.

---

### Post by neoanderthal on 2010-05-23
[QUOTE=BT1;9264108]The Intel Atom N280 1.66GHz processor is a single core? I have the N270 1.6 and it has two logical CPUs (dual-core-ish). My netbook is older than yours I suppose, but its an acer yet I don't have the start-up issues you have. I have Lubuntu, Ubuntu, Xubuntu, and the Netbook edition installed on different partitions and it still doesn't lag on start-up like what you explain. Perhaps bad install? Did you mess with the boot settings or something?

N270 and N280 Atom processors are single core processors - they are Hyperthreading-enabled, which makes them appear as two logical processors. However, they are not true dual-core processors, like the 330.

To resolve the boot issue with the Toshiba, enter the BIOS [F2] after you power it on, switch to the [Advanced] tab, and change the SATA controller mode from 'AHCI' to 'Compatibility'. That should put your boot time at around 30 seconds or so.

---

### Post by Crouton80 on 2010-06-28
> **neoanderthal said:**
> 

To resolve the boot issue with the Toshiba, enter the BIOS [F2] after you power it on, switch to the [Advanced] tab, and change the SATA controller mode from 'AHCI' to 'Compatibility'. That should put your boot time at around 30 seconds or so.

Hi there,

I am running Ubuntu in a dual boot environment with Windows 7 Starter on a Toshiba NB305. I have found problems with slow boot up: after selecting the latest Ubuntu build (2.6.32-22-generic) in the grub menu, I get a flashing cursor in the top left corner of the screen for a few minutes, and then finally X loads into the GUI.   

The above fix works for me booting into Ubuntu, shortens the time to about 30 seconds. Nice. The only problem is then when I want to boot into Windows, I find that it won't boot with the SATA controller still set to compatability. It's a bit annoying when I want to change OS to have to go into BIOS and change settings... are there any other ideas out there for a fix for this problem, without having to change the SATA settings?


Thanks.

---

### Post by Cason on 2010-07-02
> **neoanderthal said:**
> [QUOTE=BT1;9264108]The Intel Atom N280 1.66GHz processor is a single core? I have the N270 1.6 and it has two logical CPUs (dual-core-ish). My netbook is older than yours I suppose, but its an acer yet I don't have the start-up issues you have. I have Lubuntu, Ubuntu, Xubuntu, and the Netbook edition installed on different partitions and it still doesn't lag on start-up like what you explain. Perhaps bad install? Did you mess with the boot settings or something?

N270 and N280 Atom processors are single core processors - they are Hyperthreading-enabled, which makes them appear as two logical processors. However, they are not true dual-core processors, like the 330.

To resolve the boot issue with the Toshiba, enter the BIOS [F2] after you power it on, switch to the [Advanced] tab, and change the SATA controller mode from 'AHCI' to 'Compatibility'. That should put your boot time at around 30 seconds or so.

That worked really well for me (I'm running 10.04 on an NB205). Thanks a lot!

---

### Post by Jeffrey_Tech on 2010-09-28
Hey all. Here's what I did.... 
Poor kernel was waiting for interrupt events that were never to occur... HENCE,

THis is with the following grub version:

# grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu1

I edited /etc/default/grub as follows:

GRUB_CMDLINE_LINUX=""
changed to
GRUB_CMDLINE_LINUX=acpi_skip_timer_override

Then ran update-grub

My SATA controller setting is AHCI, NOT compatibility.

This seems to have dropped my boot time from 30 minutes to login screen to 22 seconds. 

I hope this helps someone.... This is my first post, so go easy one me.

-Jeffrey

---

### Post by mpswoodwal on 2010-10-11
> **Jeffrey_Tech said:**
> 
THis is with the following grub version:

# grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu1

I edited /etc/default/grub as follows:

GRUB_CMDLINE_LINUX=""
changed to
GRUB_CMDLINE_LINUX=acpi_skip_timer_override

Then ran update-grub


Thanks!! worked perfectly for me.

-M

---

### Post by Madmoose on 2010-10-13
> **Crouton80 said:**
> Hi there,

I am running Ubuntu in a dual boot environment with Windows 7 Starter on a Toshiba NB305. I have found problems with slow boot up: after selecting the latest Ubuntu build (2.6.32-22-generic) in the grub menu, I get a flashing cursor in the top left corner of the screen for a few minutes, and then finally X loads into the GUI.   

The above fix works for me booting into Ubuntu, shortens the time to about 30 seconds. Nice. The only problem is then when I want to boot into Windows, I find that it won't boot with the SATA controller still set to compatability. It's a bit annoying when I want to change OS to have to go into BIOS and change settings... are there any other ideas out there for a fix for this problem, without having to change the SATA settings?


Thanks.

Yes. I'm have this issue too. I've been looking all morning for an alternative fix for this, and there doesn't seem to be. Looks like I'll just have to change the bios every time I need to get into windows. Which isn't very often anyway.

---

### Post by alek01 on 2010-11-29
Thanks a million Jeffrey!
I had spend many long hours trying to solve that issue.
Now I finally can use my NB205 with Ubuntu Remix 10.10
Bye for now,
Alek

---

### Post by ThomasPWillickers on 2010-12-13
Thanks so much for this post.  The original poster had the EXACT same issue as myself.  You saved me from a lot of misery.  I thought that installing Ubuntu had toasted my machine.  It's nice to know that there are people out there who actually care if other people have a satisfactory user experience.

---

### Post by Fende on 2012-06-05
Thank you for your post, Jeffrey_Tech. Same solution still works with Ubuntu 12.04 version.

> **Jeffrey_Tech said:**
> Hey all. Here's what I did.... 
Poor kernel was waiting for interrupt events that were never to occur... HENCE,

THis is with the following grub version:

# grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu1

I edited /etc/default/grub as follows:

GRUB_CMDLINE_LINUX=""
changed to
GRUB_CMDLINE_LINUX=acpi_skip_timer_override

Then ran update-grub

My SATA controller setting is AHCI, NOT compatibility.

This seems to have dropped my boot time from 30 minutes to login screen to 22 seconds. 

I hope this helps someone.... This is my first post, so go easy one me.

-Jeffrey

---

### Post by Elfy on 2012-06-05
Old thread closed.

---


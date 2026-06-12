---
title: "Atheros Wireless stopped working suddenly?"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by IT_Slave on 2007-06-30
I am a little new to the world of Ubuntu after years of working with MS products. My laptop has:

Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter

This was functioning fine until I booted up the machine this morning. The card does not appear when running ifconfig or any wireless appears in network manager. I also tried an external wireless card in my card slot which also is atheros chipset based and also failed to work.

When I boot the machine into the previous kernel - kernel 2.6.20-15-generic - both devices work fine. But under kernel 2.6.20-16, I experience the issues I reported. I suspect maybe it has to do with system updates installed recently?? 

Please point me in a direction to solve the problem so I can use kernel 2.6.20-16 again.

Thanks

---

### Post by tgalati4 on 2007-06-30
You provided useful info in that it worked with the previous kernel.

Post relevant portions of:

>dmesg

and

>lsmod

and

>aplay -l

---

### Post by IT_Slave on 2007-06-30
Yes - it used to work under the new kernel, but now only under selecting via Grub to boot old kernel.

I think this is the relevant info:

>dmesg:

[   24.136000] ath_pci: disagrees about version of symbol _ath_hal_attach
[   24.136000] ath_pci: Unknown symbol _ath_hal_attach
[   24.136000] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   24.136000] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   24.136000] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   24.136000] ath_pci: Unknown symbol ath_hal_computetxtime
[   24.140000] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   24.140000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   24.140000] ath_pci: disagrees about version of symbol ath_hal_detach
[   24.140000] ath_pci: Unknown symbol ath_hal_detach
[   24.140000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   24.140000] ath_pci: Unknown symbol ath_hal_init_channels
[   24.140000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   24.140000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

>lsmod:
wlan                  204868  0 
ath_hal               233824  0

>aplay-l:
No relevant information to ath0

---

### Post by IT_Slave on 2007-06-30
I was able to correct the issue by re-installing madwifi. I am not sure why it stopped working all of a sudden.. since it has been working great since I installed Ubuntu a couple months ago...

Oh well.. its working under both kernels now....

Thanks anyways

---

### Post by Pekay on 2007-06-30
Hey, I got the same problem as you did, I had an update for linux-restricted-modules. Reboot and no wireless :((. How do you reinstall madwifi?

---

### Post by IT_Slave on 2007-06-30
I followed this the manual install part. --

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Hope it helps you too...

---

### Post by tgalati4 on 2007-07-01
Sorry about the aplay -l (I was thinking about sound cards for some reason--that's definitely a brainfart).

It looks like by reinstalling Mad WIFI, it saved a new file of digital radio settings.  These settings are used for reliable communication.  Using the old settings file with the new kernel would cause problems.

Your dmesg file hints at this:  things such as noise floor and computer TX time are related to radio performance.

This points to a larger issue with Ubuntu:

Upgrading a working system causes a non-working system and no end of grief.

You were clever enough to boot into your old kernel (some people don't realize that is why old kernels are kept around like old shoes) to get networking back.

One must anticipate that an update to the kernel could cause ANY hardware to stop working.  That is the nature of kernel development.  Fix a few things, add a few features, and then discover that several things broke in the process.

We are conditioned under Windows to download every service pack and patch available.  And do it blindly, because Windows doesn't work right in the first place, so a patch has to be A Good Thing (TM).

Under Linux, if you have a working system on a production machine (one that you wouldn't want to lose even for one hour), then you have to be ubercareful about updating.

My gripe is that the the updates don't include descriptive data.  What's up with that?  I usually like to read a summary of what changed, what got fixed, but it always comes up blank in the Update Manager.  Is it that hard to add change info to Update dialog box?

That way you can make a semi-informed choice about what parts of Ubuntu to update and what parts to leave alone--all in the interest of keeping your machine running round-the-clock.  When you've used Ubuntu with several months of uptime (165 days for one of my machines) you get upset when you lose sound, or video, or networking after an update.

---

### Post by stchman on 2007-07-09
> **IT_Slave said:**
> I am a little new to the world of Ubuntu after years of working with MS products. My laptop has:

Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter

This was functioning fine until I booted up the machine this morning. The card does not appear when running ifconfig or any wireless appears in network manager. I also tried an external wireless card in my card slot which also is atheros chipset based and also failed to work.

When I boot the machine into the previous kernel - kernel 2.6.20-15-generic - both devices work fine. But under kernel 2.6.20-16, I experience the issues I reported. I suspect maybe it has to do with system updates installed recently?? 

Please point me in a direction to solve the problem so I can use kernel 2.6.20-16 again.

Thanks

When you get a kernel update you need to make the madwifi drivers for that particular kernel.

---

### Post by mytik on 2007-07-15
I got the same problem :( but i got a poor solution! Restart over Restart, Shutdown over Shutdown :(
After a few times, the driver is completly loaded. Don't know why it happens but it's annoying. Must find out another solution.

---

### Post by mytik on 2007-07-15
Yet, after 30 reboots the atheros works again :)

---


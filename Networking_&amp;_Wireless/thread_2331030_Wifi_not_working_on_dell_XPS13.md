---
title: "Wifi not working on dell XPS13"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by colt4530rs2 on 2016-07-17
O.K., I bought a Dell XPS13 with 64-bit Ubuntu 14.04 LTS installed by Dell.  I have the same device as Max.  
lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

After the last software update, including GRUB 2.0 (?) and kernel image  3.13.0.92.99 (?) my wifi was disabled, but the bluetooth tranceiver, on  the same card still works.  I was watching for this and I am sure the  update is what killed the wifi transceiver, this time.  

The link to the newer Broadcom driver above does not work.  Where can I get the newer Driver?

---

### Post by jeremy31 on 2016-07-17
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2289270](https://ubuntuforums.org/showthread.php?t=2289270)

Please see the wireless script link in my signature and post the results

Welcome to the forums

---

### Post by colt4530rs2 on 2016-07-19
I was able to find bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2 and dkms_2.2.0.3-1.1ubuntu5.14.04.6 using Synaptic Package Manager and forced the upgrade.  After a reboot, my wireless works!  The process did require agreeing to disable UEFI and entering a password, that I have not been required to reuse, though the instructions indicated I would.  

Thanks for the help!!!

I'm sure there is a terminal command(s) that would not require a reboot, but this is a "see what you're doing" version and I forgot all the terminal commands I knew, in the '90s.

---


---
title: "[SOLVED] Wifi after this morning's updates"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Cilionelle on 2008-06-19
Okay guys, seems like this one is a reasonably fairly oft presented concern.  I installed the latest updates this morning and then, upon restarting my computer, had my wifi vanish in a puff of ethereal smoke.

How do I restore it?  I am using the ath_pci drivers for the AR5007EG wifi card, but have no device to scan with (only 'lo' and 'eth0').  After running 'lshw -C network', the computer lists it as a device onboard, but doesn't assign it a logical name (unlike the wired connection).  I can't run through Kevdog's tutorial (which has worked in the past) since I don't have the device name.

Where do I go from here?

Cheers!

---

### Post by dmizer on 2008-06-20
post the output of:
```
lshw -C network
```

---

### Post by Cilionelle on 2008-06-20
Here it is:

```
$ lshw - C network
WARNING: You should run this program as a super-user.
  * - network UNCLAIMED
         description: Ethernet controller
         product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
         vendor: Atheros Communications, Inc.
         physical id: 0
         bus info: pci@0000:01:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: cap_list
         configuration: latency=0
  * - network
         description: Ethernet interface
         product: RTL-8139/8139C/8139C+
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 1
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 10
         serial: 00:1e:ec:15:1e:12
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuation: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

I've also had a bit of trouble with the wired LAN not working (I've just had to type this out as a result).  Haven't looked into it at all, couldn't be bothered with that at this stage, but I am wondering if the two are linked.

---

### Post by dmizer on 2008-06-20
what did you to previously to make the card work, or did it work "out of the box" as they say?

---

### Post by Cilionelle on 2008-06-20
If I could remember that, I would have done it!  Ha!  Seriously, though, I can't for the life of me remember.  I have the madwifi files on my comp to change the computer's perception of my card from AR5006 to AR5007, but that's about all I know.  I have also run the tutorial from Kevdog numerous times keeping up with changes in the IPs and wifi networks at work (and at home).  But there seems to be a step (or two/three/many) missing between the two!

---

### Post by dmizer on 2008-06-20
try this: [http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

the recent update you received was a kernel update.  so any compiling of anything you did, will have to be done again, so it works for your new kernel.

---

### Post by chili555 on 2008-06-20
> **dmizer said:**
> try this: [http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

the recent update you received was a kernel update.  so any compiling of anything you did, will have to be done again, so it works for your new kernel.
Quite correct. You will have to run the command 'make clean' first, before you re-run 'make' and 'sudo make install.'

---

### Post by Cilionelle on 2008-06-22
Where/when will I have to run the command 'make clean' etc.?  What does that even do?

---

### Post by Zorael on 2008-06-22
Make sure that you have the **linux-generic** package installed. This will pull the modules package for your kernel if missing.

---

### Post by chili555 on 2008-06-22
> **Cilionelle said:**
> Where/when will I have to run the command 'make clean' etc.?  What does that even do?

> I have the madwifi files on my compDid you not build a module previously, in this directory, with 'make,' and 'sudo make install?' You will need to go through this process again, but first add the command 'make clean.'

Since the module was previously built specifically for a kernel that has been superceeded, we need to clean out the old parts and build new parts for your new kernel.

---

### Post by Cilionelle on 2008-06-22
Thanks for your help guys.  It'd been a while since I did all that 'make' and 'make install' stuff.  I appreciate the link, too.  I've now saved that page on my comp for future reference!  Kudos to all!

---


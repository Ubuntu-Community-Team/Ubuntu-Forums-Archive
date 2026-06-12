---
title: "Disappearing ethernet device"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by femtoguy on 2008-10-29
I am running Ibex on a home built with a Biostar GF8200 AM2+ motherboard and an AMD 4850e processor.  I have been running the Ibex beta for a while and everything has been pretty good (except that the only way that I can make it install is to install Hardy with all_generic_ide as a boot flag, and then do a dist-upgrade to Ibex) until yesterday.  I run the updates through the update manager, and when it rebooted, I had no ethernet device.  I booted off of a vestigial Windows XP partition, and it saw the ethernet device, but ubuntu would not.  I did a re-install, and hardy saw eth0 right away, but when I did the upgrade to Ibex, it disappeared again.  I know that similar problems have been reported with the intel e1000e driver, but this is definitely not an intel chipset.  Is there an easy way to fix this?

(I grep'ed /var/log/messages for an eth0 entry, and there was nothing.  
I ran lshw -C network and got 
 network DISABLED
    description : Ethernet interface
    physical id: 1
    logical name: pan0
    serial: a2:75:3c:4d:bf:34
    Capabilities: ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware N/A link=yes multicast=yes

when I unplugged the cable the link=yes went away

Is it configuring my ethernet as pan0?  It looks to me like pan0 is something bluetooth related.  Has anybody seen anything similar?  Is there a way to fix it?

---

### Post by lemming465 on 2008-10-30
Could we see the output of *lspci -v; lsmod*?

---

### Post by ltmon on 2008-10-30
Some similar symptoms to my eth0 (e1000e) problem.  See here for a full description (but no solution :()  - [http://ubuntuforums.org/showthread.php?p=6061643](http://ubuntuforums.org/showthread.php?p=6061643)

---


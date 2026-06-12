---
title: "Hardware drivers won't work?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Xarver on 2010-02-14
For some reason when I click activate on the wireless driver I want to install it just stands there. I don't know why but the program just won't work. I know that maybe if I update the software on my install it might fix the problem, but **I don't have internet** so I can't update. I followed this guide but Hardware Drivers won't work. [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I found out when resizing the jockey-kde window and clicking activate on the driver a dialog pops up saying "downloading and installing driver" for 2 seconds.

---

### Post by switch10 on 2010-02-14
Use an ethernet cable.  Let it find your wireless drivers.

---

### Post by Xarver on 2010-02-14
Ethernet does not work.

---

### Post by Xarver on 2010-02-14
OK I found out when resizing the jockey-kde window and clicking activate on the driver a dialog pops up saying "downloading and installing driver" for 2 seconds.

---

### Post by niffcreature on 2010-02-14
you are running kubuntu?

i just solved a few problems by realizing i did not have network-manager-gnome installed,
im mentioning this because it was the only thing that solved BOTH my wireless and ethernet being down.

does "lshw -C network" show both as DISABLED?
then it probably isnt the actual driver at least for ethernet

---

### Post by Xarver on 2010-02-15
Yes I am. Ethernet doesn't work on Windows 7 either.
So therefore I can't install anything on kubuntu.
lshw -C network gives ```
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:91100000-91103fff
 

```

---

### Post by bkratz on 2010-02-15
> **Xarver said:**
> Yes I am. Ethernet doesn't work on Windows 7 either.
So therefore I can't install anything on kubuntu.
lshw -C network gives ```
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:91100000-91103fff

``` 


If your internet doesn't even work in Windows, i think I would check and see if it is turned on in the bios and verify that any switch or key combination to turn in on is enabled.

---

### Post by Xarver on 2010-02-15
My ethernet doesn't work on Windows;
My wireless works on it because the driver was included by default.
I might just use Ubuntu and not KDE

---


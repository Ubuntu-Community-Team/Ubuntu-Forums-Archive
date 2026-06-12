---
title: "How do I get LAN to work with an ASUS P5KPL-CM motherboard"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by gully on 2008-11-17
Hi, I recently upgraded to a new motherboard, but lost my LAN in the process.
It turns out Ubuntu doesn't have the correct drivers for this one.

On the ASUS cd there are two drivers for linux, one of them is for LAN, but the readme is complete gibberish to me (where the hell is that .tar file they keep talking about?)

Then I found this: [http://ubuntuforums.org/showthread.php?t=881156](http://ubuntuforums.org/showthread.php?t=881156) also complete gibberish to me until I read reply #10 (linux_newbie101) that talked about files that were actually there on the cd.
I followed the steps and my driver was installed (it shows up in the restricted drivers list.)
But... no internet: can't browse on firefox and terminal commands like sudo apt-get update give connection errors.

BTW, internet works fine in XP (dualboot.)

Does anyone know what I did wrong?

I appreciate any help.

---

### Post by cariboo on 2008-11-18
Could you paste the output of in a Applications-->Accessories-->Terminal:

```
sudo lshw -C network
```

Because there is a driver in the latest kernel for your network adapter.

Jim

---

### Post by gully on 2008-11-18
This is what I get when I enter that command:

 *-network DISABLED      
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth3
       version: b0
       serial: 00:22:15:d8:27:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1e driverversion=1.0.0.7 firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair

---

### Post by gully on 2008-11-18
With the latest kernel do you mean Intrepid?
I haven't upgraded yet, I still have Hardy.

---

### Post by gully on 2008-11-19
Solved it: I enabled the the wired connection in "administration --> network."

No idea why it disabled itself, but it works now.

---


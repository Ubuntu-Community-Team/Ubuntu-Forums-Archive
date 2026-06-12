---
title: "problem with wirless BCM94311MCG wlan mini-PCI (rev 02) &amp; ubuntu 8.04 hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by harshaambati on 2008-04-28
i am having problem with my wirless i am using Hp Pavilion da2432nr

I am a new user i have ubuntu 8.04 after installing ubunt udetected my wireless installed b43-fwcutter which inturn has installed ndiswrapper-utlis-1.9, i also have given location the .inf file (.i.e. bcmwl6.inf) of my driver
but nothing happens wireless connection is not shown in network manager...

these are some details of my wirless card...

 #lspci -v | less

01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1374
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at b3000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

I also tried these rmmod command but no result
# rmmod b43
ERROR: Module b43 does not exist in /proc/modules
# rmmod b44
ERROR: Module b44 does not exist in /proc/modules
# rmmod ssb
# rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
# modprobe ndiswrapper
root@sriharsha-laptop:/home/sriharsha# modprobe ssb
root@sriharsha-laptop:/home/sriharsha# ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
root@sriharsha-laptop:/home/sriharsha# lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

can any one help me ..with this...problem..

---

### Post by dmizer on 2008-04-28
try taking a look at this thread: [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

you'll need to also blacklist b43-pci-bridge

---

### Post by grumpylad77 on 2008-04-28
[//http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("//http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

Or you could follow this guide...works perfectly for me.

---

### Post by dmizer on 2008-04-28
> **grumpylad77 said:**
> [//http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("//http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

Or you could follow this guide...works perfectly for me.

i have seen the guide you reference.  the script you reference is not necessary.

simply blacklist b43 and ssb, and add:
```
modprobe -r ndiswrapper
modprobe -r b44
modprobe ndiswrapper
modprobe b44
```
to /etc/rc.local

for more details see the link i posted above.

---

### Post by harshaambati on 2008-04-29
Hi...thanks for your interest in problem....I have a quick Question about ndiswrapper ...can ndiswrapper create driver for ubuntu from a Vista wireless driver ...since i was trying to create one from vista driver which is bcmwl6.inf file in and i find everyone using bcmwl5.inf file..which i suppose is xp wireless driver file..

Any comment on this....

---

### Post by sam_delta on 2008-04-29
try, ull need a internet connection
[http://300lb.blogspot.com/2008/04/how-to-get-broadcom-wireless-to-work-in.html](http://300lb.blogspot.com/2008/04/how-to-get-broadcom-wireless-to-work-in.html)

this procedure will install broadcom missing firmware to ubuntu b43-fwcutter broadcom drivers 
remember that ndiswrapper shoulb be the last option

any questions on the procedure above, ask here!

tell us how it goes

---

### Post by harshaambati on 2008-04-29
hey thanks dmizer... man your link [http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html") has worked...prefectly...valaa...
         
                the wired thing is that i tried this same thing before except for drivers i used where of vista version but any how thanks man..

---

### Post by dmizer on 2008-04-29
> **harshaambati said:**
> hey thanks dmizer... man your link [http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html") has worked...prefectly...valaa...
         
                the wired thing is that i tried this same thing before except for drivers i used where of vista version but any how thanks man..

glad you got it working.  the problem you were experiencing was, most likely, simply because you were trying to use the vista drivers which won't work with ndiswrapper.

---


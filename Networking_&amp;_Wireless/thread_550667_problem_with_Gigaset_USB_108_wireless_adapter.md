---
title: "problem with Gigaset USB 108 wireless adapter"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Uden on 2007-09-14
Hi all,

a question from a Linux newbie...

i have just installed Ubuntu 7.04 and am trying to set up an internet connection. Therefore I need to install and configure a Siemens Gigaset USB 108 adapter (which was supplied with my Siemens Experia wireless router). I have only a windows driver for this wireless adapter. So i used Google as "first line support":

I found the following thread on this forum to install the latest version of Ndiswrapper ([http://ubuntuforums.org/archive/index.php/t-190614.html](http://ubuntuforums.org/archive/index.php/t-190614.html)). This went ok.

Next i used the following thread to install the windows drivers: ([http://www.alleslinux.com/forum/viewtopic.php?p=30870&sid=7122c2ef93f1c8f0ae3786c4f74dbed1):](http://www.alleslinux.com/forum/viewtopic.php?p=30870&sid=7122c2ef93f1c8f0ae3786c4f74dbed1):)

executed steps: 
1) ndiswrapper -i athfmwdl.inf
2) ndiswrapper -i netwg11t.inf
3) ndiswrapper -l
Result:
Installed drivers:
athfmwdl   driver installed
netwg11t   driver installed

4) modprobe ndiswrapper
5) dmesg (check for text: ndiswrapper: driver netwg11t (NETGEAR...etc)
Result:
[  569.529597] ndiswrapper version 1.43 loaded (smp=yes)
[  569.733976] usb 1-2: reset full speed USB device using uhci_hcd and address 4
[  569.966309] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
[  580.016067] ndiswrapper (NdisWriteErrorLogEntry:199): log: C0001389, count: 4, return_address: d8cf3c6b
[  580.016095] ndiswrapper (NdisWriteErrorLogEntry:202): code: 0xd11da7c4
[  580.016107] ndiswrapper (NdisWriteErrorLogEntry:202): code: 0x28
[  580.016119] ndiswrapper (NdisWriteErrorLogEntry:202): code: 0xd8c49000
[  580.016131] ndiswrapper (NdisWriteErrorLogEntry:202): code: 0xd8c49000
[  580.017090] **ndiswrapper (miniport_init:271): couldn't initialize device: C0000001**
[  580.017114] ndiswrapper (pnp_start_device:425): Windows driver couldn't initialize the device (C0000001)
[  580.019745] unregister_netdevice: device eth%d/d11da000 never was registered
[  580.019776] ndiswrapper (miniport_halt:335): device d11da400 is not initialized - not halting
[  580.019802] ndiswrapper: device eth%d removed
[  580.019850] ndiswrapper: probe of 1-2:1.0 failed with error -22
[  580.019888] usbcore: registered new interface driver ndiswrapper 

the problem is shown in bold. As i understood from the mentioned link to the other forum, this should work. 
Has anyone been able to use the Gigaset USB 108 wireless adapter??


P.s. the following links on this forum gave no resolution: [http://ubuntuforums.org/showthread.php?t=397776](http://ubuntuforums.org/showthread.php?t=397776)

---

### Post by Uden on 2007-09-14
i just found this link [http://ubuntuforums.org/showthread.php?t=533840](http://ubuntuforums.org/showthread.php?t=533840),
but it offers no solution. 

It does however  describe another driver "net5523.inf" for the Gigaset USB 108. I used the ones supplied with my device. Does anyone know if this is a better/later version?

---

### Post by Coleville on 2008-01-13
Didi you try to unplugged your gigaset adapter then plug it again and then do

modprobe ndiswrapper

it works with mine but i have to do that each time i restart my computer. it seems that the gigaset does not shut down properly when you shut down the computer and then cannot be detected when you restart it. I had then same problem when windows crashed and did not shut down properly...

---


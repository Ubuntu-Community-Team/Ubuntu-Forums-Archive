---
title: "wireless not working after upgrading the kernal"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by mesmar on 2010-10-05
hi guys
i have upgrade my kernel to 2.6.35-020635rc1-generic(ubuntu10.4)
but the wireless didn't work after that.
when i tried left click on the network-manager icon i get the following msg:device not ready:(
the result of the commad [COLOR=Black]**lspci**[/COLOR] is
> host bridge: Intel corporation mobile 945gm/pm/gms, 943/940gml and 945gt express memory controller hub (rev 03)
00:02.0 vga compatible controller: Intel corporation mobile 945gm/gms,  943/940gml express integrated graphics controller (rev 03)
00:02.1 display controller: Intel corporation mobile 945gm/gms/gme, 943/940gml express integrated graphics controller (rev 03)
00:1b.0 audio device: Intel corporation n10/ich 7 family high definition audio controller (rev 02)
00:1c.0 pci bridge: Intel corporation n10/ich 7 family pci express port 1 (rev 02)
00:1c.1 pci bridge: Intel corporation n10/ich 7 family pci express port 2 (rev 02)
00:1c.2 pci bridge: Intel corporation n10/ich 7 family pci express port 3 (rev 02)
00:1c.3 pci bridge: Intel corporation n10/ich 7 family pci express port 4 (rev 02)
00:1d.0 usb controller: Intel corporation n10/ich7 family usb uhci controller #1 (rev 02)
00:1d.1 usb controller: Intel corporation n10/ich 7 family usb uhci controller #2 (rev 02)
00:1d.2 usb controller: Intel corporation n10/ich 7 family usb uhci controller #3 (rev 02)
00:1d.3 usb controller: Intel corporation n10/ich 7 family usb uhci controller #4 (rev 02)
00:1d.7 usb controller: Intel corporation n10/ich 7 family usb2 ehci controller (rev 02)
00:1e.0 pci bridge: Intel corporation 82801 mobile pci bridge (rev e2)
00:1f.0 isa bridge: Intel corporation 82801gbm (ich7-m) lpc interface bridge (rev 02)
00:1f.1 ide interface: Intel corporation 82801g (ich7 family) ide controller (rev 02)
00:1f.3 smbus: Intel corporation n10/ich 7 family smbus controller (rev 02)
02:00.0 ethernet controller: Marvell technology group ltd. 88e8038 pci-e fast ethernet controller (rev 14)
03:00.0 network controller: Intel corporation pro/wireless 3945abg [golan] network connection (rev 02)
0a:09.0 cardbus bridge: Texas instruments pcixx12 cardbus controller
0a:09.2 mass storage controller: Texas instruments 5-in-1 multimedia card reader (sd/mmc/ms/ms pro/xd
any help

---

### Post by ibizatunes on 2010-10-05
try
```
sudo service network-manager restart
```

reboot and hold down shift and boot into the old kernel, and modify your grub, but i think it the service or hasn't restarted isnt running right

---

### Post by mesmar on 2010-10-05
i have delated the old kernel :(
nothing changed after using 
> sudo service network-manager restart
the same msg :device not ready

---

### Post by TBABill on 2010-10-05
Too late now, but something to keep in mind in the future...never ever delete a working kernel until you are 100% certain you will not need that older kernel again. I normally keep one older kernel installed at all times, allowing me to revert back at least one version in case of problems. Once I know the new one is good I get rid of the oldest one and keep the previous kernel. Doesn't hurt a thing unless you need the space.

---

### Post by NightwishFan on 2010-10-05
Test this using a mainline kernel of your choice. Preferable one branded Maverick. You only need the headers and image for your arch not all of the files. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Are you using Maverick or just a new kernel on Lucid?

---

### Post by mesmar on 2010-10-05
TBABill thx for the dvise i will keep it in mind later on.
NightwishFan a new kernel on Lucid i did not upgrade to Maverick
i think it is to early to do that :)
but with kernel &wireless issue :confused:

---

### Post by NightwishFan on 2010-10-05
You can boot to an older kernel by holding shift while booting.

---

### Post by mesmar on 2010-10-06
[NightwishFan]("http://ubuntuforums.org/member.php?u=484925") i have already deleted the old kernel :(

---

### Post by acreech on 2010-10-06
If you have internet by wire, can you install the older kernel. In the synaptic search for linux-headers

Then install an older kernell.

---

### Post by mesmar on 2010-10-06
i have upgrade to 10.10 :) now
but still i have the same issue but now i got the msg:
 says fitmware is missing

---


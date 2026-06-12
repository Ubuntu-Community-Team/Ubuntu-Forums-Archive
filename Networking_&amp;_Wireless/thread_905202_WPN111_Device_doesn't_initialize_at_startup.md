---
title: "WPN111 Device doesn't initialize at startup"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by milanvora2 on 2008-08-30
0) Got a WPN111 usb adapter.
1) I installed a fresh version of 8.04. Installed all updates
2) Installed ndisgtk, common, utils
3) installed the driver v2. 

At this point the wireless is working fine. 

I reboot the system and under network no wireless option is visible.
The output of dmesg | grep -e ndis -e wlan is

[   26.490914] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   26.802290] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
[   26.802879] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
[   41.844580] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001389, count: 4, return_address: f8bb7bbb
[   41.844585] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf75d3c00
[   41.844587] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x28
[   41.844588] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf8a50000
[   41.844590] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf8a50000
[   41.844739] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   41.844743] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   41.844752] ndiswrapper (mp_halt:262): device f75d2480 is not initialized - not halting
[   41.844754] ndiswrapper: device eth%d removed
[   41.844764] ndiswrapper: probe of 5-6:1.0 failed with error -22
[   41.844775] usbcore: registered new interface driver ndiswrapper

So I downloaded ndiswarpper 1.53, compiled it. no further progress.

Anyone knows how to fix this ?

---

### Post by cdtech on 2008-08-30
After reboot what's the output of:
ndiswrapper -l

And do you have the module loading within:
/etc/modules

---

### Post by milanvora2 on 2008-08-30
New Update:

If I do sudo rmmod ndiswrapper then unplug the device and then do sudo modprobe ndiswrapper it works again.
But I have to do it manually each time at each reboot.

Any way to solve this ?

---

### Post by milanvora2 on 2008-08-30
Content of /etc/modules

fuse
lp
ndiswrapper

Output of ndiswrapper -l


netwpn11 : driver installed
	device (1385:5F01) present

---

### Post by milanvora2 on 2008-08-30
after further trials: I come to the following observation:

I have to re-plug the usb adapter after boot
and type sudo modprobe ndiswrapper
and then everything works.

Would anyone know how to automate this ?

---

### Post by milanvora2 on 2008-08-30
After further analysis i notice the following:

If i do a lsmod after startp, the usbcore doesn't contain the line ndiswrapper

After doing the manual steps descibed above the line usbcore contains ndiswrapper.

Please can anyone help ?

---


---
title: "Bluetooth No Adaptors Found"
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by nickTaylor1181 on 2016-01-03
Hi All

I'm trying to get a new PC set up (ubuntu 15.10) - and am having days of difficulty getting bluetooth / sound to work - which is a pity, because I specifically bought this laptop because my work environment means I need to use bluetooth headphones. It's the main thing I need to get working, and it isn't. 


I don't know my way around this stuff at all. However, when I type "lspci" into a terminal, I get:

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)
03:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev 
a1)

```

Which doesn't mention bluetooth at all. 

If I type "systemctl status bluetooth.service -l"

I get

```
&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2016-01-04 15:56:56 NZDT; 24min ago
     Docs: man:bluetoothd(8)
 Main PID: 727 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;727 /usr/lib/bluetooth/bluetoothd


Jan 04 15:56:59 laptop bluetoothd[727]: Not enough free handles to register service
Jan 04 15:56:59 laptop bluetoothd[727]: Not enough free handles to register service
Jan 04 15:56:59 laptop bluetoothd[727]: Sap driver initialization failed.
Jan 04 15:56:59 laptop bluetoothd[727]: sap-server: Operation not permitted (1)
Jan 04 15:57:14 laptop bluetoothd[727]: Endpoint registered: sender=:1.42 path=/MediaEndpoint/A2DPSource
Jan 04 15:57:14 laptop bluetoothd[727]: Endpoint registered: sender=:1.42 path=/MediaEndpoint/A2DPSink
Jan 04 15:57:56 laptop bluetoothd[727]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSource
Jan 04 15:57:56 laptop bluetoothd[727]: Endpoint registered: sender=:1.69 path=/MediaEndpoint/A2DPSink
Jan 04 15:57:56 laptop bluetoothd[727]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
Jan 04 16:02:14 laptop bluetoothd[727]: connect error: Host is down (112)



```

Which looks like something is running, but also has a whole bunch of error messages that I don't understand.


I don't suppose anyone knows how to get this to work?

---

### Post by matt_symes on 2016-01-04
Hi

Try this (from here [https://github.com/ev3dev/ev3dev/issues/198](https://github.com/ev3dev/ev3dev/issues/198))

```
sudo apt-get install pulseaudio-module-bluetooth
```

```
sudo nano /etc/pulse/system.pa
```

Copy and paste this into it at the bottom.

```

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif

.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif
```

```
sudo reboot
```

Does that help ?

Kind regards

---

### Post by nickTaylor1181 on 2016-01-04
Thanks for that.

Unfortunately, even though I've been using Ubuntu for about 10 years, "fixing stuff" usually involves copying and pasting things I don't understand into terminals, each time with this mild feeling of trepidation that I might be doing something that will destroy my entire system.

And sometime during yesterday, that happened. 

I now can't get it to the desktop at all. On booting, it locks up with this:

[https://goo.gl/photos/g5q92uRykXR4imD28](https://goo.gl/photos/g5q92uRykXR4imD28)

And I've run out of road with this one - I'm going to have to format the thing and start over.


If bluetooth is still not working after that, I'll try the things you suggested.

---

### Post by jeremy31 on 2016-01-04
The error in your pic is about the Intel graphics

Is the bluetooth internal or a USB dongle?  I know some Intel wifi cards have bluetooth on the same card and the bluetooth usually just need to load firmware to work

---

### Post by nickTaylor1181 on 2016-01-04
hiya 

The bluetooth is internal. 

I can't actually get to a desktop at all now though... any idea about how to get past the graphics error?

---

### Post by matt_symes on 2016-01-04
Hi

> **nickTaylor1181 said:**
> hiya 

The bluetooth is internal. 

I can't actually get to a desktop at all now though... any idea about how to get past the graphics error?

It looks like it may be a bug.

[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1511101](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1511101)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1492764](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1492764)

It looks like installing a mainline kernel may be a workaround (4.3 or above - you'll find them near the bottom).

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Can you list all the specs of you hardware in as much detail as possible.

Kind regards

---

### Post by nickTaylor1181 on 2016-01-06
Hiya - things have moved on (and backwards) alas.

I've attempted to reinstall ubuntu completely, and now it just hangs at the "Preparing to install ubuntu" screen... for which (I guess) I need to start another thread.

---

### Post by matt_symes on 2016-01-06
Hi

Check your hardware.

Kind regards

---


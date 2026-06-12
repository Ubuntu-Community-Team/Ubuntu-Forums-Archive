---
title: "Sys-Admin-Net Connections show only a dial up modem."
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Cyberbayne on 2007-01-19
My first installation of a Linux distro, i.e., Ubuntu Dapper, went off without a hitch. I get the dual boot menu at start-up. Dapper is responsive on all fronts - games, apps, terminal. I can read from, and burn to the optical drives. I can play CDs.

But, I cannot get the usb wireless adaptor to appear in the networking connections window.
Troubleshooting commands and their results are below:
__________________________________________________ _
lshw
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: wlan0
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

*-usb
description: Generic USB device
product: WUSB11v2.5 802.11b Adapter
vendor: Linksys, Inc.
physical id: 1
bus info: usb@1:1
version: 1.32
serial: 1
capabilities: usb-1.10
configuration: driver=prism2_usb maxpower=500 mA speed=12.0MB/s
______________________________________________
lsmod
prism2_usb 77060 0
______________________________________________
sudo iwlist ath0 scan
ath0 Interface doesn't support scanning.
______________________________________________
sudo iwconfig
lo no wireless extensions.
sit0 no wireless extensions.
wlan0 no wireless extensions.
______________________________________________
sudo ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:105 errors:0 dropped:0 overruns:0 frame:0
TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:7896 (7.7 KiB) TX bytes:7896 (7.7 KiB)
_______________________________________________
Bus 001 Device 003: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x066b Linksys, Inc.
idProduct 0x2212 WUSB11v2.5 802.11b Adapter
bcdDevice 1.32
~snip~
Device Status: 0x0000
(Bus Powered)
__________________________________________________ __
I have tried booting with the adaptor connected, and booting without it and connecting it after the boot (a la PnP). No difference. I tried rebooting the router while the adaptor was connected. Nothing.
__________________________________________________ _____

If I'm reading this right, the adaptor is being detected by the OS. The driver is present and functional. But the adaptor is not registering in the networking connections window, which is where it has to activated from(yes/no?). As you can see, I've put some effort into this, but my brain hurts and i'm starting to get crosseyed. Am I close? Way off base? What's next?

---

### Post by Floppyjoe on 2007-01-19
Have you installed the Linux-wlan-ng package using synaptic package manager?

---

### Post by Cyberbayne on 2007-01-19
> **Floppyjoe said:**
> Have you installed the Linux-wlan-ng package using synaptic package manager?

Thanks for the comeback. 
Those (package and package manager) were not mentioned in the various sources I read. I installed from the Live CD. Is that package not part of the installation? Am I reading the wrong pages?
What, where, and how, please...?

---

### Post by Floppyjoe on 2007-01-19
> **Cyberbayne said:**
> Thanks for the comeback. 
Those (package and package manager) were not mentioned in the various sources I read. I installed from the Live CD. Is that package not part of the installation? Am I reading the wrong pages?
What, where, and how, please...?

If you have internet connectivity with your Ubuntu install via ethernet cable you could install the "linux-wlan-ng" package with synaptic package manager by clicking on System/Administration/Synaptic Package Manager. Then search for "linux-wlan-ng".

However if you have already installed this package from the cd then you don't need to install it.

It does not come installed with the system.

---

### Post by Cyberbayne on 2007-01-19
I do not have Intenet connectivity through the Ubuntu.

I was able to use the synaptic package manager to install "linux-wan-ng" from the CD. It has not made a noticeable change in my problem. The network connections window continues to show only a dialup modem (which is weird because I don't have one on my system).

---

### Post by Floppyjoe on 2007-01-19
Click on System/Administration/Synaptic Package Manager.

Click Edit/Add CD Rom.

Put Your Install CD in the CDrom drive.

Follow the directions.

Then click Reload button.

Then search for "linux-wlan-ng"

Check the box and click on mark for installation.

Click on apply button.

I think that should do it.

Never mind then! See below.

---

### Post by Floppyjoe on 2007-01-19
Did you reboot?

---

### Post by Cyberbayne on 2007-01-20
Yes, and no change :(

---

### Post by Cyberbayne on 2007-01-21
I've given up on Dapper and done a clean install of Edgy with a PCI wireless adaptor instead of the USB adaptor. I'm not on the net yet, but at least the wireless adaptor is detected by the connection manager and the driver is present. I could even ping 127.0.0.1  :) But that's it :(

Here's my forum post if you're interested...

[http://www.ubuntuforums.org/showthread.php?t=343482](http://www.ubuntuforums.org/showthread.php?t=343482)

---

### Post by Cyberbayne on 2007-02-11
Well, its not an 'elegant' solution, and certainly not a purist *nix solution, but I'm up and running and posting this from my new distro (openSUSE - I got MUCH more help there), and thanks to the Buffalo Ethernet converter model WLW-TX4-G54HP, 5 minutes was all it took to overcome weeks of frustration. Be well, everyone, and thanks again to those from these forums (fora?) who tried to help.

---


---
title: "Wifi doesn't really work that well compared to windows"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by incedeon on 2015-12-25
[FONT=Verdana]After removing W10 and installing Ubuntu I realized that the wifi is much better under windows. On UbuntuI'm unable to pick up wifi more than 4 feet away. When I do, the wireless is really slow and my connection drops constantly. My Wireless card is RTL8723BE. What should I do?[/FONT]

---

### Post by Bucky Ball on 2015-12-25
Welcome. First, perhaps give us the output of this:

```
sudo lshw -C network
```

See the last link in my signature for how to put the output between code tags. Thanks.

---

### Post by incedeon on 2015-12-25
```
*-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 00
       serial: 48:e2:44:00:7e:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.2.0-16-generic firmware=N/A ip=10.0.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:94100000-94103fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 0a
       serial: b0:5a:da:d7:07:71
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8107e-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:128 ioport:3000(size=256) memory:94004000-94004fff memory:94000000-94003fff


```

---

### Post by Vladlenin5000 on 2015-12-26
A driver update has been suggested many time here and elsewhere for the RTL8723BE. For your convenience there's a PPA (Trusty, Vivid and Wily only) which provides fixes so try this:

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```

Reboot & test. Please give feedback. It may or may not need additional tweaking (setting reg domain, etc.).

---

### Post by praseodym on 2015-12-26
Alternatively/additionally try these module parameters
```

echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rfv rtl8723be
sudo modprobe -v rtl8723be
```

---

### Post by incedeon on 2015-12-27
I got this output when i installed
```
Building only for 4.3.3-040303-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.


```

---

### Post by jeremy31 on 2015-12-27
Is it a HP laptop?

---

### Post by incedeon on 2015-12-27
Yeah, it's an HP notebook.

---

### Post by jeremy31 on 2015-12-27
> **incedeon said:**
> Yeah, it's an HP notebook.

Is it easy to access the wifi card?  It may only have one antenna with two connectors on the card.  Switching the antenna from the one connector to the other helped one poster here

---

### Post by incedeon on 2015-12-27
Don't wanna risk breaking anything. This is a $2,000 laptop.

---

### Post by Hadaka on 2015-12-27
Hi, this is a thread with the exact card and problem you have and
what was done to fix it...last page 4
[http://ubuntuforums.org/showthread.php?t=2304607&page=4](http://ubuntuforums.org/showthread.php?t=2304607&page=4)
If you are uncomfortable doing the fix then you might want to consider
taking it to a professional laptop repair shop. Or use a usb wifi .
good luck

---


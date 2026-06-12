---
title: "Realtek  0bda:8179"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by FLGzQAL on 2013-09-06
Edit: see third post - solved issue

Hi all,

I am a long time lurker here, new poster. Thank you for the previous posts that helped me out so much, and thank you in advance for the help on this one.

I recently bought a TP Link wireless N USB dongle after seeing some positive info that it worked with Ubuntu 12.04 out of the box. Unfortunately, that was v1 of the device, and of course I was sent v2.

With the device plugged in, lsusb returns:
> Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 002 Device 006: ID 0bda:817b Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)



Note that there are two RealTek devices, the 817b is my cirago wifi-n/bluetooth combo dongle. The bluetooth worked out of the box, but it looked like getting the 802.11 to work was going to be a bear, so I bought the TP Link dongle for $8 thinking it was going to save me a ton of effort.

My first effort for both devices was to try ndiswrapper, since I have the WinXP 64bit drivers for both devices, but ran into errors installing ndiswrapper itself.

After that, I researched the 0bda:8179 and found some github info. Even with that I haven't had any luck (learned how to use nano though - silver lining).

This thread was pretty helpful: [http://ubuntuforums.org/showthread.php?t=2150729](http://ubuntuforums.org/showthread.php?t=2150729)
However, the [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") post gave me errors at the 'make' step. Seems to be a common theme, every line of commands that involve 'make' have given me errors there.

lshw -c network returns:
> 
*-network
description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: a4:1f:72:6e:f3:61
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.4 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.5.2
       logical name: wlan0
       serial: e0:91:53:69:c7:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.8.0-29-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn



Seems promising, it at least recognizes the wlan0 connection and driver. How do I get this to work?

For the record, I am just getting this computer set up to dual boot Win7 and Ubuntu. I'm okay with going to 12.10 or higher, or a reinstall of 12.04.

Thank you again.

---

### Post by praseodym on 2013-09-07
Hi,

maybe this driver does only work with kernels 3.2 and 3.5 of 12.04, respectively. You can install these kernels via synaptic, but don’t forget the respective kernel header files and "dkms"

What about the internal card? With kernel 3.8 this should work:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

It's a patched file for 3.8

---

### Post by FLGzQAL on 2013-09-07
> **praseodym said:**
> Hi,

maybe this driver does only work with kernels 3.2 and 3.5 of 12.04, respectively. You can install these kernels via synaptic, but don’t forget the respective kernel header files and "dkms"

What about the internal card? With kernel 3.8 this should work:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

It's a patched file for 3.8

Thank you, thank you, thank you!

Since I was just getting this tower set up (no internal card) I went ahead and reinstalled 12.04 so any previous changes weren't held.

I then followed the commands in the linked thread and I am now on wireless!!

uname -r returns:
> 3.8.0-30-generic

I logged in as super user
>  sudo -i

then entered the command:
> sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms

after a download, entered command:
> wget https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1.6_all.deb 

another download, then:
> dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb

finally
> echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
(for the record, that is a | not a / in ...2cu" | sudo t...)

since I was logged in as super user, enter 
>  logout
to log out.

Restarted my system and I am on the wireless!

Now lshw -c network returns:
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: a4:1f:72:6e:f3:61
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.5.2
       logical name: wlan0
       serial: e0:91:53:69:c7:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=192.168.1.103 multicast=yes wireless=IEEE 802.11bg


Thank you for the help!!!!!!

---

### Post by FLGzQAL on 2013-09-07
For the record, this was the TP LinkTL-WNN V.2. I got mine at Newegg for $8 shipped: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833704141](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704141)

Looks like it's $9 at the time of posting, it is also available from amazon/others.

---


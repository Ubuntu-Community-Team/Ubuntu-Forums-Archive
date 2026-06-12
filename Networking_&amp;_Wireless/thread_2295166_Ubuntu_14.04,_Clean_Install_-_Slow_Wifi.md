---
title: "Ubuntu 14.04, Clean Install - Slow Wifi"
date: 2015-09-16
forum: Networking &amp; Wireless
---

### Post by ooboontwo on 2015-09-16
Clean install of Ubuntu 14.04, I checked the box that said to download and install updates during the installation and wondered why it was taking so long. Checked my speeds and noticed that I was only getting about 20 KB/s down. I also experience frequent, intermittent timeouts. After the installation completed, same thing.

This is a dual-boot setup and the device pulls down around 1.5 MB/s in Windows.

I have tried disabling IPv6 and 802.11n (modprobe), but the issue persists.

Wireless device is a small USB, TP-LINK Model: TL-WN823N

'lshw' output for device:

```
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.5
       logical name: wlan0
       serial: a0:f3:c1:09:21:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.16.0-49-generic firmware=N/A ip=10.0.0.4 link=yes multicast=yes wireless=IEEE 802.11bgn
```

Thanks in advance for your help.

---

### Post by adamftzptrck on 2015-09-16
have you tried to restart the modem and the router (i.e. unplug for 10 secs)? 
There may be difficulties with the ubuntu driver utilization.

---

### Post by ooboontwo on 2015-09-16
> **adamftzptrck said:**
> have you tried to restart the modem and the router (i.e. unplug for 10 secs)? 
There may be difficulties with the ubuntu driver utilization.

I can give it a shot, but would this really make a difference if the network is working fine on all other devices and even the same PC booted into Windows?

**EDIT: I gave my modem and router a reset. No change.**

---

### Post by ooboontwo on 2015-09-16
**PROBLEM SOLVED**

I'm surprised this driver issue hasn't already been fixed. This is the article I used to fix things: [http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu](http://askubuntu.com/questions/471208/realtek-wireless-adapter-issues-rtl8192ce-and-rtl8192cu)

And here are the exact steps I followed, in case that question ever gets removed or goes down.

[I]Ensure you have the necessary prerequisites installed:
[/I]
[I]sudo apt-get install linux-headers-generic build-essential dkms git
[/I]*Clone this repository:*
[I]git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
[/I]*Set it up as a DKMS module:*
[I]sudo dkms add ./rtl8192cu-fixes
[/I]*Build and install it:*
[I]sudo dkms install 8192cu/1.10
[/I]*Refresh the module list:*
[I]sudo depmod -a
[/I]*Ensure the native (and broken) kernel driver is blacklisted:*
[I]sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
[/I]*And reboot. You're done.*

---


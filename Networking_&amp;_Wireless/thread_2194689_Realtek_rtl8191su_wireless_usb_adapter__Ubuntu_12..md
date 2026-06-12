---
title: "Realtek rtl8191su wireless usb adapter / Ubuntu 12.04"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by ray-moon89 on 2013-12-20
Hi ,
I'm fairly new to ubuntu just bought a realtek rtl8191su wireless usb antenna and i cant get the driver, ubuntu doesnt recognized it

---

### Post by tfrue on 2013-12-20
First, unplug and then plug back in the usb antenna and please post the output of the commands:
```
dmesg | tail
```
then
```
lsusb
```

Thanks,
Chris

---

### Post by ray-moon89 on 2013-12-20
**THIS IS WHAT I GOT:**

dmesg | tail
[ 3670.043485] r8712u: Boot from EFUSE: Autoload OK
[ 3670.383230] r8712u: CustomerID = 0x000a
[ 3670.383235] r8712u: MAC Address from efuse = 00:0d:81:ac:5e:7b
[ 3670.383238] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3670.383361] usbcore: registered new interface driver r8712u
[ 3671.175167] r8712u: 1 RCR=0x153f00e
[ 3671.175833] r8712u: 2 RCR=0x553f00e
[ 3671.279096] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3671.280628] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3671.590844] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 13d3:3362 IMC Networks 
Bus 001 Device 004: ID 1bcf:2885 Sunplus Innovation Technology Inc.

---

### Post by kurt18947 on 2013-12-20
I can't get on RealTek's site right now.  I suspect Realtek has a linux driver for that chipset that would work on 12.04 but can't check.  There was another person asking about that chipset recently, I believe.  If you could get the 'baked-in' driver to work, that would be my first choice because you don't have to reinstall everytime there's an image update.  I'm not of much help,  I mostly use 13.10 these days.

Edit:  I was able to get on Realtek's site and yes, they appear to have a driver for that chipset.  Has anyone tried Realtek's driver?   I have no experience with this device but have used RealTek drivers with an RTL8188CUs device and they worked well with Ubuntu 12.04 & 12.10.  There's a shell script installer so it should be pretty easy to install.  If you install RealTek's driver, you may well have to blacklist the 'baked-in' driver so it doesn't conflict with Realtek's driver.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by tfrue on 2013-12-21
> **ray-moon89 said:**
> r8712u: MAC Address from efuse = 00:0d:81:ac:5e:7b
[ 3670.383238] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3670.383361] usbcore: registered new interface driver r8712u

and 
> Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

These are good because that means that Linux is seeing the adapter,and giving it a driver. I have more commands for you friend to post, so please and thanks!:

```
sudo nm-tool
```

```
ifconfig -a
```

```
cat /etc/network/interfaces
```

Thanks,
Chris

---

### Post by ray-moon89 on 2013-12-21
cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by tfrue on 2013-12-22
I believe the adapter is trying to configure the wlan1 interface. So you could try and add this to the end of the /etc/network/interfaces file, so:
```
sudo vi /etc/network/interfaces
```
then add this:
```
auto wlan1
iface wlan1 inet dhcp
```

Hope that helps!
Chris

---


---
title: "can detect wireless networks but won't connect"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by cincinnatus on 2008-11-07
Network manager detects my wireless network, asks me to type in the WEP key, I type it in, it tries to connect, then asks for the WEP key again.

I tried using wifi radar, and it tries to connect, but then says "Could not get IP address!"

```
$ dmesg | grep -e ndis -e wlan
[   28.588731] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.831063] ndiswrapper: driver netw4x32 (Intel,03/13/2008,11.5.1.15) loaded
[   28.831263] ndiswrapper (NdisWriteErrorLogEntry:191): log: 40001B7C, count: 2, return_address: f8b745e2
[   28.831266] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x56524457
[   28.831268] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xe3
[   28.869303] ndiswrapper: using IRQ 21
[   29.123555] wlan0: ethernet device 00:1f:3b:52:5f:0f using NDIS driver: netw4x32, version: 0x1000f, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 4965AG Driver', 8086:4230.5.conf
[   29.123628] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   29.135876] usbcore: registered new interface driver ndiswrapper
[   71.717321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  103.592020] ndiswrapper (NdisWriteErrorLogEntry:191): log: 6000138D, count: 3, return_address: f8c2167e
[  103.592033] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x43414d48
[  103.592038] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x36e
[  103.592043] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x2
[  103.592085] ndiswrapper (mp_reset:62): wlan0 is being reset
[  106.021479] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  116.339431] wlan0: no IPv6 routers present
[  724.963128] ndiswrapper (set_infra_mode:150): setting operating mode to 2 failed (C0010015)
[  894.593321] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  905.184175] wlan0: no IPv6 routers present

```

I'm a complete noob to networking, please help me out!

---

### Post by rigol2000 on 2008-11-15
^^BUMP^^

I'm having the same issue.  My laptop had been working fine for a while.  A couple days ago, it started what you're describing.  I can't connect with a static or DHCP.

Ubuntu 8.04.1
Intel PRO/Wireless 2200BG

In windows, I would try resetting the network connection then enable it, but I can figure out how to do that in Ubuntu.

---

### Post by Ichido on 2008-11-15
Try this:
In Network Settings, set Wireless Connection (properties) Un-Check the  "enable Roaming Mode" box and Manually enter your ESSID.
Then set to (DHCP) and click on "OK" Button.

Here is a list of Commands to hang on to:
==========
ifconfig - lists IP address (similar to ipconfig in Windows)
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus
lsusb - Shows USB connected hardware
lshw -C usb - Additional info on USB related hardware (good for USB dongles)
cat /etc/modprobe.d/blacklist - List modules that will not be loaded by the Operating System at boot time
lsmod - lists currently loaded kernel modules. (Example usage - lsmod | grep ndiswrapper)
route -n - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1 
sudo route del default gw 192.168.1.1 - Example of how to delete the default gateway setting
sudo modprobe ***** - Loads the kernel module **** . (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
sudo modprobe -r **** - Unloades the kernel module ****. (Example usage - sudo modprobe -r ndiswrapper)
sudo ifup/ifdown <interface> - Brings up/down the interface and clears the routing table for the specified interface
sudo ifconfig <interface> up/down - Brings up/down the interface for the specified interface 
sudo dhclient <interface> - Request IP address from DNS server for specified interface
sudo dhclient -r <interface> - Release IP address associated with specified interface
sudo iptables -L - Lists firewall rules 
dmesg | more - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
uname -r - Displays kernel version
/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
cat /etc/resolv.conf - Lists DNS servers associated with network connections (Network Manager)
/etc/dhcp3/dhclient.conf - File which sets or modifies dns (domain name servers) settings

==========

Hope these help.

---

### Post by cincinnatus on 2008-11-17
Well, I had messed with the networking settings a lot, and it didn't fix anything, so I did a clean install of Ubuntu (which, by the way, is really cool, I had a separate /home partition and I was amazed how it kept all my files and settings :) heheh I'm a noob).

Anyway, I think my wireless problem actually has to do with my router or something -- the windows computers on my network are having problems as well. If I get it working I'll let you know.

---

### Post by cincinnatus on 2008-11-20
I went to the public libary and was able to connect to the wireless network there, so, apparently the problem 'is' with my home router. No problems with Ubuntu here.

---

### Post by gottferdamnt on 2008-11-20
It IS a ubuntu issue. I can't connect to my network (wpa or wep, both don't work) but It works at a public wifi hotspot (or at home if I don't secure my network) with my two computers.

I had the same issue on hardy and I solved It reinstalling the whole system but It wasn't a good way to. Indeed today I got the same trouble.

There are a Broadcom Dell 1390 (bcm43xx) card on the laptop and a USB wifi device Sagem 760A on the desktop.

---


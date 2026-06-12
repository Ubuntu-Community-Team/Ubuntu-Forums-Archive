---
title: "realtek 8188fu insmod error"
date: 2021-04-21
forum: Networking &amp; Wireless
---

### Post by vskri690a on 2021-04-21
I am trying to make a realtek wireless usb adapter (rtl8188ftv 0bda:f179) work on Ubuntu 20.04 LTS. 
To install the driver for the device, I followed praseodym's answer at 
[https://ubuntuforums.org/showthread.php?t=2410077&p=13829900#post13829900](https://ubuntuforums.org/showthread.php?t=2410077&p=13829900#post13829900)

When I entered the line 
```
sudo insmod rtl8188fu.ko
```

I got the following error

```
insmod: ERROR: could not insert module rtl8188fu.ko: File exists
```

Also, when I try to make install (I tried, while I did not expect it to work)
I get the following error error
```
install -p -m 644 .ko  /lib/modules/5.8.0-50-generic/kernel/drivers/net/wireless/
install: cannot stat '.ko': No such file or directory
make: *** [Makefile:445: install] Error 1
```

Kindly note that I am new to linux and still am nowhere near competent at understanding the comand line. Please suggest a way to resolve the problem

---

### Post by CelticWarrior on 2021-04-21
Welcome.

The instructions you followed imply an active (albeit alternative and temporary, if applicable) internet connection.

---

### Post by vskri690a on 2021-04-21
Thank you for your reply.
I think I did have an internet connection (through USB tethering); Moreover I was able to perform git clone, which I think might require an internet connection. But I shall try it again, thanks. :)

---

### Post by chili555 on 2021-04-21
With a working internet connection by ethernet, tethering or whatever means possible, do:

```
sudo apt update
sudo apt install dkms
git clone https://github.com/kelebek333/rtl8188fu
sudo dkms add ./rtl8188fu
sudo dkms build rtl8188fu/1.0
sudo dkms install rtl8188fu/1.0
sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /usr/lib/firmware/rtlwifi/
```Reboot.

---

### Post by vskri690a on 2021-04-21
Thank you! I think I managed to get the driver installed, but the network appears to be disabled for some reason

sudo lshw -C network outputs 
```
 *-network DISABLED        
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: e0:ca:94:91:73:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=5.8.0-50-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 07
       serial: 54:53:ed:b5:21:fa
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-50-generic firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII
       resources: irq:18 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:1.5
       logical name: usb0
       serial: 66:09:6e:d1:9b:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.13 link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@3:3
       logical name: wlx00e0092fa576
       serial: 00:e0:09:2f:a5:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188fu driverversion=5.8.0-50-generic multicast=yes wireless=unassociated 
```

[I don't think that the Broadcom wireless interface is a working one, moreover it appears to be hard blocked. Disabling the broadcom drivers on windows (I am dual-booting Ubuntu alongside Windows 10) produces no effect on the network connection, so I assume it is not important]

sudo rfkill list all outputs
```
 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no 
```

Is it possible to get the adapter working?

---

### Post by chili555 on 2021-04-22
And now we suspect the whole story! We suspect that the internl Broadcom wasn't working so you bought a USB wireless device and, by coincidence, picked one with the most obscure, esoteric driver in the world of Linux!!

```
0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: **yes**[/COLOR]
```In this context, hard blocked usually means that the hardware switch or key combination, Fn+F12 or some such, is set to disable the wireless radio. Find it and switch it!

Frankly, I suspect that the internal Broadcom will perform better. Once you get the Broadcom working, I'd set the Realtek aside.

---

### Post by vskri690a on 2021-04-22
ah, Thank you. Unfortunately, I am unaware the laptop's history (I had received this (albeit in a fairly working condition) from a person who wanted to dispose of it, for the purpose of using Linux), but what you say seems plausible. The laptop manual has no mention of a hardware switch or any means to toggle the wireless without accessing the OS, but I'll nevertheless mess around a bit. If all fails, at least I now know that buying a proper USB adapter will solve the problem :-) 

Thank you for your help!

---

### Post by CelticWarrior on 2021-04-23
Look for a WiFi symbol in the function keys (F1...F12). Use FN with that key.

---

### Post by jeremy31 on 2021-04-23
If you can remove the internal wifi card, it should clear the hard block

---

### Post by vskri690a on 2021-04-23
none of the function keys have a tower/wifi symbol :'( .  But thank you for your input!

---

### Post by CelticWarrior on 2021-04-23
Also try finding an aeroplane.

---

### Post by vskri690a on 2021-05-08
I am sorry having abandoned this thread for the last 2 weeks. I could not remove the hardblock on my laptop's internal wifi card, but today I found an answer suggesting me to disable it using the code
```
 sudo modprobe -r wl 
```
and it worked!
So, I blacklisted the module and am able to use wifi
Thank you all for helping out!

---


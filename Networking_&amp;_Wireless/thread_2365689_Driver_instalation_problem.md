---
title: "Driver instalation problem"
date: 2017-07-09
forum: Networking &amp; Wireless
---

### Post by mahdoob on 2017-07-09
:(:(:( Hello i have a realtek wireless usb dongle , it's full of problems since i put it in my pc.
after a lot of effort and trying i got it installed for windows.
Now my laptop is getting old and can't run windows smoothly enough to keep me calm and not wanting to destroy it.
i installed ubuntu which i am new to, and had the same issue with the usb, the driver instalation is pretty advanced for me and after trying for 48 hours i got no result
here's the linux driver ,i upload it to mediafire, and please somone help me and excuse my english, ty

[https://www.mediafire.com/?f2l66jzfchg91q1](https://www.mediafire.com/?f2l66jzfchg91q1)

---

### Post by Bucky Ball on 2017-07-09
Welcome. Firstly, please post the output of this command from a terminal.

```
sudo lshw -C network
```

Generally, the wireless dongle's manufacturer's driver is all but useless. I presuming this USB wireless dongle is made by Mediatek or branded as such? Generally, the only important thing is the wireless card inside the device, not the device, if you know what I mean. In this case, Realtek, and most of them work with a little tweaking. Once we know what the card is, we can proceed. There are many experts here (not including me!) and the info I have asked for will get them started. ;)

You may also want to provide the info using the wirelessinfo script in my signature, but the info from the command above may be enough.

This may seem like a silly question, but did you simply plug it in and see if you could see any wireless networks *before* attempting to install drivers??? Many wireless drivers come with the Ubuntu kernel by default, don't need to be installed (unlike Win), and many cards 'just work' out-of-the-box.

---

### Post by wildmanne39 on 2017-07-09
*Thread moved to **Networking & Wireless**.*

---

### Post by mahdoob on 2017-07-09
ok > mjj@MJ:~$ sudo lshw -C network[sudo] password for mjj: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlp18s0
       version: 01
       serial: 94:39:e5:e1:f0:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbe00000-fbe03fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: enp19s0
       version: 05
       serial: 18:03:73:9e:56:96
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.52 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:28 ioport:e000(size=256) memory:d0b04000-d0b04fff memory:d0b00000-d0b03fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.4
       logical name: wlx000b819849c9
       serial: 00:0b:81:98:49:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated



these are the results, and no, i knew that something will be missing , this dongle sucks. i woold have upgraded it if i wasn't short on money
also i am on a laptop and just so i don't waste your time , the original wireless card isn't working cause the previous owner said that he spit cofee on it, neither the keyboard, so i have been using the dongle and a seperat keyboard since i bought it:(:(:(:(

---

### Post by Bucky Ball on 2017-07-10
You have two wireless interface. I would presume one is in the machine. Why are you plugging in a wireless dongle? (I just read the last part of your post, and even though told internal wireless wasn't working, let's find out. It is recognised and a driver is installed for it just fine.)

Please remove the USB dongle as the card you have in the box should work fine with some persuasion (if it works at all). Once the USB wireless is gone, do an update and upgrade (you will need to plug in an ethernet cable to run these commands). 

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Reboot and see if you get any message re. the wireless. Click the wireless icon. Do you see any available networks there? The card you have in the machine is Broadcom ...

```
description: Wireless interface
product: BCM4313 802.11bgn Wireless Network Adapter
vendor: Broadcom Corporation
```

... and they also (mostly) work fine with a little persuasion. Ubuntu has automatically installed a driver for this card AND for the USB wireless, so that could be causing the issue. Remove the USB, please, reboot and let us know.

(PS: If you can't get ethernet to the machine, don't bother with update/upgrade, simply pull USB and reboot and follow above instructions. Incidentally, and importantly, which release and flavour are you using? Ubuntu 16.04 LTS or something else?)

(PPS: If we can't get the internal card going, it will probably be necessary to switch it off or remove it to get the USB dongle to work. The confusion is with the two cards and their drivers at the one time is my guess.)

---

### Post by mahdoob on 2017-07-10
Dude !!!
It Worked thank you a lot
i removed the damaged card and now it's working without any driver
thanks bro !!:D:D:D:D

---

### Post by Bucky Ball on 2017-07-10
Great news. ;)

Thanks for marking the thread as solved. Enjoy.

---


---
title: "Wireless problems"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by laurielegit on 2009-01-10
Hi,

Recently, my wireless connection has become increasingly shoddy. At first I could not see any wireless connections. I decided to use Ethernet, and then reinstalled the wireless proprietary driver. After that, I could see the routers, but when I tried to manually connect to one, it failed, and if it connected automatically, it would disconnect after a short while. My wireless driver is Broadcom B43 wireless driver. How can I get a reliable connection from my card. Thanks,

Laurie

---

### Post by Michael.Godawski on 2009-01-10
hi,

can you please post the output of 
```
sudo lshw -C network
```

Although some say the broadcom wlan cards does work now with the B43; but I am not that convinced.

Had some troubles with it myself. End of my adventure with broadcom was that I threw it out from my laptop and plugged in a usb wlan stick. :P

---

### Post by laurielegit on 2009-01-10
```

laurie@Edgar:~$ sudo lshw -C network
[sudo] password for laurie: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:19:66:72:c5:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:34:6a:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:bf:fa:bc:5e:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
laurie@Edgar:~$ 

```

There you are

---

### Post by laurielegit on 2009-01-10
I'm running 8.10 64 bit by the way.

---

### Post by Mutt77 on 2009-01-10
Connected to your ethernet, do Add/Remove then add the Windows Wireless Drivers. Then configure it with the Broadcom driver you need. I am using a Gateway with the B43. No problems. Sometimes with a secured network, but very rarely.

---

### Post by whaledawg on 2009-01-10
Mutt,

Could you please explain your process there? I have a very similar problem.

Thanks,
Whaledawg

---

### Post by Mutt77 on 2009-01-10
App>Add/Remove click add windows wireless drivers--then install from there. Go to Broadcom's driver site and download the required driver (it is in .exe format) save the file do not open it, cause it wont work. Then go to System>WindowsWirelessDrivers open it up then click install new driver. browse out to the saved file (I recommend saving it to the desktop if your unfamiliar with Ubuntu filesystems) then follow the line of directions from the program to install it.
Also check your restricted hardware drivers in the System>Admin>HardwareDrivers.

---

### Post by laurielegit on 2009-01-10
I have the driver installed through system->admin->harware drivers. My problem is that it isn't working properly.

---

### Post by Mutt77 on 2009-01-10
Then go to the Windows Wireless Driver option listed above then re-install the driver. If it doenst work after that then there is a physical problem with the card.

---

### Post by whaledawg on 2009-01-10
I have a simialar issue(with realtek chip on an airlink wireless PCI card). The hardware *seems* to be working fine, but I can't connect to my own unencrypted public network and my connection with my neighbors is shoddy. 

Super, incredibly frustrating.

---

### Post by Mutt77 on 2009-01-10
PCI card as in aftermarket or slide in card? If so follow the steps above. You may not have the exact driver for the card installed and it may be misreading the card. Also, make sure the wireless is enabled in the connections.:guitar:

---

### Post by laurielegit on 2009-01-10
> **Mutt77 said:**
> Then go to the Windows Wireless Driver option listed above then re-install the driver. If it doenst work after that then there is a physical problem with the card.

I'v done that, and there dosn't seem to be a physical problem with the card. I think I'll hold out for a second opinion before buying another card.

---

### Post by Mutt77 on 2009-01-10
No problem, maybe make sure all networking is enabled. I am at the end of suggestions on this one.

---

### Post by ugm6hr on 2009-01-10
Broadcom drivers have a sketchy past in Linux.

Your best bet is to try searching for details regarding the stability of your card (BCM4318) with the new b43 driver.

Additionally, it is useful to have a more helpful title to a thread (e.g. including words BCM4318 / b43).

---

### Post by whaledawg on 2009-01-10
So what wireless cards are pretty solid?

---

### Post by ugm6hr on 2009-01-10
> **whaledawg said:**
> So what wireless cards are pretty solid?

PCI / PCMCIA cards with Ralink, Atheros and Intel chipsets are generally pretty good.  Very modern chipsets can cause issues, due to driver development lagging behind hardware manufacture.

As for USB, only Ralink are universally supported.

---

### Post by whaledawg on 2009-01-10
Thanks Mutt, that worked for my and my RTL-8185 wireless card.

---

### Post by HotCupOfJava on 2009-01-10
I believe the utility Mutt is using is the graphical interface for NDISWrapper. If you don't have it installed, you can get it through Synaptic. Search for "NDISWrapper" and it will come up on the list (I think it is NDISGTK or something like that).

Nice avatar Mutt, BTW

---


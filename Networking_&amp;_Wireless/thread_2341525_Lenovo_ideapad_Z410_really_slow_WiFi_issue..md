---
title: "Lenovo ideapad Z410 really slow WiFi issue."
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by haly88 on 2016-10-28
Hey guys, happy friday,
i'm new in the forum, sorry if the thread is not good.
I'm been using Ubuntu (16.04 right now) in my notebook Lenovo ideapad Z410 for almost two years now,
I want to share with you some WiFi issue i'm having since the beginning.

I'm able to connect to Wifi network, but it works really really slow and have a lot of cuts.

I have read and try some solutions, but i'm really not an expert, and i don't understand most of them =(
The last thing i remember to read, is that the last version of bcmwl-kernel-source driver is having some issues with this card (Broadcom BCM43142 802.11b/g/n)
So i try to install some old versions of this driver without success.
[https://ubuntuforums.org/showthread.php?t=2257800](https://ubuntuforums.org/showthread.php?t=2257800)
[https://bbs.archlinux.org/viewtopic.php?id=193129](https://bbs.archlinux.org/viewtopic.php?id=193129)

I'm talking about the notebook internal WiFi card.
Here is my hardware info ([COLOR=#000000][FONT=&amp]sudo lshw -C network[/FONT][/COLOR]) 

```
*-network                      descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:08:00.0
       nombre lógico: eth0
       versión: 07
       serie: 28:d2:44:6c:73:a4
       tamaño: 10Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:29 ioport:3000(size=256) memoria:b5600000-b5600fff memoria:b5400000-b5403fff
  *-network
       descripción: Interfaz inalámbrica
       producto: BCM43142 802.11b/g/n
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:09:00.0
       nombre lógico: wlan0
       versión: 01
       serie: 14:2d:27:fb:ea:0d
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.83 latency=0 multicast=yes wireless=IEEE 802.11abg
       recursos: irq:16 memoria:b5500000-b5507fff
```

---

### Post by Bucky Ball on 2016-10-29
*Thread moved to **Networking & Wireless**.*

Welcome. As you are looking to focus on your wireless issue, best fit here. 

You have three support questions in one on your post. Suggest we deal with the wifi issues and you edit the others out of your first post and put them on separate threads of their own with descriptive titles in the appropriate forum areas, and retitle this thread accordingly (edit first post and 'Go Advanced'). 

One question per support thread is how we do it here as it is the quickest way for you to get support as least confusing. :)

As for your wifi, could you run this command, please:

```
sudo lshw -C network
```

... rather than having to work through every bit of hardware in your machine to find your wireless and you could also run and post the wirelessinfo script in the link at the bottom of this post. You don't mention whether this is an internal card or a USB dongle. Whatever method you use and whatever it is, if this is a USB wireless dongle _make sure it is plugged in_ when you run any of this. 

PS: Also it is very helpful to potential helpers when you include what you've done to try and fix your issues. You say you have had a good go at it. How? Provide links to anything you've used if you can. :)

---

### Post by haly88 on 2016-10-29
Thanks Bucky Ball, i already edit my post.

---


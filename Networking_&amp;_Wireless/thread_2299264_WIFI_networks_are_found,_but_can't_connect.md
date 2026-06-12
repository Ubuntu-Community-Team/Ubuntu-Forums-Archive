---
title: "WIFI networks are found, but can't connect"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by George_Poulos on 2015-10-16
Hello, I am very new to Linux, and so far I love it, but I cannot get the wifi working for the life of me. I have tried a fresh install twice, and neither the wifi or the ethernet connection will actually 'connect'. I have tried a whole bunch of terminal entries... However, I found a hint, maybe? When I enter `ip link` it shows 

wlan0  <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisk mq state DOWN mode DORMANT group default qlen 1000

I have tried setting wlan0 up, but as you can see it did not work. I'm using a TP-link WDN4800 wireless card with a gigabyte 990fx ud3 MB.


ANY HELP WOULD BE MUCH APPRECIATED, I AM TEARING MY HAIR OUT AT THIS POINT! THANK YOU!

---

### Post by Bucky Ball on 2015-10-16
Welcome. With the wireless dongle plugged in, please give the output of:

```
sudo lshw -C network
```

... between code tags (see last link in my signature). 

I take it you are positive the router/access point is online? I suspect that's how you posted this. :)

PS: There is no hardware switch on the machine for wireless? If you have Windows installed, does the device, or cable, get online there?

---

### Post by George_Poulos on 2015-10-17
I went ahead and ran the code this is what I got... 
and its not a dongle its a pcie network card, secondly my ethernet is not working either, so I cannot get packages... The router works perfectly, and I have tried to reset the router, with no luck, I have also changed to wpa2. This desktop is dual boot and gets internet one the Windows Side of things, I really need help ):

```
update-initramfs: Generating /boot/initrd.img-3.19.0-25-genericgeorge@George:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: fc:aa:14:79:bb:12
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:31 ioport:b000(size=256) memory:fe600000-fe600fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: c4:e9:84:0e:dd:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fe500000-fe51ffff memory:fe520000-fe52ffff



```


Thank you again for any help!

---

### Post by George_Poulos on 2015-10-17
I really need help, anyone have any ideas?

---

### Post by Hadaka on 2015-10-17
Hi George_Poulos;
your TP-link WDN4800 wireless card Supports dual band 2.4GHz and 5GHz channels.
because of this and world wide wifi regulations ,your card needs to see your cdra setting
your country code. to function properly. Your ethernet cabled connection should be working
why it is not i have no idea and untill you get some kind of connection, it will be difficult to
determine your problem. what country are you in? with that info i can give you the commands
for your cdra settings and hopefully bring your wifi to life.
also do these commands and report the output
```
lsmod | grep ath9k
rfkill list all
```
on the first command, just let me know if it finds ath9k
thanks

---


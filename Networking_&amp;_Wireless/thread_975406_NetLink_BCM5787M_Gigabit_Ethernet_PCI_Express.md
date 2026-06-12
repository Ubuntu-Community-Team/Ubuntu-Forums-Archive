---
title: "NetLink BCM5787M Gigabit Ethernet PCI Express"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by sand13w on 2008-11-08
Intrepid Ibix doesn't connect to the Internet via LAN. 

Hardy Heron works fine. 

How can I solve this?

description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:47:51:23
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.1.38 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

### Post by Das Oracle on 2008-11-25
I am having the same issue with this card, does anyone have a solution for this?

---

### Post by Das Oracle on 2008-11-25
the card uses the tg3 driver and when I do lspci -k it does show that the tg3 driver is in use by the card, however ifconfig only shows lo

---

### Post by downfallat111 on 2008-12-01
I am having the same problems with this card.

---

### Post by Das Oracle on 2008-12-03
any dev's or users have an idea of how to get this thing up and going? "lsmod" shows the tg3 driver in the list but nothing loaded to use it. After some googling this should be the appropriate driver??

---

### Post by Das Oracle on 2008-12-03
i was able to solve this problem in 8.10 and probably will work for Hardy.

In 8.10 I manually updated the kernel to 2.6.27-9 from the ubuntu repository
I am not sure if this was necessary but I did it anyway.

I grabbed the linux-image and linux-restricted modules package (i have an ati card) and then installed them via terminal 

```
sudo dpkg -i <linux-kernel>
```

then after a reboot i did not have my eth0 so i figured to go ahead and force it to load:

```
sudo nano /etc/network/interfaces
```

and in here i configured mine for dhcp

```
auto eth0
iface eth0 inet dhcp
```

then tried to bring the interface up

```
sudo ifconfig eth0 up
```

after that I was fed some errors when bringing it up, however the device still worked:

```
wmaster0: unknown hardware address type 801
wmaster0: unknow hardware address type801
Listening on LPF/eth0/00:1a:4b:82:7e:0b
Sending on LPF/eth0/00:1a:4b:82:7e:0b
Socket/fallback
DHCPDISCOVER on eth0 ....

```

after that went through i was able to get online

HOPE THIS HELPS!!

---

### Post by panchuloz on 2012-12-17
I know this is an old post but i wanna say thanks for your post because i was having trouble with my eth and wifi on some networks.On ubuntu 12.10, the file /etc/network/interfaces was 

```

auto lo 
iface lo inet loopback 

```

and i change it, to 

```

auto eth0
iface eth0 inet dhcp 

```

now it's working OK
thanks

---


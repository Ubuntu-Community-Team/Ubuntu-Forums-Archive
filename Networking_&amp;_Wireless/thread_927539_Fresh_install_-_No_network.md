---
title: "Fresh install - No network"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by mpcsm on 2008-09-23
Hi 
I'm new to Ubuntu.

Before the install, I ran the live CD and had network connection. While in live CD I installed ubuntu on HD and when I start from the hard disk, I get no wired network.

Any help would be appreciated...Thanks....remember newbie :)

---

### Post by willca on 2008-09-23
hello

what does the following give ya

ifconfig

Do you see an IP assigned to your nic?
IF not try restarting network..

sudo /etc/init.d/networking restart

---

### Post by mpcsm on 2008-09-23
ifconfig is
eth1      Link encap:Ethernet  HWaddr 00:1a:92:8f:c6:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79600 (77.7 KB)  TX bytes:79600 (77.7 KB)

Restarted network made no difference

---

### Post by Iowan on 2008-09-23
Check contents of **/etc/network/interfaces**. There should be an **auto eth1** line. (There should also be a line describing whether connection is static, DHCP, etc.)

---

### Post by mpcsm on 2008-09-24
Content of Interface is only 2 lines and no mention of auto eth1
here is what it has

auto lo
iface lo inet loopback

---

### Post by pedro_orange on 2008-09-24
Strange that it works on the LiveCD but not after you've installed!

What sort of card you using there?

```
lshw -C network
```

Should tell you what you need to know.

---

### Post by mpcsm on 2008-09-24
Description: Ethernet interface
Product: RTL-8110SC/8169SC Gigabit Ethernet
Vendor: Realtek Semiconductor Co., Ltd.
Physical id: 7
Bus info: PCI@0000:04:07.0
Logical name: eth0
version 10
serial: 00:1a:92:8f:c6:c2
width: 32 bit
clock: 66MHZ
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

---

### Post by pedro_orange on 2008-09-24
Hmm so your ifconfig is looking for logical name eth1, but your hardware list says your network card is eth0? 

Thats strange.

Do you have multiple network cards installed on this machine?

Whats in your /etc/udev/rules.d/70-persistent-net.rules

You may need to be sudo to open this.

---


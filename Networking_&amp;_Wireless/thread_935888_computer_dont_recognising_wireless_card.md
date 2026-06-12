---
title: "computer dont recognising wireless card"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Liametc on 2008-10-02
hi 
i bought a wireless card for my computer (which is the isys elite pro >>> [http://www.novatech.co.uk/novatech/range.html?t=pc&c=gaming&r=ISE](http://www.novatech.co.uk/novatech/range.html?t=pc&c=gaming&r=ISE) ) because im at uni atm and of course our internet is going to be wireless as everyone else has laptops in my house.

the wireless card is an edimax ieee802.11n card, which i bought because edimax is supposed to be compatible

ive installed the drivers but the card just isnt being recognised by the computer. its plugged in properly, just its not being seen by the computer. ive lsub but i cant see it on the list

can anybody help me please because having to use a 15m rj45 is not very conveinient.

---

### Post by Liametc on 2008-10-02
here is the output from iwconfig and lshw if this helps

liam@Liams-PC:~$ sudo iwconfig
[sudo] password for liam: 
lo        no wireless extensions.

eth0      no wireless extensions.

liam@Liams-PC:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 10
       serial: 00:1c:25:e1:5b:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.11 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s

---


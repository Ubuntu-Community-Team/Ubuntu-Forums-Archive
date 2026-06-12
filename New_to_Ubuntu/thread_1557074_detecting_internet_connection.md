---
title: "detecting internet connection"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by daisycrystal on 2010-08-20
on the day before yesterday, i installed ubuntu 10.04
the two operating systems in my computer r windows xp professional and ubuntu 10.04
for internet, i have a bsnl broadband connection.
it isn't being detected by ubuntu.

what should i do so that i can access internet using ubuntu?

---

### Post by anubhavrocks on 2010-08-20
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by dineshs on 2010-08-20
Q1.How do you connect to internet in XP?I mean do you have a PPPoE dialler to connect/disconnect?
Q2.What is the model name of your modem?
Q3.How do you connect to the modem?Ethernet,USB or wifi?
Q4.What do you get for the following terminal commands
```
ifconfig -a
```and ```
sudo lshw -C network
```

---

### Post by woodstock-girl on 2010-10-29
A few days ago I made dual boot and installed ubuntu 8.10 alongside with xp.
(should I perhaps install a newer version of ubuntu or is this just fine)
while in ubuntu I can't detect internet connection, or should I say I don't know how to configure network connection settings.

Q1: I have an ADSL connection, and I'm connected to the router in my home network.
Q2: THOMSON TG782i
Q3: Ethernet
Q4:
     ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:8b:98:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2015754951 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18960 (18.9 KB)  TX bytes:18960 (18.9 KB)

pan0      Link encap:Ethernet  HWaddr 9e:18:f3:ff:42:1d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```sudo lshw -C network ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:8b:98:29
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:18:f3:ff:42:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```P.S. I am really 100% new at this, so please feel free to treat me like a dummy :)
thanx for your help in advance

---

### Post by maverick555 on 2010-10-29
10.04 detects bsnl flawlessly.just open the network manager and dsl tab then enter the info.check all users at the bottom and done.

---

### Post by beew on 2010-10-29
> **woodstock-girl said:**
> A few days ago I made dual boot and installed ubuntu 8.10 alongside with xp.


Just out of curiosity, why did you install a two year old version of Ubuntu which supported life span has already ended (8.10 is not a LTS)?

---

### Post by Omnomnom on 2010-10-29
Welcome to ubuntu, and while your entering the information, make sure you go on your ISP's web page and enter all the info so that it works properly.

---

### Post by dineshs on 2010-10-30
woodstock-girl,
Please run ```
sudo dhclient eth0
```and then see if eth0 gets an IP .If it says `No DHCP offers recd' you may try 
[http://ubuntuforums.org/showthread.php?t=1480328&page=2](http://ubuntuforums.org/showthread.php?t=1480328&page=2)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---


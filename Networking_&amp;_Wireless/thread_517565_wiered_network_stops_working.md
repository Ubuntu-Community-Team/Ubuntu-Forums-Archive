---
title: "wiered network stops working"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Moezzie on 2007-08-04
I am having some trouble with my network through ethernet. 
After whiping my haddrive and reinstalling Fiesty Faw my network started being really crazy.
After a fiew minutes after login my connection stops working. However ubuntu does not say anything about that the connection was lost. When i disconnect the ethernet cable it gives me a warning tho.

I've tried to ping the internet, a couple of comuter here at home and the router. Nothing. 100% package loss.
Pinging localhost works tho.
The connection does not go down when runing ubuntus live cd so it probably isnt the network adapter.
I even reinstalled Fiesty one more time without any better restults.

Everything worked fine untill this morning and i have not had the any experience like it with any of my otehr machines(3 other fiesty installed with the same cd)

A quick sum up:

Symptoms:
Connection loss without ubuntu warning.
100% package loss at pinging other machines, same with router.
No internet connectivity.
Pinging local host works fine.

Really need help with this. 
Thanks

---

### Post by kevdog on 2007-08-04
Couple of things

Lets just cover the basics
Check to see network cables are connected securely to router, ethernet card
Could try changing network cable to see if it makes any difference
Is LED on in back of networking card

If everything looks ok from the basic end, could you post the following
lspci -nn
lswh -C network

---

### Post by noob12 on 2007-08-04
Kevdog means
```

lshw -C network

```

---

### Post by Moezzie on 2007-08-04
> **kevdog said:**
> Couple of things

Lets just cover the basics
Check to see network cables are connected securely to router, ethernet card
Could try changing network cable to see if it makes any difference
Is LED on in back of networking card



I have checked all these things a long time ago. Even hooked another machine up to the same cable and everything worked fine.

And i found out that after disconnecting and reconnecting the etehrnet cable, it works for a little while again. It feels almost like there is a limit of packages sent or recieved before the network shuts down.

Regarding these commands, this is the output i get while the network is working:

```

user@viewer:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:0c.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]


user@viewer:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: c
       bus info: pci@01:0c.0
       logical name: eth0
       version: 00
       serial: 00:03:0d:05:84:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion= 2.1 duplex=full ip=192.168.1.104 latency=64 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:c800-c8ff iomemory:dfdff000-dfdfffff irq:16 


```

and this is the output from when its not working:

```


user@viewer:~$ sudo lspci -nn
Password:
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:0c.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]



user@viewer:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: c
       bus info: pci@01:0c.0
       logical name: eth0
       version: 00
       serial: 00:03:0d:05:84:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion= 2.1 duplex=full ip=192.168.1.104 latency=64 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:c800-c8ff iomemory:dfdff000-dfdfffff irq:16 


```

---

### Post by noob12 on 2007-08-04
Can you post the output of **dmesg**?

When you're in the connectivity loss situation, can you show the output of
```

ifconfig -a

sudo ethtool eth0

```

---

### Post by Moezzie on 2007-08-04
> **noob12 said:**
> Can you post the output of **dmesg**?

When you're in the connectivity loss situation, can you show the output of
```

ifconfig -a

sudo ethtool eth0

```


Here is this. Do you know what it is you are lookng for exept for something "wrong"? :p

```


user@viewer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:0D:05:84:16  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask: 255.255.255.0
          inet6 addr: fe80::203:dff:fe05:8416/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:909649 (888.3 KiB)  TX bytes:544766 (531.9 KiB)
          Interrupt:16 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:631 (631.0 b)  TX bytes:631 ( 631.0 b)

user@viewer:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP MII FIBRE ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbags
        Wake-on: ub
        SecureOn password: 00:00:00:00:00:00
        Current message level: 0x000040c5 (16581)
        Link detected: yes



```

---

### Post by noob12 on 2007-08-04
Yep, I don't know what I'm looking for other than something wrong.

Can you please confirm that the output you provided is in the state when it is **not** working.  Can we see the ping failure output?

Can you post the **dmesg** output.  It's important to see that to confirm that things all loaded and initialized properly.

Also please provide the output of
```

sudo iptables -nL

```

---


---
title: "Wireless at work"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Buz_Light on 2008-04-02
Hi,
before I go any further in this post, let me tell you that I am fairly new to Ubuntu and Linux in general. Keep that in mind if you want to help me.

I run 8.04 beta on a Acer Aspire 1680 laptop (PRO/Wireless 2200BG Network Connection, driver=ipw2200, driverversion=1.2.2kmprq, firmware=ABG:9.0.2.6 (Mar 22 2005)). 

I had no problem getting my wireless network working on this laptop **at home(wpa key)** configuring the GUI [Systeme/Admin/Network] (however, I have to set it using roaming mode otherwise it won't work...).

I thought it would be as easy at work considering I never had a problem doing it with Win XP (I detect the network, enter the WEP key, DHCP connection). However, there is no way I can do it in Ubuntu... 
I can see the available wireless networks in roaming mode but when I try to connect to the one I have to use, it asks for the key (which I enter correctly), **one light becomes green on the connection icon, but the other one never becomes green**.

I tried to set it mnually and  followed this protocole ([http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")) but i never worked....

Here is the log of my terminal session :
```

carl@carl-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network:0             

       description: Ethernet interface

       product: BCM4401 100Base-T

       vendor: Broadcom Corporation

       physical id: 2

       bus info: pci@0000:02:02.0

       logical name: eth0

       version: 01

       serial: 00:c0:9f:70:93:ca

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

  *-network:1

       description: Wireless interface

       product: PRO/Wireless 2200BG Network Connection

       vendor: Intel Corporation

       physical id: 4

       bus info: pci@0000:02:04.0

       logical name: eth1

       version: 05

       serial: 00:0e:35:97:2c:48

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated





carl@carl-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:70:93:ca  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:6 



eth1      Link encap:Ethernet  HWaddr 00:0e:35:97:2c:48  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:6527 errors:1650 dropped:1650 overruns:0 frame:0

          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:1

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:34114 (33.3 KB)

          Interrupt:10 Base address:0xe000 Memory:e0208000-e0208fff 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1955 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1955 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:98060 (95.7 KB)  TX bytes:98060 (95.7 KB)





carl@carl-laptop:~$ sudo ifconfig eth1 down

carl@carl-laptop:~$ sudo dhclient -r eth1

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/eth1/00:0e:35:97:2c:48

Sending on   LPF/eth1/00:0e:35:97:2c:48

Sending on   Socket/fallback

DHCPRELEASE on eth1 to 192.168.0.1 port 67

send_packet: Network is unreachable

send_packet: please consult README file regarding broadcast address.





carl@carl-laptop:~$ sudo ifconfig eth1 up



carl@carl-laptop:~$ sudo iwconfig eth1 essid "Enseignants"



carl@carl-laptop:~$ sudo iwconfig eth1 key s:XXXXX                                             (where XXXXX is the 5 characters WEP ASCII key)



carl@carl-laptop:~$ sudo iwconfig eth1 mode Managed



carl@carl-laptop:~$ sudo dhclient eth1



There is already a pid file /var/run/dhclient.pid with pid 134519072

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/eth1/00:0e:35:97:2c:48

Sending on   LPF/eth1/00:0e:35:97:2c:48

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15

No DHCPOFFERS received.

No working leases in persistent database - sleeping.
```

I know the gateway of the router I try to connect to is 10.111.0.27
Also, the router is a Procurve AP420.

What can I do?

Thanks for your help,
Carl

---

### Post by Buz_Light on 2008-04-03
a little help would be more than appreciated. 

I'm sure someone can at least guide me in the good direction.

---

### Post by ugm6hr on 2008-04-03
To summarise:

You use Network Manager to connect.

WPA (home) works OK with DHCP.

WEP (work) - "sees" network SSID, recognises as WEP, asks for password, but fails after 1 green dot fills.

Both work on XP from same laptop.

Most likely problem:

The WEP password is an ASCII password rather than HEX.  Network Mager doesn't like ASCII  very much.

To confirm if I'm right:

Let me know if your WEP password length: 5 ASCII characters; 13 ASCII characters; 10 HEX digits; 26 HEX digits.

Here's an ASCII to HEX convertor if that is the problem: [http://centricle.com/tools/ascii-hex/](http://centricle.com/tools/ascii-hex/) 
(just remove the % signs in the result).

---

### Post by Buz_Light on 2008-04-03
Everything is right.

The key is a 5 digits ASCII key. 
I will try tomorrow with the corresponding HEX key.

Thanks a lot

---

### Post by ugm6hr on 2008-04-04
> **Buz_Light said:**
> Everything is right.

The key is a 5 digits ASCII key. 
I will try tomorrow with the corresponding HEX key.

Thanks a lot

Good luck.  I hope that works.

If not - sometimes putting the ASCII code in "" marks also works (i.e. **"ascii"** rather than **ascii**).

---

### Post by kevdog on 2008-04-04
If you use a hex key then this line:

sudo iwconfig eth1 key s:XXXXX 

becomes

sudo iwconfig eth1 key HEX_KEY


And technically, these two commands:
carl@carl-laptop:~$ sudo ifconfig eth1 down

carl@carl-laptop:~$ sudo dhclient -r eth1

Should be reversed.  You want to release the dhclient IP assigned address back to the dhcp server then take the networking card down.

---

### Post by leandromartinez98 on 2008-04-04
I think I have the same problem, I have just posted it:

[http://ubuntuforums.org/showthread.php?t=744950](http://ubuntuforums.org/showthread.php?t=744950)

Did you manage to fix it?
My wireless also works at home but not at work :-). 
Leandro.

---


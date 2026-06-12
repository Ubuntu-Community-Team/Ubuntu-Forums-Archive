---
title: "Internet connecttion problem from newb"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by LeAstrale on 2006-11-15
hi people

i just installed Ubuntu 6.06 LTS on my laptop yesterday.

and yesterday night i had a wireless connection sometimes, and it bothered me. so i reinstalled from scratch thinking that i must have made some kinda mistake when setting up the wireless broadcom chipset.

but this problem ill try again my self before posting more about it. my problem just now is that my Ubuntu laptop WON'T connect to the internet. the one beginner friendly thread i found about the subject doesn't seem to help me, but i have taken som information with me. (finding out how to pull out the info in the other thread)


when im connected with a cable to my Linksys 54 mbit Router the following is written when typing "ifconfig -a" in terminal.

as far as i know the output under eth0 and eth1 is the only thing we need, so its the only thing ill write here (unless someone tells me to write the rest).


eth0

Link encap:Ethernet HWaddr 00:0F:B0:6F:D8:8F
inet addr.:83.73.217.235 Bcast:83.73.223.255 Mask: 255.255.224.0
inet6 addr: fe80::20f:b0ff:fe6f:d88f/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeyelen:1000
RX bytes: 17939 (17.5 KiB) TX bytes: 3132 (3.0 KiB)
Interrupt:50 Base adress:0x8400


and this is what it's writing when connected directly to the ADSL modem.

eth0

Link encap:Ethernet HWaddr 00:0F:B0:6F:D8:8F
inet addr.:83.73.217.235 Bcast:83.73.223.255 Mask: 255.255.224.0
inet6 addr: fe80::20f:b0ff:fe6f:d88f/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:122 errors:0 dropped:0 overruns:0 frame:0
TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqeyelen:1000
RX bytes:20194 (19.7 KiB) TX bytes: 3132 (3.0 KiB)
Interrupt:50 Base adress:0x8400



network settings is not the kinda thing im most familiar with especially not under Ubuntu so i would like a kind word of advice for the beginner in Ubuntu

/astral-1
Link

---

### Post by philcdav on 2006-11-19
Hi guys.  similar story here.  Very new to Linux.

I have Blueyonder ethernet cable modem running fine in XP but cant get access in Ubuntu 6.06.

Device is listed, is connected and can be pinged (127.0.0.0) but NOT to outside  world,  BBC gives 'host unknown'

Have done some work but dont understand most of the results.

phil@phil-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:E3:F2:FA
          inet6 addr: fe80::201:6cff:fee3:f2fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:167414 (163.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

phil@phil-desktop:~$



phil@phil-desktop:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
phil@phil-desktop:~$



I have followed other advice such as oppecconf which gives error

'timed out waiting for device' and 

'access concentrator not respond'

pon dsl-provider got a response of 'garbage characters' back


My gut feel is that the modem may be blocked by a firewall or other restriction but dont know where to go now.

Help please. Regards - Phil

---

### Post by scrooge_74 on 2006-11-19
Ok guys, lets see if i can we of some help.

First philcdav, you are pinging your own machine 127.0.* is usually your own loopback address, check what ips your router is giving, maybe is not doing DHCP. From command try sudo ifdown eth0 and then sudo ifup eth0, see if it takes and ip then.

astral, unplug the ethernet cable, and look in the network manager if your wireless card is at least seeing the network, the name should come up. You can go from there, and dont use any encryption from the router until you get things going.

No need to reinstall UBUNTU

---

### Post by philcdav on 2006-11-20
hi scrooge_74.  tnx fer reply

OK.  looked at system today and eth0 not visible in network tools.

ran pppoeconf, found eth0 but reported  'concentrator not respond'

ran your commands and got ..

phil@phil-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
phil@phil-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:01:6c:e3:f2:fa
Sending on   LPF/eth0/00:01:6c:e3:f2:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

phil@phil-desktop:~$

not sure if i should then try ip in browser or terminal so

firefox ip (google/bbc) = 'unknown host

terminal ping (google/bbc) = no response

couldny ping 255..... either.

am starting to feel very 'green' after years of trouble free XP

regards - phil

---

### Post by scrooge_74 on 2006-11-20
from what I see your provider DHCP is not giving your card and automatic ip address.

Usually when a router gives you and IP you will get it at boot or by doing ifup. Last time I had a router not giving me an IP was faulty equipment from my provider.

My example: I have one eth0 card and one wireless eth1 card.  At home my eth0 gets ip automatically. At other places I have to give ip manually.

With wireless i choose network when I have the chance from the ones availables to me.

Check your router to see what kind of configuration it has to provide IPs.  You can use a Live CD and then get the info using ifconfig eth0

Good luck

---


---
title: "last night broadband worked today NO Go"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by tommynz1975 on 2007-08-20
my not working internet connection is a compaq laptop.. yesterday I had direct ehernet connection today nothing.. this was/is via dhcp.

I am wondering if i could have damaged the eth port?
I am using a d link 302g modem

from the laptop I can go 10.1.1.1  in the web browser and bring up the login screen to see the modem settings so I guess the modem is talking to the eth port.. is their a function in ubuntu that says .. look but I dont like you, NO internet for you...
I am using ubuntu 6.06 latest updates.

if this has happened b4 please re direct me to the answer thanks

Tom (new zealand)

---

### Post by will71110 on 2007-08-20
Do you have the gateway set?

---

### Post by tommynz1975 on 2007-08-20
on dhcp so it dosent give access to the gateway.

you do mean the feilds below the  dhcp/ tcp dropdown box in admin/networking?

or do I need to look another place?

---

### Post by will71110 on 2007-08-20
If you goto network settings (or do ifconfig in terminal),  see what your gateway comes up as.  It should be your Router (ADSL Modem).

EDIT:  You can also goto system -> Administration -> Network then double click on which ever is your NIC

Something else I was thinking also, make sure the subnets match on your router and your computer. (DHCP could be set up wrong)

---

### Post by tommynz1975 on 2007-08-22
I have done an ifconfig in mandy the non internet accessing laptop and one in holden my dell desktop that is accessing the internet...

mandy@mandy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:BC:36:05
          inet addr:10.1.1.55  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:d4ff:febc:3605/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3012 (2.9 KiB)  TX bytes:4652 (4.5 KiB)
          Interrupt:50 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

mandy@mandy-laptop:~$

holden@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:5D:45:78
          inet addr:10.1.1.7  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:56ff:fe5d:4578/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60346875 (57.5 MiB)  TX bytes:1808469 (1.7 MiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

holden@ubuntu:~$

---

### Post by will71110 on 2007-08-23
What do you have set up as a gateway.  Also do you have DNS set up in the computer?

---

### Post by tommynz1975 on 2007-08-23
on the working computers its 10.1.1.1 as the gateway.
I also type this in the url to get to the software on the modem..  my dns show up on the laptop and desktop as
202.27.158.40
202.27.156.72

even when I delete these from the dns in network settings they still come backhaving a desktop just running windows I also have same issue..  it gives me these details
address type assigned by dhcp
i[p address 10.1.1.52
subnet mask 255.0.0.0
default gateway 10.1.1.1
dhcp server 10.1.1.1
dns servers  202.27.158.40
                   202.27.156.72

it would seem with this windows machine and the mandy laptop that  the ip address is  10.1.1.xx and a working maching the ip is 10.1.1.x
on the machines the IP seems to be the same each time even tho its dhcp assighned...

all help appreciated...

---

### Post by tommynz1975 on 2007-08-24
a light went on...

my working systems have an dhcp ip of 10.1.1.x
the non working desktop and laptop have a dhcp ip of 10.1.1.xx

I cured the desktop by giving it a default ip of 10.1.1.4
if i do the same to the laptop  give it 10.1.1.9 or something i should have internet access agian..


with a re boot the computers got their dns to access my isp and the dhcp via the modem..  my question is why did it choose to start giving out dhcp ip's of  10.x.x.xx    and not   the usual 10.x.x.x.   that the system seems to like..


I hope this is a perm fix

---

### Post by tommynz1975 on 2007-08-27
laptop has now been assigned a perminent (spelling) IP like the un working desktop... and both now have internet connection. only thing is.. what will happen when I run out of numbers as this configeration doesn't seem to like an address of 10.1.1.57 but will like 10.1.1.5

change of IP was all I did to regain Internet connection.

---


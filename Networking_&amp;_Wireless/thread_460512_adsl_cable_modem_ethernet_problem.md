---
title: "adsl cable modem ethernet problem"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by NiviJah on 2007-05-31
hello, i've just downloaded ubuntu 7.04 (my first linux)
and it says that i have internet connection, but nothing related to the internet is working!

when i try to config my internet connection (pppoeconf) its saying that there is a connection (eth0) but when it is scanning for it nothing is found (timeout)
my comp' is doal-boot with xp and everything is working fine there...

please help me i don't know what to do anymore!!! 

this is the ifconfig code:

[PHP]/sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:ED:36:84:20  
          inet addr:172.21.14.16  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::220:edff:fe36:8420/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55422 (54.1 KiB)  TX bytes:4377 (4.2 KiB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)  [/PHP]

thank,
NiviJah

---

### Post by NiviJah on 2007-06-01
anyone?

---

### Post by MrObvious on 2007-06-01
Hmm. It's getting an ip address. My guess is a misconfigured subnet mask.

---

### Post by NiviJah on 2007-06-01
great....how do i fix this?

---

### Post by jonallport on 2007-06-01
> **MrObvious said:**
> Hmm. It's getting an ip address. My guess is a misconfigured subnet mask.

Agreed,

The broadcast doesn't agree with the netmask either, that mask should give a b/cast address of 172.21.31.255

I'm a little confused by the IP address, it's a reserved address and I wouldn't expect your cable provider to be doing NAT at the carrier level.  Are you sure this is a DHCP assigned address?

J

---

### Post by jonallport on 2007-06-01
Have just re-read your post.  Can we clarify what the nature of the internet connection equipment is?

You used ADSL, cable modem and ethernet in the title, what do you have? Is it:

1) ADSL modem
2) ADSL router
3) Cable modem
3) Ethernet to cable set-top box

Thanks
J

---

### Post by NiviJah on 2007-06-01
ok,
i have "motorola surfboard sb4200"
[IMG]http://i2.ebayimg.com/04/i/000/a2/05/b40c_1.JPG[/IMG]
if i'm not wrong, this an adsl cable modem, this is connected to an ethernet card inside my comp'.
did i get it right this time?

---

### Post by jonallport on 2007-06-02
Aha!  I have a collegue who has one of these, I shall break into hos house, steal it and do some testing.

On first impressions, yes this is a cable modem and should, as you say, use PPPoE.  I would, however, expect you to be getting a public IP address, not the 172.21... one you're showing.  Just check you are getting a DHCP address, not using a static one.

Thanks,

J

---


---
title: "network works on windows not linux, loopback??"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2007-01-08
Hey everyone

Ive just come back to uni from home where i was using a wireless network

Now at uni im using a cable and put everything to the same setting as before, all the same proxy setting.

But there is something involving a loopback or something

I dont understand what loopback is, and how do i get it to just use the ethernet connection

Any help or ideas would be great

Thanks for any help in advance

---

### Post by scrooge_74 on 2007-01-08
type ifconfig and see if you have anything else besides lo (which is the loopback @ address 127.0.0.1)

---

### Post by mattgaunt on 2007-01-08
yeah i do get a lot of information about eth0 which is my ethernet connection but nothing really has a value everythin is just 0's

---

### Post by scrooge_74 on 2007-01-08
then your router is not assigning you any ip address, did you try 

sudo dhclient eth0

or sudo ifdown eth0
sudo ifup eth0

that usually clears it up

---

### Post by mattgaunt on 2007-01-08
nope no luck and i normally have a few things under hosts but there isnt anything under there anymore

Ill show you what the terminal says in a sec if it helps

---

### Post by mattgaunt on 2007-01-08
This ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:0F:EA:5D:6D:2B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This is what i did with what you just suggested

> matt@matt-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
matt@matt-desktop:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 137.222.10.67 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
matt@matt-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   LPF/eth0/00:0f:ea:5d:6d:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by scrooge_74 on 2007-01-08
Your card seems to be working fine, it is just it can't get the router to give the address.

Try something if it is possible for you.

shutdown the computer and then reboot the router, or just reboot the router and then do sudo dhclient eth0 

Maybe that will clear it up

---

### Post by mattgaunt on 2007-01-08
eek!!

Well i cant do that because im connected to the university network from my room and there is no way i can do anything to that

Ill send them an e-mail or something

but thanks for all the help

---

### Post by koara on 2007-02-17
having the same problem.. did any solution work? I'd like to know before i start sending around emails to official places..

and also, any ideas why did the ethernet stop working all of sudden? i did nothing special, kernel update couple of days ago but internet worked just fine after that. and loading the old kernel at start up doesn't help anyway. 

only special thing i did was 'hibernate' before internet stopped working. i never did hibernate before.. could that be the reason?

using winXP to access the forums, obviously everything works fine. i am on edgy x86_64, hp nc6320 notebook, ethernet card broadcom gigabit.

---

### Post by sdide on 2007-02-17
hey,

What does 

```
#ip link 
```

and

```
#ip neigh
```

yield?

---

### Post by koara on 2007-02-17
Thanks for the reply sdide! Problem solved: it turned out to be an obscure problem that i brought upon myself. Hibernate had nothing to do with it. For those interested, I temporarily linked /bin/bash to point at sh (i.e. dash) and forgot to change back. How that manifested itself as 'SIOCGIFFLAGS: No such device' is beyond my meagre knowledge, but in any case restoring the proper bash solved the issue. Cheers again.

---

### Post by Richard_2007 on 2007-02-18
I think this might have something to do with your problem 

lo Link encap:Local Loopback
net addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1

your system is running in LOOPBACK so is listening only to 127.0.0.1  something has gone wrong in these settings.

---

### Post by sdide on 2007-02-18
Hey, 

I'm not sure what Richard_2007 means, when he says your system is only listening on 127.0.0.1.

the thing is, your interface is up, you're not getting DHCP.
to make sure you have link to the router, do 

# ip link

To see if your router identifies itself do:

#ip neigh

Please post output from these two, we'll take it from there.

---

### Post by byronical on 2007-02-19
I´ve got the same problem (Laptop running W2000 has no problems) and am also unable to ping my gateway.

The output from my ip neigh is

10.200.6.1 dev eth0 INCOMPLETE

I´m going to revert back to the previous kernel.

---

### Post by byronical on 2007-02-19
Reverting back to 2.6.17-10 made no difference

---


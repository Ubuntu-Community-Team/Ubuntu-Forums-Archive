---
title: "router.vs..ibex 8.10"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by daniz70 on 2009-06-05
HI
i just bought a netgear router DGB111G, i connect my pc with ubuntu 904 via ethernet...and i have no problem to connect my pc on internet...but when i try to connect my wife's notebook with intrepid there is no connection to the router...but if it runs under xp it makes the connection immediatly...so I thank you in advance for any help

---

### Post by jonobr on 2009-06-05
Hello


Could you open the terminal window and post the results of ifconfig?

With the info it gives you back it should have an IP address in there,
something like
192.168.x.x or similar,

Try (using the terminal) to ping that address
ping 192.168.1.x

then ping your machine , whatever IP address that has. then ping the router, see what happens.
Let us know how far you get

cheers!

---

### Post by DGortze380 on 2009-06-05
> **daniz70 said:**
> HI
i just bought a netgear router DGB111G, i connect my pc with ubuntu 904 via ethernet...and i have no problem to connect my pc on internet...but when i try to connect my wife's notebook with intrepid there is no connection to the router...but if it runs under xp it makes the connection immediatly...so I thank you in advance for any help

Lets start with some basic info.

Is the laptop wired or wireless?

---

### Post by daniz70 on 2009-06-07
hi
i upgrade to 9.04 but i still have the same problem with the notebook .
so i'm using the router via ethernet, here is the result of ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:1b:38:b7:dd:b8  
          indirizzo inet6: fe80::21b:38ff:feb7:ddb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:1428 (1.4 KB)

lo        Link encap:Loopback locale  
          inet indirizzo:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:240 (240.0 B)  Byte TX:240 (240.0 B)

then i went to system/administration/network tool and under the voice PING
i set the address 127.0.0.1...it made 5 succesful attempts...
the things that really DRIVES ME MAD is that with VISTA I don't have any problems with the router...
Thanks in advance for further help

---

### Post by jonobr on 2009-06-07
Hello

Its seems as if you are not getting an IP address from the router according to your ifconfig

Are you doing static or dynamic IP addresses?

---

### Post by daniz70 on 2009-06-07
actually i don't know

---

### Post by jonobr on 2009-06-10
Hello

In xp, open up a command prompt

start->run

type ipconfig /all

Im guessing it will return something like, 192.168.1.X
with a subnet mask of 255.255.255.0
a default router and gateway of 192.168.1.1

and a DNS of something line 192.168.1.1 or 192.168.0.1 or something like that.
The try to ping 192.168.1.50.
Hopefully it will not get a response.

Take note of that information and go to your network maanger applet.
Open it and manually configure IP addresses in your network manger,

Insert a static IP address of something the address you pinged 
192.168.1.50, then add the dns IP address and subnet mask.,
All this is setting your system up with a static IP.
Once thats all configured, try your broswer,
see if it work.
If it does, its a dhcp issue. You could run with the static IP address on your system, but get that done and see how far you get.

---

### Post by daniz70 on 2009-08-02
HI
I come out of this mess....3 steps
1 back up data
2 formatted the logical partition
3 installed 9.04 in a primary partition

now everything goes...maybe it was only my lucky day! bye

---


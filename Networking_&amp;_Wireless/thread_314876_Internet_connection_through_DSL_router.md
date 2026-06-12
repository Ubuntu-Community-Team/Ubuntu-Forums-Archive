---
title: "Internet connection through DSL router"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by modoom on 2006-12-08
hello to all.
i'm noob to the linuxes, so this must be the problem in the first place. :)
i've got ubuntu installed and it recognized my 3com 3c905c ethernet card. i connect to the internet through a router modem, so there is no need to set up a connection. the problem is, that i can ping the router, the ethernet card do recieve packets, but still it can't connect to any website. i tried manual ip and default gateway set up, but it doesn't help. on xp it works fine...
also, in the interface information it shows all the data about the ethernet card, except of link speed - it says not available...

any ideas what is the problem?... :neutral: 
thx

---

### Post by Carbonbasedmistake on 2006-12-08
I just received a dsl modem from Verizon. I had to access the modem/router through 192.168.1.1 (I believe) and set a user name and password. Next I had to run pppoe from the command line and insert user name, password, and basically just accept the default parameters for mtu etc. I also opened the Ubuntu network gui and enabled the connection, set dhcp as the mode, and activated eth0. Now running "pon dsl-provider" turns it on "poff dsl-provider" turns the connection off. There is a page in the wiki for setting up a dsl pppoe connection. Also if you go to dslreports they have a lot of info on setting up your specific modem/router. 

luck

bob

---

### Post by modoom on 2006-12-08
thx for the answer, but it's not the problem that i meant. u explained to me how to connect through an adsl modem, but my router is already configured with the username and password and is always online. in xp i just plug in network cable and i can surf. in ubuntu, it can ping the router, but does not load any websites, no matter if i give him a static ip or let router give the ip

---

### Post by dbott67 on 2006-12-08
Can you please post the output of the following commands:
```
dbott@dapper:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

```
dbott@dapper:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
and
```
dbott@dapper:/etc$ **cat /etc/resolv.conf**
nameserver 192.168.1.1

```

---

### Post by milton1 on 2006-12-08
Do you have DNS set up? Try typing your router's ip into your browser. if you get the setup page, then you have a connection. it could be that your system does not know where to look up web pages.

---

### Post by modoom on 2006-12-08
> **milton1 said:**
> Do you have DNS set up? Try typing your router's ip into your browser. if you get the setup page, then you have a connection. it could be that your system does not know where to look up web pages.

well, as i said, i do can ping the router, so i also can enter its setup. as far as i know, i don't need to set up dns manually... but i can try... where do i do it in ubuntu?

---

### Post by modoom on 2006-12-08
freethinker@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:02:E0:50:B8
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::201:2ff:fee0:50b8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:291565 (284.7 KiB)  TX bytes:138926 (135.6 KiB)
          Interrupt:5 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

freethinker@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0

---

### Post by dbott67 on 2006-12-08
> **modoom said:**
> well, as i said, i do can ping the router, so i also can enter its setup. as far as i know, i don't need to set up dns manually... but i can try... where do i do it in ubuntu?

The settings are in /etc/resolv.conf.  Can you post the output:
```
cat /etc/resolv.conf
```

Also, please wrap your output in [code ] tags [/code ]; it makes it easier to read.

Thanks,
Dave

---

### Post by modoom on 2006-12-08
sorry, forgot. but it's just the default gateway. it is listed in the previous message... anyway, here it is:
```
nameserver 10.0.0.138
```

---

### Post by dbott67 on 2006-12-08
> **modoom said:**
> sorry, forgot. but it's just the default gateway. it is listed in the previous message... anyway, here it is:
```
nameserver 10.0.0.138
```

That's fairly normal (mine is just my D-Link router as well), however, some people have had major issues with just using the DNS-forwarder built-in to the router (might require a firmware update to your router).

Anyhow, you can quickly try this fix: add the 2 servers from [www.opendns.com](www.opendns.com) to your /etc/resolv.conf file:
```
gksudo gedit /etc/resolv.conf
```
Add these lines:
```
[COLOR="Red"]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR]
nameserver 10.0.0.138
```

Let me know if this fixes it.

-Dave

---

### Post by modoom on 2006-12-09
> **dbott67 said:**
> 
Let me know if this fixes it.
-Dave

yep, it works. thx alot. writing this message from ubuntu. :)
but why does this happen?? does xp has it's own addresses built in?

---

### Post by dbott67 on 2006-12-09
> **modoom said:**
> yep, it works. thx alot. writing this message from ubuntu. :)
but why does this happen?? does xp has it's own addresses built in?

Not sure why it happens... I've personally never had a problem, however, I have noticed a fair number of folks the have name resolution issues.

I'm really just guessing here:

1. it may be a firmware issue in the router (you can check the vendor's website for an update)
2. it could be an IPv6 issue (some people are recommending disabling IPv6... again, I've never had a problem)
3. it could be little green goblins
4. it could be a conspiracy by Bill & Co. :)

My guess is it's #1.  What make & model router do you have? And what's the firmware version?

-Dave

---

### Post by modoom on 2006-12-09
> **dbott67 said:**
> 
What make & model router do you have? And what's the firmware version?
-Dave

it's eci b-focus 312+ with software version T340A.040809a1_25

---

### Post by dbott67 on 2006-12-09
I just checked their website and couldn't find any firmware updates for it.

[http://www.inoviatele.com/Products_Hi/HiBFOCuS_312+.asp](http://www.inoviatele.com/Products_Hi/HiBFOCuS_312+.asp)
[http://www.inoviatele.com/downloads/default.asp](http://www.inoviatele.com/downloads/default.asp)

You may want to contact their support team directly to see if there's an update (or just login to the router and see if it has an online link to firmware updates somewhere).

-Dave

---

### Post by cyberbuff on 2006-12-12
Dear Friends, 
I am having the same problem. I am using an ADSL router and an NIC. I can connect to the net and ping it, as mdoom. But cant open up any webpage. Also I cant find the /etc/resolv.conf file.:confused: 
Someone please help me...
Regards

---


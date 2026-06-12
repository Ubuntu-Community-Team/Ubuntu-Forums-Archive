---
title: "No idea how to get wireless router working with Ubuntu (Gutsy)"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by fullmetalgerbil on 2008-05-07
I just got a Linksys WRT54GS wireless G router that I'm trying to get working with my
box. I've never installed/configured a wireless router before and I really have no clue how to do it. The last computer the router was hooked up to was a Windows machine, and of course when I just crossed my fingers and plugged everything in it didn't work.
I'm running Ubuntu 7.10 on my desktop which is what the router is going to be hardwired to, and I'm just trying to get a wi-fi signal for my laptop (which is running Ubuntu 8.04 if that makes any kind of difference).
I'm supposing I'll just need to find Linux drivers for the router and configure it, but like I said I have no clue.
Any help would be much appreciated:)

---

### Post by lord_zerg on 2008-05-07
i'm not sure if it's going to be of any help. but usually linksys router use the 192.168.1.0 net by default. the router being at 192.168.1.1
may be you could check to see if your desktop pc is also configured to be in that network. typing ifconfig in a terminal should give some info

```
pedro@pedro-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:19:b9:79:5e:11  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:22 

[B]eth1      Link encap:Ethernet  direcciónHW 00:1b:fc:68:92:58  
          inet dirección:192.168.1.110  Difusión:192.168.1.255  Máscara:255.255.255.0[/B]
          dirección inet6: fe80::21b:fcff:fe68:9258/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:5698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5043 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:7038836 (6.7 MB)  TX bytes:548444 (535.5 KB)
          Interrupción:16 Memoria:efcfc000-efd00000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:1738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1738 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:86900 (84.8 KB)  TX bytes:86900 (84.8 KB)

```

in  the code above eth1 is the wireless card on my laptop. you can check the ip address assigned to your card on system administration - network.

---

### Post by lord_zerg on 2008-05-07
i'm not sure if it's going to be of any help. but usually linksys router use the 192.168.1.0 net by default. the router being at 192.168.1.1
may be you could check to see if your desktop pc is also configured to be in that network. typing ifconfig in a terminal should give some info

```
pedro@pedro-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:19:b9:79:5e:11  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:22 

[B]eth1      Link encap:Ethernet  direcciónHW 00:1b:fc:68:92:58  
          inet dirección:192.168.1.110  Difusión:192.168.1.255  Máscara:255.255.255.0[/B]
          dirección inet6: fe80::21b:fcff:fe68:9258/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:5698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5043 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:7038836 (6.7 MB)  TX bytes:548444 (535.5 KB)
          Interrupción:16 Memoria:efcfc000-efd00000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:1738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1738 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:86900 (84.8 KB)  TX bytes:86900 (84.8 KB)

```

in  the code above eth1 is the wireless card on my laptop. you can check the ip address assigned to your card on system administration - network.

---

### Post by Tomatz on 2008-05-07
Read the manual on howto access your router config it is _usually_ 192.168.1.1 (type in your browser url bar).

Then run the setup wizard (router config).

Then if you cant wirelessly connect (laptop) post back ;)

---

### Post by fullmetalgerbil on 2008-05-07
ran the terminal command, this is what I got:
david@david-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:A7:D0:A2  
          inet addr:192.168.1.47  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fea7:d0a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2439418 (2.3 MB)  TX bytes:613174 (598.8 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by fullmetalgerbil on 2008-05-07
I dont have the manual, thats the problem.

---

### Post by fullmetalgerbil on 2008-05-07
And I cant log in to the router since when I plug my ethernet in and hook it back to the computer with another cable I get no internet.

---

### Post by fullmetalgerbil on 2008-05-07
Hello? Anyone? Cant I just download some drivers or an application or some friggin thing that will *allow[I] me to access my router? The thing is configured for Windows and theres no way I can log into it from my machine as it is.*[/I]

---

### Post by Tomatz on 2008-05-08
You dont need drivers to access your router config. You dont even need an internet connection.

Switch your router on

Plug the ethernet cable into port 1 on the back of your router

Then plug the other end of the cable into your lan port on the back of your computer. 

Open firefox

In the url (address) bar type:

```
192.168.1.1
```

Now configure your router (you will need to plug in the **dsl connector into the dsl port on the back of the router if its an adsl modem-router** or if its a **cable router, run the ethernet cable** from the modem into the **wan** port on the router) ;)

---

### Post by lord_zerg on 2008-05-08
do as tomatz says. connect your pc to your router and point your browser to 192.168.1.1
your ethernet card is assigned an address in that network so you should be able to access the router config with no problem.
if you can't could you please check your proxy settings in ubuntu. normally you don't need a proxy when connecting directly to the router.

---


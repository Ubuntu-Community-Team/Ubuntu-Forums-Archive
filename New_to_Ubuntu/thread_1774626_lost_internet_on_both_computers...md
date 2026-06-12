---
title: "lost internet on both computers.."
date: 2011-06-03
forum: New to Ubuntu
---

### Post by gordon33 on 2011-06-03
Hello all

I did an update on my lap top yesterday and have not get to the internet since.  

While working on labtop (see: _[http://ubuntuforums.org/showthread.php?t=1774376&goto=newpost](http://ubuntuforums.org/showthread.php?t=1774376&goto=newpost)_ ) I did an up date on desk top now nether computer will let me get to the internet.

Earlyer I was able to do a live install from an old ubuntu 9.10 disk and get to the internet on the lab top.  Sadly now I can't even do that with ether computer.  


What options are their?

At the moment I am using a computer at the local libary to send this SOS.

Gordon

---

### Post by jtarin on 2011-06-03
As I read in your other thread you can connect hardwire. How do you connect? ADSL,PPPoE,Cable etc.?

---

### Post by wolfen69 on 2011-06-03
Try unplugging your modem/router for a few seconds, wait a couple minutes and see what happens. I've seen this happen before.

---

### Post by gordon33 on 2011-06-03
Hello wolfen69, and jtarin

Presently I am at the local library and unable to get to the internet using there line ether.  I did try unpluging the modem at home (that made no difference) before coming here  

I was able to use my desk top with a line until I instaalled updates about 8 hours ago.  Now I can not get ether computer to connect to the internet.  No go with line or wireless.

Gordon

---

### Post by gordon33 on 2011-06-03
Opps wolfen69

It was my net gear wireless router I unpluged.  I am going home to unplug my WOW router.  But wait The lap top is not working here.  That decreases my hope for the unplug to fix things at home.  nothing ventured nothing gained.

I will be back at the library tomorrow if the unplug does not help.

Gordon

---

### Post by corncob on 2011-06-03
Unplug the router and the modem at the same time. (The internet light is on in the modem, eh?)

---

### Post by gordon33 on 2011-06-05
Hellon Corncob

Yes the modem light is on. Unpluged the router and the modem at the same time; still no connection to the internet.

I am thinking of doing an update to Unbuntu 11.04 to get the internet connection back.


Gordon

---

### Post by jtarin on 2011-06-05
> **jtarin said:**
>  How do you connect? ADSL,PPPoE,Cable etc.?Again I will ask what kind of connection do you have when you are connected with wire?

---

### Post by gordon33 on 2011-06-05
Hello jtarin

I have WOW cable coming in to the house.  I connect to the WOW router with a USB cable to the Netgear wireless router for my lap top.  

OR, I connect the desk top computer to the WOW router with USB cablel.  When I connected the Lap top to the WOW router with the USB cable I still can not connect to the internet.

I hope I answered corectly.  I am sorry for my confusion, some times I do not understand what is being asked.

Both of these computers worked fine 3 days ago Friday.

Gordon

---

### Post by jtarin on 2011-06-05
In a terminal issue the command ifconfig -a and post the results.

---

### Post by gordon33 on 2011-06-06
gordon@gordon-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:1f:16:76:dc:4b  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KB)  TX bytes:1776 (1.7 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:af:c5:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

gordon@gordon-laptop:~$

---

### Post by jtarin on 2011-06-06
Do you have pppoe installed? Do you provide a username and password to logon to your ISP? Do you have this connection configured in Network manager?

---

### Post by LowSky on 2011-06-06
You said earlier that the internet worked fine from the LiveCD and now does not. Usually if that happens its a hardware issue.

Network manager should give a list of available wifi networks, you should also be able to connect using a wired connection. If you cannot do either I would think something happened while you did your updates. It makes little sense that both have failed.

---

### Post by jtarin on 2011-06-06
> **LowSky said:**
> You said earlier that the internet worked fine from the LiveCD and now does not. Usually if that happens its a hardware issue.

Network manager should give a list of available wifi networks, you should also be able to connect using a wired connection. If you cannot do either I would think something happened while you did your updates. It makes little sense that both have failed.We need to find out how he connects to this WOW router/modem because all his connections are seen. NetworkManager doesn't always do the job it is supposed to do on its own.

---

### Post by LowSky on 2011-06-07
> **jtarin said:**
> We need to find out how he connects to this WOW router/modem because all his connections are seen. NetworkManager doesn't always do the job it is supposed to do on its own.

Its a standard cable modem... connect directly to it and it will link up... no passwords or logins required.. thats how 99 percent of cable companies work.

if he has connection issues at other locations I'm betting his wifi adapter needs a driver. if he cant connect by wire then it has to be an issue with the router

---

### Post by jtarin on 2011-06-07
I agree on the router if the WOW box is as you say it is.

---

### Post by gordon33 on 2011-06-07
Hello  LowSky, and jtarin

I will check to see if pppoe installed latter.

I do NOT use a username and password to logon to my ISP.

Where would I check to see if this connection is configured in Network manager? 


YES YES! Its a standard cable modem I connect directly to it and it has linked up... no passwords or logins required.. thats how my cable companies works.

It will be tomorrow befor I can report back on some of the other coments.  I will be back in about 3 or 4 hours to report on what I can.

---

### Post by gordon33 on 2011-06-07
Hello LowSky

"if he has connection issues at other locations I'm betting his wifi adapter needs a driver. if he cant connect by wire then it has to be an issue with the router"


Are you talking about the computers modem?

gordon33

---

### Post by gordon33 on 2011-06-07
Hello jtarin, and LowSky

I disconnected the netgear wireless router from the WOW modem and connected the desk top directly to the WOW modem.  The desk top can now connect to the Internet.  

I am still unable to connect to the internet with the Lab top even when it is hard wired to the WOW modem.  What should I check on lap top.

The pppoe is not installed on the lap top, but pppoeconfig is installed.



Thank you for all your help so far.

Gordon33

---

### Post by dFlyer on 2011-06-07
> **gordon33 said:**
> Hello jtarin

I have WOW cable coming in to the house.  I connect to the WOW router with a USB cable to the Netgear wireless router for my lap top.  

OR, I connect the desk top computer to the WOW router with USB cablel.  When I connected the Lap top to the WOW router with the USB cable I still can not connect to the internet.

I hope I answered corectly.  I am sorry for my confusion, some times I do not understand what is being asked.

Both of these computers worked fine 3 days ago Friday.

Gordon

Have you tried bi-passing the router and connecting directly to the modem. I've had routers go bad.

---

### Post by gordon33 on 2011-06-07
Hello dFlyer

 Yes! Today I removed the netgear wireless router from the system and I can now access the internet from the desk top. The desk top is now hard wired direct to the WOW modem.


I am also able to access the internet from my lap top when it is hard wired direct to the WOW modem. I picked another kernel right clicked on the wireless icon and checked enable networking and was able to connect with my lab top.  Still able to access the internet with the lab top when I went back to the first kernel.

Looking back I wonder why things worked, or did not work, one minute and the next minute the situation flip floped.

Still all is well that ends well.  I will be looking at the wireless part of this next.  but my guess at this point is the netgear has seen better days.

Gordon

---

### Post by jtarin on 2011-06-07
Good!!! You got it working. Ensure your connections between the router and modem are correct if you think your router is still good. Maybe check it on another connection other than WOW.

---

### Post by jtarin on 2011-06-07
> **gordon33 said:**
> Hello dFlyer

 Yes! Today I removed the netgear wireless router from the system and I can now access the internet from the desk top. The desk top is now hard wired direct to the WOW modem.


I am also able to access the internet from my lap top when it is hard wired direct to the WOW modem. I picked another kernel right clicked on the wireless icon and checked enable networking and was able to connect with my lab top.  Still able to access the internet with the lab top when I went back to the first kernel.

Looking back I wonder why things worked, or did not work, one minute and the next minute the situation flip floped.

Still all is well that ends well.  I will be looking at the wireless part of this next.  but my guess at this point is the netgear has seen better days.

Gordon

When Ubuntu connects to the internet the first time it needs to communicate with the repositories to download drivers for your wireless connection. You might check to see if there is new firmware available for your router. I had some problems with my D-link and new firmware solved it.Just a suggestion. Mark this post as solved if you will so it will help someone else. Start a new post on your wireless connection if you need to.

---

### Post by gordon33 on 2011-06-07
hello jtarin

Desk Top wire to WOW modem.


gordon@gordon-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:77:4f:76  
          inet addr:67.149.79.75  Bcast:67.149.79.255  Mask:255.255.240.0
          inet6 addr: fe80::21d:9ff:fe77:4f76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:32508590 (32.5 MB)  TX bytes:3715280 (3.7 MB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12048 (12.0 KB)  TX bytes:12048 (12.0 KB)

gordon@gordon-desktop:~$

---

### Post by gordon33 on 2011-06-07
Hello jtarin

There is new firmware available for my router. While looking around over the last few days I saw the new firmware on netgears router log in page.  I will be working on that next.  

I did mark this a solved and may start a new post for the wireless if the router update fails me..  


Lap top wire to WOW modem

gordon@gordon-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:76:dc:4b  
          inet addr:24.192.13.22  Bcast:24.192.15.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:16ff:fe76:dc4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:621073 (621.0 KB)  TX bytes:62828 (62.8 KB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:af:c5:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

gordon@gordon-laptop:~$

---

### Post by jtarin on 2011-06-07
Both configs look good for wire. I notice you don't seem to have a static IP rather a Dynamic one....I would have thought it would be so on a cable connection.

---


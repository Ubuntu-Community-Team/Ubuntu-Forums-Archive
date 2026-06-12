---
title: "Can't connect to internet/network"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by orangeschoolbus on 2010-03-20
Hi, I'm a total noob with Ubuntu and I could use some help...

I can't connect to anything. I plug in the ethernet cable, click on auto eth0 after about 30 secs it say "Wired network disconnected you are now offline" I've tried connecting with/without router, I've also tried setting up the connection manually to no avail...

Any help is appreciated, thanks

---

### Post by dearingj on 2010-03-20
Could you tell us more about your computer, such as what network card it uses or whether you have any other operating systems installed (and if so, whether the network card works with those systems)?

---

### Post by orangeschoolbus on 2010-03-20
Ubuntu is the only OS on the computer, I was previously running XP and everything worked fine...I don't have a separate network card, just the ethernet plug on the MB...

My MB model is Gigabyte GA-7VAXP

---

### Post by mvelte54 on 2010-03-20
Just a stab in the dark here but why are you clicking on the auto eth0? It should auto-magically detect whether or not your Ethernet card is installed and hook it's self up. By clicking on it I believe you are telling it to disconnect.

---

### Post by orangeschoolbus on 2010-03-20
I clicked auto eth0 because I had no connection, so I was trying to 'jump start' it....

---

### Post by Trandre on 2010-03-20
Do you have red and green lights on the socket where you put your cable in?

Are you able to ping your router?

If it is a laptop is the power connected(laptops dometimes disonnect in power saving mode)?

Can someone display what the equivalent to the cmd command in windows is: ipconfig and ipconfig /release and ipconfig /renew


Trandre

---

### Post by orangeschoolbus on 2010-03-20
I have the green light where I plug in the cable. I cannot ping the router, I've also tried connecting without the router. I'm stumped, that's why I'm here... :)

---

### Post by orangeschoolbus on 2010-03-20
Still looking for help. Does anyone have any ideas that might help me solve this dilemna?

---

### Post by linuxman94 on 2010-03-20
Run this command and post the output.

```
ifconfig
```

---

### Post by orangeschoolbus on 2010-03-20
> **linuxman94 said:**
> Run this command and post the output.

```
ifconfig
```

eth0	Link encap:Ethernet HWaddr 00:20:ed:26:77:35
	inet6 addr: fe80::220:edff:fe26:7735/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:0 errors:0 dropped:22636 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0.B) TX bytes:0 (0.0.B)
	interrupt:10 Base address:0xb400

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:24 errors:0 dropped:0 overruns:0 frame:0
	TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:1640 (1.6KB) TX bytes:1640 (1.6KB)

---

### Post by orangeschoolbus on 2010-03-21
Can somebody tell me what all that means?

---

### Post by orangeschoolbus on 2010-03-21
UPDATE I don't know why, but the manual connection I had set up, just connected. I got an error message on another computer that it was using the same IP as another on the network...However I still cannot get online...

Help please

---

### Post by pushkar_k on 2010-03-21
what kind of network do you have ? (wireless/DSL)  etc.
Have you configured new connection through "Edit connections" ?

---

### Post by orangeschoolbus on 2010-03-21
> **pushkar_k said:**
> what kind of network do you have ? (wireless/DSL)  etc.
Have you configured new connection through "Edit connections" ?

I have cable internet, 2 computers "wired" through a router

---

### Post by Iowan on 2010-03-21
> **orangeschoolbus said:**
> Can somebody tell me what all that means?In brief - it means your machine doesn't have an IP address. Does your router serve as DHCP server? You say there are only two machines on your network?  Short term, you might pick another IP address. It'd be best to avoid the DHCP range, but until you find what's not working properly, you should be able to change the last number to something other than 0, 1, 255, or whatever the other machine is using.

---


---
title: "Can't access router's network interface"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by moreon on 2007-05-01
Hello Everybody!

I recently did a clean install of Feisty and when I try to access my router's web interface through FF I simply can't, where in Edgy it was working fine.

Why is this happening? Any ideas? Thanx in advance.

---

### Post by tatster on 2007-05-01
Hi,

I guess my first question would be, does Feisty have an IP address correctly?
In terminal, run **ifconfig** and paste the results.

And can you ping the router from your Feisty box?  

Depending on the answers to these questions might help steer you in the right direction.

Tat.

---

### Post by moreon on 2007-05-01
The output of ifconfig is this:

> eth0      Link encap:Ethernet  HWaddr 00:0F:EA:89:7B:FB  
          inet addr:10.0.0.8  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:eaff:fe89:7bfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5090977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6100199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2179835565 (2.0 GiB)  TX bytes:1352164667 (1.2 GiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:367880 (359.2 KiB)  TX bytes:367880 (359.2 KiB)


And I can ping my router.

Btw in the title I meant to write web interface not network interface ;)

---

### Post by Floppyjoe on 2007-05-01
Can you access other sites on the internet?
Are you typing in the correct IP address?

---

### Post by moreon on 2007-05-01
> **Floppyjoe said:**
> Can you access other sites on the internet?
Are you typing in the correct IP address?

The internet works perfectly. The problem is I can't access my router's web interface. I use the 10.0.0.2 address as the manual says.

---

### Post by Floppyjoe on 2007-05-01
Are you trying to access it wirelessly or through a cable connection?
Sometimes people turn off the ability to access the web interface from wireless connections.
If that is the case you either have to access it from a wired connection or reset the router.

---

### Post by moreon on 2007-05-01
> **Floppyjoe said:**
> Are you trying to access it wirelessly or through a cable connection?
Sometimes people turn off the ability to access the web interface from wireless connections.
If that is the case you either have to access it from a wired connection or reset the router.

I don't really get what you're saying but there is definitely nothing wireless involved. The router is connected to my ethernet card and I'm trying to access its web interface through firefox.

As I said it was working just fine in Edgy and I'm wondering why isn't the same happening in Feisty.

Do you have any clue?

---

### Post by Floppyjoe on 2007-05-01
I was just wondering if you were trying to access the web interface from a computer that was wirelessly attached to the router. There is an option in the web interface to turn off this ability and some people don't want to give people that gain access to their router wirelessly to be able to access the web interface. Scince you say you are connecting through a cable connection this is obviously not the case so it rules out that probability. I'm just trying to think of reasons why it would not work but am having difficulty explaining your routers behaviour.

You didn't by any chance change your routers IP address when you were using edgy did you?

---

### Post by kelvin spratt on 2007-05-01
are sure thats the adress my routers address in on the bottom plate and its an ip address XXX.XXX.X.X
 numbers instead of xs it should not be in the manual as the ip no is your routers address well thats how netgear do it and the password is their to unless you change it as you should

---

### Post by moreon on 2007-05-01
> You didn't by any chance change your routers IP address when you were using edgy did you?

No I haven't changed anything.


[edit] Silly me!!! I just remembered I had changed the port it was listening to. 

I'm terribly sorry to have bothered you for an issue that was caused by my amnesia. :( 
Anyway I very much appreciate your concern.

Till the next stupid post ;)

---

### Post by Floppyjoe on 2007-05-01
> **moreon said:**
> No I haven't changed anything. In fact I don't know how:)

Well you got me stumped. Maybe somebody else will have some ideas.:)

---

### Post by moreon on 2007-05-01
> **Floppyjoe said:**
> Well you got me stumped. Maybe somebody else will have some ideas.:)

Of course you're stumped. Have a look at the edit in my previous message and you'll see why.:)

---


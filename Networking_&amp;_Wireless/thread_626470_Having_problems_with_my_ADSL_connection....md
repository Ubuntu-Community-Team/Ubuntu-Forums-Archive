---
title: "Having problems with my ADSL connection..."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by c2006 on 2007-11-29
...And it's pissing me off.

Now, I'm having no issues whatsoever in Windows (case in point, I'm posting from Windows now). 

My Ubuntu installation is Gutsy.

Router: D-Link DSL-504T (wired) connected via ethernet port (I only have one, so it's eth0 in Ubuntu).

This is frustrating me to no end as it's preventing me from setting up Ubuntu completely (such as using the nvidia drivers which *is* annoying).

I'm a relatively new user, but thought it'd be better to post this here. I wasn't having this problem in Feisty, which worked fine. Unfortunately I can't reinstall Feisty because my Feisty CD has decided to go AWOL and I did a late night reinstall a while back to fix some niggles I was having in Feisty but accidentally installed it over my Windows partition (won't be doing THAT again, especially when as tired as I was then!)

Ubuntu thinks there's a connection but nothing happens.

---

### Post by mellowd on 2007-11-29
Could you open a command prompt in windows and type this:

```
ipconfig
```

Post the results.

Then boot into linux and open a terminal and type this:

```
ifconfig

```
and post the results.

---

### Post by dialgo on 2007-11-29
You can try left clicking your network icon, then going into the properties for the wired connection, from there disable 'Roaming Mode' and enter in the SSID and the IP address of your router, if you need help finding these just post again and i can help.

Alternatively if roaming mode is already off, try activating it and then choosing your router from the network list.

---

### Post by c2006 on 2007-12-02
OK, I've got the configs. Apologies for taking so long, I got a bit busy.

In Windows, this is all I get (I'm using code tags to delineate):

```

Windows IP Configuration


Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 10.1.1.3
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . : 10.1.1.1

```

Useful, huh? :lolflag:

And the below is what I get from ifconfig in Ubuntu... A LOT more information...

```


ifconfig
eth0      

Link encap:Ethernet  HWaddr 00:17:31:B6:5C:48  
          
inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          
inet6 addr: fe80::217:31ff:feb6:5c48/64 Scope:Link
          

UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          

RX bytes:1871 (1.8 KB)  TX bytes:6229 (6.0 KB)
          
Interrupt:17 Base address:0xc000 

lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          

UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:0 (0.0 b)  
TX bytes:0 (0.0 b)


```

Apologies for the poor formatting, Windows messed it up).

I don't know if it's just me, but alot of that looks too "generic" to me (as in what it defaults to if it can't find anything).

Roaming is OFF and changing that setting doesn't help any (I've already tried that, and just about everything I can think of). My gut says it's a simple matter of Ubuntu not picking up the right setting at install somewhere, but I'm far from an expert. Especially when it comes to networks.

I should make aware at this point that my connection has a Dynamic IP.

---

### Post by c2006 on 2007-12-02
Any help? It's not that it's super urgent, as I have a Windows install to use, but I do happen to be quite partial to the way Linux is (and particularly how much quicker it boots and loads everything up which I'd prefer to use if I'm just browsing the 'net).

---


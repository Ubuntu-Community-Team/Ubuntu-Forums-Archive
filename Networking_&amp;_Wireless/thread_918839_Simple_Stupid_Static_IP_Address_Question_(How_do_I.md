---
title: "Simple Stupid Static IP Address Question (How do I set it?)"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Ocelaris on 2008-09-13
This has to be a very simple stupid question. But I've had trouble everytime in Ubuntu... 

How Do I set a static address? I'm an IT guy by profession, and I can set static address is windows just fine. And on my home network, I know my addresses and which work in windows fine. i.e.

IP range 192.168.0.1-100 = static 100-254 = dhcp
Subnet 255.255.255.0
Gateway 192.168.0.1

I don't care if it's command line or GUI, but I set say my unbuntu box to 192.168.0.10 (Nobody else is using that IP), gateway and subnet, through network commander or whatever the gui is, (off of roaming) and I can't get out.

So it must be something simple, stupid of me that everyone else knows... I know my networking isn't top notch, but this has to be something brain fart easy that I'm missing...

---

### Post by darco on 2008-09-13
I have my Linksys router set as the static dhcp server and I assign a static ip via the MAC address. Not sure what in Ubuntu you need to do but I dont have any issues w/my static ip's this way...

good luck

darco

---

### Post by ansicplusplus on 2008-09-13
Hy Ocelaris
setting a static ip is really easy. Just edit /etc/network/interfaces to look like this for ip 192.168.0.54
```
  
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.0.54
netmask 255.255.255.0
gateway 192.168.0.1

```
After that restart the network using ```
sudo ifdown eth0 && sudo ifup eth0
```
Yours ansicplusplus

---

### Post by Ocelaris on 2008-09-13
Well, I have a Smoothwall (linux based) firewall, and I know I can set it from that firewall based on MAC address to give out a static IP address...

But say I want to tell the machine what address it is going to be, instead of from the DHCP server, i.e. forcing a PC onto one domain. 

Like in windows I can force an IP address, subnet, and gateway, but when I do that through the gui, it boinks out... see attached pic of connection. Is it just not getting the correct DNS lookup? It still should be able to get out of my internal network...

---

### Post by Ocelaris on 2008-09-13
> **ansicplusplus said:**
> Hy Ocelaris
setting a static ip is really easy. Just edit /etc/network/interfaces to look like this for ip 192.168.0.54
```
  
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.0.54
netmask 255.255.255.0
gateway 192.168.0.1

```
After that restart the network using ```
sudo ifdown eth0 && sudo ifup eth0
```
Yours ansicplusplus



Hey wow that was easy! Thank you! Everything works now, I'm most appreciative, now I can get on with setting Synergy between my PC and Ubuntu box. GREAT!

---

### Post by Ocelaris on 2008-09-16
You may laugh, but I'm going to keep referring to this thread until I have it memorized!

---

### Post by Iowan on 2008-09-16
You could subscribe to this thread to keep it available (unsubscribe after you have it completely memorized).  Of course, you could also use Search to "Find All Your Threads".
Also, while exploring the forum options, look under Thread Tools to mark this one [SOLVED] (if you believe it is).

---


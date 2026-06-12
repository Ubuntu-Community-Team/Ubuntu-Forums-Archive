---
title: "Port forwarding with firestarter"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by wersdaluv on 2007-04-08
I really am not familiar with these things so please bear with me.

I need port forwarding but I do not know how to do it.

I think using firestarter is the easiest way.

How do I use firestarter for port forwarding?

---

### Post by TheWizzard on 2007-04-08
am i correct you want to use the computer as a router?
for this purpose, i don't think firestarter is the tool to use. firestarter is (i think) a tool to configure iptables for a desktop pc.

---

### Post by wersdaluv on 2007-04-08
> **TheWizzard said:**
> am i correct you want to use the computer as a router?
for this purpose, i don't think firestarter is the tool to use. firestarter is (i think) a tool to configure iptables for a desktop pc.

What I am trying to do is to be able to use bittorrent clients properly and video calling apps. I am behind a router that's why I can't use them the way I should. I think, port forwarding is the solution. Can't it be done with firestarter?

---

### Post by TheWizzard on 2007-04-09
> **wersdaluv said:**
> What I am trying to do is to be able to use bittorrent clients properly and video calling apps. I am behind a router that's why I can't use them the way I should. I think, port forwarding is the solution. Can't it be done with firestarter?

no, the port-forwarding has to be done in your router. 
you have to find the ip of your router: 

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

this means my router's ip is 192.168.1.1

open your web browser and type the ip-address in the location bar. 
now you enter the settings of your router. 
with a linksys router you have to go to 'applications & gaming' to do port-forwarding. seach the net for your brand and type. 

if you have enabled your firewall, you'll have to open some ports. this can be done with firestarter.

---

### Post by wersdaluv on 2007-04-09
This is the output...
```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 ra0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

I also have a linksys router.

I tried both 192.168.1.2, and 192.168.1.254 but Firefox can't establish a connection to the server.

Why is it that way?

---

### Post by TheWizzard on 2007-04-09
is your computer directly connected to the router? 
what does your router manual say about configuration?

---

### Post by wersdaluv on 2007-04-09
> **TheWizzard said:**
> is your computer directly connected to the router? 
what does your router manual say about configuration?

I'm sorry. I lost my router manual already.

So here is the case, I have a linksys wireless-g access point Model WAP54G. The wireless router is connected to a linksys wired router. The wired router is connected to my DSL's modem.

I remember accessing the router before in Windows XP and that was the time when I changed the default IP adress from 192.168.1.1 to 192.168.1.2. For some reason, I can't access it now. I tried it in Firefox and Opera, but both browsers can't access it. What could the reason be?

---

### Post by TheWizzard on 2007-04-09
> **wersdaluv said:**
> So here is the case, I have a linksys wireless-g access point Model WAP54G. The wireless router is connected to a linksys wired router. The wired router is connected to my DSL's modem.

I remember accessing the router before in Windows XP and that was the time when I changed the default IP adress from 192.168.1.1 to 192.168.1.2. For some reason, I can't access it now. I tried it in Firefox and Opera, but both browsers can't access it. What could the reason be?

ok, this explains a few things. 
my setup is different (just wireless router + modem) so i can only give you some directions. 
try to access the router by linking it directly to your computer using the ethernet cable. 
i'm not sure, but please check if you need to do port forwarding on the wireless access point.

---

### Post by wersdaluv on 2007-04-09
Don't you think something fishy is going on? 

I used to access my router by entering its IP address, but I can't now. What could have caused that?

---

### Post by TheWizzard on 2007-04-09
> **wersdaluv said:**
> Don't you think something fishy is going on? 

I used to access my router by entering its IP address, but I can't now. What could have caused that?

did you install the wireless access point after you last accessed your router? i think that's the problem. hard-wire your computer to the router and try to access it.

---

### Post by wersdaluv on 2007-04-09
> **TheWizzard said:**
> did you install the wireless access point after you last accessed your router? i think that's the problem. hard-wire your computer to the router and try to access it.

No. I never installed a driver.

I can't connect my computer to my router because it has no LAN ports.

---

### Post by TheWizzard on 2007-04-09
> **wersdaluv said:**
> No. I never installed a driver.

??? i wasn't talking about drivers. 


> **wersdaluv said:**
> I can't connect my computer to my router because it has no LAN ports.

how is your router connected to the wireless access point? must be a cable.

---


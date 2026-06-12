---
title: "connecting to the internet"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by mitar on 2008-05-20
I installed linux a month ago on my laptop while the school was still going on and in the dorm where I lived I only needed to plug internet cable to the wall and I would have internet connection. Everything was free and I did not need to use wireless (one of the reason is I can not get it to work, but that's not the problem now)

Now I got back home, and I can't just "plug the cable in the wall" so I need help about that. On a desktop PC we have adsl modem (I am really bad with terminology). (If you know what I am talking about) **I was wandering if I could use that to have internet on my laptop.** Do I have to set up something on laptop first or what (NOTE: I can not download anything from linux cause I'm not connected) 
Second option would be to try to install dial up connection (the one that we used several years ago with speed of 52kbps :-) ). But I don't think my laptop has modem iside  :confused: 

Can anyone help with this? I would provide any further information needed.

---

### Post by iainmackay85 on 2008-05-20
you will need to tell these kind people what adsl modem is connected to your pc, they may know of some setup on linux for it. if you are needing internet on your laptop to get it sorted you can connect a crossover lead between your laptop and pc, setting up internet sharing on your pc. or you can get a wifi modem router and connect your internet to the router then your pc to it with a cable and wireless for your laptop.

---

### Post by mitar on 2008-05-20
What should I look for? It says ADSL modem DSL-360R on it. I don't know if that helps. I can't do any of those optiones you mentioned.

---

### Post by superprash2003 on 2008-05-20
if possible go to the terminal and type ifconfig and post output here

---

### Post by mitar on 2008-05-21
> **superprash2003 said:**
> if possible go to the terminal and type ifconfig and post output here

this is what I got:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c6:ea:b1   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0xa000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:10700 (10.4 KB)  TX bytes:10700 (10.4 KB)
```

---

### Post by superprash2003 on 2008-05-21
go to system->administration->network and choose eth0 properties.. then select DHCP instead of ROaming mode.. and then try connecting to the internet.. if it doesnt work post ifconfig output again

---

### Post by mitar on 2008-05-21
hey, never mind for this. I really have no idea what I am doing with this. I can't even set up internet with windows, not to mantion Linux. I'll have to  wait until fall semester begins, when I'll be able to use internet. Thanks anyway.

---


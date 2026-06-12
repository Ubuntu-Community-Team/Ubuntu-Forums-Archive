---
title: "aMSN and video conversations"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by r11_kaede on 2008-08-30
Hi guys,

I'm having some trouble with video conversations over aMSN. My webcam works fine locally with programs like aMSN and Kopete, but when i try to initiate any video convos with my friends all they get are black screens and so do I.

I'm currently using firestarter as my firewall, and I did try uninstalling it and retrying the video convos. No joy.

I'm currently directly connected to my modem, a Motorola SB5100.

Any way I could resolve this issue? I think i will need to do port forwarding, but I'm not sure how to do it with a modem.

Thanks. :)

---

### Post by Tom--d on 2008-08-30
Forward the port the webcam uses.
Its in the aMSN settings.. (it tells you which port it use(s)) and forward them in your router. 
This should solve your problem.

---

### Post by r11_kaede on 2008-08-30
the port is 6891. But I'm not connected to the wireless router at all, so how can it possibly block me? (I'm kinda not getting it)

---

### Post by Tom--d on 2008-08-30
In Firefox (or what ever browser you use) type in.. (I think, for default) 192.168.1.1 and find applications (for mine its called that) and you need to forward the port, 6891, and make sure its your **internal** IP address

EDIT:

Ah, I just saw your on a modem.
I think it still can be done.

---

### Post by r11_kaede on 2008-08-30
hmm. okay, initially i tried 192.168.1.1, and it just said "connecting" and nothing happened.

so i tried going "sudo ifconfig" and i got "inet addr:202.156.120.87", but still no joy for that one.

am i missing anything?

---

### Post by Tom--d on 2008-08-30
mm..
Post the outcome of ifconfig (no need for sudo).
But its because your on a modem (I've never used one so its kinda new to me (But have an Idea). Also, I dont know if a modem can forward ports.

---

### Post by r11_kaede on 2008-08-30
```
eth0      Link encap:Ethernet  HWaddr 00:1f:29:98:e0:d2  
          inet addr:202.156.120.87  Bcast:202.156.123.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:29ff:fe98:e0d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7045887 (6.7 MB)  TX bytes:1042970 (1018.5 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103900 (101.4 KB)  TX bytes:103900 (101.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:00:2d:1d:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Memory:fdffc000-fe000000 
```

Yup, here is the results of ifconfig.

I'm not sure though, but if I can't forward via modem, then wouldn't imply that all others who use ubuntu via LAN won't be able to do the same? :p

---

### Post by Tom--d on 2008-08-30
No. 
As normaly they are behind a router. Your behind a modem. Too different things.

Ok, try this:
Firefox and type in:

202.156.120.87
and if that doesnt work, try this

202.156.123.255

anything?

---

### Post by r11_kaede on 2008-08-30
No joy. Both give me "Page Load Error"

I switched off Firestarter before trying both.

:(

---

### Post by r11_kaede on 2008-09-01
Hi, erm. Anyone? Please? :)

My folks at home are hounding me, so I really need to get it up and working. :(

---

### Post by r11_kaede on 2008-09-30
*bump*

---


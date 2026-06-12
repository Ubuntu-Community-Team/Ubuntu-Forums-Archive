---
title: "How to change IP address on &quot;Kernel IP routing table&quot;?"
date: 2016-07-11
forum: Networking &amp; Wireless
---

### Post by alanj2007games on 2016-07-11
Static IP address works best for me, so I did it on Windows, and the connection works well, so I'm trying to do the same thing on Ubuntu; unfortunately, I've worked for two days straight and can't get it working
It's connected but no internet access

[I][B]Here are the full correct details for my internet

[/B][/I]```
IP Address: 192.168.1.6
Subnet: 255.255.255.0
Gateway: 192.168.1.1
DNS: 8.8.8.8 8.8.4.4
```

I noticed that my "Kernel IP routing table" output differently than "ifconfig"

You can see the full image [here]("http://i.imgur.com/C194fQO.jpg")!

_**Q: So how do I make the *destination *right on the table?**_

---

### Post by chili555 on 2016-07-11
I don't see anything wrong except that you have both wireless and ethernet connected with the *same address*. I'd turn off one or the other.>  I've worked for two days straight and can't get it working
It's connected but no internet accessWhat settings are you using? Where; in Network Manager?

---

### Post by alanj2007games on 2016-07-12
Take a look at (wlan0 on the Kernel table) and (wlan0 output from ifconfig)

Those are different to each other, the kernel ones is using **192.168.1.0**
while the output of ifconfig states that it's using [B]192.168.1.6
[/B]

---

### Post by chili555 on 2016-07-12
192.168.1.0 is shown as the Destination; that is, all traffic for wlan0 and, for that matter, eth0, will go to the 192.168.1.0 network. Then, under Gateway, it correctly identifies the specific gateway address as 192.168.1.1.

There is nothing at all extraordinary or wrong in what you've shown.

Is your wireless working correctly? If so, and I suspect it is, then all is well. If it is not, please tell us what the problem is instead of the suspected symptom.

For comparison, here are the settings from my machine which operates correctly:```
chili@T440p:~$ ifconfig
<snip>
wlp3s0    Link encap:Ethernet  HWaddr xx:3d:82:7a:fe:xx
          inet addr:[COLOR="#FF0000"]192.168.0.125[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ce3d:82ff:fe7a:fe9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10951970 (10.9 MB)  TX bytes:654447 (654.4 KB)

chili@T440p:~$ route -n
Kernel IP routing table
[COLOR="#FF0000"]Destination[/COLOR]     [COLOR="#FF0000"]Gateway [/COLOR]        Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [COLOR="#FF0000"]192.168.0.1[/COLOR]     0.0.0.0         UG    600    0        0 wlp3s0
[COLOR="#FF0000"]192.168.0.0[/COLOR]     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

```

---


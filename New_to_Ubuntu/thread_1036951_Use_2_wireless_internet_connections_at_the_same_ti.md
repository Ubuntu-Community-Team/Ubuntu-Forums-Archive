---
title: "Use 2 wireless internet connections at the same time?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-11
Hi, is it possible to use more than one wireless adapter to connect to more than one network. Both of the networks have Internet connections with 512kb/s. I don't think it is possible to merge the connections and make a 1mb/s connection but if I am able to connect to more than one network at a time. I think I can use separate Internet connection for each program.

[IMG]http://img379.imageshack.us/img379/7159/screenshotoo6.png[/IMG]

For example can I use 3Com for using Firefox and Livebox-6934 for using Pidgin?

---

### Post by andresmh on 2009-01-11
Good question. I am able to connect to via my CDMA wireless modem and my WiFi network at the same time. But I have found that apps tend to prefer the WiFi more. It might be totally random though.

---

### Post by Dr Small on 2009-01-11
I don't know. I've never had two different networks that I could try this from. This would be interesting though, if it was possible. Maybe bridge the connections or something.

---

### Post by Captain_tux on 2009-01-11
This sounds like an interesting concept. I'm just trying to figure out how, even if you bridge the two connections, can you merge the separate HTTP (or whatever protocol you're using to connect wherever) connections to acquire more throughput...?

Think I'll make that my project this week...

---

### Post by looi76 on 2009-01-11
Does this mean that I'm connected to 2 wireless networks?

[IMG]http://img171.imageshack.us/img171/3767/screenshot2xb7.png[/IMG]

> **Dr Small said:**
> I don't know. I've never had two different networks that I could try this from. This would be interesting though, if it was possible. Maybe bridge the connections or something.

Great! If you open a thread about it please inform me \\:D/

---

### Post by croto on 2009-01-11
I'm not an expert in networks, but I think you may be able to do something similar to what you're describing. I think the "key" of the problem is encoded in the routing table. See for example my routing table (to see yours run /sbin/route, or wherever it is in you box):
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```
The first line is telling the kernel that whenever it has to send a packet to the network 192.168.1.0/255.255.255.0 it has to send it through wlan0, and someone in that network will pick it up. If the packet should go to 127.0.0.1/255.0.0.0, the second line says it should go through the lo interface, and someone in that network will pick it up (you). The third line is different. If the packet destination was not resolved in the previous lines, the default gateway is used. It is telling the kernel take the packet and send it to the host 192.168.1.1, it will pick it up and resend it so it gets to the real destination. 

Ok, my point is that the routing table determines how network connections will be used. In fact, in my case (and surely yours too) there are more than one network connection: "lo" is used when the destination ip is in the network 127.0.0.0, and "wlan0" is used both when the destination ip is in the network 192.168.1.0 and when the destination ip is in some other network (in such a case it will use the gateway 192.168.1.1 which should go through wlan0 anyway).

I guess you'll have to figure out some scheme to decide what destination ip should go through what interface...

Anyways, maybe there's an easier and better solution, and I would like to know it too :)

Cheers.

---

### Post by bgerlich on 2009-01-11
You can do it manually using "bonding", this will create a bonding device that uses both Internet connections, or multihoming. Do a search on (channel) bonding and multihoming in Debian, also applies to Ubuntu.

Example multihoming config of two wireless links:
[http://tetro.net/misc/multilink.html](http://tetro.net/misc/multilink.html)

---

### Post by pinged on 2009-01-11
I wonder what would happen if you connected both wireless connections to the same network?

*Goes off to try it*

---

### Post by bgerlich on 2009-01-11
Pinged, exactly the same thing as if you would connect two wired NIC's to one cable - both connections will be at maximum speed but the sum of transfer rates will never exceed it.

You can always buy a card with Turbo Mode - which is exactly what you want to achieve with the difference that instead of using another interface it simply uses more channels.

---

### Post by HermanAB on 2009-01-11
Well, you can only use bonding if you control both ends of both pipes, which you probably don't.

Using two internet network connections for increased bandwidth and reliability is not a simple matter.  You need to read the 'Advanced Routing Howto' on tldp.org.  

You can also look at this guide:
[http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

Cheers,

Herman

---

### Post by bgerlich on 2009-01-11
I am fairly certain that you don't need to control both ends of the pipe with bonding, you just need to be able to use the same IP and hw address on both interfaces, which in case of two wireless networks is highly probable. In worst case scenario you just need to control both ends of one pipe and match the settings to the one you don't control. If I'm wrong clarification would be much appreciated.

---


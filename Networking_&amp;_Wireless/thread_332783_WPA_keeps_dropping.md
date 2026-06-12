---
title: "WPA keeps dropping"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by jimmyxx on 2007-01-06
Hi,
I've recently had 16 MB sky broadband fitted in my apartment. When i connect via a wire its great, I get ~12 MB when i run this speed test: [http://sod.ms/fast/](http://sod.ms/fast/)

When i run wireless using WPA (sky forces this, doesn't let you use WEP) I connect and internet works, but its totally unusable, pages take like 3 minutes to come up. When i run the same speed test i get anything from ~0.5mbs. The network-manager-gnome icon keeps showing a connection then it drops all of a sudden and shows unconnected, then reconnects and so on.... When i download a file over the wireless it appears to build up speed then suddenly drop and start again from a low speed and build up only to drop again.

WEP works great - i connect to my neighbors unsecured wireless network (they apparently have 2mb ADSL) and when i run the speed test it achives 1.8 - 1.9 mb every time.

I'm not sure if this is a problem with the Sky WPA router (little white netgear box, no web admin available) or if its a problem with my ubuntu not dealing with WPA well.

Any feedback, comments or suggestions would be greatly appreciated.

Thanks,
Jimmy x

---

### Post by jimmyxx on 2007-01-06
**update**

I've just tried plugging my old wireless router into the SKY router so i could try connecting via WEP. It all worked fairly easily and i can get online wires or wireless (WEP) through the second wireless router.

What's totally weird is that this connection keeps dropping too... It gets a much better speed than the WPA but still disconnects every 1-2 seconds when im doing something bandwidth intensive (download or BB speed test). when connected to the wireless second router via WEP i get erratic results on the speed test (due to the d/c's) anything from 2mbs to 5mbs.

Now im really confused as the neiubours wireless WEP ADSL works fine, absolutely no d/cs and constantly archives 1.9mbs on the speed test.

urgh!    ](*,) 

Jimmy x

---

### Post by wieman01 on 2007-01-06
What card have you got? Are you using "ndiswrapper"?

---

### Post by jimmyxx on 2007-01-07
Hi wieman01,

I'm not sure if im using ndiswrapper. I'm just using a IBM Thinkpad T41. When i run ifconfig this is what comes up:

```

jimmy@jimmypad:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:23:81:C1:26  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe81:c126/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2230 errors:1 dropped:1 overruns:0 frame:0
          TX packets:1956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1368262 (1.3 MiB)  TX bytes:555862 (542.8 KiB)
          Interrupt:11 Base address:0x4000 Memory:c0200000-c0200fff 

eth1      Link encap:Ethernet  HWaddr 00:11:25:85:7F:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74837 (73.0 KiB)  TX bytes:74837 (73.0 KiB)


```

I've noticed that when running through WEP the connection doesn't drop until i start hitting higher bandwidths like DLs, p2p or intensive web pages (flash etc). dont know if that helps

Thanks,
Jimmy x

---

### Post by wieman01 on 2007-01-07
So you are facing the same issue only when you use the SKY router, is that correct? Do you have access to the router? There must be section where you can configure a multitude of wireless network settings, i.e. the physical network settings. Could you post those? Perhaps changing some of these will help... it did so in my case.

Another thing: Could it be that your router is set to wireless B only while your card supports wireless G & B?

---

### Post by jimmyxx on 2007-01-07
Hi again wieman01,

Well Sky have provided this router with absolutely no advanced options, no control panel and no admin area to configure the network. All they send to you is a the box, the cable and a little card with your wireless network name & WPA key printed on to it. I guess they don't want users fiddling with the product which they have to support?

I'm experiencing the problem with the SKY router when i access it over the wireless WPA connection. I am also getting the same problem (yet not as extreme) when i daisy chain the WEP router onto the Sky router and connect using WEP. The WEP router has worked great for me in previous networks (i used it for my NTL cable connection and never experienced this connection dropping i'm getting now, that was a slower connection speed tho, just 1mbs).

The WPA wireless connection is pretty much unusable, where as the same internet connection through the WEP router is usable until it hits the higher speeds (like > 3 mbs), the sky connection should support 16mbs and achieves 12mbs when wired). 

It's almost as if my laptop is tripping over itself when it gets to high speeds?

This is the spec of my laptop: [http://reviews.cnet.com/ThinkPad_T41/4507-3121_7-30567436.html](http://reviews.cnet.com/ThinkPad_T41/4507-3121_7-30567436.html)
This is what it says in the networking part:

> 
Networking

    * Networking / Wireless LAN Supported
    * Yes

    * Data link protocol
    * Ethernet, IEEE 802.11b, Fast Ethernet, Gigabit Ethernet

    * Remote management protocol
    * CIM, DMI 2.0

    * Networking standards
    * IEEE 802.11b


Thanks for your support,
Jimmy

---

### Post by jimmyxx on 2007-01-07
I've just tried setting my WEP router to only wireless B and not B & G, this hasn't fixed the problem! :mad:

---

### Post by wieman01 on 2007-01-07
Hi, 

It sounds more like a problem with your physical network. Not sure whether I can help you there if SKY does not let you change any settings...

---


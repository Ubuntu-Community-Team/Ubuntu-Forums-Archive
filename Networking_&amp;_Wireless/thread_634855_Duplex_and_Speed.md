---
title: "Duplex and Speed"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by prodezigner on 2007-12-08
I was wondering, I've got one onboard NIC, and I want to configure it for 10BaseT Half-Duplex as soon as Ubuntu starts (Server Ed.) so it conserves band-width.

Any ideas?

---

### Post by leonidas666 on 2007-12-08
> **prodezigner said:**
> I was wondering, I've got one onboard NIC, and I want to configure it for 10BaseT Half-Duplex as soon as Ubuntu starts (Server Ed.) so it conserves band-width.
I think you can do something like that with ifconfig. Type
```
man ifconfig
```
in the console to get the help with all the options.
However, your idea sounds very strange. If you write something about why you want to do this, maybe somebody can give you a better solution for your problem.

---

### Post by netztier on 2007-12-08
> **prodezigner said:**
> I was wondering, I've got one onboard NIC, and I want to configure it for 10BaseT Half-Duplex as soon as Ubuntu starts (Server Ed.) so it conserves band-width.


This only makes sense if the speed of your internet access is faster than 10Mbit and if you have pricing per data volume or per CIR (Committed Information Rate) while the CAR (Committed Access Rate) is higher than 10Mbit. Is that the case?

You could use **ethtool** or **mii-tool** in a short shell script, depending on which one works with your NIC.  Make the script executable and place it in the directory **/etc/network/if-pre-up.d/**, so it gets executed each time befor the interface is brought it's settings from /etc/network/interfaces.

best regards

Marc

---

### Post by prodezigner on 2007-12-08
Well, I'm going to install another NIC card set to 100Mbs Full-Duplex... I want the torrent client on my Linux box setup for 10Mbs Half-Duplex so that when the other computers on my network are gaming it has no slow-down. I figured this would be the best way to do it.

---

### Post by prodezigner on 2007-12-09
Just bumping this up, and verifying if the statement I posted above is true or not, if running NIC1 on 10BaseT Half-Duplex for downloading Torrents would be good and then 100BaseT Full-Duplex for networking internals would be good?

---

### Post by Lostincyberspace on 2007-12-09
Just set a speed limiter in the torrent program, 90% have them. If your doesn't try deluge you can control individual torrents with it to.

---

### Post by prodezigner on 2007-12-09
I'm not using a GUI, I'm using CLI. Right now I'm using rTorrent, but even if I throttle it it slows down others on a 6Mbs cable connection.

---

### Post by netztier on 2007-12-10
> **prodezigner said:**
> I'm not using a GUI, I'm using CLI. Right now I'm using rTorrent, but even if I throttle it it slows down others on a 6Mbs cable connection.

Well if that connection is 6mbps, there is absolutely no point in using 10Mbit/s Half Duplex for that - even with a 10Mbit/s card, you're going to saturate a 6Mbps Internet access line with ease.

Besides, you're going to have some decent configuration trouble if you want to use one NIC for some things and the other NIC for the rest. "Difficult" is an understatement for this task.

The other poster is right: do throttling with the application itself, but don't forget to **throttle upstream** bandwith as well! 

Having a saturated uplink kills all your download speeds, if you don't apply Qualitiy-of-Service rules on the broadband router that manages the congestion on the upstream bandwith. See the graphs on this page (yeah, german, allright, but just look at the graphs):

[http://www.avm.de/de/Produkte/FRITZBox/FRITZ_Box_Fon_WLAN_7270/traffic_shaping.html](http://www.avm.de/de/Produkte/FRITZBox/FRITZ_Box_Fon_WLAN_7270/traffic_shaping.html)

So if you make sure that the uplink doesn't get saturated, the buddies sharing your bandwith won't have any trouble keeping their download rates up.

regards

Marc

---

### Post by prodezigner on 2007-12-11
I don't have QoS enabled on my Linksys WRT54GS router... I don't know what the best settings would be for all this, it's all new to me.

Any idea?

I was wrong too about speed.

We have 5Mbs Down and 256Kbs Up

---

### Post by netztier on 2007-12-11
> **prodezigner said:**
> I don't have QoS enabled on my Linksys WRT54GS router... I don't know what the best settings would be for all this, it's all new to me.

We have 5Mbs Down and 256Kbs Up

Ok, then as first approach, try to do software throttling with the torrent client and make sure that you don't use more than ~200kbps upstream. Like this, the upstream bandwith won't be congested and all the small "ACK" packets (that must go upstream while downloading) still have a fair chance to make it to the servers your buddies are downloading from.

Second approach - from what I've heard, WRTs have pretty good QoS features. Is there some "basic" setting you can activate? Maybe there is one like on professional Cisco routers that's called "fair queuing". It recognizes ACKs or connections that rely on small packets needing expedite forwarding and can adjust their order of preference - this can make a telnet or SSH session work again across a link that is completely stuffed with FTP downloads.

You could of course go ahead and configure specific QoS for bittorrent and the likes, but this can become complex - what with identifying (ever changing) port numbers etc. on the other hand - there should be plenty of Web ressources about how to configure QoS on WRTs.


regards

Marc

---

### Post by mellowd on 2007-12-11
Just make sure QoS actualyl works correctly. I've got a netscreen configured with QoS for torrent traffic giving it lowest priority but it doesn't make a huge difference.

And having 2 seperate nic's isn't going to make any difference at all because it'll all connect to your single internet pipe.

I generally leave my downloads going but when I play online I'll just pause them. I never have time to play more than an hour online so it doesn't really matter to me.

---


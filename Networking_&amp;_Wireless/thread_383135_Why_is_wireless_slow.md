---
title: "Why is wireless slow?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Crashmaxx on 2007-03-12
I got my desktop up and running again, but this time with edgy (finally!). But for some reason my wireless is really slow. Its not my network, as the laptop next to it with intel wireless is blazingly fast. And I don't think it is the 'card' cause I don't remember dapper being noticeably slow.  And its not ipv6 or anything as I am using swiftfox which disables that.

Its a linksys WMP54G v4 card that is based on the RT2500 chipset, on a P4 edgy system. So what could be wrong? The drivers? How would I update them? Thanks.

---

### Post by gradedcheese on 2007-03-12
I am not sure, but if you do want to update your driver (by building a new one from source) try:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

You will need a compiler and kernel headers:

```

sudo apt-get install build-essential kernel-headers-`uname -r`

```

Generally speaking, you uncompress the driver source, cd to its directory, 'make', and 'sudo make install'.  After that, reload the driver (bring down the interface and then 'rmmod rt2500' and 'modprobe rt2500' should do it).  Now bring the interface back up and try it out.  However read whatever instructions they provide.

---

### Post by siciliancasanova on 2007-03-13
If you used fwcutter to get your wireless working it will be slow.

---

### Post by Crashmaxx on 2007-03-13
Alright, I'm downloading the source for the beta driver right now. Maybe that will fix it.

But I still think it is strange. It worked right out of the box. I didn't need to use ndiswrapper fwcutter or anything to get it to work. Nor did I do anything for it in dapper. So it just seems strange that something built in like that would preform like this when it didn't prior.

I'll let you know if the new drivers helps.

---

### Post by Crashmaxx on 2007-03-13
Nope, the driver wasn't it. The newest beta freshly compiled and added didn't help noticeably.

I got some sort of bottleneck, and its only on this machine. All the others test at around 5000Kb/s and this one only gets 200Kb/s. And I'm not sure its even that good, it seems to have a lot of freezes and stuff like the repositories only get 15Kb/s or worse.

Something is just wrong here...

---

### Post by gradedcheese on 2007-03-13
Hmm, I wish i could help but I don't have this chipset here.  Perhaps, if you have time, you should go to the rt2x00 site and fill out a bug report, giving them a rundown on what's going on and which version you built.  If a report exists, see what they said about it.  Maybe it's a real driver bug and it can be resolved.

---

### Post by Mr. C. on 2007-03-14
> **Crashmaxx said:**
> And its not ipv6 or anything as I am using swiftfox which disables that.

Swiftfox does not disable IPv6 globally.  See and try this:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by Crashmaxx on 2007-03-14
Thanks for reminding me of that. I tried that and it made a big difference. I guess ipv6 was a lot more of the problem then I thought.

Any other ideas? That seemed to help browsing especially, but the speeds are still about 200Kb/s and I am dropping about 10%-20% of packets. Its still not working as it should be.

---

### Post by Mr. C. on 2007-03-14
Great, sounds like things are looking better.

Losing 10-20% of the packets is terrible for Ethernet.  1-2% can cause significant problems.

Where are you seeing the loss, and how have you taken the measurements?

MrC

---

### Post by Crashmaxx on 2007-03-15
Well, just pinging my router. I do a ping 192.168.2.1 and let if run for a while. After disabling ipv6, the pings went down to more like 1-5ms, but I'm still losing around 10-20% of packets. Which is really bad for the closest thing I can ping. None of the other machines drop any packets, and have similar latency.

---

### Post by Mr. C. on 2007-03-15
If the other systems are not losing packets, and they are connected to the same gear, then one can assume it is your NIC, NIC's drver, or cable on the ubuntu station.  You should be able to ping your router all day and have essentially no loss.

Try replacing the cable (or swapping with a known good system) and retesting.

If this shows no improvement, update the NIC's driver if an update is available, update its firmware (if any), and if all that shows no improvement, replace the NIC.

Post output from below if you are able:

```
ifconfig -a
netstat -s
sudo ethtool -S eth0  # replace eth0 with your device
sudo ethtool -i eth0   # replace eth0 with your device

```

MrC

---

### Post by Crashmaxx on 2007-03-15
In case it wasn't already blatant enough, this is a wireless, so there is no cable to plug.

And in case you didn't see, I have already compiled the latest beta driver.

And with dapper my speeds were fine, though that was a while ago.

So here is the output you wanted:
```

crash@crashbox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:8D:C2:C4:B1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0F:66:6E:7E:9F  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10260 errors:110 dropped:110 overruns:0 carrier:0
          collisions:2275 txqueuelen:1000 
          RX bytes:11226516 (10.7 MiB)  TX bytes:1507986 (1.4 MiB)
          Interrupt:169 Base address:0x8000 

crash@crashbox:~$ netstat -s
Ip:
    9962 total packets received
    2 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    9893 incoming packets delivered
    9238 requests sent out
Icmp:
    0 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
    0 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
Tcp:
    376 active connections openings
    0 passive connection openings
    0 failed connection attempts
    5 connection resets received
    13 connections established
    9681 segments received
    9113 segments send out
    111 segments retransmited
    0 bad segments received.
    49 resets sent
Udp:
    123 packets received
    0 packets to unknown port received.
    0 packet receive errors
    125 packets sent
TcpExt:
    159 TCP sockets finished time wait in fast timer
    1 packets rejects in established connections because of timestamp
    560 delayed acks sent
    Quick ack mode was activated 13 times
    2 packets directly queued to recvmsg prequeue.
    5382 packet headers predicted
    889 acknowledgments not containing data received
    665 predicted acknowledgments
    71 congestion windows recovered after partial ack
    0 TCP data loss events
    1 timeouts after SACK recovery
    100 other TCP timeouts
    8 DSACKs sent for old packets
    24 DSACKs received
    3 connections reset due to unexpected data
    2 connections reset due to early user close
crash@crashbox:~$ sudo ethtool -S ra0
no stats available
crash@crashbox:~$ sudo ethtool -i ra0
driver: RT2500STA
version: 1.1.0 BETA4
firmware-version: 
bus-info: 0000:02:00.0

```

And my /etc/network/interfaces while I'm at it:
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid ramit
wireless-key s:

```

---

### Post by Mr. C. on 2007-03-15
> **Crashmaxx said:**
> In case it wasn't already blatant enough, this is a wireless, so there is no cable to plug.

And in case you didn't see, I have already compiled the latest beta driver.

It was.  I missed it.  I answer a lot of posts, and they are start melding together.

I don't go back and re-read each and every post I reply to.  I'm sure you understand.

> **Crashmaxx said:**
> 
And with dapper my speeds were fine, though that was a while ago.
Ok.  Wireless troubles come and go; hard to know what the problem is without seeing data.   Your wireless AP have any stats or logging of value ?

MrC

---

### Post by chili555 on 2007-03-15
Is your router on the default channel 6 like 80% of the other routers in the neighborhood, most of the cordless phones, some of the microwaves? Mine is very fast on channel 11.

---

### Post by Austin_KW on 2007-03-15
Silly question, maybe I missed it but what is your bitrate
iwconfig ra0 ?

You sure you ain't dropped down to/below 802.11b

iwlist ra0 rate ?

---

### Post by Crashmaxx on 2007-03-17
Well, it gets even stranger. I was starting to think the card itself was dying. I even tried a different PCI slot to see if that one was bad. No change.

So I got a Edgy and a Dapper live CD and tried them both. The Edgy one worked out of the box, had the beta driver installed, ipv6 enabled, and got 1500Kb/s and no loss packets on a ping to the router. Dapper was the exact same. So there is something wrong with my setup that is killing my bandwidth, and dropping packets. but the 1500Kb/s still isn't the 6000Kb/s I can get with my laptop.

So is there anyway to activate the process that happens in installation to auto detect network settings? Cause when I did it for this install, my MAC address wasn't in my router so it was blocked initially. So I'd like to reconfigure it properly to have a good baseline.

Anyway, next thing I found out, was that the RT2500 chip set is the only one that the FSF officially supports. Realtek is one of the few with true open source drivers. And my exact card is one of the ones they recommend buying and say will work best for linux. So me having any trouble with it seems very old.

And I have a new problem. I installed winbindd and the proper samba bits to get netbios to work. I even added it to the nsswitch file and it is all setup identical to my laptop. But it won't resolve any of my hosts except one. And that one is my server, but it doesn't resolve to my server, it instead gives its own ip address. Not local host either, but the internal address of itself. Totally bizarre.

Any clue what is wrong, or where I should look?

---


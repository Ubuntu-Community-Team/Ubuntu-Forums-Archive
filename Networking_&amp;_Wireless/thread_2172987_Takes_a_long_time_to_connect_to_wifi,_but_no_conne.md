---
title: "Takes a long time to connect to wifi, but no connection if I actually connect."
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by ty4 on 2013-09-07
EDIT: The title of the thread may be misleading, as I tend to update the original post as I figure stuff out, hoping it helps with the problem.

Hey everyone!  I'm new here but I'm sort of familiar with Ubuntu.  I built a computer a few months ago, and it ran Windows 7 just fine, but I formatted and did a nice fresh install of Ubuntu 13.04 because I missed good ol' Linux, and since Steam has a Linux port now.  :)  I can only connect if I set up the network with a static IP.  If I were to go to Chrome and put in my gateway then, I can't even get to my router settings, I'll just get a connection error.  The only way I can connect to the internet is if I use a WiFi hotspot application called Connectify on my laptop, which is in the same room as me, but my brother uses it a lot as I have this desktop so I can't use it often.  So it can't be a distance issue.  I've tried countless options toward fixing it but nothing works.  I've tried upgrading the kernel, the dhclient command doesn't do anything as it just sits there.  I don't know how anyone could help, I tried pinging google but this happened...

```
ty@ty-desk:~$ ping -c 5 google.com
ping: unknown host google.com
```

If anyone can give me a command or two to help diagnose the problem, let me know!  :)

---

### Post by Bucky Ball on 2013-09-07
Welcome.

Perhaps give us the output of these two commands:
```

sudo lshw -C network
iwconfig
```

Where are you setting the static IP address (should be on local machine, not router) and can you ping the router (you need to know the router IP, of course)? 

Does your bro have his machine there on the same LAN?

Can you ping that machine if on the same LAN (forgetting about WAN for now)? 

Thanks.

PS: Just a thought on the static IP. Is your router set up as a DHCP server to serve IP addresses to devices on the LAN? There can be mixups there if you are also setting a static IP on the local machine which is in the range the router is serving IPs. 

Say if you set a static IP of 192.168.0.101 on the local machine and the router's DHCP server is configured to serve between 192.168.0.100-200 there can be a clash. The router is trying to serve you an IP and you are trying to force one at the router. Clang!

---

### Post by ty4 on 2013-09-07
Yes, I have a DHCP server, going from 192.168.1.2-254.  But as I said, it just times out when I go for DHCP.  It'll try connecting for a while, then it disconnects.

Alrighty, here's the output of the first command.  Also, it's a desktop with a TP-Link PCI WiFi card.  If that helps, I have no way of getting Ethernet to my router.

```
  *-network                      description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:6f:98:7f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbf8000-fdbfbfff
  *-network
       description: Wireless interface
       product: AR9227 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 01
       serial: f8:d1:11:38:3f:97
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.9.0-030900-generic firmware=N/A ip=192.168.1.164 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fddf0000-fddfffff

```

Here's the second. I replaced my Access point name with XXXXXXXX, since I wanna leave that classified. :P

```

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"XXXXXXXX"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:23:4D:54:5A:46   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:144   Missed beacon:0

```

When I ping my router.

```

ty@ty-desk:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.164 icmp_seq=1 Destination Host Unreachable
From 192.168.1.164 icmp_seq=2 Destination Host Unreachable
From 192.168.1.164 icmp_seq=3 Destination Host Unreachable
From 192.168.1.164 icmp_seq=4 Destination Host Unreachable
From 192.168.1.164 icmp_seq=5 Destination Host Unreachable


--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4013ms
pipe 3

```




And I get the same thing when I ping to our laptop.
```

ty@ty-desk:~$ ping -c 5 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.164 icmp_seq=1 Destination Host Unreachable
From 192.168.1.164 icmp_seq=2 Destination Host Unreachable
From 192.168.1.164 icmp_seq=3 Destination Host Unreachable
From 192.168.1.164 icmp_seq=4 Destination Host Unreachable
From 192.168.1.164 icmp_seq=5 Destination Host Unreachable


--- 192.168.1.3 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4016ms
pipe 3

```

---

### Post by Bucky Ball on 2013-09-07
Hmm. Strange. Looks like there is no problem with the card. That has a driver and is up and seeing the router/AP no probs. 

The TP-Link appears to be using the Atheros chipset. 

My iwconfig says 'RTS thr=2347 B' whereas yours says 'RTS thr=off'. Only diff I can see. 

Is your brother using a static IP or getting one served from the router? Might be an idea to do a comparison with his wireless configuration, regardless of OS, just to see if there's anything obvious. Nothing is jumping out at me but I'll keep thinking. :-k

PS: You might try using madwifi but not sure that will fix this. As I mentioned before, if you are setting a static IP in the range the router is trying to serve you one you will get issues (sometimes connect, sometimes not, never connects ... it varies).

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by ty4 on 2013-09-07
It currently isn't.  I would also like to mention that the only time it actually worked was when I was on Live Mode for the first time before I installed it, but it was VERY slow.  If I were to open Live mode now, it would not work.  I'm taking a look at both connections right now but I'm going to try the oldest kernel that's installed.  Linux sites say that my specific card works right out of the box since kernel 2.xx I believe.

---

### Post by Bucky Ball on 2013-09-07
Exactly. The card *_is_* working out of the box. As I say, nothing wrong with the card as far as the output reads; it is recoginised and up and seeing your AP no problem. Has drivers and all is good from the output you provided. You're just not getting on the LAN or through the router to the WAN. In fact, your not even getting to the router, even though your machine can see the network and connect to it no problem. 

The problem lies elsewhere which is why I was asking about where the IPs are coming from. Is your bro's machine also static or getting served from the router?

---

### Post by ty4 on 2013-09-07
I got it fixed!  I honestly don't know what did it, specifically, but I set my computer up with a static IP that wasn't already being used according to my router, so I used 192.168.1.4, set the DNS to 4.2.2.2,4.2.2.1 and I always left the domain name blank, but I just typed google.com in there since I found out that my iphone has apple.com as the search domain.  And it connected like it always does, but this time I was able to get into my router settings.  It was most likely a clash in the network.  Thank you so much for your help!  :)

---

### Post by Bucky Ball on 2013-09-07
> **ty4 said:**
> I got it fixed!  I honestly don't know what did it, specifically, but I set my computer up with a static IP that wasn't already being used according to my router, so I used 192.168.1.4, set the DNS to 4.2.2.2,4.2.2.1 and I always left the domain name blank, but I just typed google.com in there since I found out that my iphone has apple.com as the search domain.  And it connected like it always does, but this time I was able to get into my router settings.  It was most likely a clash in the network.  Thank you so much for your help!  :)

This is exactly what I have been saying! You were setting a static IP in the range the router was trying to serve. ;)

Good luck and enjoy.

Just a note. I have all devices set with static IPs outside the range I have the router set to serve. The router serves between 192.168.0.100-110. 

That way, when a guest is around they are served and IP between 192.168.0.100-110 just fine while all my machines can keep their statics without issue always.

---

### Post by ty4 on 2013-09-07
Um, about that, I got a little excited, because it worked for only 10 minutes or so.  :mad:
I'll try just that though!  I might downgrade to the LTS version of Ubuntu 12.04 if that doesn't work, or go back to Windows 7 if all hope is lost.  I really do appreciate the help though!

---

### Post by Bucky Ball on 2013-09-07
What broke it? Any clues? Anything happen or you changed anything? Not sure a reinstall to 12.04 is going to make much difference as, as I say, your output is showing your card is up and running.

---

### Post by ty4 on 2013-09-07
I have no idea.  It just cut off out of nowhere.  But after that, I couldn't even connect to the hotspot.  I tried power cycling but that didn't work.  I performed a factory reset on my router to start on a clean slate so now I'm right back at the beginning of my problem to change settings one at a time, but I noticed something else when I was googling the issue some more, someone was able to only get internet on their Netgear guest network, but not their actual network.  So I went into my netgear router settings, and made a guest network with the same privileges as everything else, and it worked, oddly enough.

---


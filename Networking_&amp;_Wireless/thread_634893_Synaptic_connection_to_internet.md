---
title: "Synaptic connection to internet"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by max05643 on 2007-12-08
I use to work with Ubuntu 7.04. To upgrade the system I formated the HD and I've installed 7.10. The internet connection did not work. I follow some instructions that I find in internet

In the firefox address/URL space type "about:config" , scroll down to network.dns.disableIPV6 = false ,double click this line to change it to true. In the above do NOT type in any quotes. 

Open a terminal and enter: 
sudo gedit /etc/modprobe.d/aliases 

Look for the line that reads: 
alias net-pf-10 ipv6 

Change it to: 
alias net-pf-10 off #ipv6 

Save and reboot your PC. 

Now Firefox works but Synaptic can not connect to internet or any server. Can someone help me????

Thanks a lot,
Max

---

### Post by jonomayo on 2007-12-08
I have the same problem.
someone please help!

---

### Post by jonomayo on 2007-12-09
Bump

---

### Post by jarvoll on 2007-12-13
This is *exactly* me, too.  I'm sure I speak for all three of us when I say: we'd really appreciate any advice anyone might offer. :)

---

### Post by jarvoll on 2007-12-13
Here's an ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1B:FC:3E:DA:8E  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5047397 (4.8 MB)  TX bytes:536390 (523.8 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48800 (47.6 KB)  TX bytes:48800 (47.6 KB)

```
If there's anything else I can post to help diagnose the problem, please let me know :)

---

### Post by jonomayo on 2007-12-14
Please someone help or ill have to go back to windows :(

---

### Post by erfahren on 2007-12-14
I originally had no idea what ipv6 did but your pleas caught my attention so I went and looked for a little info on it.

I found the thread here that is pretty informative (post #13 especially): [http://ubuntuforums.org/showthread.php?t=87798&page=2](http://ubuntuforums.org/showthread.php?t=87798&page=2)

my question is this: is it completely necessary for you to disable ipv6 systemwide? can you just try disabling it Firefox and see if that helps?

Along with that you might try changing your DNS address in /etc/dhcp3/dhclient.conf to the OpenDNS addresses to try to get faster lookup. see: [http://ubuntuforums.org/showthread.php?t=511486](http://ubuntuforums.org/showthread.php?t=511486)
[http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml](http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml)

can't say I know alot about this, just thought I'd try to help.

My question: it's my understanding from what I read that it's necessary to disable ipv6 if your router or ISP doesn't support it. Is it your router that doesn't support it?

---

### Post by max05643 on 2007-12-15
I must admit that I am quite new using Linux and honestly I have no idea about Ipv6. My problem is more simple (I think). I installed Ubuntu 7.10 for the first time in a computer  (not upgrading the system but installing it for the first time). And I did not get internet connection. The computer and the router configuration use to work perfectly with Ubuntu 7.04 (so it works). Then I went to some forum in internet to what was possible to do. I followed the instructions but honestly without knowing what I was doing. 

Can someone forward me to an Ubuntu first time configuration or first time internet connection.

Thanks a lot,
Max

---

### Post by jonomayo on 2007-12-21
Try changing your DNS server to OpenDNS.

Worked for me.

---

### Post by max05643 on 2008-01-06
No way.

For me the only solution has been to reinstall 7.04 and then do the upgrade. It is not a clean solution but it works.

Thanks everyone,
Max

---


---
title: "Upgraded to very fast fibre optic but now finding internet not working very well"
date: 2016-06-17
forum: Networking &amp; Wireless
---

### Post by Fsirett on 2016-06-17
First of all, I had better give a little background. The title looks to me to be a little anaemic.

We recently upgraded to rather quick fibre optic service (300m) which seems to be working well enough via wifi on my wife's Windows laptop, but my wired system is acting very oddly indeed. Pages tell me they are not available, styling does not render downloads decide not to start, etc. I thought it might have been insufficient RAM, so I added 16gb of new ram ( now 24gb) and that did not help at all, (but non internet functions seem to feel their prime!.)  

I have focused on this answer: [http://ubuntuforums.org/newthread.php?do=newthread&f=336 ]("http://ubuntuforums.org/newthread.php?do=newthread&f=336") I shall be trying to follow the diagnostics listed there in order to give all the material needed, but much of it is something of a mystery to me. However, my wife's smart phone is something of a mystery to me as well - when faced with a phone that does nearly everything but call people easily, I can easily see the Luddite point of view!

I digress. 

First of all, under the old ADSL service (10mb) service, using Ubuntu 15.10, things worked quite well doing all of the same loads. After it was changed over to the faster service I upgraded to Ubuntu 16.04. This was a case of replacing the old system and my /home  folder was on another disk. That was something of a disaster, having the internet almost stop working. I reformatted and installed and the performance improved substantially, but it is still not as good as it was before. Using a /home folder that has been in use for four(?) years makes me think there may be some configuration problems there, but I am not certain.

I also note that the file I am referring to is suggesting that there may be driver problems, but I am quite at sea with that as well.

On to the facts.

[COLOR=#000000][FONT=&amp]ifconfig:

[/FONT][/COLOR] ```

enp1s0    Link encap:Ethernet  HWaddr 40:8d:5c:7d:c4:1e            inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::267b:11e5:597a:499/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14385979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14653215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16825809066 (16.8 GB)  TX bytes:2689383657 (2.6 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:508871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:65287012 (65.2 MB)  TX bytes:65287012 (65.2 MB)



```

I have read this and can confidently say I fel a complete idiot.

Reading on I see they asked the writer to ping the internet. That sounds like that might be helpful!

ping  -c3  8.8.8.8

```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=12.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=12.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=12.6 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 12.370/12.581/12.724/0.152 ms



```

I want to note, when I was trying this earlier, it lost one of those packets but, of course, whenever you go to the doctor, all of the problems seem to disappear in the waiting room. 

I see there is a request for the lspci report, so I will include that as well:

lspci:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Complex00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Root Port
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 30h-3fh) Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)



```

The motherboard and the microprocessor are quite new, and this is all pretty much as they came.

The rest of the post I am referring to begins to ask about things I think are already mentioned, so I am assuming I do not need to add them in at the moment. I do not want to confuse...no, really!...I am confused since little of this makes real sense to me. If this is a problem with the Realtek software, I have no idea where to find it or how to install it, let alone how to now if it needs changing. 

Is it true you guys are CSIs (Computer Scene/Silliness Investigators)?

Cheers

Frank Sirett

---

### Post by jeremy31 on 2016-06-17
See the wireless script link in my signature and post results

I don't know where > Computer Scene/Silliness Investigators came from but some of the best internet trouble shooters are posting here

---

### Post by Fsirett on 2016-06-17
That (the depth and breadth of expertise) is why I come here! The "Silliness" comes from people like me. I suspect the investigator comes, again, from people like me who have the extraordinary ability to make the clearest problem into a Gordian knot of words and impressions that take a true genius to understand. No matter how much I learn from these forums, I never seem to be able to dig very much farther into the Operating system mindset.(?) Honestly, I have no idea how you chaps have the patience to put up with us and what (I suspect) is the repeat of the same mundane problem that we cannot analyse sufficiently to realise it is being answered multiple times (a week?)  

The name was actually meant as a joke and a compliment, but, as with so much I do, may not have been well thought through.

Frank Sirett

---

### Post by Fsirett on 2016-06-18
Having read through my post again, I realise my following the thread [http://ubuntuforums.org/newthread.php?do=newthread&f=336](http://ubuntuforums.org/newthread.php?do=newthread&f=336) does not exactly explain the what and why I am different to the original. The fifth post mentions that the ethernet connection is not listed and I posted at that point because I DO show an ethernet connection. this makes me think I have a configuration problem and I am in a much better position, having done something rather stupid, or overlooked something simple, instead of having a major problem. My real problem is that I am ignorant of the ways and means.

However, if I skip on ahead I see there was a request to see if the "bridge and localhost are good." that seems like something that you might want to know so:

```
ping -c3 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=12.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=12.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=12.7 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 12.709/12.769/12.864/0.146 ms

```

This looks (to me!) very similar to the other problem result, although I think my results are much slower. My speed tests are showing a solid 300mb each up and down, with more likely 320mb. No idea if that has any relevance, but, as stated earlier, I have no idea.

Then there was a request to check if a route is established. I used the previous command "[COLOR=#000000]ls /sys/class/net" to get the right source for my system and applied the command 

[/COLOR]```
$ ip addr show enp1s02: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 40:8d:5c:7d:c4:1e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.33/24 brd 192.168.1.255 scope global dynamic enp1s0
       valid_lft 33932sec preferred_lft 33932sec
    inet6 fe80::15cc:9164:32c9:264e/64 scope link 
       valid_lft forever preferred_lft forever

```

When I put in the IP route list, I had this:
```
$ ip route listdefault via 192.168.1.1 dev enp1s0  proto static  metric 100 
169.254.0.0/16 dev enp1s0  scope link  metric 1000 
192.168.1.0/24 dev enp1s0  proto kernel  scope link  src 192.168.1.33  metric 100 

```

Here I notice that I have 192.168.1.1 as opposed to 192.168.0.1. Could that be a possible problem?

In any case I went on todo the three ping tests. In the first, I substituted 192.168.1.1 instead of the original. I hope this is correct. In any case this was the result:

```
$ ping -c3 192.168.1.1PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.443 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.321 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.271 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.271/0.345/0.443/0.072 ms

``` 

I then used the ping 8.8.8.8:

```
ping -c3 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=12.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=12.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=12.6 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 12.658/12.705/12.756/0.136 ms

```

That all looks much like the other problem to me.

last of all I pinged Ubuntu:

```
$ ping -c3 ubuntu.comping: unknown host ubuntu.com

```


this seems the same as the other thread and possibly I can now see where we share a problem (or not!) No real idea what the significance of this is.

At this point the two threads are tracking in parallel. 

Hopefully I have now put things clearly enough to help those who follow in my footsteps (keysteps? keystrokes?)

Cheers again, 

Frank Sirett

---

### Post by praseodym on 2016-06-18
Try changing the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.042.00-1_all.deb
sudo dpkg -i r8168-dkms_8.042.00-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-r8169.conf 
```
Reboot.

---

### Post by Fsirett on 2016-06-18
I have done all of that and, I have to say, the internet connection has come up so much faster than it has for years that I am truly astonished! 

I shall monitor this for a few days to see if this is a permanent fix, but before I let you go ( with my heartfelt thanks!) may I ask if I can use these commands when I think there is a driver problem or does it have "side effects?" I did notice the "sanity check" line and it immediately became my friend. Nothing I need more! I have an Ubuntu based HTPC as well that I think might like this treatment as well, if it is safe. 

All I can say, aside from thanks, seems to be WOW! Everything seems to work much better right now!

Cheers again!

Frank Sirett

---

### Post by praseodym on 2016-06-18
Hi,
glad it worked. DKMS should build the driver on every kernel upgrade. If not, just run

```
sudo dkms autoinstall
```

---

### Post by Fsirett on 2016-06-21
Let me apologise for a very late reply. The world decided to open and swallow me; at least there was so much work that came in and demanded instant attention that I was swamped. 

In any case, Things have much improved and now the (much rarer) events are coming from only a few servers. However, I also have a rather large backup of downloads that suddenly have decided they will be coming down ASAP and I know that does wonders to one's bandwidth. I expect by the end of the day I will have down everything down and left bewildered as to why I would consider most of it worth the trouble. However the internet connection should be back to normal then.

I am keeping this code to update my drivers very close indeed. Other niggling irritations have miraculously disappeared. I now give a heartfelt recommendation.

I do thank you all for your help, it is much appreciated, as always. i stand in awe at your expertise.

Cheers

Frank Sirett

---


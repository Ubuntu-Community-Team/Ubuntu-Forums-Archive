---
title: "Downloads / network connections slow!"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Zoo2 on 2007-03-05
Hi all,

I am having a problem with my ethernet connection. :shock:

Large downloads are slow, but what is strange is that very often the first 60-80% downloads fast, and then the speed drops off almost completely, with the usual end result being a time-out. This is the case both for "normal" downloads (i.e., from websites) and also when I use apt-get or Synaptic for anything. The internet is also slow sometimes, but this I can live with and I'm not sure if the two issues are connected. I'm not a complete newbie to Linux, but this is my "first cup" of Ubuntu.

Seems I am not the only one with this problem, but I still haven't found a solution that works for me... Here's a thread from a few weeks ago which seemed to show the same problem as mine, but without anything tangible to help me.

[http://ubuntuforums.org/showthread.php?t=348435]("http://ubuntuforums.org/showthread.php?t=348435")

I am in university accomodation too and so am plugged straight into the wall running a 100Mbps connection. The embarrassing thing is Windows XP worked very well (fast downloads) until I upgraded to sp2, at which point I figured a change of OS might be in order (heehee). =D> 

Here are a few details and outputs I've picked up from other threads that might help:

'ifconfig -a -v' gives me:
> eth0      Link encap:Ethernet  HWaddr 00:0D:56:38:A4:BB  
          inet addr:10.10.34.90  Bcast:10.10.34.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:a4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14312735 (13.6 MiB)  TX bytes:2177756 (2.0 MiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:702 (702.0 b)  TX bytes:702 (702.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

'dmesg |grep eth' gives me:
> [17179595.848000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:38:a4:bb
[17179598.940000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179598.940000] b44: eth0: Flow control is off for TX and off for RX.
[17179620.272000] eth0: no IPv6 routers present

'ifconfig eth0' gives me:
> eth0      Link encap:Ethernet  HWaddr 00:0D:56:38:A4:BB  
          inet addr:10.10.34.90  Bcast:10.10.34.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:a4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14314526 (13.6 MiB)  TX bytes:2177756 (2.0 MiB)
          Interrupt:177

'cat /etc/network/interfaces' gives me:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I have also disabled IPV6, but from what I have read this shouldn't be affecting downloads anyway, only browsing, and there I am not really having any problems.

Hope someone can help, promise to pass it on if I find a cure... :biggrin:

---

### Post by RomeReactor on 2007-03-05
Hi. From your interfaces file, i suggest you comment out (add a **#** at the beggining of the line) the interfaces you're not using, so the file looks like this:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

So, in a terminal enter

```
gksudo gedit /etc/network/interfaces
```

and edit it so. Save the file, close it and reboot; see if that makes a difference.

---

### Post by Mr. C. on 2007-03-05
Welcome!

I see nothing wrong with any of the data you presented (and very nicely I might add).

These can be difficult problems to analyze and uncover.

First, I do not believe disabling other interfaces will matter, but stranger things have been found.

Certainly large downloads will be are more likely to be problematic than short ones, simply due to being exposed to the woes of the net for a longer period of time.  Second, there can be bandwidth throttling for large downloads.  Third, there can be QoS type prioritization occurring.  Fourth, the likelihood of route changes increases with the connection duration.

Have you run any long term traceroutes to see how connectivity to the destination sites behaves?

Do you have any other systems on the LAN you can use to test large downloads - to and from your system?

What type of download traffic is experiencing problems?

Let's get some answers to the above, and see what comes next.
MrC

---

### Post by Zoo2 on 2007-03-06
Morning!

Thanks for the suggestions, will get down to trying them out one by one as soon as I have some time this afternoon (and have figured out exactly what they mean...). :-k

---

### Post by Zoo2 on 2007-03-06
Thanks again for the replies: haven't had much time to go through the suggestions MrC, but will hopefully do just that in the next few days.

RomeReactor: I disabled the other interfaces, as you suggested, but it made no difference. I'm beginning to suspect that bandwidth throttling might be a problem (I mentioned I was in university accomodation), but before I can answer any of those other questions about QoS and traceroutes (seemed normal to me before...) I need to do some reading.

btw, firefox is actually quite slow today, too, and in terms of downloads I am still having the same problems. A typical example is the linux-restricted-modules-2.6.17-11-generic update I'm trying to get via update manager (Size: 7.0 MB). Just now it got to ~85% in no time at all, before the download rate plunged to between "unknown" and about 1500 B/s. Seems to be stuck at 98% now, but maybe if I give it some time it will complete this time! Anyway, this fast-slow problem is pretty typical, and is (of course) a problem when I try to get larger files from the repositories with apt-get...

Oh well, tomorrow is a bright new day.

Thanks again! #-o

---

### Post by Mr. C. on 2007-03-06
Sounds fine.  When you see the problem is a good time to start running traceroutes - so that you can see how long the packets are taking to reach the same host you are downloading from.

---

### Post by AR33 on 2007-03-07
Hey, i had the same problem and fixed it by setting speed to 10MB/s with ethtools.

like this: sudo ethtool -s eth0 autoneg off
                sudo ethtool -s eth0 speed 10

Don't know if it will work for you but it worked fine for me!

---

### Post by Mr. C. on 2007-03-07
> **AR33 said:**
> Hey, i had the same problem and fixed it by setting speed to 10MB/s with ethtools.

like this: sudo ethtool -s eth0 autoneg off
                sudo ethtool -s eth0 speed 10

Don't know if it will work for you but it worked fine for me!

There is nothing in the OPs Ethernet stats that shows any networking errors.  His rate has been negotiated to 100Mbps/Full, which implies there is a switch on the other end, and it is working just fine.

Setting to 10Mbps will mask problems, or not trigger them, because download speeds are cut by a factor of 10.

The stats show that the connection is fine.  The problem is elsewhere.

MrC

---

### Post by AR33 on 2007-03-08
There were no errors here according to the stats, maybe the real problem is somewhere else but my download speed has speeded up from 20 kbps to 250-300 kbps.

---

### Post by Mr. C. on 2007-03-08
Then this would indicate your have a faulty piece of hardware somewhere, that cannot cope with the demands of 100Mbit Ethernet.  Cable length, twist rates, cable category, shielding, robust connectors, non-kinked cables are all critical in 100Mbit Ethernet; 10Mbit is much more forgiving.

As I said, your problem went away, only because you masked  it.  If it suits your needs, that's excellent to hear.  But it does not *solve* the problem, and that's what the OP desires until we hear otherwise.

MrC

---

### Post by Zoo2 on 2007-03-10
Hi everyone,

Thanks for the patience MrC, am at my girlfriend's with my laptop trying to see if I can find any differences in settings. I have DSL here (~16000kBit/s up, 1000kBit/s down, as measured on my Xp machine) and everything works faster... Websites load much faster and my "standard" download tester (Real Player package, 5.5MB) takes seconds to download here, instead of taking forever back in halls. As I mentioned before, the curious thing is that here I am getting consistent download speeds of around 300-400 Kb/s, whereas before it started out like this and then dropped down close to 0, which seems to be why loading/downloading anything usually took so long. In terms of browsing I'm using OpenDNS for the DNS servers: again, the problem at home appears to be that I get an initially "high" speed which drops off (website is found fast enough, then takes ages to load fully), whereas here it's consistent (even if the connection speed isn't, apparently, so fast) and therefore seams faster overall.

I checked all the settings, as before:

> eth0   Link encap:Ethernet  HWaddr 00:0D:56:38:A4:BB  
          inet addr:192.168.178.20  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:a4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:374403 (365.6 KiB)  TX bytes:38604 (37.6 KiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0     Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[17179596.552000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:38:a4:bb
[17179599.640000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179599.640000] b44: eth0: Flow control is off for TX and off for RX.
[17179611.084000] eth0: no IPv6 routers present

eth0   Link encap:Ethernet  HWaddr 00:0D:56:38:A4:BB  
          inet addr:192.168.178.20  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe38:a4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:374531 (365.7 KiB)  TX bytes:38604 (37.6 KiB)
          Interrupt:177

The only thing that strikes me here is that the RX / TX rates are lower here than before, even though the whole system appears to work better. I am reaching my knowledge limits with networking jargon here, how do the RX / TX values actually describe my back-and-forth traffic? Also, can you give me some clues as to what to look for when tracerouting? I can't seem to see much difference when I traceroute here or there, could it be that with small packets flying around no differences are visible? In any case I am beginning to feel that there is a problem with buffering (?) or some other traffic control issue on the university side, but I haven't given up yet.

Anyway, will also get in touch with the university people again, although they weren't exactly much help last time... Their suggestion was just to go back to Xp, since it seems that for most people in the apartments this works without a problem, and although they were full of admiration for my "great desire" to use Linux they didn't really know what to do. :-({|= :-\" #-o (nice smilies, but don't do justice to the facial expressions after that phone call).

Thanks again for the help and any further suggestions would certainly be welcome. Will be very busy in the next few days, but will try to keep an eye on the post and continue with my troubleshooting when I get the chance.
Z

---

### Post by Mr. C. on 2007-03-10
The Tx / Rx data you see is the number of packets Transmitted (Tx) and Received (Rx).  These are note rates, rather just payload size + networking overhead.

The KiB values are just Kilobyte; not rates (eg. RX bytes: 374403 / 1024 = 365.62 KiB).  The simplest way to get transfer speed is to use a known sized data file (like 1-10 meg), transfer it, and do a quick timing with a watch.  That's a rough estimate.  But you can also use something like wget of ftp which will give you approximations of transfer speed.  Even more accuracy can be gained with various benchmarking programs.  In a real world scenario, these are less meaningful, because the network is very dynamic in terms of rates, routes, and latency.

Have you disabled IPv6?  Many users have experienced speed problems with IPv6 with some hardware.  This might be worthwhile for you, and will create no issues, so its safe.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by inthedryer on 2007-08-20
Hi everyone. I'm having an eerily similar problem with my wireless internet connection. I use a broadcom bcm4306 adapter which i got working using bcm43xx-fwcutter. That process was fairly smooth but I'm am still having issues with connectivity. The problem is pretty much the same as zoo2's except browsing sometimes works decently fast, then for no apparent reason it slows to a crawl. It acts the same when using adept as well as apt-get. I cant pinpoint a reason why my network connection is behaving this way. Hopefully someone can help.

One possibly related symptom I noticed is that when activating my wireless connection, knetworkmanager ocaisionally stalls at 28% the "activating device" stage, and more often at 57% the "ip configuration" stage. Sometimes this causes the whole thing to time out and it wont conncet. After multiple tries I eventually get it to connect. But other times my internet will automatically start up without a hitch.

Also, i will randomly loose my connection for no apparent reason.

Here's some outputs I get (eth1 is my wireless card);

ifconfig -a -v

> 
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:75:1E:59
          inet addr:192.168.1.14  Bcast:192.168.1.63  Mask:255.255.255.192
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x400

eth1      Link encap:Ethernet  HWaddr 00:14:A5:10:6A:B5
          inet addr:192.168.1.12  Bcast:192.168.1.63  Mask:255.255.255.192
          inet6 addr: fe80::214:a5ff:fe10:6ab5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11848 errors:0 dropped:4508 overruns:0 frame:0
          TX packets:10462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15400523 (14.6 MiB)  TX bytes:762328 (744.4 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1964 (1.9 KiB)  TX bytes:1964 (1.9 KiB)[/CODE]

The 4508 dropped RX packets seem to be a problem but i don't know enough about networking to be sure


dmesg | grep eth1

> 
[   59.600000] eth1: no IPv6 routers present
[   95.396000] eth1: no IPv6 routers present
[ 3250.772000] eth1: no IPv6 routers present
[ 3273.520000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3274.084000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3292.812000] eth1: no IPv6 routers present


iwconfig eth1


> 
eth1      Link encap:Ethernet  HWaddr 00:14:A5:10:6A:B5
          inet addr:192.168.1.12  Bcast:192.168.1.63  Mask:255.255.255.192
          inet6 addr: fe80::214:a5ff:fe10:6ab5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11953 errors:0 dropped:4604 overruns:0 frame:0
          TX packets:10655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15482311 (14.7 MiB)  TX bytes:773559 (755.4 KiB)
          Interrupt:10


cat /etc/network/interfaces

> 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I hope this is enough info for someone to get to the bottom of this very frustrating issue. If there are any more diagnostic commands i should run (im sure there are, as i am still very green with unix), please tell me, any help will be greatly appreciated.

---

### Post by inthedryer on 2007-08-20
Sorry for the double post, but i found another symptom. The light on my wireless button blinks on and off rapidly when its working, it does this when loading a youtube video or downloading something from adept etc. When windows was installed on this computer (hp zv6000 laptop) the light remained on constantly. What would cause this?

---


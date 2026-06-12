---
title: "Download Speeds are 200X Slower than what they Should Be!"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Lauxmonster on 2009-10-23
Hi,

Sorry I haven't really picked up on everything in Ubuntu yet... But, I am really confused and I seem to see very few people with the same problem. Here is the problem...

I have a fast Verizon FiOS connection. Its 20mb/s Download and 5mb/s Upload. 

[[IMG]http://www.speedtest.net/result/601048330.png[/IMG]](http://www.speedtest.net)

On my Windows computers, its blazing fast. Downloading a movie takes under 5 minutes. Now, I am getting literally < 100KB/s on Ubuntu. (This is both from Firefox, Torrents, and Add/Remove Apps. I haven't a clue why this should be.

Thanks for any of the help.

~

---

### Post by halitech on 2009-10-23
is the screenshot from your windows computer or the Ubuntu computer?

---

### Post by the.phantom on 2009-10-23
NOTE"
there is a BIG difference between B and b
b= bits
B=bytes=one word of 8 bits
on your screen shot you are showing
19 mega BITS

---

### Post by jbrown96 on 2009-10-23
How do your computers connect to your Verizon modem? Wired or wireless? It could be due to bad network drivers, or perhaps Ubuntu is dropping into a very low speed mode. I set up a computer once where network speeds were very slow. It ended up that the laptop was using Broadcom wireless (poor drivers at the time) and the laptop was like 1-2 feet away from the router. The signal was so strong that it was interfering with itself, and Ubuntu had to decrease the speed to avoid connection errors. 
You said that it works as expected on your Windows computers. If you have your Ubuntu disk, could you try to boot it on one of the windows computers and test the speed? Or does the Ubuntu system have Windows as well in dual boot?

We could use some more info about your setup hardware. In a terminal (apps-->accessories-->terminal), post the output of the following commands ```
suod lshw -c network
``` ```
ifconfig
``` ```
iwconfig
``` ```
ping -c 10 google.com
```

---

### Post by Lauxmonster on 2009-10-23
Oh my...I feel really dumb. Verizon had me thinking it was Megabytes and not bits. I looked up the FiOS plan I had an it was mbps not MBps....darn. 

[[IMG]http://www.speedtest.net/result/601071700.png[/IMG]](http://www.speedtest.net)

---

Still, why am I getting 100KB/s downloads and not 2500KB/s downloads?

---

My Computer is connected to my Verizon router via a Cat5e Cable that runs into a 10/100 Ethernet switch. If the Ethernet switch can handle up to about 25MB a Second, I do not think it would be a cause. But, what do I know.

---

### Post by Lauxmonster on 2009-10-23
*-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       serial: 00:08:74:dc:e4:e7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s

---

eth0      Link encap:Ethernet  HWaddr 00:08:74:dc:e4:e7  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fedc:e4e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:308161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:438387245 (438.3 MB)  TX bytes:33608952 (33.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1840 (1.8 KB)  TX bytes:1840 (1.8 KB)

---

lo        no wireless extensions.

eth0      no wireless extensions.


---

PING google.com (74.125.53.100) 56(84) bytes of data.
64 bytes from pw-in-f100.1e100.net (74.125.53.100): icmp_seq=1 ttl=39 time=101 ms

---

### Post by jbrown96 on 2009-10-23
Intel network cards should be very well supported. What version of Ubuntu are you using? What kernel? ```
lsb_release -a
``` ```
uname -r
``` When you boot the computer you should get a list of kernels to choose from (you may need to press escape as soon as the BIOS screen goes away). Try choosing an older one (not recovery), and see if it is still really slow.

---

### Post by Lauxmonster on 2009-10-23
jbrown96,

Thank you oh so much for your help. 

Jaunty 9.04
2.6.28-16 Generic.

I just tested a download and for some odd reason or another it was much higher than it was for about the past week. Maybe it is simply ISP related...funny how it changed so quickly. =/

So, maybe I will see if this trend continues. If not, I will get back. Thanks alot to everyone. Sorry to make you waste your time on me....but this problem is not yet "solved" ;).

---

### Post by misfitpierce on 2009-10-23
> **Lauxmonster said:**
> Sorry to make you waste your time on me....but this problem is not yet "solved" ;).

Not a waste of time for anyone... Its what everyone is here for :P

---

### Post by egalvan on 2009-10-23
> **Lauxmonster said:**
> 
---

Still, why am I getting 100KB/s downloads and not 2500KB/s downloads?

---

My Computer is connected to my Verizon router via a Cat5e Cable that runs into a 10/100 Ethernet switch. 
If the Ethernet switch can handle up to about 25MB a Second, I do not think it would be a cause. But, what do I know.

100BaseT is rated at 100-mega-BITS-per-second.

Which translates (taking into account overhead and such) approx 10-mega-BYTES-per-second transfer rate. In Theory.

Per port, one way.

The switch may be able to handle 25MB-second, but that would be **bi-directional**.
 Which has no bearing on download speeds.

and as for speeds being better on some days, and worse on others,
this is just the ISP's being ISP's...
some days are diamonds, some days are coal.


I'm on a 1.5Mb/s DSL connection.

GigaBit NIC connected via CAT5E to a GigaBit switch,
connected to the 10Mb port on the DSL router.

I average 100KB/S, and max out at 150KB/S.

---

### Post by jbrown96 on 2009-10-23
> **Lauxmonster said:**
> jbrown96,

Thank you oh so much for your help. 

Jaunty 9.04
2.6.28-16 Generic.

I just tested a download and for some odd reason or another it was much higher than it was for about the past week. Maybe it is simply ISP related...funny how it changed so quickly. =/

So, maybe I will see if this trend continues. If not, I will get back. Thanks alot to everyone. Sorry to make you waste your time on me....but this problem is not yet "solved" ;).

gotta love this. Everything always seems to start working when you are getting help. 
My suggestion is to do a clean install of 9.10 RC. The final version comes out next week, and the RC has been very stable on my system. It has kernel 2.6.31 which is much newer than 2.6.28 that you are running. There should be some driver improvements, but honestly I think this is some sort of bug that has worked its way into your system. Doing a clean install is probably the least painful way to fix the problem, but it's perfectly understandable if you don't want to dive into 9.10 before it's a little big more mature.

---

### Post by falconindy on 2009-10-24
Just FYI, those speed tests are done to your router, not to your computer on the LAN. You should get the exact same results whether you're on a wireless or wired connection.

---

### Post by Lauxmonster on 2009-10-24
Ok, thanks for all of the help. I will definitely be upgrading to 9.10 anyway. 

Also, as others have said, it could simply be to do with MY network...although I think I have a quick setup.

Thanks again.

~

---

### Post by Lauxmonster on 2009-10-24
I am downloading a Zip as we speak and I am getting 2MB/s....grr....why does it always happen that way.

---

### Post by QLee on 2009-10-24
> **falconindy said:**
> Just FYI, those speed tests are done to your router, not to your computer on the LAN. You should get the exact same results whether you're on a wireless or wired connection.

What makes you think that? The various speed test sites download a file to your system and measure how long the download took in order to calculate the connection speed. There isn't any place on a router for the file to download. Your connection is between your system and the test site because the router NATs your LAN IPs.

---


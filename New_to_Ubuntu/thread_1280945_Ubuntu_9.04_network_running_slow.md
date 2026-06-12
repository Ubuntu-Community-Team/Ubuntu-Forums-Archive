---
title: "Ubuntu 9.04 network running slow"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Aayn on 2009-10-02
I am kinda new to Ubuntu and can't seem to get things working right on my system.  So first I will list my system specs.

Model ~
Brand 	ASUS
Series 	G Series
Model 	G1S-B1

Operating System  Ubuntu 9.04 32bit !!!!! :KS     ...and vista....
CPU Type 	Intel Core 2 Duo T7700 2.4G
Screen 	15.4" WSXGA+
Memory Size 	2GB DDR2 667
Hard Disk 	200GB 7200RPM
Optical Drive 	DVD Super Multi
Graphics Card 	NVIDIA GeForce 8600M GT
Video Memory 	256MB GDDR3 VRAM, TurboCache up to 512MB
Communication 	Modem, Gigabit LAN and WLAN
Card slot 	1 x Express Card

My wireless card uses the intel 4965 drivers, I think... (I don't think that's the issue, but you never know)

I have been having very very very slow networking and internet speeds.  I also have Vista installed... and I don't get any problems at all with my networking and internet there.:confused:

When I was trying to update it went even slower and synaptic downloads at 15kbs.  At it's highest download rate I get 30kbs in synaptic, but that doesn't last very long.

My vista speeds are over 500kbs....

It doesn't seem to matter if I am hard wired or on wireless, the speeds are the same.  I have been reading on the forums about the ipv6 and tried to disable it.  I'm not sure if I did it right, but nothing looked like it was fixed.  Everything stayed the same.

So, here's some outputs using "ifconfig" and "iwconfig".

eth0      Link encap:Ethernet  HWaddr 00:1d:60:dc:c7:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:ce:3f:b9  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fece:3fb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3458346 (3.4 MB)  TX bytes:505709 (505.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-CE-3F-B9-66-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~>>>>


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ElaTioN"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6F:61:96   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-45 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~>>>>>>


Any help would be greatly be appreciated!!!

Thank you in advance :)

~Ayn



Things I have tried so far... I will continue to update what I have tried.

This seems to disable ipv6 as I do not get an output from ( lsmod | grep inet6 ) when I run it.

 echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

So, ipv6 does not seem to be the problem.

I have tried changing the bit rate with ( sudo iwconfig wlan0 rate 5.5M ) and still a no go...

I have tried changing the /etc/nsswitch.conf ( hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 ) and replacing it with ( hosts: files dns ).  Still a no go....

---

### Post by Iowan on 2009-10-02
I found [this]("http://ubuntuforums.org/showthread.php?t=1080417") somewhat old thread in my subscriptions.

---

### Post by LewRockwell on 2009-10-02
with the beta release the tubes are clogged

.

---

### Post by Aayn on 2009-10-02
Iowan: Thank you for your quick reply :}  I read through the thread you linked and followed the instructions.  I did a reboot and I still get the same speeds.  So, it doesn't seem to be an acpi problem.

LewRockwell: Ah yes, lots of post on the new Karmic beta.  I would love to be trying it myself, but it seems I have these Jaunty issues....

---

### Post by Aayn on 2009-10-02
Things I have tried so far... I will continue to update what I have tried.

This seems to disable ipv6 as I do not get an output from ( lsmod | grep inet6 ) when I run it.

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

So, ipv6 does not seem to be the problem.

I have tried changing the bit rate with ( sudo iwconfig wlan0 rate 5.5M ) and still a no go...

I have tried changing the /etc/nsswitch.conf ( hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 ) and replacing it with ( hosts: files dns ). Still a no go....

~Ayn

---

### Post by skern03 on 2009-10-03
> **Aayn said:**
> Things I have tried so far... I will continue to update what I have tried.

This seems to disable ipv6 as I do not get an output from ( lsmod | grep inet6 ) when I run it.

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

So, ipv6 does not seem to be the problem.

~Ayn

I've been unable to disable ipv6 myself in 9.04. Connection speeds are either so slow they're unusable (can't even update), or else don't work at all. This machine is triple boot - U8.10, XP and U9.04. Both 8.10 and XP work fine. Why they haven't fixed this is beyond me. As is why they even did it in the first place. :(

The command you list (lsmod | grep inet6) above doesn't seem to work - or to be a reliable indicator - at least on my machine. Even tho I followed instructions to disable ipv6, and the command produces no results, when I look under System, Administration, Network Tools, I see ipv6 listed as Host for the Loopback Interface, and Link for the Ethernet Interface on the Devices tab.

If i run any of the bandwidth speedtests out there, on XP and u8.10 I get really great results - like 18 Mbps. For U9.04? 2 Mbps. If I'm lucky.

---

### Post by skern03 on 2009-10-03
BTW, no need to stay frustrated w/9.04. Unfortunately, it looks like the beta for 9.10 (Karmic) has same problems w/ipv6. No need to stay on the bleeding edge to enjoy Ubuntu. Soo.... 

You can always install the long term support: Ubuntu 8.x. You can find an ISO image to burn onto a CD here:

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

**Make sure you click "Ubuntu 8.04 LTS Desktop"** (9.04 is the default). Once you install 8.04, after a few upgrades, you'll get a prompt to update to 8.10. Go ahead and do that. I've been running 8.10 for quite a while now with no network issues. Other issues, like sound (PulseAudio is crap), but not network.

Shout if you have questions... many people here will help you.

---

### Post by Aayn on 2009-10-04
Ok, so I got my lan to work at good speeds, but my wireless is still having problems.  I am really thinking about just downgrading to ubuntu 8.10 and at the same time I really want to figure this out...  :x

Do you have any suggestions on things I can try with the wireless?

---

### Post by skern03 on 2009-10-04
> **Aayn said:**
> 
Do you have any suggestions on things I can try with the wireless?

I haven't tried wireless and 9.04. I'm keeping my laptop at 8.10 cuz I know it works.

Best thing to do is search with parameters like: ipv6 wireless

In one of the many posts I read during my two marathon attempts to get decent performance out of 9.04, I saw something about wireless, but I didn't keep a link to it, sorry.

Good luck! You can also try posting a new thread with a subject that indicates you're having wireless problems with 9.04.

---

### Post by Aayn on 2009-10-04
Thank you so much for your replies!!  I don't seem to be alone in this weird wireless issue and the more that I read on other threads, it seems that people have different wireless fixes.  Sadly, none of them have worked for me.  So, I think I will make a new thread on Ubuntu 9.04 wireless and it's slowness....

---

### Post by skern03 on 2009-10-04
> **Aayn said:**
> Thank you so much for your replies!!  I don't seem to be alone in this weird wireless issue and the more that I read on other threads, it seems that people have different wireless fixes.  Sadly, none of them have worked for me.  So, I think I will make a new thread on Ubuntu 9.04 wireless and it's slowness....

Glad to help. One suggestion - you might try what I'm doing - triple booting. XP, U8.10, U9.04. When the next version of Ubuntu is stable and working, then I'll upgrade to it. Here's my setup:

First HD: XP only
Second HD: 10 GB U8.x OS, 2 GB Swap, 10 GB U9.x OS. The rest is data - home directories, etc.

This way, I can reinstall OS's if they're completely toasted, as when I mistakenly upgraded to 9.04.

If you follow this suggestion, you can have 8.10 functioning and stable while you test 9.04.

---

### Post by Aayn on 2009-10-05
Awesome idea!! I think I will shrink my partition, then add on.  I use external drives for a lot of my data and backing-up, I kinda made that a habit from having so many windows problems in the past....

Thanks again for all of your help :D

---

### Post by Iowan on 2009-10-05
Have you tried jockeying around (or checking) MTU values (via **ifconfig**)? Probably just a wild stab, but thought I'd throw it out.

---

### Post by Aayn on 2009-10-05
I haven't tried checking the mtu setting till I read your post.

My mtu settings were 1492 and I changed them from 1450-1600 and just played with some numbers on there and didn't really see any improvement.

Is there an optimal mtu setting?

The only ones I ever found was 1450 and 1500 that seemed to solve other peoples web browser problems.

The highest speeds I'm getting right now are 72 latency and 80kbs.  

If you have any other suggestions, I'm definitely open to them :KS

---

### Post by Aayn on 2009-10-07
I have started a new thread on just my wireless being slow since I have fixed the wired problems.

[http://ubuntuforums.org/showthread.php?t=1285487](http://ubuntuforums.org/showthread.php?t=1285487)

---


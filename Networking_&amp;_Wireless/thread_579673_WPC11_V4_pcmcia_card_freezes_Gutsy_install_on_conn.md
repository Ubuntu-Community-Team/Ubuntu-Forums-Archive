---
title: "WPC11 V4 pcmcia card freezes Gutsy install on connect"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by CheeseEatingBulldog on 2007-10-18
I just did a fresh install on my laptop (Vaio). I can see wireless networks, but if I try to connect to one it hangs my machine completely. I know this card (WPC11 v4) has given problems in the past, so does anyone else have issues?

---

### Post by CheeseEatingBulldog on 2007-10-18
I just removed the WEP security and now it does connect if I add the wlan0 interface to the /etc/network/interface with only a wireless-essid. So I am assuming the WEP makes the machine hang.

---

### Post by sbennettgso on 2007-10-20
I'm having pretty much the same issue with this card.  I have a ThinkPad A22p, and this card worked fine in it under Dapper, Edgy, and Feisty.

When I remove WEP as recommended above, it associates with my AP (and doesn't hang my machine), but it doesn't seem to be connected to the rest of my network.

I had issues using Network Manager with this card in Feisty.  I might not have those same issues, but because it doesn't seem to get connected to my network I can't tell - it automatically looks for another network to connect to.  For the information provided below, I removed Network Manager and used the Network Settings tool.

Here's what I get in response to iwconfig:

```
scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b linked  ESSID:"3ComHome"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:AC:E6:21:63   
          Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=82/100  Signal level=-45 dBm  Noise level=-238 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

```

And here's what I get in response to ifconfig:

```
scott@scott-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:B7:82:49  
          inet6 addr: fe80::203:47ff:feb7:8249/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2018279 (1.9 MB)  TX bytes:305252 (298.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1020 (1020.0 b)  TX bytes:1020 (1020.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:3F:12:21  
          inet addr:192.168.1.23  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe3f:1221/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:31 overruns:0 frame:0
          TX packets:5615 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:189633 (185.1 KB)
          Interrupt:11 Memory:e09ea000-e09ea100 

```

Any help would be appreciated.

Thanks,
Scott

---

### Post by 416hammy on 2007-10-22
> **sbennettgso said:**
> Any help would be appreciated.

Chuck it in the trash (like I did to mine), and get one of these:

[http://www.dlink.com/products/?pid=476](http://www.dlink.com/products/?pid=476)

:D

---

### Post by sbennettgso on 2007-10-23
I finally got this working (I think)...

I did end up using ndiswrapper.  I used the W98 drivers downloaded from the RealTek WWW site ([http://www.realtek.com.tw]("http://www.realtek.com.tw") - thanks to Kevdog and his [thorough tutorial on ndiswrapper]("http://ubuntuforums.org/showthread.php?t=574501") for this information) and everything seemed to work (controlled through Network Manager, WEP, etc.).

While troubleshooting this issue, I was able to connect to an open network using the native driver.  But I had to do a sudo modprobe r8180 (and add 'r8180' to /etc/modules) to get this running.  Seems a little strange to me - I would have expected that to load by default.

Thanks,
Scott

---

### Post by CheeseEatingBulldog on 2007-10-24
Went out and bought a new one, but the card wpc11 also has the same effect on my gf's vaio. Instant freeze upon connect with WEP enabled.

---

### Post by stillerz on 2007-10-28
Hi,

I'm using Gutsy on a Thinkpad T22 with the WPC11 v4 card and I'm still having the problem with it freezing and locking the system after I enter a WEP key, even after I've installed ndiswrapper and downloaded drivers from the realtek site.

Could someone post a link to the exact driver file they used on Gutsy?  And, if there were any post-install steps after using the GUI version of the ndiswrapper tool?

Thanks!

---

### Post by lazyart on 2007-10-28
had the same problem with this card as well.  Didn't work in Feisty, locks up Gutsy.  Cisco Aironet is my other card though.

---

### Post by sbennettgso on 2007-10-30
Here is the link I downloaded the drivers from.
[URL="ftp://202.65.194.212/cn/wlan/ndis5x-8180(173).zip"]
ftp://202.65.194.212/cn/wlan/ndis5x-8180(173).zip[/URL]

I don't know if there's a difference between the W98 and WXP drivers on the RealTek site, but Kevdog made specific mention of using the W98 drivers, so that's what I downloaded.

Thanks,
Scott

---

### Post by bconverse on 2007-11-01
Hi,
I am running Gutsy, and I am having these problems as well.  Can someone spell out the correction steps for me, I am an Ubuntu newbie.  I'll probably just get a new wireless card soon, but, for now, I really need to use the wpc11. 

Thanks for any help with the procedures...

---

### Post by stillerz on 2007-11-01
Try following the instructions in this link:

[http://ubuntuforums.org/showthread.php?t=584046&highlight=t21](http://ubuntuforums.org/showthread.php?t=584046&highlight=t21)

I was able to use them to solve my issue and now my WPC11 works on Gutsy.

---

### Post by bconverse on 2007-11-04
awesome. thanks i'll check it out.

---


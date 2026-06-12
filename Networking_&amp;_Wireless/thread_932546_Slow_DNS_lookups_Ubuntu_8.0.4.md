---
title: "Slow DNS lookups Ubuntu 8.0.4"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by nlspeirs on 2008-09-28
Hi all.

I've been running Ubuntu for a couple of months now. I am an Apple and Windows system administrator and Linux will be my next challenge. Overall I find it hard to troubleshoot Linux, I just don't know my way around the system enough I guess. For instance this problem, I don't know where to start...

I've been using wireless networking without any problem on my Dell XPS M1530. My laptop goes everywhere with me and just a week ago I needed to plug in UTP because at the site I was there wasn't wifi. This went without any problem whatsoever. But then I needed wifi again: DNS seems to be broken. It just is slow as h#ll! Example: I've navigated to this forum and it hangs a couple of seconds on "looking for..." Then i click a few topics and start a search for my problem: Again it hangs on "looking for..." The same site it looked for 1 minute ago! Besides it being painfully slow, doesn't it use a cache of some sort?

I've used different DNS servers, checked my /etc/resolv.conf, edited my /etc/nsswitch.conf, restarted all kinds of stuff, ran latest updates, etc. My Mac and PC don't have this problem. I also have this problem at different sites I am at.

Any help is greatly appreciated.

:)

---

### Post by nlspeirs on 2008-09-29
Anybody? It is driving me crazy and seems to get worse (or I am running out of patience). Maybe the output of ifconfig and iwconfig helps?

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3e:cd:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:3e:cd:0c  
          inet addr:169.254.4.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:132000 (128.9 KB)  TX bytes:132000 (128.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.222.1  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.34.1  Bcast:172.16.34.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:81:e5:e1  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe81:e5e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19124298 (18.2 MB)  TX bytes:1551047 (1.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-81-E5-E1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"23"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:5A:49:58   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-51 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```

---

### Post by iponeverything on 2008-09-29
kick back the output a "route -n" lets also have look at your
/etc/resolv.conf

it smells like you have two default routes.

---

### Post by nlspeirs on 2008-09-29
Thanks for the reply!

route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.34.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.222.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

/etc/resolv.conf

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5206
#
### END INFO



nameserver 83.80.1.236


```

---

### Post by iponeverything on 2008-09-29
Try adding the opendns servers below the one .nl one that your using in your resolve.conf 

nameserver 208.67.222.222
nameserver 208.67.220.220

0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

You do still have your wireless gateway (wlan0). Not sure why it is still there. Try to turn off your wireless with the nm-applet and tell it to use wired. Your ifconfig is quite busy. No address on eth0? Its RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)! Odd,I don't think you were using that interface to get out.  avahi is auto discovery doohickey. I think that your 1000 metric default on eth0 is for avahi.

---

### Post by nlspeirs on 2008-09-30
Hi and thanks. I'll add the open DNS servers and report back.

It is correct that wlan0 is still active, maybe my original post was a bit confusing but I am always using wireless and not wired. After I used wired one time my wireless started acting up. So as far as I know eth0 isn't being used.

I don't understand what you want me to do with 'avahi'.

---

### Post by aladinonl on 2008-09-30
the default network manger in ubuntu sucks. Its nightmare if u r using wireless, constantly drop connection, forget settings. I suggest u use wicd. Use the latest version 1.5.2, download from soureforge, its great.

---

### Post by iponeverything on 2008-09-30
> **nlspeirs said:**
> Hi and thanks. I'll add the open DNS servers and report back.

It is correct that wlan0 is still active, maybe my original post was a bit confusing but I am always using wireless and not wired. After I used wired one time my wireless started acting up. So as far as I know eth0 isn't being used.

I don't understand what you want me to do with 'avahi'.

ahh.. ok. take down eth0.   From the prompt do "ifconfig eth0 down"
you might net avahi not to start in services so prevent eth0 from coming up uninvited. Not sure what it is now. When you take down eth0 your second default route will disappear. when you try nslookups from the command line do you see anything strange?

---

### Post by iponeverything on 2008-09-30
> **aladinonl said:**
> the default network manger in ubuntu sucks. Its nightmare if u r using wireless, constantly drop connection, forget settings. I suggest u use wicd. Use the latest version 1.5.2, download from soureforge, its great.

I have not had problems with nm-applet and wireless it works great for me and it sure beats having diddle around with iwpriv, hostap and iwconfig all the time.  The rt61pci module has been a bit pain though..

---

### Post by kpkeerthi on 2008-09-30
I use [dnsmasq]("https://help.ubuntu.com/community/Dnsmasq") to cache DNS lookups locally.

---

### Post by nlspeirs on 2008-09-30
> ahh.. ok. take down eth0.   From the prompt do "ifconfig eth0 down"
Done.

> you might net avahi not to start in services so prevent eth0 from coming up uninvited. Not sure what it is now. When you take down eth0 your second default route will disappear
Could not find avahi in 'Administration - Services' What is avahi?

> when you try nslookups from the command line do you see anything strange?
This first few lookups went well and then:

```
sysop@zion:~$ nslookup apple.nl
;; connection timed out; no servers could be reached

```

Two seconds later it does resolve apple.nl

I'll add the open dns servers in a bit

---

### Post by nlspeirs on 2008-09-30
> 

nameserver 208.67.222.222
nameserver 208.67.220.220


Added, same problem :(

I checked and eth0 did come up again after a restart but didn't add a route as shown in route -n.

---

### Post by nlspeirs on 2008-10-02
Anyone any tips? I'm about to reinstall this whole thing because of this problem, it's driving me crazy.

---


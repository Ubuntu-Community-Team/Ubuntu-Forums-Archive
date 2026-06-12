---
title: "Ubuntu Stopped Playing Nice With Router"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by loganrapp on 2008-07-30
Hey, everyone - 

I've spent the last two days trying to figure this out on my own, but I've just been having too hard a time of it, and none of the threads I can find have worked. 

I've got the Broadcom 4312 wireless card, and after getting it to work through ndiswrapper (easier said than done), I got it to work fine. It could connect through ethernet as well as wireless, and I'd get an internet connection without trouble. I should also note that I dual boot Windows XP (for now, until I'm satisfied with VMWare) and Ubuntu.

After creating a virtual WinXP machine with VMWare - and this probably isn't the culprit, but I figured I'd throw it out there - the laptop will be able to connect to my network, but cannot reach the Internet. 

This happens only on my network. I am currently on someone's open WiFi just so that I can output if/iwconfig to you guys. 

While I'm on Windows XP, I can connect to the Internet fine through my network.

I am able to ping my router and get a response. But I cannot ping anything outside of the router. 

But *neither wired nor wireless* can get to the internet while on Ubuntu. I get an IP assigned to me. The router recognizes that there's someone connected through that IP. However, even while that IP is set to the DMZ, it cannot get through to the internet. 

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:d3:21:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386777 (377.7 KB)  TX bytes:7615 (7.4 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:523060 (510.8 KB)  TX bytes:523060 (510.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.171.1  Bcast:192.168.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:4c:ca:9f  
          inet addr:129.1.1.110  Bcast:129.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe4c:ca9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6922554 (6.6 MB)  TX bytes:517381 (505.2 KB)
          Interrupt:16 Memory:c0200000-c0204000 

```
 
```
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1D:7E:28:59:D6   
          Bit Rate=18 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


```

---

### Post by dmizer on 2008-07-30
Try disabling IPv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Some routers handle IPv6 better than others.  Some can't handle it at all.  Since IPv6 is not a universal standard, and a vast majority of websites either serve only IPv4 or both IPv6 and IPv4.  So, unless you have a serious need for IPv6, it won't hurt anything by disabling this.

---

### Post by loganrapp on 2008-07-30
Disabling ipv6 does not work. I'm just absolutely at a loss here. I spend hours getting the wireless network card to work with ndiswrapper, it finally works, and works as intended, even after reboot, and then - poof, nothing. It makes absolutely no sense to me.

---

### Post by dmizer on 2008-07-30
Your card does appear to be working.  Something else is blocking your access.

Can you ping google.com?

Try using opendns DNS servers: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by jimv on 2008-07-30
Can you post the output of 

```
route -n
``` 

from Ubuntu and ipconfig from Windows when connected to your router?

You can save the output of route -n to a file by going 

```
route -n > somefile.txt
```

---

### Post by chuckbert on 2008-07-30
This sounds similar to mine and someone else's problem. Recent update leads to lack of access beyond the router.
[http://ubuntuforums.org/showthread.php?p=5488288#post5488288](http://ubuntuforums.org/showthread.php?p=5488288#post5488288)
The other guy has solved it by rebooting to an earlier kernel. 
[http://ubuntuforums.org/showthread.php?p=5488275#post5488275](http://ubuntuforums.org/showthread.php?p=5488275#post5488275)
I have yet to try this.

---

### Post by loganrapp on 2008-07-30
Route -n output: 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.171.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
```

Windows ipconfig:

```
Ethernet adapter Local Area Connection:

        Media State . . . . . . . : Media disconnected

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix . :
        IP Address. . . . . . . . . . . : 192.168.0.106
        Subnet Mask . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . : 196.168.0.1

```

I can already see the discrepancy, but how to fix it, no clue.

I have yet to try rebooting into an older kernel, but hopefully I won't have to.

---

### Post by loganrapp on 2008-07-30
Okay, I (rather, my brother) solved the problem. 

VMWare was insisting on an IP for vmnet1 that I had assigned to my router. Any and all attempts to change it on vmnet's side failed and just re-wrote whatever changes I made. 

Frustrating, but I gave it its way and changed the IP of my router. Now I can connect to the Internet just fine on Ubuntu.

---

### Post by dmizer on 2008-07-30
Wow, glad you (or rather, your brother ;)) got that working.

Okay, so my question is ... why did your wireless card have an ip address of 192.168.1.110 back in your first post?  Did you set that statically?

---

### Post by jimv on 2008-08-01
> **loganrapp said:**
> Okay, I (rather, my brother) solved the problem. 

VMWare was insisting on an IP for vmnet1 that I had assigned to my router. Any and all attempts to change it on vmnet's side failed and just re-wrote whatever changes I made. 

Frustrating, but I gave it its way and changed the IP of my router. Now I can connect to the Internet just fine on Ubuntu.

That's kind of what I thought was happening when I saw the 192.168.0.1 address on the vmware adapter.

BTW, VirtualBox is a good alternative to VMWare if you ever want to check it out.

---


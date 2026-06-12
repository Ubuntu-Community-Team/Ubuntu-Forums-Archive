---
title: "No internet without VPN connection"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by richiemcc on 2014-03-08
Hi There, I have looked around for a solution to this but unfortunately nothing has worked so far. I use an ethernet over power adapter to connect to the internet, but for some reason, since I changed over to the adapter the only way I can connect to the internet is via a VPN. I have a HTPC in my living room that is also running 13.10 and connects via exactly the same method and that is fine.

At the time, when this problem first arose, my study PC was running 13.04. I upgraded to 13.10 hoping that would fix the issue, but it still remains. Whilst I am quite accomplished with Ubuntu, networking remains a mysterious black art to me so I may need a bit of guidance along the way.

Any suggestions are very much appreciated.

Cheers
Richard.

---

### Post by varunendra on 2014-03-11
Welcome to Ubuntu Forums richiemcc!

I am not yet familiar with VPN, so hope someone having real experience with it may see this and join us.

But for now, can you show me your routing table? Plus some other outputs, before and after connecting to the VPN -
```
ifconfig -a
route -n
nm-tool
```
Like I said, please post the result of above commands in two sets - one from before connecting to VPN, the other after connecting to it.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by richiemcc on 2014-03-14
Hi Varun,  thank you for responding. Here is the output without the VPN -

```
richard@study-desktop:~$ ifconfig -aeth0      Link encap:Ethernet  HWaddr bc:5f:f4:97:e1:96  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe97:e196/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1019572 (1.0 MB)  TX bytes:383540 (383.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host

[CODE]
```

          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83628 (83.6 KB)  TX bytes:83628 (83.6 KB)


[/CODE]

```
richard@study-desktop:~$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0



```

```
richard@study-desktop:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        BC:5F:F4:97:E1:96


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1



```

[SIZE=3]With the VPN[/SIZE]

```
richard@study-desktop:~$ ifconfig -aeth0      Link encap:Ethernet  HWaddr bc:5f:f4:97:e1:96  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe97:e196/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1934118 (1.9 MB)  TX bytes:737807 (737.8 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160970 (160.9 KB)  TX bytes:160970 (160.9 KB)


ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.200.21.3  P-t-P:10.200.20.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10610 (10.6 KB)  TX bytes:8254 (8.2 KB)




```

```
richard@study-desktop:~$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0          0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.200.20.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
103.12.9.1      192.168.1.1    255.255.255.255 UGH   0      0        0 eth0
103.12.9.1      192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0



```

```
richard@study-desktop:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           no
  HW Address:        BC:5F:F4:97:E1:96


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1






- VPN:  [HMA - Australian Server] ----------------------------------------------
  State:             connected
  Default:           yes


  Message:



```

Thanks again for taking the time to help out. I was going to do a clean install today to try and fix the issue, so hopefully I can avoid that.

Regards
Richard.

---

### Post by varunendra on 2014-03-14
Having no experience with VPN, and having no idea what you mean by "Ethernet power adapter", I'm afraid I am confused myself with the above outputs.

Unless I can understand the whole setup properly (how many devices in between your computer and Internet, how do they all mutually connect and what are their (local) IPs), I don't think I may be able to help here.

If you could, please explain for me how many devices are involved, and how are they connected.
How were you connecting before this "Power adapter" came into scene (what is it by the way? A network switch? A router?).

Your routing table (With VPN) looks weird. But it seems that whatever that "192.168.1.1" device is (mostly is a router with DNS internally configured), it is not working properly as a gateway.

What do you connect to via VPN? A different machine outside your local network? Sorry if this sounds a stupid question, but I know about VPN only so much.

I'm sure more questions will only make my post more confusing, so please explain the setup (with respect to above questions and anything you consider relevant) in as much detail as possible. I may be able to figure out the troubleshooting steps.

With the VPN out of picture, it should be as simple as -

The computer should connect to a router/modem that connects to internet.
The router should act as a gateway (connecting internet to local network)
The computer should have a valid IP, Gateway and DNS set, either assigned by DHCP (can be in the same router) or Manually.

For now, along with above details, please post if you can ping these -
```
ping -c4 192.168.1.1
ping -c4 8.8.8.8
```

But **IF** I successfully scared you enough with my dangerously confusing questions, and you now consider it better to try a fresh installation, I think you should try a Live session first. If the problem persists on the live session (it will, if the problem is in your router configuration), it will persist on the fresh install as well.

---

### Post by richiemcc on 2014-03-16
Hi Varun,

Thank you for responding.

Just to explain the setup, I have 3 desktop computers in the house (All run Ubuntu 13.10, and one I dual boot with Windows 8.1) that connect via Ethernet over Power adapters, (3 x iphones, 2 ipads & 1 Nexus 7 that connect via wireless)  

The ethernet over power adapters enable you to network your internet connection via power cables rather than using Cat 5/6 cable. Ubuntu effectively sees these connections as a normal 'wired' connection.  

[http://www.jw.com.au/netcomm-np204-powerline-with-ac-pass-through-p-2159](http://www.jw.com.au/netcomm-np204-powerline-with-ac-pass-through-p-2159)  This link shows the type that I use. There is one plug on the modem/router and a plug for each other desktop in the house. These plugs encrypt the internet connection over the household power lines.

I only have the issue on one PC which is the one that dual boots Windows 8.1.  The other two PC's can connect directly to the internet without having to go via the VPN.  I use the VPN to encrypt my internet connection when I am doing sensitive stuff such as online banking or to bypass geo-blocked web sites.  

The strange part is that if I boot up Windows 8.1 on the same machine it can connect to the internet without any issues as do the other desktops, so for that reason I don't believe it is a setting on the router.

I am responding while at work at the moment, but will try to ping the ip addresses when I get home tonight.  I will update this post once I have done that.

I hope that better explains my set up in the interim.

Thanks again for taking the time to help out.

Cheers
Richard.

---

### Post by richiemcc on 2014-03-17
Hi Varun,

I was able to ping both sites with or without the VPN.

I have copied the output below:

VPN on

```
richard@study-desktop:~$ ping -c4 192.168.1.1PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=4.83 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=3.97 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=4.82 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=3.41 ms


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 3.415/4.262/4.839/0.603 ms
richard@study-desktop:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=59 time=65.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=59 time=362 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=59 time=61.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=59 time=59.6 ms


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 59.615/137.089/362.412/130.107 ms
richard@study-desktop:~$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.40 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=3.34 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.41 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=4.09 ms

With VPN off


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 3.344/3.564/4.095/0.315 ms
richard@study-desktop:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=53.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=52.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=52 time=55.8 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=52 time=56.2 ms


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 52.114/54.448/56.292/1.722 ms



```

I am not sure if this helps answer the issue, but if it is all too difficult then I will do the clean install. I have gotten to the point though where it would be nice to know what the issue actually is. Let me know if we can't progress the issue and I will close the thread.

Cheers
Richard.

---

### Post by varunendra on 2014-03-18
Sorry for a late reply, I got too busy with celebrations of "Holi" - one of the two biggest Hindu festivals.

I think we have a pretty good hope with this here -
> **richiemcc said:**
> I was **able to ping** both sites with or **without the VPN**.

I overlooked the fact earlier that your nm-tool output didn't show any DNS. With the above confirmation, it now looks like a simple DNS issue to me (the "Power adaptor" thing is still absolutely new to me, quite interesting too, but I don't think it matters here).

Are you getting the IP address (192.168.1.8) automatically by DHCP or have you manually configured it?

Since your other computers are working correctly with the same router, I am assuming here that either you have assigned the IP addresses manually, or there is some problem in the Ubuntu installation in question why it is not getting DNS address automatically (by DHCP).

Please try this -

In Network Manager settings for eth0, select "***Method***" under IPv6 to "**Ignore**" and under "IPv4" to either "**Manual**" *(if you are manually assigning IP addresses)* or "**Automatic (DHCP) address only**" *(if getting IP automatically from DHCP)*. Then, in the "DNS servers" field, enter these values -

**8.8.8.8, 8.8.4.4**

These are Google's DNS servers, you can also use other tested ones if you like.

Save and close the settings and with only eth0 connection, try -
```
ping -c4 google.com
```
Can you get a ping reply now? If yes, can you browse internet without VPN now?

---


---
title: "special steps in replacing network card?"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2014-06-14
After a MAJOR lightning strike that took out my entire network, I am attempting to replace a blown network card in my server. The system is running 12.04 LTS and the old card was a DLINK DFE-530TX+ (I think that's the model number). I have tried to replace this with a handful of different cards, including a Kingston, a Belkin, a 3com an IDE DLINK and a couple of generic cards. Each time, the system waits 60+ seconds for network configuration and then "continues without full network support". iftop returns:

error getting hardware address for interface: eth0
ioctl (SIOCGIFHWADDR): no such device
pcap_open_live(eth0): eth0: you don't have permission to capture on that device
(socket: operation not permitted)

Is there anything that I need to do to make the system recognize the new card? I would have thought I could just plug the new card in and it work, but I guess not?

---

### Post by chili555 on 2014-06-14
I suspect that the 530TX was mapped to eth0 in /etc/udev/rules.d/70-persistent-net.rules. The next card gets assigned eth1. Your /etc/network/interfaces tries to start eth0 automatically, but it no longer exists. It may be as simple as:```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```Reboot.

If it doesn't work correctly, see what the interface is:```
ifconfig
```...and be sure it is the same as called for in /etc/network/interfaces.

I am just a tiny bit concerned that, since you've tried multiple cards, the latest may map to eth9 or some such!

---

### Post by rebeltaz on 2014-06-16
I don't know why I gave the output of iftop... I MEANT to quote ifconfig. Long day! But... removing that file did allow the interface to be properly mapped to eth0... BUT... now I am getting:

Not starting internet superserver: no services enabled

-and-

[warn] NameVirtualHost *:443 has no VirtualHosts
[warn] NameVirtualHost *:80 has no VirtualHosts


I found a post here - [https://www.linuxquestions.org/questions/debian-26/internet-superserver-not-starting-debian-etch-569117/](https://www.linuxquestions.org/questions/debian-26/internet-superserver-not-starting-debian-etch-569117/) - that says to use:
```
update-rc.d -f openbsd-inetd remove
```

but before I did that, I wanted to understand WHY and WHAT that does and WHY I (might) need to do that anyway... Thanks so far :)

---

### Post by rebeltaz on 2014-06-16
I don't know why I gave the output of iftop... I MEANT to quote ifconfig. Long day! But... removing that file did allow the interface to be properly mapped to eth0... BUT... now I am getting:

Not starting internet superserver: no services enabled

-and-

[warn] NameVirtualHost *:443 has no VirtualHosts
[warn] NameVirtualHost *:80 has no VirtualHosts


I found a post here - [https://www.linuxquestions.org/questions/debian-26/internet-superserver-not-starting-debian-etch-569117/](https://www.linuxquestions.org/questions/debian-26/internet-superserver-not-starting-debian-etch-569117/) - that says to use:
```
update-rc.d -f openbsd-inetd remove
```

but before I did that, I wanted to understand WHY and WHAT that does and WHY I (might) need to do that anyway... Thanks so far :)


-edit-
I am able to see the server from my local network, by the way, I just cannot access the sites it hosts and the server doesn't see the internet (e.g. apt-get cannot connect).

---

### Post by chili555 on 2014-06-16
May we see:```
ifconfig
cat /etc/network/interfaces
ping -c3 192.168.1.1  [COLOR="#FF0000"]<--or whatever the gateway address is[/COLOR]
```> update-rc.d -f openbsd-inetd remove
but before I did that, I wanted to understand WHY and WHAT that does and WHY I (might) need to do that anyway... Thanks so farI have never seen this before. I'd be a bit skeptical of an answer given in 2007 which is 1492 in Linux years. 

Let's see what we can do before we throw random commands at it.

---

### Post by rebeltaz on 2014-06-16
> **chili555 said:**
> May we see:```
ifconfig
cat /etc/network/interfaces
ping -c3 192.168.1.1  [COLOR="#FF0000"]<--or whatever the gateway address is[/COLOR]
```I have never seen this before. I'd be a bit skeptical of an answer given in 2007 which is 1492 in Linux years. 

Let's see what we can do before we throw random commands at it.

Bear with me, because I am having to hand type all of this since I cannot access the computer to copy-paste:

```

ifconfig

eth0   Link encap:Ethernet   HWaddr 00:48:54:8f:25:e1
          inet addr:192.168.1.13   Bcast:192.168.1.255   Mask:255.255.255.0
          UP BROADCAST MULTICAST   MTU:1500   Metric:1
          RX packets:0   errors:0   dropped:0   overruns:0   frame:0
          TX packets:0   errors:0   dropped:0   overruns:0   frame:0
          collisions:0   txqueelen:1000
          RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

lo       Linkencap:Local Loopback
         inet addr:127.0.0.1   Mask:255.0.0.0
         inet6 addr:   ::1/128   Scope:Host
         UP LOOPBACK RUNNING   MTU:65536   Metric:1
         RX packets:1272   errors:0   dropped:0   overruns:0   frame:0
         TX packets:1272   errors:0   dropped:0   overruns:0   carrier:0
         collisions:0   txqueuelen:0
         RX bytes:127684 (127.6 KB)   TX bytes:127684 (127.6 KB)

```

```

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 192.168.1.13
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      gateway 192.168.1.254
      dns-nameservers 205.152.37.23 205.152.150.23

```

and since I didn't know if you wanted ping from that server or from another TO that computer, here is both...

ping FROM that computer:
```

PING 192.168.1.13 (192.168.1.13) 56(85) bytes of data.
64 bytes from 192.168.1.13: icmp_req=1 ttl=64 time=0.260 ms
64 bytes from 192.168.1.13: icmp_req=2 ttl=64 time=0.191 ms
64 bytes from 192.168.1.13: icmp_req=3 ttl=64 time=0.191 ms

--- 192.168.1.13 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2012ms
rtt min/avg/max/mdev = 0.191/0.214/0.260/0.032 ms

```

ping TO that computer:
```

PING 192.168.1.13 (192.168.1.13) 56(84) bytes of data.
64 bytes from 192.168.1.13: icmp_seq=1 ttl=64 time=2.01 ms
64 bytes from 192.168.1.13: icmp_seq=2 ttl=64 time=0.397 ms
64 bytes from 192.168.1.13: icmp_seq=3 ttl=64 time=0.414 ms

--- 192.168.1.13 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.397/0.940/2.011/0.757 ms

```

---

### Post by chili555 on 2014-06-16
> PING 192.168.1.13 (192.168.1.13) 56(84) bytes of data.
64 bytes from 192.168.1.13: icmp_seq=1 ttl=64 time=2.01 msThat's the equivalent of pinging yourself, isn't it? What I wanted was:> ping -c3 192.168.1.1  <--or whatever the [COLOR="#FF0000"]gateway[/COLOR] address isSo, what does this tell us?```
ping -c3 192.168.1.254
```You don't have to type it all out, just tell us if it gets a ping return. Then:```
ping -c3 205.152.37.23 
ping -c3 www.google.com
```Again, just tell us if it gets a ping return.

---

### Post by rebeltaz on 2014-06-16
D'oh! I'm sorry... I didn't see the GATEWAY declaration. Yeah, that does make more sense. 

I got it working... for some reason, the signal wasn't getting through my network switch. I appreciate the help with everything, though, especially the original problem :)

---

### Post by rebeltaz on 2014-06-16
I take that back... crap... for some reason, I can access it from ONE computer on my network but not any others. Can you tell me if you can access the site in my signature? 

In answer to your questions, ping results are intermittent. I am going to move the server back to the router I had it on before and I'll give you the results of the ping test tomorrow.

---

### Post by chili555 on 2014-06-17
> **rebeltaz said:**
> I take that back... crap... for some reason, I can access it from ONE computer on my network but not any others. Can you tell me if you can access the site in my signature? 

In answer to your questions, ping results are intermittent. I am going to move the server back to the router I had it on before and I'll give you the results of the ping test tomorrow.Here is what I get.[ATTACH=CONFIG]254014[/ATTACH]

---

### Post by rebeltaz on 2014-06-20
I'm sorry. I've been busy at work this week. I will try to get that information to you tomorrow.

---

### Post by rebeltaz on 2014-07-25
I am sorry this has taken so long... since I first asked this the server motherboard failed so I had to build a new system. I put the old harddrive in the new system and I still have the same problem.

To answer your original questions, I can ping the gateway (192.168.1.254) just fine and get 100% responses. I tried pining google and ONE time I get a response, but with -c3 I got a 66% failure rate. After that it gives a 100% failure rate some times, some times it give 100% success. I have even tried connecting the same ethernet cable that is connected to the computer I am on now (which is 100% up) to be sure that isn't the problem. I have tried several different network cards...

I booted in "recovery mode" and attempted to run apt-get upgrade. For some of the time, I get 666kB/s speeds, then it'll just stop for minutes at a time before picking back up. 

network/interfaces is:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address    192.168.1.13
     network    192.168.1.0
     netmask    255.255.255.0
     broadcast    192.168.1.255
     gateway    192.168.1.254
     dns-nameservers   205.152.37.23    205.152.132.23

```


The DNS servers are the same ones noted by the router's main page. 


----

I allowed apt-get to upgrade (which took forever with the slowdowns) and let the server boot normally. It kept hanging up with this line:

LibClamAV Warning: Virus database is older than 7 days!

Since I don't use mail on this server anyway, I booted back to recovery, uninstalled clamav and rebooted. It booted all the way to a login prompt, but it did show this first:

Not starting internet superserver - no services available

I tried ping again and, like before, pinging the gateway was fine (well... it did fail completely the first time) but google was hit and miss. 

I accessed the website ([www.RobotsAndComputers.com](www.RobotsAndComputers.com)) and it seems to pull it up, from one computer within my local network, but nowhere else. I think that may be because I have that address directed to the local IP address in this computers hosts file. Something obviously isn't right.

---

### Post by chili555 on 2014-07-26
And I am sorry for the delay in my reply. I was away from home for a couple of days.

Yours is a tricky case. It could be the network configuration or it could be the hardware/driver combination. I suggest we try to narrow down the possibilities. First, I find your /etc/network/interfaces a bit busy. Let's strip down to the essentials and see if there is any improvement. Please edit your file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address    192.168.1.13
     netmask    255.255.255.0
     gateway    192.168.1.254
     dns-nameservers 205.152.37.23 205.152.132.23
```In addition to the other changes, please tighten up the spacing in 'dns-nameservers' to just one space between each element. I am not sure it is critical, but let's try everything we can think of. Restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
ping -c3 www.google.com
```

Next, let's address the hardware and driver. What is the card that's currently installed?```
lspci -nn | grep 0200
```

---

### Post by rebeltaz on 2014-07-26
I have nothing if not interesting cases :)

The spaces in my interfaces file actually were single spaced... It didn't look like it here, so I added a couple more space here. Sorry for the misunderstanding. I did edit out the network and broadcast lines, restarted the interface and pinged google. The first run gave 100% success. The second run gave 66% failure and the third run gave "unknown host www.google.com".

Output of the lspci is:

```

02:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:0d.0 Ethernet controller [0200]: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem [14e4:4211]

```

On the plus side.. with the host file on this computer pointing to the server IP, at least I can ssh in from this computer. Makes copying output much easier! :)

---

### Post by chili555 on 2014-07-26
This gets more interesting by the moment! Is it the HomePNA that maps to eth0 or the Realtek 8139? If it is the HPNA, I may retire from Ubuntu and take up something easy like time travel. Buy GOOG at 80.

May we see:```
cat /var/log/syslog | grep -e 8139 -e eth0 | tail -n20
```

---

### Post by rebeltaz on 2014-07-26
Holy wow! That's a lot of text!

```

derek@shelbyserver:~$ cat /var/log/syslog | grep -e 8139 -e eth0 | tail -n20
Jul 26 16:17:57 shelbyserver kernel: [84214.404678] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=19969 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 16:18:04 shelbyserver kernel: [84221.401580] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=8.8.8.8 DST=192.168.1.13 LEN=195 TOS=0x00 PREC=0x00 TTL=42 ID=50977 PROTO=UDP SPT=53 DPT=39162 LEN=175 
Jul 26 16:18:12 shelbyserver kernel: [84229.889315] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=56 TOS=0x00 PREC=0x00 TTL=255 ID=19979 PROTO=ICMP TYPE=3 CODE=0 [SRC=192.168.1.13 DST=23.72.224.127 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=37182 DF PROTO=TCP INCOMPLETE [8 bytes] ] 
Jul 26 16:18:13 shelbyserver kernel: [84230.560547] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=183 TOS=0x00 PREC=0x00 TTL=255 ID=19983 PROTO=UDP SPT=53 DPT=52632 LEN=163 
Jul 26 16:18:14 shelbyserver kernel: [84231.400723] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=202 TOS=0x00 PREC=0x00 TTL=255 ID=19985 PROTO=UDP SPT=53 DPT=56548 LEN=182 
Jul 26 16:18:16 shelbyserver kernel: [84233.409459] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=19986 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 16:18:17 shelbyserver kernel: [84234.296428] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=8.8.8.8 DST=192.168.1.13 LEN=148 TOS=0x00 PREC=0x00 TTL=42 ID=38843 PROTO=UDP SPT=53 DPT=47210 LEN=128 
Jul 26 16:18:17 shelbyserver kernel: [84234.839912] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=202 TOS=0x00 PREC=0x00 TTL=255 ID=19992 PROTO=UDP SPT=53 DPT=59097 LEN=182 
Jul 26 16:18:30 shelbyserver kernel: [84247.410545] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=20009 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 16:18:37 shelbyserver kernel: [84254.410324] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=20013 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 16:18:40 shelbyserver kernel: [84257.342374] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=202 TOS=0x00 PREC=0x00 TTL=255 ID=20015 PROTO=UDP SPT=53 DPT=59097 LEN=182 
Jul 26 16:18:51 shelbyserver kernel: [84268.411845] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=20018 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 17:29:47 shelbyserver kernel: [88524.931304] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=212 TOS=0x00 PREC=0x00 TTL=255 ID=24887 PROTO=ICMP TYPE=0 CODE=0 ID=0 SEQ=0 
Jul 26 18:27:15 shelbyserver kernel: [91972.142457] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=83 TOS=0x00 PREC=0x00 TTL=255 ID=30494 PROTO=UDP SPT=53 DPT=43341 LEN=63 
Jul 26 18:27:17 shelbyserver kernel: [91974.957156] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=8.8.8.8 DST=192.168.1.13 LEN=83 TOS=0x00 PREC=0x00 TTL=42 ID=17960 PROTO=UDP SPT=53 DPT=40369 LEN=63 
Jul 26 18:27:20 shelbyserver kernel: [91977.767779] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=83 TOS=0x00 PREC=0x00 TTL=255 ID=30501 PROTO=UDP SPT=53 DPT=43341 LEN=63 
Jul 26 18:48:15 shelbyserver kernel: [93232.568104] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=183 TOS=0x00 PREC=0x00 TTL=255 ID=32719 PROTO=UDP SPT=53 DPT=39296 LEN=163 
Jul 26 18:48:18 shelbyserver kernel: [93235.397090] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=8.8.8.8 DST=192.168.1.13 LEN=148 TOS=0x00 PREC=0x00 TTL=42 ID=34405 PROTO=UDP SPT=53 DPT=46228 LEN=128 
Jul 26 18:48:22 shelbyserver kernel: [93239.443036] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=192.168.1.254 DST=192.168.1.13 LEN=183 TOS=0x00 PREC=0x00 TTL=255 ID=32726 PROTO=UDP SPT=53 DPT=39296 LEN=163 
Jul 26 18:48:28 shelbyserver kernel: [93245.074607] [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 SRC=8.8.8.8 DST=192.168.1.13 LEN=148 TOS=0x00 PREC=0x00 TTL=42 ID=34405 PROTO=UDP SPT=53 DPT=46228 LEN=128 

```

---

### Post by chili555 on 2014-07-26
It may be a misconfiguration in the firewall. Let's turn it off for a moment and see what changes, if anything:```
sudo ufw disable
ping -c3 192.168.1.254
ping -c3 www.google.com
```We wonder where 8.8.8.8 is coming from:> [UFW BLOCK] IN=eth0 OUT= MAC=00:10:b5:10:e4:c6:00:26:42:7e:e7:b0:08:00 [COLOR="#FF0000"]SRC=8.8.8.8 [/COLOR]DST=192.168.1.13 LEN=148 TOS=0x00 PREC=0x00 TTL=42 ID=34405 PROTO=UDP SPT=53 DPT=46228 LEN=128 That's Google's DNS nameserver, however, you've set other than 8.8.8.8 in interfaces.

---

### Post by rebeltaz on 2014-07-26
I ran ufw status verbose before disabling it, just to see what was there and this is what it shows:

```

derek@shelbyserver:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         ALLOW IN    192.168.1.5
22                         ALLOW IN    192.168.1.15
80                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
8888                       ALLOW IN    192.168.1.5
21                         ALLOW IN    192.168.1.5
21                         ALLOW IN    192.168.1.15

```

I did put in the other entries, but I do not remember adding, nor is there any reason I would have added, the entry for google. 


After disabling ufw:

```

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms


--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 36.414/36.665/36.891/0.295 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.338/0.338/0.338/0.000 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 32.883/33.447/34.483/0.762 ms

```

The site is still accessable from this computer. but no others.

---

### Post by chili555 on 2014-07-26
Verrrry interesting. Notice your pings to Google went through and at reasonably fast speeds. Let's keep plugging away at this.> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address    [COLOR="#FF0000"]192.168.1.13[/COLOR]
     netmask    255.255.255.0
     gateway    192.168.1.254
     dns-nameservers 205.152.37.23 205.152.132.23Is this address outside the DHCP range used in the router or are you using reservations? This is sometimes but not always an issue because of the chance for collisions.

Are you quite certain of the gateway address 192.168.1.254? Is it the same on several other computers in your network?

What do you get for route and IP address if you change to DHCP and reboot?```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```And then, after reboot:```
ifconfig
route -n
```

---

### Post by rebeltaz on 2014-07-26
Hmmm... that might actually be the problem. Most of my IP assignments are all over the board, so I never really set any to be "outside" the router's DHCP range. If the HWaddr output of the ifconfig command is the MAC addresss of the server, then that doesn't match the MAC address of the device mapped to the .13 IP address:

```

derek@shelbyserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:b5:10:e4:c6


http://192.168.1.254:8080/StatTool
LAN Host Discovery Table:
Host-Name        IP               MAC               Interface State
NP-J0A17V014713  192.168.1.13     00-0d-4b-93-c6-68 Eth 100BT online

```

I'm not sure right off hand what that device actually is. I need to go around, writing down the IP addresses of every 'net connected device and find out what that belongs to. I'll change the router's DHCP server to a smaller pool. 

To answer your questions, yes... .254 is the gateway used for all other devices, including the laptop I am on now. I do know that some devices don't acquire the correct gateway/DNS servers from the router for some reason, and the only way to get those working is to manually enter the IP, netmask, gateway and DNS addresses - but that's another issue I'm not really too concerned with right now. 

I'll have to go over to my shop to gain physical access to the server to access it once I change it back to DHCP so I may not be able to reply back until tomorrow, but I will let you know what happens.

---

### Post by rebeltaz on 2014-07-26
Ok... I found the conflict. It was with a Roku. After the lightning strike, I replaced the Roku before I rebuilt the server, and it just so happened that the Roku was assigned the .13 address that the server required. I narrowed the DHCP pool, had the Roku reassigned a new address within that pool and rebooted the server. Now there isn't a conflict in the IP addresses, but I still don't seem to be able to access the site from outside this computer. 

Do you still want me to try changing the server to DHCP?

```

derek@shelbyserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:b5:10:e4:c6  



http://192.168.1.254:8080/StatTool
LAN Host Discovery Table:
Host-Name        IP               MAC               Interface State
192.168.1.13     192.168.1.13     00-10-b5-10-e4-c6 Eth 100BT online

```

Ping result are perfect, so we're making headway :)

```

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.369/0.379/0.398/0.026 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.406/0.437/0.500/0.050 ms

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.368/0.450/0.607/0.113 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 36.885/37.453/37.812/0.436 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 36.537/36.843/37.168/0.257 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 36.575/36.817/36.972/0.173 ms

```

---

### Post by chili555 on 2014-07-27
I'd say we have made great progress. This computer connects to the world perfectly well and without any apparent issues. So do I now understand that the goal is for the world to be able to contact this computer? How? http? ssh? ftp? All of the above?

If so, this is an area beyond my limited expertise. I'd suggest you search the forum for the answer; I am certain that there are many similar threads. If, after a careful search, you find none, start a new thread that describes the issue in the title; something like: 'How to make my server accessible to the world.'

If I have misunderstood, please help me understand and we'll continue.

---

### Post by rebeltaz on 2014-07-27
Yeah... before all this I had it accessable via http, ftp and ssh. Since this has worked just fine before the lightning strike, I'm not sure how to search for help on that, so I will start a new thread. I truly appreciate all of your help, though! Thank you.

---


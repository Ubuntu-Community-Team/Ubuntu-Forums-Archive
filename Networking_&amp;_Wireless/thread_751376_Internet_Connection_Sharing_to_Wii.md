---
title: "Internet Connection Sharing to Wii"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by sbartz on 2008-04-10
Hi,
I am trying to use my laptop to share the internet with my Wii.
My internet connection is through my school which assigns an IP address based on mac address which is registered under my name.
eth0 is my ethernet card which connects to the internet. eth1 is my wireless card with which I want to connect to the wii so it can access the internet.
I have tried many different ways, but the masquerading does not seem to work. I assume the masquerading is through my laptop which puts it through on the laptop's ip and mac address.
Can anyone give me a surefire way to set this up?
My wireless card is Broadcom 4306 with ndiswrapper.
I have looked at the wiki docs and search on the forum with no luck.
Thanks for your time,
Steve

---

### Post by SpaceTeddy on 2008-04-10
first off, verify that you wii can talk to your laptop. That is the first step - make sure the basic connectivity bewteen the devices is given. Once that is done, enable ip_forwarding, hand out a dns-server and gateway to your wii and then go into masquerading the paket that flow through your ubuntu box.

i've written down the steps to do in this [thread]("http://ubuntuforums.org/showthread.php?t=713874")... If there are any further problems, just tell me which step fails and we can try to solve it together...

---

### Post by sbartz on 2008-04-12
I've done all the steps in your helpful tutorial. I redid them but they seemed to be a subset of the things I have already tried. Here's some info that may help:
```

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:B3:AE:4F
          inet addr:172.16.128.53  Bcast:172.16.135.255  Mask:255.255.248.0
          inet6 addr: fe80::20f:1fff:feb3:ae4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1573270 (1.5 MB)  TX bytes:329039 (321.3 KB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:90:96:C3:8D:01
          inet addr:10.8.16.1  Bcast:10.8.16.0  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fafee000-faff0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19217 (18.7 KB)  TX bytes:19217 (18.7 KB)

```

and my iwconfig
```

lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wii"
          Mode:Ad-Hoc  Frequency:2.452 GHz  Cell: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

I'm not quite sure how iptables directing works. If I want it to work properly i need to redirect all the traffic through eth0 as my laptop.

Thanks for your reply and help.

---

### Post by sbartz on 2008-04-12
I've discovered the problem. Wii won't do Ad-Hoc networking. ndiswrapper doesn't support master mode, so there is currently no way to do this.

---

### Post by superprash2003 on 2008-04-12
then the only option is to go for a wifi router

---


---
title: "Azureus/Ubuntu"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by auraithx on 2007-07-26
Okay I am trying to optimize my Azureus to work at full speed on my machine. 

I changed the port to 49153 and fowarded that on my router to my IP (192.168.1.106). However, when I did this..Azureus was still showing as "Firewall/NAT (TCP reachability problem" and when I did a firewall test on the port (49153) it said it was closed. 

So I have a look about google and found out that Ubuntu has a built in firewall, I download firestarter, and disable the firewall. Now my entire internet connection stops (can't even load google) and I'm forced to restart.

It's all working fine again but Azureus is still showing as "Firewalled" and all the trackers have me labeled as "Not Connectable"

> The tracker has determined that you are firewalled or NATed and cannot accept incoming connections.

This means that other peers in the swarm will be unable to connect to you, only you to them. Even worse, if two peers are both in this state they will not be able to connect at all. This has obviously a detrimental effect on the overall speed.

The way to solve the problem involves opening the ports used for incoming connections (the same range you defined in your client) on the firewall and/or configuring your NAT server to use a basic form of NAT for that range instead of NAPT (the actual process differs widely between different router models. Check your router documentation and/or support forum. You will also find lots of information on the subject at PortForward). 

Here are some things I often see asked for in other threads

```
glasgowm@glasgowm-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:20:1B:59:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
```
glasgowm@glasgowm-desktop:~$ sudo ethtool -i eth0
Password:
driver: e100
version: 3.5.17-k2-NAPI
firmware-version: N/A
bus-info: 0000:01:08.0

```
```
glasgowm@glasgowm-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

Here is someone who had the exact same problem 2 years ago on Ubuntu Warty. The fix is now outdated and does not work in Fiesty.
[http://ubuntuforums.org/showthread.php?t=4089](http://ubuntuforums.org/showthread.php?t=4089)

---

### Post by auraithx on 2007-07-26
Bump - here is a imagine that shows my IP (192.168.1.106), The port being forwarded on my router settings - and azureus telling me the port is closed.

[http://image.bayimg.com/gaeloaabj.jpg](http://image.bayimg.com/gaeloaabj.jpg)

Okay - Now I've actually opened the port on ubuntu using
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 49153 -j ACCEPT
```

Is there anyway to test to see if a port is open - so that I can see if the program I'm running is the problem.

---

### Post by auraithx on 2007-07-26
I changed the port to 50500 now and it's all working fine :D,

---


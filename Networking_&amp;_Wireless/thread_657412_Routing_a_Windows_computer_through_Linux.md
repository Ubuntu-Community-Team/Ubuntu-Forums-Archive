---
title: "Routing a Windows computer through Linux"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Ambush Commander on 2008-01-03
I'm an absolute newb when it comes to networking (thanks to a lot of fudging around with Network Manager's settings, my wireless connection works, and I don't exactly know why, but it works, so there.) So I've a got a little, non-essential project to get my hands dirty with networking with Linux. Trouble is, I don't know where to start. Here's the task:

I have a Windows Vista computer and a Ubuntu Linux computer in the same room. Currently, they are both wirelessly connected to a router, which connects to the Internet. I'd like to connect an ethernet cable between these two computers, and share files directly, rather than bounce them off the router. Also, my wireless card intermittently stops working on Windows, so it gives me another way to "get" to my Windows computer remotely (ssh to Linux, and then bounce over the ethernet to Windows).

I understand that this setup wouldn't work in reverse (Linux to Windows to Router to Internet), since Windows is not exactly router-material; however, Linux has the capabilities to do this. However, I don't know what I need to do: do I muck around with iptables, edit /etc/network/interfaces, set up firewall rules for Linux, etc. Can someone give me a list of steps (tutorial-ish) with key terms for each step so that I can research each step and figure my way around the tool? (Or, if you think you've got a better idea, I'm all ears)

Thank you!

---

### Post by solar george on 2008-01-03
Try installing firestarter,
```
sudo aptitude install firestarter
```
It has a simple gui to allow you to do this.

---

### Post by Ambush Commander on 2008-01-03
Thank you, this GUI looks very promising. However, I am having some problems:

When I tell the firewall to allow Internet Connection sharing, set the local device to eth0, and attempt to start the firewall, an error dialog comes up that says: "device eth0 is not ready." This problem has [appeared](http://ubuntuforums.org/showthread.php?t=76217) [before](http://ubuntuforums.org/showthread.php?t=203127), and it doesn't appear anyone found a satisfactory solution, so that quickly sinks Firestarter. However, has a firewall, it looks quite useful, so I'll be keeping it around.

Any other suggestions, or fixes for the above?

**Edit:** More information for the curious:

```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:C5:63:DA  
          inet6 addr: fe80::20b:dbff:fec5:63da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135261 (132.0 KB)  TX bytes:9767 (9.5 KB)
          Interrupt:19 
$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
$ sudo ifdown eth0
ifdown: interface eth0 not configured
```

Also, Windows sees Ubuntu and is marking the network as an "Unidentified network" with "Limited connectivity." Network Manager has eth0 with roaming mode enabled. Cycling through the other options doesn't seem to do anything.

---

### Post by solar george on 2008-01-04
Give the local device a static ip address using the network manager.

---

### Post by Ambush Commander on 2008-01-04
Following your directions, I opened Wired connection's properties from the Network Settings prompt, and set the following connection settings after disabling roaming mode:

Configuration: Static IP address
IP address: 192.168.0.255
Subnet mask: 255.255.255.0
Gateway address: 192.168.0.1

However, the firewall won't still gives the same error. Did I do your procedure incorrectly? Also, Network Manager didn't show any dialog saying "Configuring network settings" or something similar, which I have seen before when I changed other settings.

---

### Post by solar george on 2008-01-04
The ip address should be 192.168.0.1 (the last digit must not be 255) and therefore the same as the gateway address (your pc will be the gateway.

---

### Post by Ambush Commander on 2008-01-04
Still same problem. New configuration is:

Configuration: Static IP address
IP address: 192.168.0.1
Subnet mask: 255.255.255.0
Gateway address: 192.168.0.1

My router on the wireless network is located on 192.168.0.1

---

### Post by solar george on 2008-01-05
Choose a different private address range for your local device.
maybe,
Configuration: Static IP address
IP address: 192.168.1.1
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1

---


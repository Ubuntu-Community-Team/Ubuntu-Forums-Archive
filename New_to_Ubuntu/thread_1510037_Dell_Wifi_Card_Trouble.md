---
title: "Dell Wifi Card Trouble"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Loveablesurfer on 2010-06-15
Hi there!

I've just installed ubuntu 10.04 on my dell vostros 1500. Everything seems to work accept wifi. Initially it wouldn't work at all, after downloading all the updates ubuntu let me then access "restricted drivers". Since installing these, ubuntu now picks up and  recognises my home wifi, it accepts the password and tells me I'm connected. However when I log onto FIrefox, it acts like there is no internet connection at all. Firefox works with the ethernnet connection so I don't think Firefox is the issue.

Any help would be greatly appreciated.

---

### Post by Peter09 on 2010-06-15
HI,
can you post the output of the commands. Note do these commands without a hardwired connection and if possible with a working wireless connection.
 
```
ifconfig
```
and
```
lshw -C network
```
 
 
 
Also do the command
 
```
route
```

---

### Post by Loveablesurfer on 2010-06-15
No prob, I'll do it tonight when I get home from work.

Cheers

---

### Post by Loveablesurfer on 2010-06-15
adrian@adrian-laptop:~$ ipconfig 
 No command 'ipconfig' found, did you mean: 
  Command 'tpconfig' from package 'tpconfig' (universe) 
  Command 'iwconfig' from package 'wireless-tools' (main) 
  Command 'ifconfig' from package 'net-tools' (main) 
 ipconfig: command not found 
 

 adrian@adrian-laptop:~$ lshw -C network 
 WARNING: you should run this program as super-user. 
   *-network                
        description: Wireless interface 
        product: BCM4312 802.11b/g 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:0c:00.0 
        logical name: eth1 
        version: 01 
        serial: 00:1f:e1:1b:95:8f 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11 
        resources: irq:17 memory:fe8fc000-fe8fffff 
   *-network 
        description: Ethernet interface 
        product: BCM4401-B0 100Base-TX 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: eth0 
        version: 02 
        serial: 00:1d:09:c9:3e:07 
        width: 32 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical 
        configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes 
        resources: irq:17 memory:fe5fe000-fe5fffff 
 

 adrian@adrian-laptop:~$ route 
 Kernel IP routing table 
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
 10.42.43.0      *               255.255.255.0   U     2      0        0 eth1 
 link-local      *               255.255.0.0     U     1000   0        0 eth1 
 adrian@adrian-laptop:~$ ^C 
 adrian@adrian-laptop:~$

---

### Post by Peter09 on 2010-06-15
You miss-typed - the command is

```
ifconfig
```

do you know what ip-schema you are using on your network - 192.168.0... or 10.... etc

---

### Post by Peter09 on 2010-06-15
From what I can see your router does not appear as a gateway, are you using DHCP or a static IP.

What happens with the command

```
ping www.google.com
```

---

### Post by Loveablesurfer on 2010-06-15
adrian@adrian-laptop:~$ ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:1d:09:c9:3e:07   
           inet6 addr: fe80::21d:9ff:fec9:3e07/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:2128 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1706 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:2247492 (2.2 MB)  TX bytes:272695 (272.6 KB) 
           Interrupt:17  
  
 eth1      Link encap:Ethernet  HWaddr 00:1f:e1:1b:95:8f   
           inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
           inet6 addr: fe80::21f:e1ff:fe1b:958f/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:784 
           TX packets:11 errors:6 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:2909 (2.9 KB) 
           Interrupt:17 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:40 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:40 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:3024 (3.0 KB)  TX bytes:3024 (3.0 KB) 
  
 adrian@adrian-laptop:~$ ping [www.google.com](www.google.com) 
 ping: unknown host [www.google.com](www.google.com) 



Sorry I don't know how to answer your other questions.  Could you explain a bit more?


Thank you

---

### Post by the.scarecrow on 2010-06-15
This could be a DNS problem that exists with some WiFi routers (mine included). Try this

1 Click on the WiFi indicator and disconnect from it.
2 Goto System>Preferences>Network Connections then Wireless Tab
3 Select your WiFi and click Edit
4 Click Wireless Security and enter your Wifi password etc.
5 Click IPv4 Settings and select Automatic (DHCP) addresses only
6 Enter in the box DNS Servers: 8.8.8.8 8.8.4.4
7 Make sure the box Connect Automatically is checked
8 Click Apply button, then Close
9 Click on the WiFi indicator and connect to it.

Then see if you can browse after re-starting Firefox.

If this doesn't work then just put step 5 back to what it was.

This method bypasses your ISP's DNS and connects to Google's DNS service. If you looked deeper you would probably find that your router admin IP address is being picked up as the DNS server.

I hope this helps you out and welcome to Ubuntu.

---

### Post by Loveablesurfer on 2010-06-15
It wouldnt let ,me apply after i put in 8.8.8.8.8.8.4.4

However i noticed the wifi network was listed twice in the Network Connections box. After deleting the one that was used the longest ago, the other one suddenly worked! Which is a good job because my ethernet connection has been randomly missing half of the time tonight. Sometimes when i boot up it isn't there. Plugging it out and in again doesn't seem to affect it. Any ideas why it has suddenly gone missing? I haven't changed anything in the wired section of Network Connections.

---

### Post by bkratz on 2010-06-15
> **Loveablesurfer said:**
> It wouldnt let ,me apply after i put in 8.8.8.8.8.8.4.4

However i noticed the wifi network was listed twice in the Network Connections box. After deleting the one that was used the longest ago, the other one suddenly worked! Which is a good job because my ethernet connection has been randomly missing half of the time tonight. Sometimes when i boot up it isn't there. Plugging it out and in again doesn't seem to affect it. Any ideas why it has suddenly gone missing? I haven't changed anything in the wired section of Network Connections.

I don't believe he/she wanted you to put in that whole string---
8.8.8.8.8.8.4.4:  Looking closely there were actually two given, the first ending where there was no decimal.


(sorry-just finally read the whole response--shame.

---

### Post by the.scarecrow on 2010-06-15
you must enter exactly what I showed to be valid

8.8.8.8 8.8.4.4
that is 8.8.8.8<space>8.8.4.4

pleased to see you are making progress though

---

### Post by Loveablesurfer on 2010-06-16
Thanks for all your help!

---


---
title: "NetworkManager Drops Connections"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by wOOge on 2007-09-24
Hey all - 

**Problem:**
Large downloads and internet streams are stopped/dropped after a short/random amount of time.

**Setup:**
Firewall Ubuntu (7.04) - Shoreline - running DHCP Client on Cable Modem - Acting as home network DHCP Server

**Scenario:**
I try connecting to an internet radio stream, or try download a large file (20+MB) on one of the  computers inside my network (behind the Ubuntu FW) - after some time the download dies off - then internet stream dies and attempts to buffer endlessly.

I can download the file and stream just fine from the firewall, but not from any machine on the inside of my network. So I checked the logs and all I see is NM going down due to some DCHP client unhappiness right after some "martians"???
This causes a hiccup in my net connection, then it drops everything.

I killed the NetworkManager daemon, and things are better, but downloads still die after a few megs - I have to constantly resume or restart downloads.
Below is a dump of my syslog at the point the connection drops (this happens often in the log files).

Is this a bug in NetworkManager?
Also, any help on how I could go about fixing this permanently?


```

Sep 24 11:46:18 hive NetworkManager: <information>^IDevice 'eth0' DHCP transaction took too long (>99s), stopping it. 
Sep 24 11:46:18 hive dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 23745
Sep 24 11:46:18 hive dhclient: killed old client process, removed PID file
Sep 24 11:46:18 hive dhclient: DHCPRELEASE on eth0 to AAA.AAA.AAA.AAA port 67
Sep 24 11:46:18 hive kernel: [228535.520000] printk: 23 messages suppressed.
Sep 24 11:46:18 hive kernel: [228535.520000] martian source 192.168.0.11 from 201.66.207.141, on dev eth0
Sep 24 11:46:18 hive kernel: [228535.520000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:18 hive kernel: [228535.580000] martian source 192.168.0.11 from 60.234.214.221, on dev eth0
Sep 24 11:46:18 hive kernel: [228535.580000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:18 hive kernel: [228535.600000] martian source 192.168.0.11 from 83.249.224.147, on dev eth0
Sep 24 11:46:18 hive kernel: [228535.600000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:18 hive kernel: [228535.730000] martian source 192.168.0.11 from 84.49.208.82, on dev eth0
Sep 24 11:46:18 hive kernel: [228535.730000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive kernel: [228535.910000] martian source 192.168.0.11 from 206.251.226.70, on dev eth0
Sep 24 11:46:19 hive kernel: [228535.910000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive kernel: [228536.260000] martian source 192.168.0.11 from 84.212.137.65, on dev eth0
Sep 24 11:46:19 hive kernel: [228536.260000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive kernel: [228536.280000] martian source 192.168.0.11 from 89.179.15.197, on dev eth0
Sep 24 11:46:19 hive kernel: [228536.280000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive kernel: [228536.390000] martian source 192.168.0.11 from 60.242.148.195, on dev eth0
Sep 24 11:46:19 hive kernel: [228536.390000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 24 11:46:19 hive NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Sep 24 11:46:19 hive NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 24 11:46:19 hive NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) failed. 
Sep 24 11:46:19 hive NetworkManager: <information>^IDeactivating device eth0. 
Sep 24 11:46:19 hive NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Sep 24 11:46:19 hive dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep 24 11:46:19 hive NetworkManager: <information>^IWill activate connection 'eth0'. 
Sep 24 11:46:19 hive NetworkManager: <information>^IDevice eth0 activation scheduled... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) started... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 24 11:46:19 hive NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 24 11:46:19 hive kernel: [228536.760000] martian source 192.168.0.11 from 60.234.214.221, on dev eth0
Sep 24 11:46:19 hive kernel: [228536.760000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:19 hive kernel: [228536.800000] martian source 192.168.0.11 from 60.234.214.221, on dev eth0
Sep 24 11:46:19 hive kernel: [228536.800000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:20 hive NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Sep 24 11:46:20 hive dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 24 11:46:20 hive NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 24 11:46:20 hive NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 24 11:46:24 hive kernel: [228540.980000] printk: 26 messages suppressed.
Sep 24 11:46:24 hive kernel: [228540.980000] martian source 192.168.0.11 from 189.19.210.189, on dev eth0
Sep 24 11:46:24 hive kernel: [228540.980000] ll header: 00:a0:cc:e2:05:8e:00:13:5f:07:9a:4f:08:00
Sep 24 11:46:25 hive dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep 24 11:46:25 hive dhclient: DHCPOFFER from 10.103.32.1
Sep 24 11:46:25 hive dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 24 11:46:25 hive dhclient: DHCPACK from 10.103.32.1
Sep 24 11:46:25 hive dhclient: bound to BBB.BBB.BBB.BB -- renewal in 1520 seconds.
```

There are two IP's in this log dump:
BBB.BBB.BBB.BBB - Is my Ubuntu firewall
192.168.10.110 - is the computer behind the FW
AAA.AAA.AAA.AAA - I have no idea who this is...

Thanks for any help anyone can provide.

---


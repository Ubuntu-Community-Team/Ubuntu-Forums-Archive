---
title: "Slow upload speed"
date: 2020-09-02
forum: Networking &amp; Wireless
---

### Post by satimis on 2020-09-02
Hi all,

I'm subscribing FTTH 500G up/down speeds.

Network connection:-
Wired connection:
FTTH -> ONT --> Gigabit WiFi Router -> Ubuntu 18.04 PC

On Ubuntu 18.04 PC
$ speedtest-cli --share```

Retrieving speedtest.net configuration...
Testing from Netvigator (42.98.86.7)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by STC (Hong Kong) [3.91 km]: 2.314 ms
Testing download speed..........................................................
......................
Download: 451.20 Mbit/s
Testing upload speed............................................................
..........................................
Upload: 4.15 Mbit/s
Share results: http://www.speedtest.net/result/10012825913.png

```

The upload speed is very slow.

But on Samsung S9Plus Notepad via WiFi
Running SpeedTest Master-Lite
```

Ping 3
Download Mbps 326
Upload Mbps 332

```
Download and Upload speed are almost equal.

It seems that there should be something wrong on Ubuntu 18.04 PC ?

On Terminal
$ sudo dmidecode -t 2```

# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.
# SMBIOS implementations newer than version 3.1.1 are not
# fully supported by this version of dmidecode.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: PRIME X570-P
        Version: Rev X.0x
        Serial Number: 190753869002923
        Asset Tag: Default string
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Default string
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

```

ASUSTeK PRIME X570-P Motherboard Specification
[https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/specifications/](https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/specifications/)
Realtek RTL8111H Gigabit NIC

Kindly advise how to sort out the problem?

Thanks in advance

Regards

---

### Post by TheFu on 2020-09-02
A few crazy ideas[LIST]
[*]Govt blocking because it sees "linux"?
[*]Realtek NIC? Intel NICs have lower overhead.
[/LIST]

But those wifi speeds clearly say it is the cable plug in the router to the OS as a problem.

Really, just simplify and retest.  Isolate different hardware, eliminate any problem hardware.  It could be a bad switch port.  Are LAN only transfers fast - in both directions?
Simplify and retest.

---

### Post by satimis on 2020-09-02
> **TheFu said:**
>  -snip-

But those wifi speeds clearly say it is the cable plug in the router to the OS as a problem.
Sorry, I don't follow this advice

> 
Isolate different hardware, eliminate any problem hardware.  It could be a bad switch port.  Are LAN only transfers fast - in both directions?

When I tested the speeds on Samsung Notepad S9Plus, Ubuntu 18.04 PC was not running.

Also when I tested the speeds on Ubuntu 18.04 PC, Samsung Notepad S9Plus was NOT on.

Regards

---

### Post by TheFu on 2020-09-02
Does the samsung use the same ethernet cable as the ubuntu machine?
All we know is that the connectivity from the samsung out works better, but we haven't ruled out the router ethernet port, the cable, the NIC, the Ubuntu computer.  We need to rule out the simple stuff first.  Jumping to conclusions before doing that is not responsible troubleshooting.  Check the easy stuff first.  Ports, cables are the simple stuff.

To see if the issue is just internet or also LAN, you need to test local transfer speeds.  Commonly, we'd use iperf3 with a client and server on the same LAN for a quick check.  My router has iperf3, but most routers do not.  You can use 2 _Try Ubuntu_ boot systems, install iperf3 on both, and test between them.  f you have only 1 PC and one android thing, you can transfer a known file with a stopwatch and estimate how fast it is,  By using Try Ubuntu flash boots, we remote bad settings that might have gotten in somehow.

There is a method for everything. A reason.

---

### Post by satimis on 2020-09-02
> **TheFu said:**
> Does the samsung use the same ethernet cable as the ubuntu machine?
-snip-

Samsung Notepad S9Plus is connected via WiFi, not cable connected.

Just made another test, both Ubuntu 18.04 PC and Samsung Notepad S9Plus running.

Same result:
Ubuntu 18.04 PC - upload test very slow

Samsung Notepad S9Plus - download and upload speeds almost equal

> 
To see if the issue is just internet or also LAN, you need to test local transfer speeds.  Commonly, we'd use iperf3 with a client and server on the same LAN for a quick check.  My router has iperf3, but most routers do not.  You can use 2 _Try Ubuntu_ boot systems, install iperf3 on both, and test between them.  f you have only 1 PC and one android thing, you can transfer a known file with a stopwatch and estimate how fast it is,  By using Try Ubuntu flash boots, we remote bad settings that might have gotten in somehow.

I don't have server here.

Regards

---

### Post by TheFu on 2020-09-02
> **satimis said:**
> Samsung Notepad S9Plus is connected via WiFi, not cable connected.
I don't have server here.

Exactly.  So we don't know that the router port or cable aren't the issue.

Any ubuntu machine is a server.  Just needs to provide a file xfer service for the samsung.  sftp is fine.

---

### Post by satimis on 2020-09-02
> **TheFu said:**
> Exactly.  So we don't know that the router port or cable aren't the issue.
I have changed the router port but with the same result, slow upload speed.

Regarding cable, how to identify whether it is a Cat5e cable?  I have connected ONT direct to Ubuntu 18.04 PC with the same cable but with same result, slow upload speed.

> 
Any ubuntu machine is a server.  Just needs to provide a file xfer service for the samsung.  sftp is fine.
I'll find a spare PC to do this test and come back later.

Edit:
One strange thing found after reconnecting ONT to Wifi router with the same cable;
Local IP address changed from 192.168.0.164 to 192.168.1.164
0--> 1
I don't know why?

Regards

---

### Post by satimis on 2020-09-02
Hi,

Spare Ubuntu 18.04 PC
ip address: 192.168.1.163

Daily working Ubuntu 192.168.1.164

$ iperf3 -c 192.168.1.164 -f K```

iperf3: error - unable to connect to server: Connection refused

```

My router doesn't have iperf3

Edit:
On daily working Ubuntu 18.04 PC
$ sudo systemctl stop firewall```

Failed to stop firewall.service: Unit firewall.service not loaded
```

Regards

---

### Post by TheFu on 2020-09-02
Install iperf3 on 2 unix machines.
[LIST=1]
[*]On one, run the server 
```
$ iperf3 -s
```
[*]On the other, run the client
```
$ iperf3 -c xx.xx.xx.xx
```
[/LIST]
If this fails to work, disable the firewall on the "server" and try again.

An example on my network.
hadar will be the "server" - I have DNS setup so all systems can find each other by name.
regulus will be the "client".
On hadar: $ iperf3 -s
On regulus: $ iperf3 -c hadar

The result on both screens look about the same:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 39128 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  1.82 GBytes  15.6 Gbits/sec    0   2.34 MBytes       
[  5]   1.00-2.00   sec  2.66 GBytes  22.8 Gbits/sec    0   2.58 MBytes
    ...
[  5]   9.00-10.00  sec  1.52 GBytes  13.0 Gbits/sec    0   2.99 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  19.7 GBytes  16.9 Gbits/sec    0             sender
[  5]   0.00-10.00  sec  19.7 GBytes  **16.9 Gbits/sec**                  receiver
```
So, on my LAN, I'm getting almost 17 Gbps.  Ok, I'm cheating. Regulus is a VM that runs on hadar. ;) Virtual machines rock for many reasons, including networking. 

Move the client to a different machine ... posc
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 57560 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   922 Mbits/sec    0    134 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   921 Mbits/sec    0    141 KBytes    
...
[  4]   8.00-9.00   sec   110 MBytes   922 Mbits/sec    0    182 KBytes       
[  4]   9.00-10.00  sec   110 MBytes   922 Mbits/sec    0    279 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.07 GBytes   921 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.07 GBytes   **920 Mbits/sec**                  receiver
```

920 Mbps - is what I expect between (2) 1 GigE connected systems.  Posc is in a different room, going through 2 GigE switches before hitting the router and hadar.

From hadar, my speedtest-cli is just:
```
Download: 29.64 Mbit/s
Upload: 5.90 Mbit/s

```

See the clear difference between the internet and LAN speeds?  I know my router hardware WAN connection cannot support more than 650 Mbps because I tested it between 2 LANs before I connected it to the internet.  That's an expected limitation for that specific router due to the aggressive firewall, packet priorities and because BSD doesn't use multiple CPUs for each NIC on the system..  But clearly, my internet speed is less than 1/10th what the router hardware + software supports.

Clear as mud?  This difference is what I've been trying to get you to test for a few hours now.

You could easily have tested using that samsung, BTW.  just use any sftp client and connect to the ubuntu machine that has the ssh package loaded. Find a 1GB file and pull it to the Samsung. How long did that take - use a watch.

---

### Post by TheFu on 2020-09-02
firewall.service is new to me.  Does iptables have any rules active?

The only way I know to see the sort of ethernet cable being used is if the cable happens to be labelled. not all are.  The LAN tests can tell, but the connection speed seen by the OS may tell us too.  But sometimes the connection speed that the OS claims is not true.

---

### Post by satimis on 2020-09-02
Hi TheFu,

Thanks for your advice.

I think it would be better to restart the test after next Wed (Sept. 09, 2020) because I have signed a new subscription contract.  The current contract will end on Sept 22, 2020.  The new ISP will install FTTH, 500M up/down speeds, network on next Wed.  I'll wait to see what will happen.

Regarding the Gigabit WiFi router, TP-Link, which has been used for more than 2 years, if the problem comes from it, I'll purchase a new Gigabit WiFi.  Any suggestion on the maker?

In seldom occasion I need WiFi but I need a router to assign IP address to the VMs of VirtualBox.

I'll come back then.  Thanks

Regards

---

### Post by satimis on 2020-09-10
Hi all,

New ISP
FTTH 500M download/upload

Problem still remains.

On Terminal
$ speedtest-cli --simple```

Ping: 4.446 ms
Download: 475.08 Mbit/s
Upload: 4.03 Mbit/s

```

On Speedtest.net website
Download - 465.94
Upload - 470.18
almost equal

Please see attached photo

Wired connection direct from ONT to PC with a Cat 5e cable

Regards

---

### Post by kurt18947 on 2020-10-03
If it were me, I think I'd the TheFu's advice and time downloads and uploads. Use a large enough file that it takes several seconds at least to download and upload. I've seen different speedtest apps produce different results when checked seconds apart so am skeptical about the accuracy of speedtest apps and web sites .

---


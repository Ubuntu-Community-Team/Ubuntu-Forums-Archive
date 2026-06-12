---
title: "Wireless will access local network but not internet."
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by wlbai on 2008-05-03
I hope someone can help me with this. I am new to Ubuntu and Linux and I'm trying to learn. 
I have a Dell Inspiron 5160 laptop which is a dual boot between Windows XP and Ubuntu 8.04. The wireless card is a Dlink that uses the Atheros chipset. The info on the chipset (obtained via lspci -v) is as follows:

 > Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
	Subsystem: D-Link System Inc D-link DWL-G650 (Rev B3,B5) Wireless cardbus adapter
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at 68000000 (32-bit, non-prefetchable) [size=64K]
I installed Ubuntu via Wubi if that makes any difference.
My system consists of a cable modem hooked to a Linksys WRT54G router running WEP encryption (yes I know not that secure). The IP addresses are obtained via DHCP.
For the first few days this system connected to internet fine in Ubuntu. This morning when I turned the machine on, I fired up the browser and nothing would connect. I also tried Pidgin and that would not connect either. Both were working fine last night. I then tried accessing some files on other machines in my local network and that DID work. I also rebooted into Windows and verified that the internet connection was working. It was.
I then went back into Ubuntu and tried pinging several sites from the terminal (Yahoo, Google, and a domain that I own) and they did ping fine. 
I searched the forum but was unable to find anything that applied directly to my situation and the few things I saw that were similar did not help. Here is some more info that I obtained that I thought might be needed to diagnose my problem:
From lspci:

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

From ifconfig-a

> ath0      Link encap:Ethernet  HWaddr 00:13:46:13:70:41  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4386 (4.2 KB)  TX bytes:8491 (8.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:11:43:7b:6a:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16200 (15.8 KB)  TX bytes:16200 (15.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-13-70-41-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11507 errors:0 dropped:0 overruns:0 frame:5497
          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1029684 (1005.5 KB)  TX bytes:23013 (22.4 KB)
          Interrupt:16 


and finally the info from /etc/network/interfaces

> auto lo
iface lo inet loopback


I should also mention that I am running NO firewall on the linux install at this time. 
I apologize if I've "over-info'ed" or "under-info'ed" this post but I really am quite new to this. I am hopeful that someone can lead me in the right direction because I really don't know what I could have done to break this. It was working fine last night and the only thing I have been messing with is the fonts on the system.

---

### Post by wlbai on 2008-05-04
No one has any ideas? I have torn my hair out on this. I really like Ubuntu but it's unfortunately useless to me if the wireless doesn't connect to the internet.:(

---

### Post by Monicker on 2008-05-04
> **wlbai said:**
> No one has any ideas? I have torn my hair out on this. I really like Ubuntu but it's unfortunately useless to me if the wireless doesn't connect to the internet.:(

Can you ping any external hosts while using the wireless?  Try to ping 4.2.2.2 and ping.symantec.com

What are the results when you try those pings?

What is the output of netstat -rn ?

Also, when you say the browser would not connect, what type of error message did you receive?  Do you have any proxy settings configured in the browser?  Did you  try a different web browser?

---

### Post by tvtech on 2008-05-04
This is my 100th post!

this sounds like it's most likely a dns problem.  as though your not accessing the wonders of dynamic name services try accessing the internet through a direct ip ping. 

**system>administration>network tools**  
go to the ping tab  and type in 216.239.51.99  

also take a look at the following file for more information
you'll need to open a terminal for this
```
username@localhost~$sudo gedit /etc/network/interfaces
```

it should read ```
auto lo
iface lo inet loopback
```in order to have your ethernet device set to auto dhcp

also check out ```
sudo gedit /etc/resolv.conf
```  this is your network resolution configuration file if your previous file is set to auto this should automatically authenticate your dns servers it should give you two name servers in this file.  if it does not then you can manually add your dns servers from your isp. at the end of the file just add the following lines 
```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```  this should get you up and running.

---

### Post by wlbai on 2008-05-04
Thanks for answering!
Monicker
The output of my ping to 4.2.2.2 is as follows
> PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=54 time=12.9 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=54 time=16.4 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=54 time=15.9 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=54 time=14.8 ms
64 bytes from 4.2.2.2: icmp_seq=5 ttl=54 time=18.5 ms
64 bytes from 4.2.2.2: icmp_seq=6 ttl=54 time=21.7 ms
64 bytes from 4.2.2.2: icmp_seq=7 ttl=54 time=13.5 ms
64 bytes from 4.2.2.2: icmp_seq=8 ttl=54 time=15.1 ms
64 bytes from 4.2.2.2: icmp_seq=9 ttl=54 time=13.7 ms
64 bytes from 4.2.2.2: icmp_seq=10 ttl=54 time=14.6 ms
64 bytes from 4.2.2.2: icmp_seq=11 ttl=54 time=21.0 ms
64 bytes from 4.2.2.2: icmp_seq=12 ttl=54 time=15.0 ms
64 bytes from 4.2.2.2: icmp_seq=13 ttl=54 time=14.9 ms
64 bytes from 4.2.2.2: icmp_seq=14 ttl=54 time=12.9 ms
64 bytes from 4.2.2.2: icmp_seq=15 ttl=54 time=15.6 ms
64 bytes from 4.2.2.2: icmp_seq=16 ttl=54 time=13.0 ms
64 bytes from 4.2.2.2: icmp_seq=17 ttl=54 time=16.7 ms
64 bytes from 4.2.2.2: icmp_seq=18 ttl=54 time=14.3 ms
64 bytes from 4.2.2.2: icmp_seq=19 ttl=54 time=13.4 ms
64 bytes from 4.2.2.2: icmp_seq=20 ttl=54 time=19.1 ms
64 bytes from 4.2.2.2: icmp_seq=21 ttl=54 time=13.0 ms
64 bytes from 4.2.2.2: icmp_seq=22 ttl=54 time=14.4 ms
64 bytes from 4.2.2.2: icmp_seq=23 ttl=54 time=16.1 ms
64 bytes from 4.2.2.2: icmp_seq=24 ttl=54 time=14.7 ms
64 bytes from 4.2.2.2: icmp_seq=25 ttl=54 time=14.5 ms
64 bytes from 4.2.2.2: icmp_seq=26 ttl=54 time=12.9 ms
64 bytes from 4.2.2.2: icmp_seq=27 ttl=54 time=13.3 ms
64 bytes from 4.2.2.2: icmp_seq=28 ttl=54 time=15.8 ms

--- 4.2.2.2 ping statistics ---
28 packets transmitted, 28 received, 0% packet loss, time 27015ms
rtt min/avg/max/mdev = 12.918/15.331/21.729/2.295 ms



pinging symantec.com did NOT work.
the output of netstat -rn is as follows:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 ath0



The browser Firefox is configured to connect directly with no proxy and the message it gives is "Network Timeout. The server at cm.my.yahoo.com is taking too long to respond". I did try other sites with the same result.
I dont have another browser installed but the fact that the Pidgin IM client won't connect leads me to believe that is something more than browser.

tvtech
The results of the ping you requested are as follows:
> PING 216.239.51.99 (216.239.51.99) 56(84) bytes of data.
64 bytes from 216.239.51.99: icmp_seq=1 ttl=242 time=30.0 ms
64 bytes from 216.239.51.99: icmp_seq=2 ttl=242 time=30.1 ms
64 bytes from 216.239.51.99: icmp_seq=3 ttl=242 time=45.8 ms
64 bytes from 216.239.51.99: icmp_seq=4 ttl=242 time=38.7 ms
64 bytes from 216.239.51.99: icmp_seq=5 ttl=242 time=35.2 ms
64 bytes from 216.239.51.99: icmp_seq=6 ttl=242 time=38.0 ms
64 bytes from 216.239.51.99: icmp_seq=7 ttl=242 time=32.2 ms

--- 216.239.51.99 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6005ms
rtt min/avg/max/mdev = 30.077/35.774/45.871/5.235 ms


The contents of /etc/network/interfaces is exactly what you posted
> auto lo
iface lo inet loopback

The contents of /etc/resolv.conf are as follows:
> ### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4937
#
### END INFO



nameserver 24.89.0.22
nameserver 24.89.0.21


So to me at least it looks like the nameservers are there. I suspected a DNS problem initially as well. 
An ipconfig /all from a Windows machine on the same network gives the same nameserver info. See below:
> Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Wireless-G PCI Adapter
        Physical Address. . . . . . . . . : 00-0C-41-64-8E-5A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 24.89.0.22
                                            24.89.0.21
        Lease Obtained. . . . . . . . . . : Saturday, May 03, 2008 10:44:14 PM
        Lease Expires . . . . . . . . . . : Sunday, May 04, 2008 10:44:14 PM

Any ideas?? Thanks for the input so far!

---

### Post by Monicker on 2008-05-04
Definitely seems like a dns issue.

Please try this:

```
nslookup www.microsoft.com
nslookup www.microsoft.com 4.2.2.2
```


If the problem is with your default dns entries the first nslookup should fail, and the second one should succeed.

Not sure why they would work under Windows but not linux.  Perhaps one of the servers is failing/timing out, and linux is not trying the other.

You could try them individually:

```
nslookup ping.symantec.com 24.89.0.22
nslookup ping.symantec.com 24.89.0.21
```

Do they both fail?

---

### Post by wlbai on 2008-05-04
Everything returned results. Doing a nslookup on [www.microsoft.com](www.microsoft.com) returned
> wlbai@wlbai-laptop:~$ nslookup [www.microsoft.com](www.microsoft.com)
Server:		24.89.0.22
Address:	24.89.0.22#53

Non-authoritative answer:
[www.microsoft.com](www.microsoft.com)	canonical name = toggle.[www.ms.akadns.net](www.ms.akadns.net).
toggle.[www.ms.akadns.net](www.ms.akadns.net)	canonical name = g.[www.ms.akadns.net](www.ms.akadns.net).
g.[www.ms.akadns.net](www.ms.akadns.net)	canonical name = lb1.[www.ms.akadns.net](www.ms.akadns.net).
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.19.254
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.192.254
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.19.190


Doing an nslookup on [www.microsoft.com](www.microsoft.com) 4.2.2.2 returned
> wlbai@wlbai-laptop:~$ nslookup [www.microsoft.com](www.microsoft.com) 4.2.2.2
Server:		4.2.2.2
Address:	4.2.2.2#53

Non-authoritative answer:
[www.microsoft.com](www.microsoft.com)	canonical name = toggle.[www.ms.akadns.net](www.ms.akadns.net).
toggle.[www.ms.akadns.net](www.ms.akadns.net)	canonical name = g.[www.ms.akadns.net](www.ms.akadns.net).
g.[www.ms.akadns.net](www.ms.akadns.net)	canonical name = lb1.[www.ms.akadns.net](www.ms.akadns.net).
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.19.254
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.19.190
Name:	lb1.[www.ms.akadns.net](www.ms.akadns.net)
Address: 207.46.192.254


The results of nslookup ping.symantec.com 24.89.0.22 were as follows:
> wlbai@wlbai-laptop:~$ nslookup ping.symantec.com 24.89.0.22
Server:		24.89.0.22
Address:	24.89.0.22#53

Non-authoritative answer:
Name:	ping.symantec.com
Address: 206.204.18.22

and the results of nslookup ping.symantec.com 24.89.0.21 were
> wlbai@wlbai-laptop:~$ nslookup ping.symantec.com 24.89.0.21
Server:		24.89.0.21
Address:	24.89.0.21#53

Non-authoritative answer:
Name:	ping.symantec.com
Address: 206.204.18.22

Still the browser will not connect to a site nor will the Pidgin client work. :(

Just for curiousity sake I also tried typing an IP address (207.46.19.254) from above directly into the URL bar of the browser. That did not work either.

---

### Post by Monicker on 2008-05-04
Eh?  I am confused now.  At first you could ping hosts by name, and then you said it did not work when pinging ping.symantec.com.

```
ping ping.symantec.com
```


That is what you tried, right?


If you CAN ping by name from the terminal, then it may be your browser itself.

Do you have a different web browser installed?  If not, you can do
```

telnet www.microsoft.com 80
```

which should return something like the following

```
Trying 207.46.192.254...
Connected to lb1.www.ms.akadns.net.
Escape character is '^]'.

```

---

### Post by wlbai on 2008-05-04
Regarding the ping.symantec.com. I misread your instructions and that is why you're confused. Instead of typing " ping ping.symantec.com" I typed "ping.symantec.com". I apologize for the confusion.
Typing "ping ping.symantec.com" returns the following:
```
PING ping.symantec.com (206.204.18.22) 56(84) bytes of data.
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=2 ttl=243 time=181 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=3 ttl=243 time=175 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=4 ttl=243 time=201 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=5 ttl=243 time=186 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=6 ttl=243 time=206 ms
64 bytes from ping.symantec.com (206.204.18.22): icmp_seq=7 ttl=243 time=212 ms

--- ping.symantec.com ping statistics ---
7 packets transmitted, 6 received, 14% packet loss, time 6009ms
rtt min/avg/max/mdev = 175.038/194.001/212.851/13.823 ms

```
So I CAN ping from the terminal.
Running the telnet command telnet [www.microsoft.com](www.microsoft.com) 80 returns

```
Trying 207.46.192.254...
```
but it never connects.

Just as an experiment I tried downloading Pan newsreader from the Add/Remove Programs interface but that did not work either. It never downloads the file. That along with the IM client not connecting leads me to believe it's something more than the browser but if you can tell me how to download another browser from the terminal I will be happy to try it. Thanks for your help so far!

---

### Post by Monicker on 2008-05-04
If the telnet to port 80 failed then its not the browser, which is why I wanted you to try that in order to see if that was in fact the case.

Do you have any kind of firewalling configured under linux?  Someone a while back still had some leftover configs from Firestarter which were blocking outbound traffic by default.


What is the result of the following command?

```
sudo iptables -n -L
```

---

### Post by wlbai on 2008-05-04
I never installed any firewall programs so that shouldn't be an issue. The output from "sudo iptables -n -L" is as follows:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

---

### Post by Monicker on 2008-05-04
The only other thing I can think of is filtering at the router itself.  Going back over the previous posts, I noticed that you have 192.168.1.101 address when using linux, and a 192.168.1.102 address when in Windows.  Is there anything in the router configuration which would handle traffic differently between those 2 ip addresses?

Is the linux ip address also assigned by dhcp?  I have seen some instances where a home router would not accept traffic from a static ip when that ip was not assigned by the router itself.

---

### Post by wlbai on 2008-05-04
The .102 address came from another machine on my network. I was trying the commands you asked for on my linux laptop (the .101 machine) but then  having to copy/paste the results to the .102  machine via my local network so that I could post them on the net. When I ran that ipconfig /all it was on the Windows machine (the .102) which was not the linux laptop. I just did that to show that the nameserver ip's were the same. Sorry for the confusion there. When I reboot the laptop from Linux to Windows it does still carry the .101 address and the laptop works on the  net when it's in Windows. The router does assign IP's via DHCP in both Windows and Linux.

---

### Post by Monicker on 2008-05-05
I'm pretty much out of ideas then.

You could try some outbound pings with increasing packet sizes, to see if there is some kind of MTU issue.

```
ping -c 4 -s 500 ping.symantec.com
ping -c 4 -s 1000 ping.symantec.com
ping -c 4 -s 2000 ping.symantec.com
```

...and so forth.  After that, I have no clue.

---

### Post by wlbai on 2008-05-05
It's working! I found out this morning from my wife that we had some brief power outages between the time it last worked and when it stopped working. Apparently the router was down for a short period of time and then came back up when the power came back on. For whatever reason when the router re-powered it did something to block this machine on linux. When this machine or any of the others were on Windows they were working fine. I did a power off/power on on the router this morning and when it came back online everything worked. This was not a Linux problem at all but rather a quirk in my router. Thanks for all your assistance Monicker, I really appreciate it!!:)

---

### Post by Monicker on 2008-05-05
Interesting.  Glad its working, but it still seems odd that it only affected linux.  I had thought briefly about suggesting a reset of the router, but dismissed the idea since you said XP had no problems with network connectivity.

Oh well, as long as its up now.  :)

---

### Post by wlbai on 2008-05-05
That threw me too. I would think at that level of connectivity it would all be pretty much the same whether Windows or Linux but I had 3 other machines on the network, all running Windows, with no connectivity issues during this period. At any rate, I acquired an old burned out APC UPS this weekend via the dumpster that I am currently rebuilding. As soon as I have it up it will be going on that router. :)
Thanks again for the help!

---

### Post by lemming465 on 2008-05-05
It looks like you have both IP networking and DNS resolution, which makes me wonder if something has gone haywire in the Firefox config and set up a non-existent proxy server.  You might check that.

As a cross-check on the networking, have you tried another web browser, such as konqueror (sudo apt-get install konqueror).  For that matter, does installing or updating software work?

---

### Post by wlbai on 2008-05-05
lemming
It's working now, see the post above. It turned out to be some quirk in the router due to the router going down in a power outage. When the router came back up it allowed Windows to connect to the internet but not Linux. Very strange but a power off/power on reset on the router fixed the issue.
Thanks for your response!

---


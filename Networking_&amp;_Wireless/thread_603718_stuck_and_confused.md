---
title: "stuck and confused"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by johntoomany on 2007-11-05
Been trying for weeks to get connected to the Internet with no success.  Have been through the forum threads and tried all that were even remotely possible.  I'm running Ubuntu  6.06 on a separate hard drive and Windows XP Pro on another hard drive.  My Internet connection by way of a wired router and that connects to a wireless system.  Ubuntu installed with no problems several months ago and I've been using it since that time with no problems except, I can't get online.

On this computer my Windows IP configuration is:
     Host Name                                 JOHNPOLY 594794
     Primary DNS Suffix
     Node type                                  Unknown
     IP Routing enabled                    No
     WINS Proxy enabled                No
     DNS Suffix Search list             tcsn.net

Ethernet Adapter  Local Area Connection:
     Connection-specific DNS Suffix                tcsn.net
     Description                                               NVIDIA  nForce networking controller  
     Physical Address                                      00-1A-92-15-CC-5D 
     Dhcp enabled                                           Yes
     Auto configuration enabled                      Yes
     IP address                                                 192.168.1.101
     Subnet Mask                                             255.255.255.0
     Default gateway                                        192.168.1.1 
     DHCP server                                             192.168.1.1
     DNS servers                                              208.64.216.1
                                                                       208.64.216.2
This configuration is on HDD1(250GB) is, and has been, working correctly

On this computer my Ubuntu IF configuration (one of many variations) is:
g
eth0      Link encap:Ethernet  HWaddr 00:1A:92:15:CC:5D
          inet6 addr: fe80::21a:92ff:fe15:cc5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11232 (10.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

This configuration, or any other tried, on HDD2(160GB) doesn't get me 
connected to the Internet.
I'm sure it's obvious that I'm new to Linux and starting to flounder at this point.
Is there some mistake I've been making or something staring at me I can't see?
Any and all help will be appreciated.

---

### Post by l33t_3lv3n_g33k on 2007-11-05
Post your /etc/network/interfaces file.  
 
Are you using a wireless connection from this computer to the internet or an ethernet cable?
 
If you're trying to use wireless, it doesn't look like your wireless card is enabled/configured.
 
If you're using ethernet, I'm not sure what's going on, but your interfaces file is the best place to start.

---

### Post by johntoomany on 2007-11-08
I'm using an ethernet connection from the computer to a wired router and the router has an ethernet connection to a transceiver that sends/receives to/from my ISP.
The ethernet card is NVIDIA nForce Networking Controller and I believe this is the problem.  Your request for the network interface files set me on the right track..   This card is not being recognized by Ubuntu.  Some research on this card indicates that it's been a problem working with Linux so I've got some work to do now to get the right fix.
Thanks much for setting me on the right track.

---

### Post by johntoomany on 2007-11-12
No joy yet.  No matter what I try I come up with no connection.
Did run the following but don't know where to go next:

johnjg@johnpoly594794:~$ lsmod | grep forcedeth
forcedeth              23428  0
johnjg@johnpoly594794:~$ uname -a
Linux johnpoly594794 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
johnjg@johnpoly594794:~$

Any suggestions?

---

### Post by R00t3rMan on 2007-11-12
Your ethernet card isn't transmitting any packets.  Just for kicks, try hardcoding an IP address on your eth0, such as 192.168.1.102/24, and see if you can ping it.  Check the ifconfig again and see if eth0 is transmitting.  I think maybe you are right that this is a peculiar hardware issue.

---

### Post by johntoomany on 2007-11-13
Tried to put in 192.168.1.102/24 but wouldn't accept anything past .102
Has a mind of its own....

---

### Post by johntoomany on 2007-11-20
Finally gave up on 6.06 and installed 7.10.  Installed with no problems and did an ifconfig.
I was connected right out of the gate and I've been running with no problems.
Thanks much for the help but I guess Ubuntu 6.06 just wasn't going to cooperate.Maybe even I will be able to help someone someday.

---


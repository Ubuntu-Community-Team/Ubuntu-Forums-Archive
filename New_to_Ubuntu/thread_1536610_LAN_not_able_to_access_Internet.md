---
title: "LAN not able to access Internet"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by aarav2306 on 2010-07-22
hi
I have been using 9.04 for the past 1year. 
The configuration is as follows
ISP (MTNL) - modem - 9.04 desktop - switch - LAN ( 6 Ubuntu 9.04 + 1 WinXP + 1 Ubuntu 9.10)
And I used to run the following commands
> sudo iptables -A FORWARD -i eth0 -o  eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
 sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
sudo service squid restartAnd everything was perfect
Ever since I have changed my ISP service provider, my LAN isnt able to access internet. 
Only when I plug a LAN cable from a PC directly onto the MTNL modem alongwith the main PC, do I get the 2PCs on internet, else only my main PC.
In "connection information" on the top panel of main PC, I find IP address information only against external interface eth1 as 192.168.1.21, doesnt show IP information of internal interface eth0 even though it is manually keyed as 198.168.0.2 with gateway 192.168.1.1
Some friend further tinkered with it and now I am not even able to assign IP to eth0 using the command 
> ifconfig eth0 192.168.0.2
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied                      the ifconfig -a gives the foll
> eth0      Link encap:Ethernet  HWaddr 00:e0:5a:4d:11:2d  
          inet6 addr: fe80::2e0:5aff:fe4d:112d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9086 errors:105 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:587657 (587.6 KB)  TX bytes:79993 (79.9 KB)
          Interrupt:22 Base address:0xb800 

eth1      Link encap:Ethernet  HWaddr 00:11:11:23:99:5c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe23:995c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109809182 (109.8 MB)  TX bytes:5885432 (5.8 MB)

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:5a:4d:11:2d  
          inet addr:169.254.3.161  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38674 (38.6 KB)  TX bytes:38674 (38.6 KB)

pan0      Link encap:Ethernet  HWaddr 9e:8f:6e:04:e6:06  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
How do I get eth0 to be assigned the IP 192.168.0.2 automatically (Edit connections in Network connections doesnt seem to be working)
Is that why it doesnt show in "Connection Information"
how do I get LAN to access internet again?
Pls help
regards
Aarav

---

### Post by pricetech on 2010-07-22
Since you changed ISPs, you have a different upstream IP address.  See if you can set ETH0 to receive its IP via DHCP.  Then you won't have to guess at it.

---

### Post by The Cog on 2010-07-22
To set the internal address, you need to use sudo in front of the command, to get root rights:
sudo ifconfig eth0 192.168.0.2

I would worry about why eth0 is no longer being given an IP address. Where did it used to come from? Did you have a DHCP server on the internal LAN? How do the other PCs know to use your PC as a sefault gateway to the internet?

The absence of the internal address suggests that something on your local LAN has changed.

---

### Post by aarav2306 on 2010-07-23
thanks
am able to set the internal IP using sudo ifconfig eth0
We have been a lot of tinkering recently to get our LAN up, something must have got changed
till last week we would get the eth0 details to appear in connection information
dont remember installing/using DHCP server on the LAN, 1 smartie in our team has installed Ubuntu 10.4 on his system in the LAN, will it have DHCP server, how do I check?

The other PCs were connected to eth0 on the main PC through a LAN switch with gateway and DNS configurations same as external interface

Since I am able to get internet on 1PC on the LAN by directly plugging it into the MTNL modem, let me see if I can make that as the hub by installing an additional LAN card on it, do I have to install squid as well or will NAT commands simply work
regards
Aarav

---

### Post by aarav2306 on 2010-07-23
hi
It is working now, I ran the NAT commands from the 2nd PC on the LAN which is now directly connected to the MTNL modem and it is working beautifully now. Thanks
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) was very useful
Oh, I love Ubuntu
Any links where I can download antiviruses for ubuntu 
regards
Aarav

---

### Post by The Cog on 2010-07-23
I'm glad to hear you got it working.

If you really want AV for Ubuntu, I suggest you look in the sticky threads in the security forum - like this one: 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by aarav2306 on 2010-07-24
Internet to my LAN is again down today
The main PC and 2nd PC on LAN which are directly connected to MTNL modem gets internet
And when I turn on the LAN switch which connects the 2nd PC with the rest of the LAN, the net stops. The net restarts when I switch off the LAN switch
Also today Mozilla Firefox keeps crashing on the main PC every 2mins. Is this due to virus, has it gone corrupt, I am typing this using Opera.
Should I uninstall Mozilla and reinstall

Regards
Aarav

---

### Post by aarav2306 on 2010-07-24
hi
The Mozilla problem was due to a lot of bookmarks
But how do I get my LAN to start using internet
I ran the same commands as I did ytday
And tried it another PC as well
But not working
Pls help
regards
Aarav

---


---
title: "new to ubuntu. Need help connecting to the internet (wired connection)."
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by utsav on 2008-01-03
Need help connecting to the internet.

I have just shifted over to Ubuntu and am finding trouble connecting to the internet. I am a still a novice in networks and before posting this question have scoured the forum for answers, but didn't find one applicable to me. Please direct me to a post on how to solve my problem.

I use a wired connection in a windowsXP desktop. I connect to the internet by logging on with a username and password through my local ISP (the reason i mentioned this is i couldn't find a similar app in linux.)

the ipconfig command in the windows environment yeilds the following. 

Ethernet adapter Local Area Connection:      

```
Connection-specific DNS Suffix  . :       
Autoconfiguration IP Address. . . : 169.254.84.136        
Subnet Mask . . . . . . . . . . . : 255.255.0.0        
Default Gateway . . . . . . . . . : 

PPP adapter hons cable:        
Connection-specific DNS Suffix  . :         
IP Address. . . . . . . . . . . . : 124.41.199.76        
Subnet Mask . . . . . . . . . . . : 255.255.255.255        
Default Gateway . . . . . . . . . : 124.41.199.76
```

I have pasted the outputs from the commands below . Can someone help? Thanks in advance.

outpust from ifconfig
```
	auto eth0
	eth0      Link encap:Ethernet  HWaddr 00:19:D1:99:C7:EE  
	          inet6 addr: fe80::219:d1ff:fe99:c7ee/64 Scope:Link
	          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:1000 
	          RX bytes:0 (0.0 b)  TX bytes:9174 (8.9 KB)

	eth0:avah Link encap:Ethernet  HWaddr 00:19:D1:99:C7:EE  
	          inet addr:169.254.11.73  Bcast:169.254.255.255  Mask:255.255.0.0
	          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

	lo        Link encap:Local Loopback  
	          inet addr:127.0.0.1  Mask:255.0.0.0
	          inet6 addr: ::1/128 Scope:Host
	          UP LOOPBACK RUNNING  MTU:16436  Metric:1
	          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
	          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
	          collisions:0 txqueuelen:0 
	          RX bytes:2368 (2.3 KB)  TX bytes:2368 (2.3 KB)

```

Output from lsusb

```
Bus 005 Device 003: ID 14cd:6600  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
```

Output from lspci
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:04.0 Communication controller: Conexant Unknown device 2f50 (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
```

---

### Post by Bandolin on 2008-01-03
Are you connecting to your ISP via DHCP or PPPoE? I'm not expert either but if you are logging in with a username and password like me, you are using PPPoE. Personally, I'm using a DSL connection.

Because if you are connecting via PPPoE, I believe you are out of luck with Ubuntu.

I haven't been able to connect to the internet with Ubuntu over PPPoE. But can easily do so with Knoppix. My next attempt will be with Fedora.

Did you try: In Terminal

sudo pppoeconf

this will lead you through a step by step procedure to activate your internet connection. I did this and it allowed me to ping my ISP's server, but authentication failed and I still can't surf the net.

---

### Post by ARhere on 2008-01-03
Errrm... not sure if this will help but...

I use a PPPoE, on a DSL line.  The difference is my DSL modem goes to a cheap Linksys wireless switch.  I can set the username and password in the Linksys and it will keep the connection alive for me. At that point adding a laptop or other machine to my internet is 1/100 of the hassle in any OS.

I hate to tell you to buy some hardware just for Ubuntu, but you might consider it for several other reasons.

1.  Ease of use to your PPPoE
2.  Wireless connection for laptop
3.  Firewall & port filtering
4.  blah blah blah

If you don't like Linksys there are a bazillion other cheap wireless switches you can buy that do the exact same thing.  Worth the $40.

-AR

---

### Post by erfahren on 2008-01-03
There's "pppoeconf" - it's preinstalled on Ubuntu - it looks like a command line configuration utility

to start it just enter into the terminal:
```

pppoeconf

```
I started it and it asked for my password -  the Ubuntu username password - since the utility would be editing configuration files.

a [Google search on it](http://www.google.com/search?hl=en&q=linux+pppoeconf&btnG=Search) came up with what may be some good guides.

note: for the DNS addresses you can use the OpenDNS addresses:
208.67.222.222
208.67.220.220

There is a directory - /etc/ppp - that is for those configuration files, so I know it's possible in Linux to set it up without any additional hardware. I seached for just "Linux ppp" and "Linux pppoe" and came up with a lot of results, but some of the guides looked a little outdated, and most dealt with dialup, but probably still applicable to a degree. 

all "pppoe" stands for is point-to-point protocol over ethernet - you do have ppp and connect to a modem with ethernet so I'm sure it's what you're looking for.

---

### Post by utsav on 2008-01-06
thanks for your help....

I will see about the router thing.. if there is any other way to reconfigure to support PPPoE without a router do please reply to this thread...

Regards,
Utsav

---


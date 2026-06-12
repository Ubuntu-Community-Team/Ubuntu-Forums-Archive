---
title: "Wired network interface, &quot;No DHCPOFFERS received&quot; error"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by skueppers on 2008-12-25
I'm brand new to Linux and Ubuntu.  Just so you know where I'm coming from, I have some Windows experience, but my primary computing experience is with Mac OS X.  I do have extensive user-level experience with UNIX servers, so I am comfortable with command-line tools, but have no system administration experience.   

I have a Dell XPS 400 computer, which I have installed Ubuntu 8.10 on using the Live CD.  There are no other operating systems installed on the computer.  It is currently connected to a Linksys wireless access point/router using an Ethernet cable; I also tried connecting it to the Ethernet port on a DSL modem in a different location. 

I can't get my network connection working.  I have tried the following:

[list][*]Adding eth0 to the /etc/network/interfaces file, which now reads:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

[*]Using ifdown/ifup; sudo ifup eth0 results in the following output:

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:72:10:94:1d
Sending on   LPF/eth0/00:13:72:10:94:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory
```

[*]Uninstalling the Network Manager using Add/Remove Applications.  I noticed some messages related to the Network Manager were still appearing in the syslog, so I used the Synaptic Package Manager to remove the Network Manager. 

[*]Disabling IPv6 using the instructions in the Ubuntu documentation. [/list]

However, none of this has helped me get connected to the network.  

Here is the output from lshw -C Network:

```
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:10:94:1d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.4-1 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:e2:5d:45:a3:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

And here is the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:13:72:10:94:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe3e0000-fe400000 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:72:10:94:1d  
          inet addr:169.254.4.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fe3e0000-fe400000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16000 (16.0 KB)  TX bytes:16000 (16.0 KB)
```

I will say that I cannot guarantee that the network card is working, but I have no reason to think that it isn't -- it was working the last time the computer was used (with Windows XP) about six months ago.  I am sure that the ethernet cable and the router are working, as they work fine with another computer.  The other computer is configured to obtain its IP addresses via DHCP, which it does without any trouble. 

Any thoughts you may have on how I should be approaching this problem would be much appreciated!

---

### Post by skueppers on 2008-12-26
I have now also tried installing 8.04 instead, just in case it would work better.  8.04 is using the e1000 driver for this card instead of the e1000e driver, but the results are no different. 

As an aside, I have not yet figured out where I can tell Ubuntu Linux which driver to use for the network card.  I feel like maybe /etc/modprobe.d/aliases would be the place?  I'd love a pointer to some documentation that would clear this up for me. 

The output of sudo ethtool eth0 is:

```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: no
```

---

### Post by ieee488 on 2008-12-26
Are you able to connect with another computer? Sometimes it is not Linux's problem. Your router might have firewall blocking the connection or something.

---

### Post by skueppers on 2008-12-26
Yes, I can connect another computer to the same cable and the same port on the router, configured to use DHCP, and it connects no problem.

Thanks for responding!

---

### Post by dragos_iliescu_2005 on 2008-12-26
It seems that the file resolv.conf is missing.

(grep: /etc/resolv.conf: No such file or directory)

So, if you have a back up, restore it, if not just create it (as root). This file must contain your DNS address like:
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

---

### Post by skueppers on 2008-12-26
> **dragos_iliescu_2005 said:**
> It seems that the file resolv.conf is missing.

(grep: /etc/resolv.conf: No such file or directory)

So, if you have a back up, restore it, if not just create it (as root). This file must contain your DNS address like:
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

Thanks for your response!  

While I agree that the resolv.conf file is not present, I'm not sure that's related to this issue.  It seems to me that my problem is occurring at a much lower level, since the ethtool output says no link is detected.  I don't yet have an IP address at the point this problem is occurring, so I don't need DNS yet. 

Also, I'm not sure I even ought to have a resolv.conf file at this stage with the configuration I'm using, since I am expecting to acquire my IP address and DNS addresses via DHCP.

Does that make sense, or am I missing something?

---

### Post by sleepyjon on 2008-12-26
Have you checked that it's plugged in? 

Have you tried setting the IP manually?

---

### Post by skueppers on 2008-12-26
> **sleepyjon said:**
> Have you checked that it's plugged in? 

Have you tried setting the IP manually?

Yes, I have checked to make sure that it is plugged in.

In response to your query, I have also tried setting an appropriate IP address manually and specifying DNS entries in /etc/resolv.conf.  However, this did not really help.  Yes, the computer now thinks it has an IP address and tries to make network connections, but I don't actually get anywhere.  

In the ethtool output, "Link detected" remains "no," and "Speed" and "Duplex" remain Unknown.  It definitely appears to me that the issue lies in the Ethernet card not successfully communicating with the router at a lower level, so nothing that I can do at the IP level makes any difference.  

I tried using ethtool to turn off autonegotiation and specify the correct speed and duplex manually, but while I was able to turn off autonegotiation, ethtool continued to report the speed and duplex as "Unknown" even after I issued the command:

sudo ethtool -s eth0 speed 100
sudo ethtool -s eth0 duplex full

I also attempted to specify what speed/duplex the card would advertise using the command:

sudo ethtool -s advertise 0x008

which resulted in the error:

ethtool: bad command line argument(s)

---

### Post by Sealbhach on 2008-12-26
I guess you could check if the module for this ethernet card is loaded. The module is 

 module=e1000e 

so you could look for it in lsmod

```
lsmod | grep e1000e
```

If not you could load it by:

```

sudo modprobe e1000e
```


.

---

### Post by skueppers on 2008-12-26
> **Sealbhach said:**
> I guess you could check if the module for this ethernet card is loaded. The module is 

 module=e1000e 

so you could look for it in lsmod

```
lsmod | grep e1000e
```

If not you could load it by:

```

sudo modprobe e1000e
```


.

Thanks for the suggestion!

The driver is loaded, and I have tried unloading it and reloading it using the modprobe command.  

No improvement, but I appreciate your input!

---

### Post by Sealbhach on 2008-12-26
Check out this link, 

[http://ubuntuforums.org/showthread.php?t=868077](http://ubuntuforums.org/showthread.php?t=868077)

There may be other links here also that could help:

[http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla:en-US:official&hs=s1f&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=82573L+Gigabit+ubuntuforums&spell=1](http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla:en-US:official&hs=s1f&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=82573L+Gigabit+ubuntuforums&spell=1)



.

---

### Post by dragos_iliescu_2005 on 2008-12-26
I understood that you have dual boot. Do you have internet connection on WIndows? If yes, what are the connection parameters?

---

### Post by skueppers on 2008-12-26
> **dragos_iliescu_2005 said:**
> I understood that you have dual boot. Do you have internet connection on WIndows? If yes, what are the connection parameters?

Sorry, I don't have dual boot.  This computer only has Ubuntu on it.  

Though I am considering installing XP, which originally came installed on the machine and which I have the original DVD for, just so I can find out if the Ethernet card still works in XP.  It seems like a bit of a drastic measure, though, since I have no intention of running XP on the machine. 

I have ordered a wireless PCI card for the computer, as my eventual objective is to install this computer in a place in my home that doesn't have an Ethernet connection.  I was careful to order one with an excellent reputation for working in Ubuntu, so I am hopeful that even if I never succeed in getting Ethernet to work, I will be able to connect via wireless.   I am keeping my fingers crossed!

---

### Post by w4ett on 2008-12-26
At the risk of sounding silly, when you were running the live cd, did the ethernet work? (or did I miss that question?)

---

### Post by handydan918 on 2008-12-26
And at the risk of sounding even sillier, is there any chance the router is doing MAC filtering?

Just a thought.

---

### Post by skueppers on 2008-12-26
> **w4ett said:**
> At the risk of sounding silly, when you were running the live cd, did the ethernet work? (or did I miss that question?)

No, networking didn't work with the Live CD either.  :-)

---

### Post by skueppers on 2008-12-26
> **handydan918 said:**
> And at the risk of sounding even sillier, is there any chance the router is doing MAC filtering?

Just a thought.

Nope, not a chance.  I have connected several items to this router in the last few days that have never connected to it before, without difficulty.

---

### Post by skueppers on 2008-12-26
Just to update, I decided to download the latest version of the e1000e driver from Intel's web site.  I built the new version and installed it.  I am pretty sure the new version is being used because the output from lshw -C network indicates the new version number.  

Unfortunately, the new driver didn't solve my problem.  Oh, well, it was worth a try!

---

### Post by skueppers on 2008-12-27
First of all, I want to thank everyone who tried to help me with this problem.  Having people make the effort to help me out really means a lot to me. 

I finally decided to give up on the onboard Ethernet controller and buy a PCI Ethernet card.  After doing some research on the Ubuntu Hardware section, I got a NetGear FA311 card with a RealTek 8139D chipset. 

It was completely plug and play -- I just installed the hardware, booted up the computer, and was on-line.  

So, my problem is now solved, in that I'm writing this message from my new Ubuntu system!  Unfortunately, I didn't solve the actual underlying problem, but I'm not going to devote any more attention to the problem -- I have too many other things to do with my new system!

---

### Post by Sealbhach on 2008-12-27
> **skueppers said:**
> 

I finally decided to give up on the onboard Ethernet controller and buy a PCI Ethernet card.  After doing some research on the Ubuntu Hardware section, I got a NetGear FA311 card with a RealTek 8139D chipset. 

It was completely plug and play -- I just installed the hardware, booted up the computer, and was on-line.  



It's a pity you had to buy new hardware but sometimes it's the quickest solution. Glad you're up and running.:)


.

---


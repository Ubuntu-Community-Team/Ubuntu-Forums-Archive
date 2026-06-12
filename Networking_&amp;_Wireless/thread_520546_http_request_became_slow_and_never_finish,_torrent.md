---
title: "http request became slow and never finish, torrent, pop3 works"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by holdfenytolvaj on 2007-08-08
Hi,

I tried opera, ff, but apt is the same. I get the first webpage after a boot, but than
none of the webpages work, I mean the firefox says loading page, the favico/title/maybe some text appears but nothing more the page keeps loading forever (only exception is google/gmail/googlemaps these pages work all the time)
Under windows everything is fine. Torrent/ mail/ ping works. This situation is the same if i connect by wire or wireless. And the same at home, and at work (for the same machine). I tried to install older-newer ubuntus also the last stable debian all the same.
Here are some output:

lshw -C network

  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:98:37
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.145 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:02:e9:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-8-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.5     0.0.0.0         UG    0      0        0 eth0

/etc/resolv.conf
nameserver 217.194.96.10
nameserver 62.108.1.65

/etc/nsswitch.conf
passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 #(i tried with files dns also)
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


Many many thanks in advance for any suggestion!!!

G.

---

### Post by noob12 on 2007-08-09
Two things to check. Your DNS servers may be slow, or your browser proxy settings may be wrong.  For the latter, in firefox: Edit | Preferences | Advanced | Network | Connection | Settings ...   
If you don't have a proxy, select "Direct connection to the Internet".

---

### Post by holdfenytolvaj on 2007-08-09
These are not the problem, since 
1, ping respond immediately for urls as well
2, the pages are never finished.
3, I tried actually with proxy and also with port forwarding none of them worked
actually if i tried proxy or port forwarding even the gmail didt load, only the google (i could search on it).

---

### Post by Irony on 2007-08-09
This sounds the same as the problem I have.

I'll open up Firefox and it loads pages okay but a couple of hours later it doesn't load anything.

Boot up into Windows and all is okay.

I've installed Opera and the same thing happens - its slows until it is unuseable.

I wonder if its something to do with the updates.

I also use PCLinuxOS and this doesn't happen.

---

### Post by Data Doctor on 2007-08-10
I had this problem after loading recent Dapper updates. Suddenly Firefox started dragging its heels. Turned out to be a problem with my DNS resolution. I use a Linksys router for my home network.

Establishing a direct DNS connection may solve your problem. 

1. Find your DNS servers. You may need to check your router settings (usually 192,168.1.1 or 192.168.0.1). Look for a status tab, or similar with the current DNS information. Write down your DNS servers (x.x.x.x & x.x.x.x).

You may wish to back up your dhclient.conf file at this point. In the Terminal, type:
cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak

2. Enter these DNS servers directly in your dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

You should see your dhclient.conf file displayed (with text in it). Add two lines to the end:

supersede domain-name-servers x.x.x.x,x.x.x.x;
prepend domain-name-servers x.x.x.x,x.x.x.x;

The x's represent your DNS server IP addresses that you found in Step 1.

Save your dhclient.conf file, close gedit and return to the Terminal.

Now restart your DNS lookup with (assuming eth0 is your connection to the router):

sudo ifdown eth0 && sudo ifup eth0

You should immediately experience an improvement in your Internet speed.

After I updated Dapper, pages loaded very slowly until I made these changes.
I researched the solution on [https://forum.bytemark.co.uk/viewtopic.php?pid=1790](https://forum.bytemark.co.uk/viewtopic.php?pid=1790) as well as other Ubuntu forum entries.

---

### Post by holdfenytolvaj on 2007-08-12
Hi, 
I tried but it seems i have different problem.
i installed the dapper and my internet did work on it,
although when i upgraded to edgy the problem appeared immediately.
Tmr i will try to upgrade step-by-step... maybe I can tell you more.

G.

---


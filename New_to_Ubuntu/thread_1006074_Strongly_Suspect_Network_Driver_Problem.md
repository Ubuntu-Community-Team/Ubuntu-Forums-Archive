---
title: "Strongly Suspect Network Driver Problem"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by GrayArcadian on 2008-12-08
Okay, earlier today with the help of a very nice guy  

http://ubuntuforums.org/showthread.php?p=6334108#post6334108">

I eliminated most of the possibility this was a physical problem with my set up.  He gave me a link to find out more information, but nothing there made sense, so I'm coming here.

I have a Realtek Semiconductor Co., Limited RTL-8139/8139C/8139C+ (rev 10) ethernet card.  I have it hooked up to a ethernet cable.  After I updated my system the network is detected, but no pings can be sent either to the other computers in the house or outside of it.  I suspect there's a driver issue.  I have gone to *system--->admin--->hardware drivers* and it's blank.  I found and reinstalled ndisrapper but there's been no change.  I tried other threads, but I don't have enough savvy to translate what seems to be working for them to my system.

---

### Post by tarps87 on 2008-12-09
> **GrayArcadian said:**
> After I updated my system the network is detected, but no pings can be sent either to the other computers in the house or outside of it.

I don't know what you have tried so far, but if you can see the network, (also did you update from the network?) the first thing to try if checking you IP settings.
Ubuntu
```
ifconfig
```
Windows
```
ipconfig
```
Compare the output of one of the other computers to your one.

Do you have a dhcp server, also can you post the settings in this file:
/etc/network/interface

---

### Post by GrayArcadian on 2008-12-09
Love the userpic...

The updates were automatic updates Ubuntu 8.10 is set up to find and download.

When running **ifconfig** it offers the following:

eth0 Link encap:Ethernet HWaddr 00:14:2a:54:82:5d
inet address: 192.168.1.2 Bcast: 192.168.1.255 Mask: 255.255.255.0
inet6 addr: fe80::214:2aff:fe54:825d/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MIU: 1500 METRIC: 1
RX packets: 605 errors:0 dropped: 0 overruns:0 frame:0
TX packets: 8 errors:0 dropped: 0 overruns: 0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 79193 (79.1 KB) TX bytes: 1152 (1.1 KB)
Interrupt: 16 Base address: 0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MIU: 16436 METRIC: 1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX: packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX: bytes:0 (0.0 B)

When I run **netstat **there's a long list, but everything shows as "connected."

Not sure what to do with code and Windows.  I should note the computer I'm working with does not have a dual operating system.  I know the IP addresses are all different.  I checked.

Ran **sudo dchlient eth0** in terminal earlier and got the following:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:2a:54:82:5d
Sending on LPF/eth0/00:14:2a:54:82:5d
Sedning on Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 -- renewal in 34955 seconds.

Running **/etc/network/interface** got me "bash: /etc/network/interface: No such file or directory," but I remembered a file like that, so I went to *File System--->etc--->network* and there are the following files:

if-down.d
if-post-down.d
if-pre-up.d
if-up.d

And what looks like a text file of "interfaces."

---

### Post by bobnutfield on 2008-12-09
A couple of things...

1.  That network chipset is supported completely by 8.10, and as far back as I have been using Ubuntu (Dapper), so it is unlikely a driver issue.

2.  This:

> Listening on LPF/eth0/00:14:2a:54:82:5d
Sending on LPF/eth0/00:14:2a:54:82:5d
Sedning on Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 -- renewal in 34955 seconds

means you have been assigned an IP address by your router (192.168.1.2), so, at least from this information, you should be good to go on the network.

Have you opened Firefox to see if you can get online with the net?  Do you have a firewall running?

---

### Post by cek on 2008-12-09
I have used that card since at least 2002 without incident.  The "driver issue" in the link provided is for broadcom wireless cards, which have nothing to do with the Realtek 8139 series cards.

What is the output of the following command in a terminal:

ping -c 3 [www.google.com](www.google.com)

---

### Post by GrayArcadian on 2008-12-09
Glad to know that all that text means.  Thank you.

I get the IP address but when I ping anything: ubuntu, google, a computer on the same router it appears to be not pinging.  0% transmission.

**ping -c 3 [www.google.com](www.google.com)** gets me:

ping:unknown host [www.google.com](www.google.com)

When I tried **ping 192.168.1.1**

ping: sendmeg: Operation not permitted

Firewall:  None, or at least none I installed or can find.

Firefox:  Yep, that what started this was a complete inability to load pages on Firefox and get anything on Pidgin to come up.  I keep trying after running commands to see if anything changes.

I don't know if this helps, but I decided, "what the heck" and tried putting in the CD to run things and it works - kind of.  I can connect to the 'net just fine except that it goes back to what appears to be default settings (except there are no icons on the desktop) and I can't reload Java which I need to access my classes.  I take out the CD and I'm back to the exact desktop and other settings I started with and the same "access the net" problem.

---

### Post by bobnutfield on 2008-12-09
Open a terminal and type:

> cat /etc/resolv.conf

and post the results.  You may have a DNS issue.

---

### Post by GrayArcadian on 2008-12-09
**cat /etc/resolv.conf** gets me:

# Generated ny NetworkManager
nameserver 192.168.1.1

---

### Post by bobnutfield on 2008-12-09
OK, that is how it should read. Now, check /etc/hosts and /etc/hostname and make sure your hostnames are the same.  I can think of no other reason why you should not have a network connection since you have been assigned an IP address.

---

### Post by GrayArcadian on 2008-12-09
This could be it:

**sudo /etc/hosts**: command not found

sudo /etc/hostname: command not found

I should note Network Manager says I'm connected.  It's just not doing anything functional a connected system does, like load Firefox pages and connect to chat.

---

### Post by karlr42 on 2008-12-09
You didn't specify an editor in those commands, like ```
sudo **gedit** /etc/hosts
```

---

### Post by GrayArcadian on 2008-12-09
Um, my bad.  What are "editors" and how do you find the right one?

I used **sudo gedit/etc/host** and got "command not found" again.

---

### Post by karlr42 on 2008-12-09
A text editor, like notepad. gedit is the default a lot of people use. That command failed because you need a space like:
```
sudo gedit /etc/hosts
```
which basically says "start the program 'gedit' using the file '/etc/hosts'"

---

### Post by GrayArcadian on 2008-12-09
Thank you very much Karl42.

sudo gedit /etc/hosts brings up a text editor which says:

127.0.0.1   local host
127.0.1.1   (name of my system)

# The following lines are desirable for IPv6 capable hosts
::1   ip6 localhost ip-6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

sudo gedit /etc/hosts brings up just the name of my system

I'm getting tempted just to reinstall this thing.

---

### Post by handydan918 on 2008-12-09
Ya know, there is also the possibility that the router (if present) is not getting it's dns right.

If you are using your isp's defaults, you might do better with opendns

208.67.222.222

and
208.67.220.220

It might not hurt to try rebooting your router or modem...

---

### Post by tarps87 on 2008-12-10
> **GrayArcadian said:**
> Love the userpic...
Thanks

> **GrayArcadian said:**
> 
I know the IP addresses are all different.  I checked.
When you say different do you mean
192.168.1.*somenumber* or are any of the other numbers different?

> **GrayArcadian said:**
> 
And what looks like a text file of "interfaces."
Sorry I want very clear, I was the contents of the interfaces file that I wanted to see. This was to check the interface was set to dhcp but from the rest of the posts it sounds like it is.

> **bobnutfield said:**
> Do you have a firewall running?
There should be the default firewall running (iptables) but this should not effect this unless the setting have been changed?

DNS should not effect pinging using IP's, can you ping yourself?
```
ping 127.0.0.1
```
and then
```
ping 192.168.1.2
```

---


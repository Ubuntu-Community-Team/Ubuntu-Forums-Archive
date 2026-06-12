---
title: "Need help sharing internet connection"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by umanzor on 2006-11-28
Hi,

I need help sharing my Internet connection. I'm directly connected to my cable modem through USB. Now I want to share this connection to my laptop through my ethernet port. It's fairly easy in Windows, but I have no idea how to do it in Ubuntu.

The how to I read wasn't very clear.

---

### Post by ssalman on 2006-11-28
[here ]("https://help.ubuntu.com/community/InternetConnectionSharing")is what I used... give it a try.

---

### Post by umanzor on 2006-11-28
It didn´t work... some steps aren't very clear either... my laptop (windows XP) gives an Connection Limited or No connection message.

Is there any application that can make this easier?

---

### Post by umanzor on 2006-11-28
Didn't work, tried several things. I need an Ubuntu to XP ICS tutorial or someone who can explain me what to do. Instrucctions on that link aren't very clear for me either... :(

---

### Post by ssalman on 2006-11-29
I read that you can use firestarter to help you accomplish this.... never tried it my self, I used the commands on wiki page I posted earlier.

see post #3 [here]("http://www.ubuntuforums.org/showthread.php?t=290242&highlight=firestarter+share")

give it a try and post back.

---

### Post by umanzor on 2006-11-29
I'd try it...

but I tried so much other things that I screwed up the configuration (maybe) and my internet connection doesn't work.

Made a mess, is there any recover or do I have to reinstall ubuntu (again)?

---

### Post by ssalman on 2006-11-30
if you kept a backup copy of /etc/networking/interfaces file, use it and restart your network via 

```
sudo /etc/init.d/network restart
```

if not (this is a good lesson to always back up :)), use the GUI tool to reconfigure your network, make sure you enable the card, and select DHCP if you don't use static IP configuration.

in any case [here ]("http://www.ubuntuforums.org/showthread.php?t=25557")is a useful link to network trouble shooting, once you get it sorted out, try firestarter.

good luck.

---

### Post by umanzor on 2006-11-30
Thanks for the reply.

No backup :(.......

The GUI tool? You mean, Preferences-->Networking?

Tried that, card is enabled and DHCP selected. The DNS servers are shown... (weird).

hmm, I can actually apt-get update if I start Ubuntu in recovery mode. Maybe there is a backup file I need to restore but where can I look for it. I have no backup of the interfaces file.

---

### Post by ssalman on 2006-11-30
okay, lets try to fix your network configuration ;)

post the output of the following commands. replace eth0 with your correct interface.

```
ifconfig eth0
ping 127.0.0.1 -c 4
 ping localhost -c 4
ping 209.191.93.52 -c 4
ping www.yahoo.com -c 4
cat /etc/resolv.conf
cat /etc/hosts
route
arp -a
```

---

### Post by umanzor on 2006-11-30
I'm reading this on my laptop, otherwise I'd have to reboot, try, read, reboot try, post, etc. Hence, I'll type what I see on the command line.

$ ifconfig eth1:

eth1 Link encap: Ethernet HWaddr 00:0E:5C:7F:B8:CB
     inet addr: 169.254.66.40 Bcast: 169.254.255.255 Mask: 255.255.0.0
     BROADCAST MULTICAST MTU: 15000 Metric: 1
     RX packets: 99 errors:0 dropped:0 overruns:0 frame:0
     TX packets: 23 errors:0 dropped:0 overruns:0 carrier:0
     collisions: 0 txqueuelen:1000
     RX bytes:29008 (28.3kiB) TX bytes:3354 (3.2KiB)

$ ping 127.0.0.1 -c 4 (I'll give you the results)
4 packets transmited, 4 recieved, 0% lost, time 2999ms
rtt min/av/max/mdev = 0.064/0.067/0.073/0.008ms

$ ping localhost -c 4 (I'll give you the results)
4 packets transmited, 4 recieved, 0% lost, time 3001ms
rtt min/av/max/mdev = 0.066/0.067/0.068/0.000ms

$ ping 209.191.93 .52
Connect:Netowork is unreachable

$ ping [www.yahoo.com](www.yahoo.com) -c 4
ping: unknown host [www.yahoo.com](www.yahoo.com)

$ cat /etc/resolv.conf
nameserver 196.40.15.193
nameserver 196.40.15.200
nameserver 196.40.62.209

$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 home

hmm...

---

### Post by ssalman on 2006-11-30
try

```
sudo dhclient
```

and post back the results of 

```
route
```

---

### Post by umanzor on 2006-12-01
$ sudo dhclient
password:

Internet Systems Consortium DHCP Client V.3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:08:54:22:42:bb
Sending on LPF/eth0/00:08:54:22:42:bb
Listening on LPF/eth1/00:0e:5c:7f:b8:cb
Sending on LPF/eth1/00:0e:5c:7f:b8:cb
Sending on Socket/Fallback
DHCPDISCOVER on eth0 to 255.255.255.255 to port 67 interval 3
DCHPDISCOVER on eth1 to 255.255.255.255 to port 67 interval 7
DCHPDISCOVER on eth0 to 255.255.255.255 to port 67 interval 5
DHCPOFFER from 196.40.62.1
DCHPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 196.20.62.1
bound to 10.1.7.10-- renewal in 3269 seconds

(since I can't copy/paste, I figured it would be easir to make the table portrait instead of landscape)

$ route
Kernel IP routing table

Destination  10.1.0.0     default
Gateway      *            10.1.0.1    
Genmask     255.255.0.0   0.0.0.0
Flags        U            UG
Metric       0            0
Ref          0            0
Use          0            0
Iface        eth1         eth1

edit: Hmm, after those commands, it works! After reboot, it doesnt... 

I moments like these I'd like to reinstall, but the beryl site is down so I can't reinstall bery later... so lets keep trying!

---

### Post by ssalman on 2006-12-01
Okay, here is the deal, your connection is not setup to get the IP address from the router/modem/server through dhcp. Every thing is running fine, but you don't get the IP address or the DNS info. when you run dhclient, a request is sent to get this info, thats why it works after you run it.

Let try the obvious first. 

I see that you have two network cards eth0 and eth1, do you have both setup to use DHCP? remember that you may have eth1 as your 1st card and eth0 as your 2nd... when you checked on your DHCP setup you could have checked the wrong card. Did you add your second network card before or after Ubuntu installation?

list the cntents of your iftab and interfaces files. use the following commands.

```
cat /etc/iftab
cat /etc/networking/interfaces
```

---

### Post by Balaam's Miracle on 2006-12-02
On my Ubuntu box, eth0 (static IP) connects to a WinXp machine and eth1 (DHCP) connects to the internet.
I wanted to set up something similar to ICS so that my wife can surf the net as she used to do before i installed Ubuntu on my PC.

I have tried getting ICS/Masquerading working using Firestarter+DHCP3 but the truth is that Firestarter caused me more problems that that it solved. Besides, on the client computer, the connection (to the net) was slow and unreliable and a lot of traffic, both inbound and outbound, was blocked that wasn't supposed to be blocked (which is a different problem togheter with a couple of other FS-related problems).

I've tried other methods too, including following the directions in the much referred to [https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28network%29%7C%28translation%29%7C%28address%29) but nothing really made it work like i was used to if it worked for me at all.

Until i came across this post on [http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370) and got it immediately working beautifully!!!

I hope this helps, it did help me :-)

---


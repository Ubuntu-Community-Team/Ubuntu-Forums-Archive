---
title: "strange behaviour of ethernetcard"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by TeasesTheBear on 2007-05-01
Hi there!

Been searching for, and trying to solve this problem on my own for two days now, with no results. Probably you guys and gals can help me out:)

I've set up an old AMD 1.2Ghz machine as fileserver with the ubuntu server-edition. The networkcard is a noname-card with realtek RTL8169S chipset and appropriate driver (had to compile it though). Since i dont have a spare monitor (and actually dont really want one either) i thouhgt it'd be a good idea to maintain and configure it via ssh. Well, practically this is harder to do than it sounds:

upon ssh connection i'm randomly told i had a bad MAC or the package length (assuming IP here) does not match the expected length. Even when i do gain access, the session freezes after a random time, somewhere between 0.5min and 30min. By freezing i mean, no input is recognized, but the session is still up and running (verified by opening a second session and having a look at ps output). Well, maybe I'm too impatient on this one. Still, watinig more than a minute for commandline-response is unacceptable, even via ssh:/
The system also seems to have massive problems, when communicating with my router. This is the output of dhclient:
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:e0:4c:69:1e:32
Sending on   LPF/eth0/00:e0:4c:69:1e:32
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Again the package length seems to be the problem. I've set a static ip-address by now (at the server, not the router). This way i can at least open an ssh-connection (sometimes at least:)), no connection to internet though, since all necesary data is obtained by DHCP, which is not used now...
However, I have once(!) been able to  get a valid lease, but then trying to use apt was practically impossible. I have no cdrom (physically) mounted on the server (anymore), and apt-get update tends to throw nested errors from bzip2 about corrupted archives.
Additionally, though i dunno, if this is something to concerne about, i saw some packages were dropped, via ifconfig.

Solution attempts so far/error exclutions:
The router seems to work fine, two other machines + a Wii are communicating with it flawlessly over lan and wlan.
The cable seems to work fine too, never encountered any problem with it and it was used only recently for another machine, before it was assigned to the server.
Since this is a gigabit card, i was told to set it to 100Mbit (router's speed), but ethtool told me the card is already running on 100Mbit.
The card came i a not really suitable (for hardware in general) package, resulting in a bended sheeting. although I had the thought I just can't imagine, the very hardware could be broke. I mean, I'd expect it to work properly or not at all after mechanical mistreatment (I'm not talking about defects caused by electrostatic discharges;)). Still I'd believe you, if you told me otherwise;)
I've tried to do a selftest via ethtool, but the driver does not seem to support it :/

Appreciating any help,
Teases the bear

P.S.: Just while writing this post i received the impression, that the ssh-sessions seem to freeze, when I'm typing too fast, could've been coincidents though

EDIT:
just got following error form ssh-session while typing:
Received disconnect from 192.168.1.50: 2: Bad packet length 544865142

---


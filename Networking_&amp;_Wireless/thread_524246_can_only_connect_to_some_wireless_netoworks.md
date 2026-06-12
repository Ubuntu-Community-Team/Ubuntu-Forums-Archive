---
title: "can only connect to some wireless netoworks"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by jsgarvin on 2007-08-12
I have an odd issue.

I can successfully connect to my wireless router at home with WPA encryption just fine.  I can connect to a few different public wireless hotspots, no problem.  But, some others, nada. For instance, I'm in my favorite watering hole at the moment, but can't connect to their network, even though the signal strength is very, very good. However, sitting right here,I can connect to a weak signal from the greasy spoon across the street (which is how I'm typing this now).

Looking at the files in /var/log, I can see it getting the DHCPOFFER from the server, making the DHCPREQUEST, and then instantly getting a DHCPNAK, lather, rinse, repeat.  When trying to connect to the server across the street, it just jumps right on.

However, I'm surrounded by other people all connected fine (albiet, in winblows).

Anybody got any suggestions???  I'm quickly running out of ideas.

---

### Post by moore.bryan on 2007-08-13
*you could tryout [wicd]("http://wicd.sourceforge.net/") and see if that fixes your problem...*

---

### Post by jsgarvin on 2007-08-13
Thanks, I'll give that a try next time I'm there (tomorrow evening).

Any other suggestions to try as well?

---

### Post by moore.bryan on 2007-08-13
*not yet... i suspect it's a network-manager issue and wicd usually solves those.  if wicd has the same issue, then that'll give us a starting spot.*

---

### Post by jsgarvin on 2007-08-14
Ok, thanks for the info.... however.


Just installed wicd on the laptop and tried to connect it to the home network but it just sticks on  "Obtaining IP address..." and eventually times out.  If I set a static IP, it claims to be connected, but I can't connect to or ping any websites.

[Update]
Disregard.  It sure helps if you've got the WPA key set properly.  Fixed that and now both DHCP and Static IPs work and Firefox can see google again.

Will report back tomorrow evening with results of tests on the problem network.

---

### Post by moore.bryan on 2007-08-14
*excellent news.  progress is never a bad thing...*

---

### Post by jsgarvin on 2007-08-14
Ok, no luck. Here's excerpts my daemon.log for the non-working network, and the working one across the street.

```

Aug 14 17:32:24 vostro dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 14 17:32:24 vostro dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 14 17:32:24 vostro dhclient: All rights reserved.
Aug 14 17:32:24 vostro dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 14 17:32:24 vostro dhclient:
Aug 14 17:32:25 vostro avahi-daemon[5199]: Registering new address record for fe80::21b:77ff:fe71:9bbc on eth1.*.
Aug 14 17:32:25 vostro dhclient: Listening on LPF/eth1/00:1b:77:71:9b:bc
Aug 14 17:32:25 vostro dhclient: Sending on   LPF/eth1/00:1b:77:71:9b:bc
Aug 14 17:32:25 vostro dhclient: Sending on   Socket/fallback
Aug 14 17:32:26 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:32:26 vostro dhclient: DHCPNAK from 192.168.1.1
Aug 14 17:32:26 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 14 17:32:27 vostro dhclient: DHCPOFFER from 192.168.1.1
Aug 14 17:32:27 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:32:27 vostro dhclient: DHCPNAK from 192.168.1.1
Aug 14 17:32:32 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:32:32 vostro dhclient: DHCPNAK from 192.168.1.1
Aug 14 17:32:40 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Aug 14 17:32:41 vostro dhclient: DHCPOFFER from 192.168.1.1
Aug 14 17:32:41 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:32:41 vostro dhclient: DHCPNAK from 192.168.1.1
Aug 14 17:32:44 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:32:44 vostro dhclient: DHCPNAK from 192.168.1.1
Aug 14 17:32:52 vostro dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 14 17:32:53 vostro dhclient: DHCPOFFER from 192.168.1.1
Aug 14 17:32:53 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:33:00 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:33:00 vostro dhclient: DHCPNAK from 192.168.1.1
```

```
Aug 14 17:33:34 vostro avahi-daemon[5199]: Withdrawing address record for fe80::21b:77ff:fe71:9bbc on eth1.
Aug 14 17:33:35 vostro dhclient: There is already a pid file /var/run/dhclient.pid with pid 134993416
Aug 14 17:33:35 vostro dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 14 17:33:35 vostro dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 14 17:33:35 vostro dhclient: All rights reserved.
Aug 14 17:33:35 vostro dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Aug 14 17:33:35 vostro dhclient:
Aug 14 17:33:36 vostro avahi-daemon[5199]: Registering new address record for fe80::21b:77ff:fe71:9bbc on eth1.*.
Aug 14 17:33:36 vostro dhclient: Listening on LPF/eth1/00:1b:77:71:9b:bc
Aug 14 17:33:36 vostro dhclient: Sending on   LPF/eth1/00:1b:77:71:9b:bc
Aug 14 17:33:36 vostro dhclient: Sending on   Socket/fallback
Aug 14 17:33:40 vostro dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 14 17:33:40 vostro dhclient: DHCPACK from 192.168.0.1
Aug 14 17:33:40 vostro avahi-daemon[5199]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.34.
Aug 14 17:33:40 vostro avahi-daemon[5199]: New relevant interface eth1.IPv4 for mDNS.
Aug 14 17:33:40 vostro avahi-daemon[5199]: Registering new address record for 192.168.0.34 on eth1.IPv4.
Aug 14 17:33:40 vostro dhclient: bound to 192.168.0.34 -- renewal in 42593 seconds.
```

---

### Post by noob12 on 2007-08-14
The question is why the DHCPNAK from the server?   In that state the client has selected the offer and DHCPNAK indicates that the server is withdrawing/rescinding the offer.   The client is supposed to go back just as the trace shows, i.e. the lather, rinse, repeat behavior is what's prescribed by the protocol.

There's a decent state diagram and description here:
[http://www.tcpipguide.com/free/t_DHCPGeneralOperationandClientFiniteStateMachine.htm](http://www.tcpipguide.com/free/t_DHCPGeneralOperationandClientFiniteStateMachine.htm)

You may be able to get dhclient to log the actual interchange  with the right debug flags.

Here's a wild-*** guess.  You have a client lease state file in /var/lib/dhcp3/dhclient.eth1.leases.  That lease file identifies a lease you had from another server where that server was identified only by its IP address 192.168.1.1  (not rare, certainly).    You can look at this file to confirm this. This is somehow confusing the dhclient code into sending the final request with its old leased address.  NAK!

Notice the other server is at 0.1.  No confusion.

Based on this guess, stop networking.  Remove the client lease state file.  Restart networking.  See if things change.

---

### Post by Fernanernie on 2007-08-14
> **moore.bryan said:**
> *you could tryout [wicd]("http://wicd.sourceforge.net/") and see if that fixes your problem...*
I was having pretty much the same issue as jsgarvin. And I thought I was the only one that took his 'Buntu lappy to the bar :) Followed your advice and it worked perfectly. THANK YOU! I was getting sick of wrestling with WiFi-Radar, and Network Monitor going between wired/wireless. I think you saved the last, remaining bit of hair I have left.


FYI Wired;
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
and
Wireless Ethernet controllers (using NDISWrapper):
04:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by noob12 on 2007-08-14
Not sure if it's the same issue here, as I think at this point jsgarvin is on wicd.  Or we think he is.

---

### Post by jsgarvin on 2007-08-14
> **noob12 said:**
> 
Here's a wild-*** guess.  You have a client lease state file in /var/lib/dhcp3/dhclient.eth1.leases.  That lease file identifies a lease you had from another server where that server was identified only by its IP address 192.168.1.1  (not rare, certainly).    You can look at this file to confirm this. This is somehow confusing the dhclient code into sending the final request with its old leased address.  NAK!

Notice the other server is at 0.1.  No confusion.

Based on this guess, stop networking.  Remove the client lease state file.  Restart networking.  See if things change.

Nope, deleted that file and tried to reconnect... same behavior and same stuff in the log.

> **noob12 said:**
> 
You may be able to get dhclient to log the actual interchange  with the right debug flags.


Just browsed through the man page for dhclient, and not sure I bhave any idea what flags to send just to get it to try to connect normally, but I don't see any flags for doing any verbose logging, so I don't think that's going to help much.  Any other ideas, or am I SOL?

And, yes, I am using wicd now, as suggested.  ;-)  I like the granularity of it's config, so I think I'll stick with it, regardless of whether I ever get this particular network to work.

---

### Post by noob12 on 2007-08-14
> 
Nope, deleted that file and tried to reconnect... same behavior and same stuff in the log.

Did you actually stop networking before deleting the file and reconnecting?   If not, retry that.

Not sure if tcpdump will work on the interface, but you might learn something interesting with this running in one window
```

sudo tcpdump -n -x -i eth1 -vv portrange 67-68

```

while you do

```

sudo dhclient -r eth1
sudo dhclient eth1

```

in another.

---

### Post by jsgarvin on 2007-08-15
> **noob12 said:**
> Did you actually stop networking before deleting the file and reconnecting?   If not, retry that.

Ok, maybe I don't understand what you mean by 'stop networking'.  I told wicd to 'disconnect' before deleting the file.  If you meant something more than that, then I'll need some more specifics.  Thanks.

---

### Post by imdano on 2007-08-15
Open a console and type the command ```
sudo /etc/init.d/networking stop
```Make the changes you were supposed to make (not sure what they are as I haven't read through the thread) then type ```
sudo /etc/init.d/networking start
```

---

### Post by jsgarvin on 2007-08-15
Ah.. ok, thanks.  Learned something new today.

I'll give this a shot next time I'm within range.

---

### Post by moore.bryan on 2007-08-15
> **Fernanernie said:**
> I was having pretty much the same issue as jsgarvin. And I thought I was the only one that took his 'Buntu lappy to the bar :) Followed your advice and it worked perfectly. THANK YOU! I was getting sick of wrestling with WiFi-Radar, and Network Monitor going between wired/wireless. I think you saved the last, remaining bit of hair I have left.
*you're very welcome... just glad to hear you got it working!*

---

### Post by jsgarvin on 2007-08-19
> **noob12 said:**
> Did you actually stop networking before deleting the file and reconnecting?   If not, retry that.

Not sure if tcpdump will work on the interface, but you might learn something interesting with this running in one window
```

sudo tcpdump -n -x -i eth1 -vv portrange 67-68

```

while you do

```

sudo dhclient -r eth1
sudo dhclient eth1

```

in another.

Ok. here we go again.   Stopped networking properly this time, removed the dhclient lease files, restarted networking, and then fired up wicd and tried to connect.  But just got the same  OFFER/REQUEST/NAK messages as before.

tcpdump just returns "tcpdump: bind: Network is down" on eth1.  I'm guessing this isn't a big surprise.

I managed to talk to the closest thing they have to the computer guy, and he admitted that their access point isn't very good.  Apparently other people have problems fairly regularly... I'm just the only one that can NEVER get on.   So, they'll be getting a new access point as soon as they can convince the manager...  so, that may end up being the resolution to this.  However, if anyone has anything else for me to try, I'll give it a shot.  Who knows maybe I'll learn something new (like how to stop and start networking). ;)

---

### Post by noob12 on 2007-08-19
Well it was worth a shot.  The mystery stands I guess.

---


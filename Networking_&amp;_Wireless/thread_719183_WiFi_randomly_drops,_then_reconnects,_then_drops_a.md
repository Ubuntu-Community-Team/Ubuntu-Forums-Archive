---
title: "WiFi randomly drops, then reconnects, then drops again"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by LuciaZephyr on 2008-03-08
I'm a relative Ubuntu newbie working with 7.10 and have been able to solve a lot of problems with the aid of Google and forum archives. Finally, I have hit a wall.

My connection keeps cutting out. As far as I can tell, there is no reason why it is doing so. This started about a week ago and is starting to make plain old research needlessly difficult. Every time I lose the connection, I have to wait as it fights to reconnect, which can take up to five minutes.

I'm running a Dell Inspiron 6000 laptop with the usual integrated Intel hardware. I'm almost certain this is a problem on my end, not with the router. Any help with this would be greatly appreciated.

(As a side note, over the last hour, I've lost connection about seven times and twice just while I wrote up this post. It's getting a bit ridiculous.)

:hits "Submit" quickly before the connection is again lost:

---

### Post by Bubba64 on 2008-03-08
Do you have your network set up as roaming rather than on your router alone. Check your network setup.

---

### Post by kevdog on 2008-03-08
What chipset/driver are you using?  Are you using Network Manager?

---

### Post by LuciaZephyr on 2008-03-08
@Bubba64: As soon as I disabled roaming, I lost all connections and nothing was showing up under the list of nearby networks. Am I doing it wrong?


@kevdog: Yep, Network Manager. As for drivers, it says ipw2200.

---

### Post by kevdog on 2008-03-08
Try connecting using the command line.  The only point of this exercise is to rule out that its not a network manager issue rather than a driver issue.  It could be either. See the link in my sig for details.  If its a NWM issue, then maybe we will try WICD.  If its a driver issue, lets troubleshoot the driver.

---

### Post by LuciaZephyr on 2008-03-08
@kevdog: Okay, I followed the Unencrypted instructions and checked the "a successful connection will look like this" box. My results don't look like that.

```
zephyrus@Serenity:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:45:00:dc
Sending on   LPF/eth1/00:13:ce:45:00:dc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 38570 seconds.
```

---

### Post by Bubba64 on 2008-03-08
Hopefully kevdog's link will help you I have had some problems with network manager but I know how to deal with my network. If I use roam then turn it off the same thing happens to me, but I just do a restart because I have a wep key and user name in the computer that fixes itself with a restart.

---

### Post by LuciaZephyr on 2008-03-08
@Bubba64: That helped. After a quick restart, it seems to be working. Hopefully this will solve my problem? :barely dares to hope:

**ETA:** It did not fix the problem.

---

### Post by kevdog on 2008-03-09
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 38570 seconds.

Your connection did work -- you were issued 192.168.1.2 by your router/dhcp server.  You should be able to peruse the internet with this.  If you can, I would wait to see if the connection is dropped.

---

### Post by LuciaZephyr on 2008-03-09
I'm not sure I understand what you mean. My connection does continue to randomly drop (though not as often since Bubba64's fix- now it only seems to be twice an hour or so).

---

### Post by kevdog on 2008-03-09
So with Bubba's fix you are down to 2x per hour -- if that is acceptable to you then procede no farther.  Again there are no right answers here -- you are in charge.  If you find that not acceptable, just give the command line connection a shot, and then see how long until you get a drop.  It might be no different, pinning this down to a driver issue rather than a nwm issue.

---

### Post by LuciaZephyr on 2008-03-09
I think it's not different, though I did notice one thing when doing the command line connection that might be the cause?

```
zephyrus@Serenity:~$ sudo iwconfig eth0 essid "ESSID_IN_QUOTES"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Operation not supported.
```

Is that there an issue?

---

### Post by kevdog on 2008-03-09
Whats the name of your access point?? --  certainly its not ESSID_IN_QUOTES

sudo iwconfig eth0 essid "ESSID_IN_QUOTES"

it should be something like:
sudo iwconfig eth0 essid "DAVID"
sudo iwconfig eth0 essid "university_lan"

---

### Post by LuciaZephyr on 2008-03-09
Well, I'm an idiot. I didn't realize that was what ESSID meant.

Either way, I'm hitting way too many snags in the command line configuration. I'll stick to the slightly-less-broken connection from Bubba64's fix for now.

Thank you for your help. I greatly appreciate it.

---

### Post by kevdog on 2008-03-09
No problem -- check back if you are unhappy with your current setup -- Happy computing!

---


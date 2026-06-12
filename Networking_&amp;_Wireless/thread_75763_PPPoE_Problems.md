---
title: "PPPoE Problems"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by bo_emperor on 2005-10-14
I was using Hoary till yesterday when I installed Breezy(i deleted Hoary's partition first and then installed breezy in the free space) It's really wondeful, but I have this weird problem. I used pppoeconf to setup my Internet connection and modified /etc/network/interfaces to change the mac address of my network card, because my provider uses mac address recognizing as part of the athentication process, and my original lan card is broken. 
So thats ok and when I connect to the internet using pon dsl-provider it does connect, but my connection is damn slow and it's even impossible to open some sites. I don't have these problems in Windows, and I didn't have them un Hoary, but in Hoary I was using RP-PPPoE. I tried using it under Breezy too, but the result ws the same. 

I have three Lan cards in my computer. Two of them are RTL8139D, and the broken one is my nForce 2 network controler, which is integrated in the chipset. Currently using eth2 for internet connection. 

Here is my /etc/network/interfaces :
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
#iface eth1 inet dhcp
auto eth2
iface eth2 inet manual

iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
    pre-up /sbin/ifconfig eth2 down
    pre-up /sbin/ifconfig eth2 hw ether 0020ed83aa4e
    pre-up /sbin/ifconfig eth2 up # line maintained by pppoeconf

# added by pppoeconf
#auto eth1

# added by pppoeconf


Please help!

---

### Post by emilov on 2005-10-15
same thing here. it connects but its slow beyond usable.
what i saw in syslog is this:

Plugin rp-pppoe.so loaded.
Oct 15 20:26:55 localhost pppd[19848]: pppd 2.4.3 started by root, uid 0
Oct 15 20:26:55 localhost pppd[19848]: PPP session is 19969
Oct 15 20:26:55 localhost pppd[19848]: Using interface ppp0
Oct 15 20:26:55 localhost pppd[19848]: Connect: ppp0 <--> eth0
Oct 15 20:26:55 localhost pppd[19848]: Couldn't increase MTU to 1500
Oct 15 20:26:55 localhost pppd[19848]: Couldn't increase MRU to 1500
Oct 15 20:26:55 localhost pppd[19848]: Couldn't increase MRU to 1500
Oct 15 20:26:58 localhost pppd[19848]: PAP authentication succeeded
Oct 15 20:26:58 localhost pppd[19848]: peer from calling number xxxx authorized
Oct 15 20:26:59 localhost pppd[19848]: Cannot determine ethernet address for proxy ARP
Oct 15 20:26:59 localhost pppd[19848]: local  IP address xxx
Oct 15 20:26:59 localhost pppd[19848]: remote IP address xxx
Oct 15 20:26:59 localhost pppd[19848]: primary   DNS address xxxx
Oct 15 20:26:59 localhost pppd[19848]: secondary DNS address xxxxx

---

### Post by bo_emperor on 2005-10-16
Is there nobody to help?

---

### Post by rth on 2005-10-20
[http://www.dslreports.com/faq/7801]("http://www.dslreports.com/faq/7801")

You may want to check your MTU. Can't think of anything else off the top of my head.

---

### Post by drtvasudevan on 2005-10-20
try changing the firefox settings.
type about:config in address bar
toggle network.dns.IPv6disable value from false to true

tv

---

### Post by jochex on 2005-12-28
:confused: 
I got that problem too.
i can't change the MTU, here's my /etc/ppp/peers/dsl-provider

```

plugin rp-pppoe.so eth1
mtu 1492
noauth
defaultroute
usepeerdns
user "****@****.****"

```

and here's my plog ouput:

```
jochex@delorean:/etc/ppp/peers$ plog
Dec 28 21:52:18 localhost pppd[9058]: Couldn't increase MTU to 1500
Dec 28 21:52:18 localhost pppd[9058]: Couldn't increase MRU to 1500
Dec 28 21:52:19 localhost pppd[9058]: Couldn't increase MRU to 1500
Dec 28 21:52:19 localhost pppd[9058]: PAP authentication succeeded
Dec 28 21:52:19 localhost pppd[9058]: peer from calling number 00:90:1A:41:7C:44 authorized
Dec 28 21:52:19 localhost pppd[9058]: Cannot determine ethernet address for proxy ARP
Dec 28 21:52:19 localhost pppd[9058]: local  IP address 200.112.109.155
Dec 28 21:52:19 localhost pppd[9058]: remote IP address 10.52.104.3
Dec 28 21:52:19 localhost pppd[9058]: primary   DNS address 200.28.4.129
Dec 28 21:52:19 localhost pppd[9058]: secondary DNS address 200.28.4.130

```

as you can see, i changed the mtu at the /etc.../dsl.provider file, but it doesn't seem to the mtu has change it....
plz help

---

### Post by moopere on 2006-01-07
[QUOTE=jochex]:confused: 
I got that problem too.
i can't change the MTU, here's my /etc/ppp/peers/dsl-provider

```

plugin rp-pppoe.so eth1
mtu 1492
noauth
defaultroute
usepeerdns
user "****@****.****"

```

and here's my plog ouput:

```
jochex@delorean:/etc/ppp/peers$ plog
Dec 28 21:52:18 localhost pppd[9058]: Couldn't increase MTU to 1500
Dec 28 21:52:18 localhost pppd[9058]: Couldn't increase MRU to 1500
Dec 28 21:52:19 localhost pppd[9058]: Couldn't increase MRU to 1500
Dec 28 21:52:19 localhost pppd[9058]: PAP authentication succeeded
Dec 28 21:52:19 localhost pppd[9058]: peer from calling number 00:90:1A:41:7C:44 authorized
Dec 28 21:52:19 localhost pppd[9058]: Cannot determine ethernet address for proxy ARP
Dec 28 21:52:19 localhost pppd[9058]: local  IP address 200.112.109.155
Dec 28 21:52:19 localhost pppd[9058]: remote IP address 10.52.104.3
Dec 28 21:52:19 localhost pppd[9058]: primary   DNS address 200.28.4.129
Dec 28 21:52:19 localhost pppd[9058]: secondary DNS address 200.28.4.130

```

as you can see, i changed the mtu at the /etc.../dsl.provider file, but it doesn't seem to the mtu has change it....
plz help[/QUOTE]

I think this is a bug, I've just hit a wall on this one too.  

Last night my debian pppoe box died and I thought it might be a good chance to rebuild it with an ubuntu unit.  Everything went well, up to the point of actually using the internet for anything.  My provider can't/won't pass overly large packets and I used to have to squeeze them down to 1412 bytes.  Breezy won't let me do it though - it borks in the log at 1500 as on your box (above) then settles on 1492 (do an ipconfig and you'll see) - 1492 for me is too large though, and the mtu stanza in dsl-provider is being ignored.

Had to go back to debian for the router (by the way, running Debian with a 2.4.x kernel is _much_ _much_ _much_ quicker on old machinery than ubuntu 2.6.x).

I intend to look into this a little more tonight and will post a bug report if I can't find a work around.

Cheers,
Craig

---

### Post by mips on 2006-01-07
1. If you have a **router** I would recommend you let the router handle the PPPoE & authentication stuff, no need to do it in Linux and add extra overhead to you pc.

2. Slow and Sites not opening could indicate IPv6 & DNS issues, look at the **Wired Ethernet Troubleshooting Process** sticky to sort this out, [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

3. If you still need to change your MTU settings look here;
[http://ubuntuforums.org/showthread.php?t=82093&highlight=MTU](http://ubuntuforums.org/showthread.php?t=82093&highlight=MTU)
[http://www.ubuntuforums.org/showthread.php?t=104371](http://www.ubuntuforums.org/showthread.php?t=104371)

---

### Post by jochex on 2006-01-08
thanks for the attention, but i had to change the distribution to a old mdk.
i hope than in the Ubu 6.04 can fix that problem.

i think too this is a bug. how we can report it on bugzilla?

---

### Post by moopere on 2006-01-15
[QUOTE=jochex]thanks for the attention, but i had to change the distribution to a old mdk.
i hope than in the Ubu 6.04 can fix that problem.

i think too this is a bug. how we can report it on bugzilla?[/QUOTE]

I've reported it on launchpad:

[https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652](https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652)

Could someone reading this confirm the problem on launchpad?

Cheers,
Craig

---

### Post by moopere on 2006-01-19
[QUOTE=moopere]I've reported it on launchpad:

[https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652](https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/28652)

Could someone reading this confirm the problem on launchpad?

Cheers,
Craig[/QUOTE]

Anyone watching this thread but not able to do anything about the bug might be interested to know that temporarily pointing your sources.list file to dapper instead of breezy and upgrading the package "ppp" will get you over this hump.  

As of this date there are few dependencies and only one package forced upgrade so the impact on your breezy should be minor.

Cheers,
Craig

---

### Post by GTvulse on 2006-01-19
[QUOTE=moopere]Anyone watching this thread but not able to do anything about the bug might be interested to know that temporarily pointing your sources.list file to dapper instead of breezy and upgrading the package "ppp" will get you over this hump.  

As of this date there are few dependencies and only one package forced upgrade so the impact on your breezy should be minor.
[/QUOTE]

In principle, this should be handled by a backport, or an update. And yes I can confirm it. Will post to launchpad and request a fix or backport.

---


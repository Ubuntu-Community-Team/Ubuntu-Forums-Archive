---
title: "Wireless woes and the Network Configuration panel"
date: 2004-12-26
forum: Networking &amp; Wireless
---

### Post by offby1 on 2004-12-26
I'm just a bit new to the Ubuntu situation, as my other posts will attest, but I've generally got the hang of working with *desktop* linuxes.

Right now, though, I've got Ubuntu installed on my laptop, and there are some issues with the configuration of networking that are giving me fits.

Okay, first thing:  I connect to several different wireless networks, some of which use WEP (different keys per network, call them "wep1" and "wep2" for now) and others of which do not -- those last, though, don't always have the same essid, although they all use the same connect method (and in fact are just different access points to the same school network, call it "school")

The problem I'm having is that switching from profile to profile in the network control applet doesn't seem to work properly.  Nor does it really appear to detect the current profile all that well.  Right now, for example, I'm on wep2, which has a named profile already set up for it with the essid and wep key, which I have set the Networking profile to, but in the Networking panel after a reboot, I now have "Unknown" as my profile name.

This occurs at "wep1" and and "School" as well.  Furthermore, switching from, say, "school" to "wep1" and back (the most common operation) seems to require a semi-random combination of profile switches in the Networking panel and command line ifup/ifdown commands on the eth1 interface -- the latter part is a big problem, since my less tech-inclined girlfriend, who shares the laptop with me, is not going to tolerate things like that when she tries to use the net.

Hardware-wise, here's what I have:

Linksys WPC11.3 PCMCIA WiFi card
at wep1: DLink DI-514 wireless 802.11b router, doesn't do DHCP, just acts as an access point, DHCP is provided by another system on the network and is working flawlessly.
at wep2: Linksys router of some kind, has an issue where sometimes I cannot get a connection that works -- it'll grant an IP and my resolv.conf will be fine, but I cannot ping and have no route to host for any system in the local subnet or the wider internet.  This is NOT an issue for the winXP laptop that is connecting (1m away, no less) to the same network.
at school: DHCP, but as to what specifics are there, I have no idea.

Sony Vaio PCG-GR370 laptop, everything else seems to work just fine.

Can anyone offer me any tips on making this Networking thing work more sanely?  I'm getting a bit aggravated with the whole thing, but I really do like Ubuntu and would like to see it work out for me.

---

### Post by chascon on 2005-05-01
I'm having the same problem with the same router but with a syntax usb-400 that uses the prism2_usb module and the linux-wlan-ng driver on hoary 2.6.10-5 powerpc.

---


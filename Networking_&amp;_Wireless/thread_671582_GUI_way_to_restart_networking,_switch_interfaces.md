---
title: "GUI way to restart networking, switch interfaces?"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by clsgis on 2008-01-18
Sorry if this is just too dumb.

I just added the Linuxant controllerless modem driver to a friend's Ubuntu 7.10 box.  Seems to work.  Now it's got three interfaces: wlan0, eth0, and ppp0.  When I want to switch among them, I get a terminal and go "**ifdown eth0 && pon**" or some such thing.  The Debian Way.

But my friend is not going to want to get a terminal and type commands all the time.  Sometimes she can use the upstairs neighbor's wireless, with permission.  Other times she needs to dial out.   (I set her up on freeshell.org.)  So I get the Network Settings dialog from the toolbar, and I can describe all three interfaces.  But I can't find the "connect" button!  I can get the same exact dialog from System -> Administration -> Network, again no connect button.  I tried Places -> Network and got Nautilus.  I tried Places -> Connect to Server and got some kind of GUI front end to various network clients.  I tried starting ssh to a known host but it didn't trigger an **ifup**..

  I've never done Linux networking through a GUI before.  Where's the button that says okay, dial out now?

---

### Post by Floppyjoe on 2008-01-18
> **clsgis said:**
> Sorry if this is just too dumb.

I just added the Linuxant controllerless modem driver to a friend's Ubuntu 7.10 box.  Seems to work.  Now it's got three interfaces: wlan0, eth0, and ppp0.  When I want to switch among them, I get a terminal and go "**ifdown eth0 && pon**" or some such thing.  The Debian Way.

But my friend is not going to want to get a terminal and type commands all the time.  Sometimes she can use the upstairs neighbor's wireless, with permission.  Other times she needs to dial out.   (I set her up on freeshell.org.)  So I get the Network Settings dialog from the toolbar, and I can describe all three interfaces.  But I can't find the "connect" button!  I can get the same exact dialog from System -> Administration -> Network, again no connect button.  I tried Places -> Network and got Nautilus.  I tried Places -> Connect to Server and got some kind of GUI front end to various network clients.  I tried starting ssh to a known host but it didn't trigger an **ifup**..

  I've never done Linux networking through a GUI before.  Where's the button that says okay, dial out now?

To dial out with a dial-up modem you might check out this guide:
[http://ubuntuforums.org/showthread.php?t=308098]("http://ubuntuforums.org/showthread.php?t=308098")

---

### Post by clsgis on 2008-01-20
Perhaps I was too verbose.

I am looking for the GUI equivalent of the shell commands "ifconfig eth0 down",  "pon" and "poff".

I already know how to use the shell to configure serial ports, winmodems, pppd, the resolver, and the routing table.  Those are the topics addressed in the guide at showthread.php?t=308098 and the DialupModemHowto it refers to.  My question is about Ubuntu's Graphical User Interface to some of those things, not about the things themselves.

Incidently, [DialupModemHowto ]("https://help.ubuntu.com/community/DialupModemHowto")says "Some people have had a problem with the modem dialing during bootup. This may be related to setting the modem as default route to the internet on the Options tab of Interface properties."  Apparently not.  Since installing the Linexant drivers, my Ubuntu-7.10 system dials out on boot.  The "Set modem as default route to internet" flag in Network Settings is turned off.  Not only that, but it dialed out when I used Network Settings to change the "Wired connection" from "Enable roaming mode" to "Address: dhcp".  That's another GUI bug.
:sad:

---


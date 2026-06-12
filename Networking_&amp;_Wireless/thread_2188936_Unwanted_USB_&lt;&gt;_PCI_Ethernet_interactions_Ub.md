---
title: "Unwanted USB &lt;&gt; PCI Ethernet interactions Ubuntu 13.10"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by jdallara on 2013-11-19
Hello,

  I'm having an interaction between my Internet connection via my USB port and my LAN connection via my PCI Ethernet interface card.  My Internet connection is through my Iphone via a USB porton my desktop computer.  It shows up as 'Wired Connection 2' and 'Ethernet Network (Apple Iphone)' on the networking icon pop-up menu.  My LAN connection is through the PCI Ethernet Interface card in my desktop computer and it connects to my other computers and printer.  It shows up as 'Wired Connection 1' and 'Ethernet Network (RealTek PCI Express Fast Ethernet Controller)'.  Both interfaces work just as expected IF you connect them in the proper order.  The Iphone has to be connected FIRST, then the PCI card can be connected and disconnected at will.  If the PCI card is connected FIRST, then the Iphone is plugged into its USB cable, it will show as connected in the pop-up menu, BUT no communication will go through it.  Disconnecting and then re-connecting the PCI connection will allow communication through the Iphone.  Is there a way around this interaction?  I plug and un-plug my Iphone often during the course of the day and I'd like to not have to remember to drop the LAN connection each time I plug the Iphone back in.

Thanks in advance,

Jon.

---

### Post by varunendra on 2013-11-20
Sounds like a routing table issue to me. Check if you are experiencing something like what is discussed/explained in [post=12819114]this post[/post].

---

### Post by jdallara on 2013-11-20
Thank you very much!  Close enough to what I was seeing.  I'm working on an if-up.d script.

Thanks again,

Jon.

---

### Post by varunendra on 2013-11-21
You're welcome !

Since I am also just a learner in this field, I'd be very much interested in finding a decent solution to it. Hope you are better than me regarding the scripting stuff. :)

---

### Post by jdallara on 2013-11-22
Here's what I came up with.  Nothing fancy, just brute force, basically just having the system do what I had been doing manually.

eth0 is the wired LAN
eth1 is the USB port for my Iphone

script in /etc/network/if-up.d:
#!/bin/sh
# filename: eth1-up
# This script will disconnect and then reconnect the LAN interface
# when the Iphone is plugged into its USB cable as eth1

if [ "$IFACE" = eth1 ]; then
  /usr/bin/nmcli dev disconnect iface eth0
  /usr/bin/nmcli con up id 'Wired connection 1' iface eth0
fi

---

### Post by varunendra on 2013-11-22
Well, simpler is better, fancy=bugs :)

Besides, as long as it works, who cares !

---


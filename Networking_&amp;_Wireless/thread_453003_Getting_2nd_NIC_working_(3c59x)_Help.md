---
title: "Getting 2nd NIC working (3c59x) Help"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Forum Joe on 2007-05-23
I've been running a server with Ubuntu 7.04 server edition for a while.  Everything is fine, except that the network connection is intermittent because I'm using a known faulty NIC.  (just has a loose connection that is easily knocked out).

Anyway, I installed a second NIC, intending to switch it over to the primary, but I can't get it running.  If I plug it into my router there's no connection, I can't ping anything.

Looking around the forum here, I've discovered a few other suggestions, so I can give this information:

```
> lspci

...
00:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:0c.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```

The top one is the new one I'm trying to get working, the bottom one is the old one that is still active.

```
> dmesg | grep eth

[    9.316788] eth1: ADMtek Comet rev 17 at Port 0xec00, 00:05:1C:0D:E9:45, IRQ 16.
[   26.703345] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   38.787701] eth0: no IPv6 routers present

```

```
> lsmod | grep 3c59x

3c59x                  46760  0 
mii                     6656  1 3c59x

```

So as far as I can tell, it can detect the card fine, and the drivers for the 3c59x are there.  How do I get the card running from here?

---

### Post by lloyd_b on 2007-05-23
Take a look at the file "/etc/network/interfaces".  What you probably need is to define an "iface" entry for the new NIC, and add an associated "auto" line.  For example, if there's no "iface eth1" in the file, just add the following two lines:
```
auto eth1
iface eth1 inet dhcp
```
Then, in a terminal window, run "sudo /etc/init.d/networking restart".

Note that you'll need a "sudo" or "gksudo" to be able to edit this file - it requires root permissions.

These instructions assume that the card will get it's IP address and other config info via DHCP, from the router.  

If the above lines are already in this file, then please post the following:

1.  The output from the "ifconfig" command (run in a terminal window)
2.  The output from the "route -n" command (run in a terminal window)

Lloyd B.

---

### Post by Forum Joe on 2007-05-23
Ok, thanks.  I'll try those.

If I've enabled this NIC as eth1 though, what happens when I take the original eth0 interface out?
Will this interface still function as eth1, or be renamed to eth0?

I ask because, when I first installed the card, I took the other one out first.  When the new card didn't work, I put the old card back in to allow connectivity during testing and stuff.  Surely if it was just a case of activating eth1 then the card should have worked when it was by itself in the server, because then it would have been eht0, no?

---

### Post by lloyd_b on 2007-05-24
> I ask because, when I first installed the card, I took the other one out first. When the new card didn't work, I put the old card back in to allow connectivity during testing and stuff. Surely if it was just a case of activating eth1 then the card should have worked when it was by itself in the server, because then it would have been eht0, no?

Not necessarily.   Each time you put NIC into a machine, the "MAC" (Media Access Control, I think) address is saved by the system, and associated with the "eth..." entry. If you look in the file "/etc/iftab", you should see a list of all know interfaces, and their associated MAC addresses.  So when a NIC is detected, its MAC address is read, then compared to the MAC addresses stored in "/etc/iftab".  If it matches, then the NIC is assigned to the interface associated with that MAC address.  If there's no match, then the NIC gets the next unused interface ("eth2", "eth3", etc).

This is done so that if you have two or more NICs, you can reliably tell which will be eth0, which eth1, etc, if if by some chance the system detects them in a different order after a reboot.

So once that new card is defined in "/etc/iftab" as "eth1", it is going to remain "eth1", even if you remove the other card.

I *believe* that if you clear the "/etc/iftab" file and then reboot, then things will reset so that the first detected NIC will become "eth0" - you may or may not want to do this (it might be simpler than modifying the "interfaces" file).

Lloyd B.

---


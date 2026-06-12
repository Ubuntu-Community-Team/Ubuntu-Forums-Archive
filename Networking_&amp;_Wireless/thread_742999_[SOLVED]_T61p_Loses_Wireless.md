---
title: "[SOLVED] T61p Loses Wireless"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-04-02
My T61p has a built-in wireless card and was working. I hooked it up to a wired connection, and now the wireless information is missing from System -> Administration -> Network 


This is what is in /etc/network/interfaces

auto lo
iface lo inet loopback

I've tried restarting the network without the eth0 plugged in.

Here's some output:

 lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


What do I need to do to restore wireless?

---

### Post by kextyn on 2008-04-02
I'm having a similar problem on a T43.  I installed a USB wireless adapter and now I can't get the internal, mini-pci card to show up.  lspci shows it but it never comes up as an interface.

---

### Post by cmnorton on 2008-04-03
Most other recent posts in these forums dealt with getting wireless configured on Thinkpad or other laptops or switching to WPA encryption. I had wireless connectivity and then did not.

This turned out to be having the physical wireless switch on the bottom cover of the T61 at the front switched to off, something that was not deliberate.

---


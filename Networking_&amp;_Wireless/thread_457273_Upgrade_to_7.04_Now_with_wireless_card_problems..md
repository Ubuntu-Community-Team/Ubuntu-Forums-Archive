---
title: "Upgrade to 7.04? Now with wireless card problems."
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by diacronic on 2007-05-28
Before I decided to upgrade it worked fine. Now the card has no lights on , doesnt show up in the network. I dont have the windows drivers or wrapper installed on the computer to get it to work either. I have been seeing a lot o problems with people and the wireless cards and 7.04, if i would have known this before-hand i would have never updated it. anyone have any suggestions ?  I can't use the desktop wired because its on the complete other side of the house. :(





iwconfig shows:

lo               no wireless extensions.

eth0           no wireless extension.




lspci -v shows :

00:06.0 Ethernet controller: Belkin Wireless PCI card - F5D6001 (rev 20)
             Subsystem: Belkin Wireless PCI Card - F5D6001
             Flags: bus master, medium devsel, latency 32, IRQ 11
             I/O ports at ea001000 (32-bit, nonprefetchable) [size=256]

---

### Post by red_smeg on 2007-05-28
Hi,

I have a similar problem.  Never could get the wireless working (netgear 311v2) now works great with acx version in Fawn but....

It does everything except get an ip address from the router ???  it connects it shows signal strenght but won't go any further.

Every other computer on the network works ok .... even switched off all the security to test it.  using 192.168.1.1 as the DHCP server.

any ideas anyone ??

---

### Post by diacronic on 2007-05-28
Anyone ? Noone has any idea that I could try ? Or at least help me figure out what is wrong with it.

---

### Post by kevmore on 2007-05-29
The easiest way to fix the problem is to get a hold of the old versions of network manager, somebody posted them and they were two packages that worked just like a good old windows program.  I clicked on the link and then clicked on the files and they did whatever they had to do and after I restarted my laptop, the wireless worked.  The only thing that happens is that you always have two applications that want to be updated, but don't let them!!

---

### Post by diacronic on 2007-05-29
how would network manager fix it ? when it cant even show the card under the normal network settings in the admin section. the card only shows up in the hardware.

---


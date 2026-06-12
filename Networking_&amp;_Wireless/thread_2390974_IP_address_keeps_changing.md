---
title: "IP address keeps changing"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by Liamdale on 2018-05-04
I have recently bought a new computer but kept my old one for certain tasks.  The old computer has ubuntu 14.04 and the new one mint 18.2 (KDE).  On the new computer I have written a script to sync three folders with the ones on my new computer.  I use Rsync.  The script works fine but the old computer keeps changing IP address.  I don't know why.  I am wondering if the system updates have some thing to do with it.  So far since I've written the script the IP has changed twice.  I adjust the script to the new IP and it works.

Why does it change and how to solve the problem

---

### Post by ank2 on 2018-05-04
Are they connected in an internal network with IP addresses like 192.168.X.Y?

I suppose the old computer gets its IP address via DHCP. If it's WLAN select its source, then IPv4 and set it to "Manual". Below also provide a fixed IP address. Should work similar if connected via Ethernet.

---

### Post by Liamdale on 2018-05-04
That is correct, I am connected by an internal network with IP addresses like 192.168.X.Y.  It's the last number that changes 101 to 104 to 106.  I have a cable connection via my router. (ssh connection)

---

### Post by ank2 on 2018-05-04
Ok. Then set the IP address acquisition to "Manual". That will fix the problem.

---

### Post by Liamdale on 2018-05-04
Took me a while to realize where to set the "Manual" setting.  Don't play around with network settings very often.  I found it in Editing the "Wired connection 1" > IPv4 settings.  Changed the automatic DHCP to Manual and entered the current IP address, Netmask and gateway. (all taken from Network info icon on Ubuntu.
Did a sync command on new computer and it worked.  If, in a month, the IP does not change I'll come back to this tread and mark it as solved.

Thanks for the help AnkMan

---

### Post by The Cog on 2018-05-04
With DHCP, the router tracks IP addresses and allocates them to computers that ask for an address. There is a danger that if you use a manual IP address, the router may happen to allocate that same address to a different device on your network so that you have two boxes with the same address. That would cause you hours of grief trying to figure out what's wrong with your network. It would be better to go into the router config and tell it to always allocate the IP address you want to that MAC address. Or find out if the router only allocates addresses from a limited pool of numbers, and use an address outside that pool.

---

### Post by Liamdale on 2018-05-04
Thanks The Cog, I will do that.

---

### Post by ank2 on 2018-05-05
Good point I forgot to mention!

Although routers I came across seem to silently reserve an once allocated IP address for this computer again. But I might just have been lucky... But I usually use "high" addresses starting with 200 while these routers usually start allocating at 100.

Anyway, good point. :-)

---

### Post by SeijiSensei on 2018-05-06
That router has a pretty poor DHCP server installation if it keeps giving out new addresses to the same device.  Most well-designed DHCP servers, like isc-dhcp-server, keep track of the addresses they assign to MAC adapter addresses and give the adapter the same address each time.

---


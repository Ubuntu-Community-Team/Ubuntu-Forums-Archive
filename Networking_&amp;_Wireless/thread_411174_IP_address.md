---
title: "IP address"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by creamcheeze77 on 2007-04-16
i can't seem to find the IP address assigned to my computer by the router.  It should be 192.168.1.1.xxx, but i cant find the extension anywhere.  i need it to enable some ports for some programs.  is there any way to find this?

---

### Post by Floppyjoe on 2007-04-16
> **creamcheeze77 said:**
> i can't seem to find the IP address assigned to my computer by the router.  It should be 192.168.1.1.xxx, but i cant find the extension anywhere.  i need it to enable some ports for some programs.  is there any way to find this?
ifconfig in the terminal
click on Applications/Accessories/Terminal.

---

### Post by PurplePenguin on 2007-04-16
> **creamcheeze77 said:**
> It should be 192.168.1.1.xxx, but i cant find the extension anywhere.

Looks like you've got an extra .1 in there, too.

---

### Post by PurplePenguin on 2007-04-16
You'll want to give yourself a static IP address if you're interested in opening ports.

To assign a static IP address, run ifconfig like Floppyjoe asked you to.  Write down your gateway address (ie. your router).  Then go to System->Administration->Networking (in Edgy, anyway, don't know about the others), select your connection, then Properties, and select Static IP instead of DHCP.  You'll have to give your computer a static IP address (eg. 192.168.1.xxx - choose a number for the xxx part), subnet mask (255.255.255.0) and gateway address (which you just wrote down).

Now every time you reboot, you'll have the same IP address.  If you don't do this, you'll go crazy if DHCP gives you a different IP address and your ports are no longer forwarded to the right place.

---

### Post by Erlander on 2007-04-17
> **PurplePenguin said:**
> Looks like you've got an extra .1 in there, too.

Not necessarily.

My pc's are 192.168.2.2  192.168.2.3  and 192.168.2.4

Rob

---

### Post by Floppyjoe on 2007-04-17
> **Erlander said:**
> Not necessarily.

My pc's are 192.168.2.2  192.168.2.3  and 192.168.2.4

Rob

I think he means an extra period because:
> 192.168.1.1.xxx
is in the original post. So unless he is using an IPV6 router it is not likely to have the last. XXX part.

---


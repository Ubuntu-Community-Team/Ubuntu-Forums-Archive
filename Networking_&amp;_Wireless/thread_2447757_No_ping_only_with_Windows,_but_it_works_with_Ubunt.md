---
title: "No ping only with Windows, but it works with Ubuntu (Dual boot)"
date: 2020-07-25
forum: Networking &amp; Wireless
---

### Post by WhiteTigerIT on 2020-07-25
I have three PCs with Dual boot Win10Pro and Xubuntu 18/20
I then have a Raspberry Pi4 with Ubuntu Server 20.04.


Two PCs have two network cards and Wi-Fi. A PC has a network card and Wi-Fi.
All connections are active.


If from a PC in Windows I PING the other two I can get the address of all the cards and all the Wi-Fi.
And I can get the addresses whether the other two PCs are in Windows or if they are in Xubuntu.
So PING works, both in Windows and in Xubuntu.


On the Raspberry then things change.
If the PCs are on Windows I can't ping.
If the PCs are in Xubuntu, pinging works.


I checked, the IP addresses are correct and, as I said above, in Windows PING work.
It is only from Raspberry that I cannot ping on Windows PC.

---

### Post by TheFu on 2020-07-25
Can you ping by IP address? If so, it isn't a "ping" problem.

I suspect it is a name resolution problem.  Name resolution for Unix isn't automatic. It needs to be setup using some method.  For Ubuntu desktops, avahi has been added for years, which sorta does this.  Ubuntu Server does not include avahi - thank Dog.
Name resolution can be handled by 
[LIST]
[*]running a DNS server
[*]setting up /etc/hosts on every system with all the IP-to-name lookups
[*]running avahi (zeroconf) on every system and using {hostname}.local for resolution
[*]running NIS or NIS+ with a "hosts" DB
[/LIST]
perhaps a few other methods.  So, it is up to you to decide how to accomplish name resolution on your LAN.  I would caution against having multiple solutions, since that can lead to "split brain" issues --> confusion.

For under 5 systems, the /etc/hosts method is pretty easy.  A little ansible task can manage it for all Unix systems and perhaps Windows, though I've never gotten Ansible working to manage Windows. Really didn't try too hard.

---

### Post by WhiteTigerIT on 2020-07-26
> **TheFu said:**
> Can you ping by IP address? If so, it isn't a "ping" problem.

I m using only IP address

---

### Post by TheFu on 2020-07-26
> **WhiteTigerIT said:**
> I m using only IP address

Does it work or not?

---

### Post by WhiteTigerIT on 2020-07-28
> **TheFu said:**
> Does it work or not?
No! 
I'm using IP address and ping doesn't work

---

### Post by durexlw on 2020-07-29
I kinda thought windows 10 firewall blocks icmp (ping requests) by default. So pinging 'from' windows shouldn't be a problem, but pinging 'to' windows, I don't expect that to work out of the box due to firewall rules.

So if I understand correctly: you have 2 windows, one ubuntu and one raspberry.
Try pinging from the ubuntu to the windows, see if that works.

---


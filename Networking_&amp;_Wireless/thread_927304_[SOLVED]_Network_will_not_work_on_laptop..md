---
title: "[SOLVED] Network will not work on laptop."
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2008-09-22
I'm running Ubuntu 8.04.1 on a Gateway Solo 2500 laptop.  Try as I might, I can not get my internet connection to work.  I'm using a 3Com Megahertz 10/100 LAN Cardbus PC Card (eth0).

Using my desktop in either XP or Ubuntu (dual-boot), the network works fine, and when I directly connect the desktop to the laptop, I can ping back and forth so the card is not the problem.  

I've tried DHCP and static IP to no avail.  ISP is zoominternet.

Thanks.

---

### Post by Iowan on 2008-09-22
How does the laptop connect (attach) to internet - router, modem? Some modems "lock onto" MAC address, so they must be power-cycled to allow a different computer access.

---

### Post by marshmallow1304 on 2008-09-22
> **Iowan said:**
> How does the laptop connect (attach) to internet - router, modem? Some modems "lock onto" MAC address, so they must be power-cycled to allow a different computer access.

It's connected to what I believe is a router (the ISP people are very mysterious about it; I don't think they even allow users to access config).  It takes input from a cable TV jack and outputs network and phone.  I'll try resetting it after disconnecting the desktop and before connecting the laptop.

---

### Post by marshmallow1304 on 2008-09-22
I reset the router and tried it with DHCP, but no luck.

BTW, I'm getting a link light on both the PCCard and the router.

---

### Post by Iowan on 2008-09-22
If it works, you may wish to connect a router of your own between "the box" and your network - that way, either the desktop or laptop (or both...) could access internet without resetting "the box".

---

### Post by marshmallow1304 on 2008-09-22
> **Iowan said:**
> If it works, you may wish to connect a router of your own between "the box" and your network - that way, either the desktop or laptop (or both...) could access internet without resetting "the box".

Yes, I was planning to do that eventually, but first I want to get the laptop to work.

---

### Post by marshmallow1304 on 2008-09-29
Some new information:

The "box" is an Arris TM502G Cable Modem.  In addition to a CAT-5 port, it has a USB port.  I've tried the USB with XP, and though the device seems to install, it refuses to assign an IP.  I've also tried the USB with Ubuntu on the laptop and that doesn't work either.

I've also found a driver disk for the USB connectivity of the cable modem, but I have no idea how to or if it's even possible to install the driver in Ubuntu.


Getting the USB to work would be a temporary solution at best because it would be dreadfully slow (USB 1.1) and I don't have a long USB cable (defeating the purpose of using a laptop), but it would be a small victory.

---

### Post by marshmallow1304 on 2008-10-09
Well, I've figured it out thanks to [this page]("https://answers.launchpad.net/ubuntu/+question/42631").  By following the advice found there, I did 

sudo /etc/init.d/networking restart 

with great success.  I have yet to find out whether I have to do that every time I switch back and forth between laptop and desktop or if once was sufficient.  Also,  I do have to power-cycle the modem when switching.  Now to find a cheap router...

---


---
title: "Computer adress"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by tashe on 2008-04-11
I need to register me and my roommate to a webpage. However, they don't allow  2 registrations form the same computer. We tried to register from his computer, but since we are sharing the internet connection, we also failed. 
Can someone tell me which are ways that the web page admins know that we are registering from the same place? Is it the  IP, MAC adress. Can anyone tell me all the ways that they are using?
Really appreciate it.
Cheers

---

### Post by wired465 on 2008-04-11
It's most likely IP address, try resetting your router/modem. Also, there are ways to change the MAC address. I'm not sure the exact program, maybe 'macchanger'?

---

### Post by tashe on 2008-04-11
Our IP s are set to: Obtain an IP adress automaticaly. Is there a chance that they will be the same?

---

### Post by countrylane on 2008-04-11
Are you using 2 different computers at 2 different times, as in your roommate is connected to the network....he finishes...logs off...disconnects the LAN cable, then you connect your PC to the LAN cable, boot up and try to access the network, or are you both connected simultaneously  through a router?  Or is one computer connected to the second computer, which is connected to the wall?

---

### Post by tashe on 2008-04-11
This is  how its set up:
We have a cable modem with a LAN cable (Computer A)  and USB cable (Computer B)  outs. I use the LAN cable he uses the USB cable. We also have third computer (Computer C) which shares the Internet connection with the one that has USB cable connection. So 2 computers are online at a time. Also, A and C can't be online at the same time cause there is only one cable in that room. B is in other room.

So I registered on the website from A, turned off the computer, and then turned on C and registered but it displayed error.

---

### Post by Iowan on 2008-04-12
What does your computer show for IP address? I'm still on dialup, so haven't learned all the marvelous things about cable modems - but I suspect the modem is acting as a NAT (Network Address Translation).  It may act as your DHCP Server - giving you a "local" address.  All internet traffic looks like it came from the modem's external address. _IF_ the modem happens to get it's address via DHCP from your ISP, (this is the part I don't know about) resetting the modem may get it a different IP address.  If the modem has a static address, you may have a problem registering on the website.

---


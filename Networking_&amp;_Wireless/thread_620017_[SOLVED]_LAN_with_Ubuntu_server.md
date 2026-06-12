---
title: "[SOLVED] LAN with Ubuntu server"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by Zer0d on 2007-11-22
This is how I want the structure of the LAN to be:
[IMG]http://img148.imageshack.us/img148/7686/networkop6.jpg[/IMG]
The server will have two network interface cards and all traffic will go through them.

[B]1 NIC: Receive all data from the internal LAN and push it to the second NIC.
2 NIC: Send/Receive data from the Internet.[/B]

The LAN will be under a commune network so some ports are blocked, that's where the Proxy server will come in handy. I need to find a solution for the server so it knows what port's to send to a Proxy server and which should go straight into the Internet without Proxy. Is there tool's for such configurations?

There will also be a DHCP server that will send IP-Addresses to the Switch on the internal network, whom will be distributed to the personal computers.

The problem is that I'm not sure how to make these two NIC's communicate with each other on Ubuntu server, some help or information would be greatly appreciated.

---

### Post by fvds on 2007-11-22
Here's a link:
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

### Post by Zer0d on 2007-11-23
Thank you for putting me on the right track :)

---


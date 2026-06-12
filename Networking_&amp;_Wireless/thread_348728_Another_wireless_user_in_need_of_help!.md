---
title: "Another wireless user in need of help!"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by B204FM on 2007-01-29
OK, I've read through the help section for setting up my wireless connection, and I'm still not having any luck. I'm using an Edimax 7064g+, and I'm guessing that the chipset I have is the Ralink RT2500. There's no mention anywhere with the Ralink software what chipset I'm using, but as my network name is RT2561_6, I'm just assuming it's that one.

On the instructions it says that I should just enable the connection and it'll automatically find the network, but nothing's happening. I've then tried taking down the IP address, gateway etc. just to make sure it wasn't that, but again, nothing happens.

There's probably something really stupid I'm missing out on, but this is my first day with Ubuntu so I'm a proper n00b :)

Oh yea, another thing. Is the RT2561_6 my ESSID? And if not, how do I find out what it is?

Thanks in advance!

---

### Post by dbqp on 2007-01-29
> **B204FM said:**
> OK, I've read through the help section for setting up my wireless connection, and I'm still not having any luck. I'm using an Edimax 7064g+, and I'm guessing that the chipset I have is the Ralink RT2500. There's no mention anywhere with the Ralink software what chipset I'm using, but as my network name is RT2561_6, I'm just assuming it's that one.

On the instructions it says that I should just enable the connection and it'll automatically find the network, but nothing's happening. I've then tried taking down the IP address, gateway etc. just to make sure it wasn't that, but again, nothing happens.

There's probably something really stupid I'm missing out on, but this is my first day with Ubuntu so I'm a proper n00b :)

Oh yea, another thing. Is the RT2561_6 my ESSID? And if not, how do I find out what it is?

Thanks in advance!

Welcome to the world of Ubuntu!

In your routers control panel, your wireless network is given an SSID - in most cases this defaults to something like MyWLan or LinkSys.  It is just the "name" of the router.

Secondly, do you know if your wireless card is a supported linux device?  If it is not, please search ndiswrapper in these forums to learn more.  ndis wrapper takes a Windows *.inf driver file and allows it to be used in Linux.  Go to your Synaptec Manager and search for ndis

We are all noobs at the beginning, just keep learning and we all benefit!

---


---
title: "Xubuntu and ethernet doesn't even work"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by Genecks on 2007-06-01
I recently installed Xubuntu to my computer. I must state before going into detail, that this problem seems to be an all around Internet connection problem. I recently wrote a thread [about my wireless USB not working]("http://ubuntuforums.org/showthread.php?t=460804").

Therefore, I decided to work off the ethernet card and the router. However, even the ethernet card is grabbing a connection. I'm using firefox on Xubuntu, with the wire running from the computer to the router, and a connection is not being established. I don't know why, which is pretty odd. I suppose it has to do with why my wireless USB won't connect. However, I do see it as highly important to solve this ethernet problem. I can't figure out why the Internet isn't working when using a direct, computer to hardware, connection.

Very odd, indeed.

Anyone have some solutions to this problem?

---

### Post by Genecks on 2007-06-01
I think this might be a problem with how hardware is assigned in the computer.

Here's the scenario:

First installation:

During the first installation of Xubuntu on my computer, I had the USB adapter plugged into the computer. At no time did I have the computer plugged into a router through the ethernet card.

The installation processed. I began to use Xubuntu, but I wasn't able to use wireless Internet nor Internet through the ethernet card. Neither could process.

Second installation:

I decided to be a good philosopher and figure out the logical situation I was in. I took out my wireless USB adapter this time and repartitioned and reinstalled. I decided to think back about to the installation and how it was searching for an Internet connection during installation. I typically ignore this part, because I figure the ethernet drivers are well-known for old hardware. But I decided to connect the connect via wire from the ethernet card to the router during the installation of Xubuntu.

After the installation, I was able to use the Internet via the ethernet port. Sure, this is ok; but I want to use the wireless USB adapter. I actually found that network information I wanted to know about in another thread inside of the system section with Xubuntu's "start menu."

I noticed various listings of network devices. After the _first installation_, I noticed a profile for the USB adapter. However, this wasn't any good, because I could access USB or ethernet.

After the second installation, I didn't see the USB profile. I did, however, see the ethernet profile. I was also able to use the ethernet card for Internet.

So, this leaves me with a couple of other possibilities:

1) Reinstall with the USB netgear connected; also have the wire to the router connected.
2) Reinstall with none of the network devices attached to the router: take out the usb; don't wire the ethernet card to the router.

---


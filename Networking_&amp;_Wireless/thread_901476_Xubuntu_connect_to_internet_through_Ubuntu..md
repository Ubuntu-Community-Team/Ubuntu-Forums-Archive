---
title: "Xubuntu connect to internet through Ubuntu."
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Tjcrazy on 2008-08-26
I have a problem. I have recently set up Xubuntu on a old Intel 900MHz/128 Ram. In the room I have set it up in I only have 1 homeplug adapter to get to the internet with.

I have Ubuntu on a decent computer in the room as well. I have 2 network cards in the decent computer and 1 on the xubuntu. I also have enough ethernet cables.

My problem is that I don't know how I can connect to the internet _through_ my ubuntu computer.

What would I need to do to get a internet conenction on my old xubuntu computer through my new decent ubuntu computer?

Tim

---

### Post by jigsaws on 2008-08-26
You have to:

1. Configure network on Ubuntu and Xubuntu - the same subnet, both can ping each other.
2. Activate ip_forwarding at Ubuntu
3. Configure NAT with iptables at Ubuntu

---

### Post by Tjcrazy on 2008-08-26
Are there any guides to configure NAT with iptables on Ubuntu 8.04? I've searched and can't find any.

---

### Post by jigsaws on 2008-08-26
I've checked google searching "iptables nat howto". [http://www.revsys.com/writings/quicktips/nat.html]("http://www.revsys.com/writings/quicktips/nat.html") looks ok and quite simply. Try it.

---

### Post by Tjcrazy on 2008-08-26
Ive tried, nothi :( Im finding really hard with the settings of the network cards :(

---

### Post by jigsaws on 2008-08-26
First. Give us ifconfig -a from both machines.
Can you ping both?

---

### Post by Iowan on 2008-08-27
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is information about ICS.

---


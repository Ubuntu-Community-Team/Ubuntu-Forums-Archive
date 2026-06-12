---
title: "how do I activate a second ethernet port?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by hodad on 2007-02-11
Hi!

I'm trying to hook up my kids pc to the second ethernet port on the back of my pc.  The first port, eth0, is connected to my internet wireless modem.  I'd like to activate eth1 and connect to the kid'd pc ethernet port.  I'm installing Edubuntu on their pc, but it needs to see thru my pc to the internet to install properly.

I looked at other postings, and looked at /etc/network/interfaces.  eth1 is listed there (along with eth0). eth0 shows all of the address settings for my working internet provider connection, but eth0 only lists DHCP.

How can I start up eth0 for the connection to the kids pc?

THanks!

---

### Post by moshuptrail on 2007-02-11
You are wanting your PC to act as a router.
I have not seen any posts on how to do that, although I have seen a few asking how.
(You could always buy a cheap router, or even a hub might work)
You'll need a special ethernet cable called a cross-over cable to connect from the kids PC to yours.

p.s. Try this.  I did search on "linux as router"
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

### Post by hodad on 2007-02-11
Thanks for the reply!

I've already got a crossover cable for the connection to the kids pc.  The problem right now is that I simply need to electrically "turn on" eth1, so that I can Ping the other pc.  Then I can worry about routing, and any configuration that I need to accomplish in order to get to the internet.

---


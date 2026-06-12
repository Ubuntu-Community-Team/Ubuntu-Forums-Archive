---
title: "Can't connect to Internet"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by ChristopherL on 2007-04-22
I have recently installed Ubuntu 6.10 on a laptop.
It had Windows XP before that, then Internet worked.

I'm connected to a LAN.
I've tested both DHCP and static IP addresses in the
network settings.

---

### Post by josephus on 2007-04-22
need more  details, pls post 

```
ifconfig
sudo lshw -C network
```

---

### Post by ChristopherL on 2007-04-25
ifconfig

---

### Post by josephus on 2007-04-28
Looking at lshw, it's odd that it doesn't list the driver associated with your network card.  I would have expected to see a line driver=e100.  use dmesg to see if there are any errors associated with your network card.

Are you behind a router or connected directly to the internet (not that it really matters, but just want to make sure I know what I'm looking at, because the ip address is really odd if you are sitting behind a router).  

The IP address that I'm looking at is that one that you manually inputted or one assigned to you by the DHCP server.  If it's one that's automatically assigned to you then it's a good sign that something is working.

If you can get an IP address then my first guess is that there is something wrong with your dns server.  Can you access google just based on the ip address (64.233.167.99).  Either ping that address or try your pointing your browser to that address.  If it works then check network-admin and see if you have a dns server assigned.

---

### Post by ChristopherL on 2007-05-01
I don't see anything that is wrong in dmesg.
I'm connected directly to Internet.

That message I got from Ifconfig, was when I used a static IP address. When I use DHCP, I got no addresses.

---

### Post by ChristopherL on 2007-05-01
I can connect to Internet, when using DSL.

---

### Post by josephus on 2007-05-01
i'm a little bit confused as to when you can and cannot connect to the internet.  can you describe the setup a little more?

---

### Post by ChristopherL on 2007-05-02
I can connect to the net using this:
[http://en.wikipedia.org/wiki/DSL](http://en.wikipedia.org/wiki/DSL)

I can't connect to the net using this:
[http://en.wikipedia.org/wiki/LAN](http://en.wikipedia.org/wiki/LAN)

---

### Post by josephus on 2007-05-02
that's not helpful at all.

so you can connect when you plug in directly to the dsl modem, but can't connect when you plug into your router? router is then connected to the dsl modem, or is this a different setup altogether?

---

### Post by jmartrican on 2007-05-02
Christopher, are you behind a router?  I would epxect the following setup:  Modem ->(wan port) Router (LAN port) -> PC.

I'm also a little confused as to when you are able to connect and not able to connect.

---

### Post by jmartrican on 2007-05-02
Also, when you have DHCP enabled, do you get an IP address?  If so are you able to ping your default gateway?  If you are able to ping default gateway then the problem might be with your route table (maybe it has a static route pointing 0.0.0.0 to an obscure IP) or there is a rpoblem with your router connecting to the modem or modem to DSL.  Now a days router and modems for DSL come as one unit, so it could be the case that your router and modem is one.

---

### Post by ChristopherL on 2007-05-02
I have DSL at work and LAN at home.
The Internet works fine at work, but not at home.

At work, my setup is like this:
PC > DSL modem > Telephone line

At home, my setup is like this:
PC > DATA line

In home, I plug the cable directly to the wall through a dedicated Data line.
Every house in our community have this LAN setup.

---

### Post by ChristopherL on 2007-05-02
When using DHCP, I get no IP address.

---

### Post by jmartrican on 2007-05-04
Interesting.  Sounds like a  pretty cool LAN service.

So the problem is not your NIC, else you'd have the problem at work.

1)  Does your link light on your NIC light up when plugged into your home's LAN interface?  The problem could be you home's LAN interface.
2)  Using tethereal do you see the DHCP requests coming out of your PC?  If so do you see a response?  I'm assuming you have DHCP correctly configured in your /etc/network/interfaces file.  If you only have one interface on your PC, you can just use tethereal with no options and it will sniff/display all network traffic.

---

### Post by ChristopherL on 2007-05-07
Wireshark

---


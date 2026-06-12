---
title: "Local Area Networking"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jgoguen on 2008-12-14
Over the next couple of weeks, I'm going to be working on a crash course on Local Area Networks (LANs).  What sort of information about networking would you find useful?  I'm open to ideas and suggestions, they'll all help improve the content and make it more relevant to you :)

---

### Post by Shhnap on 2008-12-14
What do you mean? Are you talking about what they are or how you can program on them or what you can setup accross them?

---

### Post by linuxford on 2008-12-15
Some things I already know but were helpful...
-basic binary stuff and the mask info 255.255.255.0 (and why it is 255 and not 999)
-MAC/IP addresses and how every network interface has to have a unique address.
-Routers (I guess they are really switches?, what is the difference?) has a WAN interface that connects to the internet, and has a LAN interface that connects to the home network
-just found out (makes sense now) but I can use loopback to test a certain function is working like ssh, ie. ssh loopback, to make sure it works before trying to connect outside host.-
-edit the /etc/network/interfaces file for static ip

Things I would like to know more:
- looking at log files and understand them, ie. /var/log/auth.log
- basics of securing your network (don't permit root login if you use ssh)

Other interesting things to do on network
-be able to ssh even when you have a router (port forwarding, use non-standard port)
-setup a file server

---

### Post by jgoguen on 2008-12-15
> **Shhnap said:**
> What do you mean? Are you talking about what they are or how you can program on them or what you can setup accross them?
Probably not how to write network programs, that would fall under a "How To Program" topic better than this.  But what they are and a couple things you can do with them at home (like, for example, set up three computers to share files and print to a printer that's attached to one of the computers) are a couple ideas.  The idea of this is to give you an idea of what a network is and the basics of how to work with one.

---

### Post by Vantrax on 2008-12-15
Look up TCP/IP and how it works, and UDP
Look up port forwarding.
Look up routers, network address translation, and DHCP
The difference between a switch and a hub.
Learn about localhost/127.0.0.1 and loopback devices

If you want to learn alot then look up CCNA training materials.

---

### Post by jgoguen on 2008-12-15
I think there's been some confusion, and I think it's my fault too :)  I'm going to be doing up a wiki page containing information about local area networks.  I'm looking to see what sort of information people would like to see on that page to make it most useful and informative to them.

---


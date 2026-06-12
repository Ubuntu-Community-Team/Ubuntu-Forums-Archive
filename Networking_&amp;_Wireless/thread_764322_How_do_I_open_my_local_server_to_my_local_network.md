---
title: "How do I open my local server to my local network?"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2008-04-23
Hi there!

I currently have my local server (Apache2) working so when I go to 127.0.1.1 it shows the home page ("It Works!"). I have other Kubuntu computers on a local Samba network. When I try 127.0.1.1 in these computers browsers though it can't find the address.

Is there any way that other computers on my local network can see the website on the local server, too?

Many thanks in advance!

Ubuntiac

---

### Post by jetsam on 2008-04-23
127.0.1.1 is a second form of the loopback interface; I'm not quite sure why it's there in Ubuntu.  Anyway, it won't work from another machine.  

Type ifconfig in a terminal and look for the line labeled "inet addr:" on your real eth0 or other nic interface.  The first number on that line is the address you use to connect from another machine on the same lan.  

Assuming you don't have any firewall problems, that address should allow you to browse from your local network by ip address.

---

### Post by Ubuntiac on 2008-04-24
Sweet! Works perfectly thanks!

---


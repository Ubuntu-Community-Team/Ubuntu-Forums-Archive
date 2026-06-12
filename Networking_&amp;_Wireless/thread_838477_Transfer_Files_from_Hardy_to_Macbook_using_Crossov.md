---
title: "Transfer Files from Hardy to Macbook using Crossover Cable"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by StuipedandUgly on 2008-06-23
Hi, I'm switching from my parents computer to a MacBook that I just ordered(I'm going to miss Ubuntu but I need mac for its music mixing and recording capabilities, although I will continue to spread Ubuntu).

Any who I need a guide or something on how to Connect Ubuntu Hardy to a brand new MacBook running OS X Leopard 10.5.2 Using a Cross over Cable. It is only going to be a one time connection to transfer about 200gb of information.

I found this guide:
[http://labs.iamkoa.net/2007/10/27/networking-ubuntu-mac-os-x-fugu-it/](http://labs.iamkoa.net/2007/10/27/networking-ubuntu-mac-os-x-fugu-it/)
I do not know if it exactly pertains to what I'm trying to accomplish; seeing as I only have a crossover cable, no router or any of that jazz. My Question is Will this guide work and if not could you point me in the direction of one that will or even be so kind to as write me one.

Any help would be greatly appreciated.
Thanks in Advance

---

### Post by lswb on 2008-06-23
If avahi (the linux implementation of "zero config" installed by default in ubuntu for some time now) is running on the ubuntu system, the 2 systems should recognize each other automatically. You should be able to ping either system from the other by using the form "hostname.local" shortly after connecting both machines. If not they both should have a self-assigned ip address in the 169.254.x.x range. I'd recommend installing ssh server on the ubuntu system for easy trasfers with sftp or you could use an ftp server or any other method. If sshfs or a ssh server is available for the mac, it would simplify things even more. 

First thing to try is go ahead and connect the systems with the crossover cable, wait a moment, and see if you can ping each from the other. Remember to open any firewalls if necessary) Post again & let us know how you made out or if you need any help setting up sshd or ftp server on one end.

---

### Post by jamadagni on 2008-07-02
Hello. I have a similar setup with Hardy desktop connected to Hardy laptop via crossover cable and I am able to ping from each to the other. However I don't know how to transfer files. In Windows I have Network Neighbourhood and by sharing the required drives/folders I am immediately able to copy files from one system to another. I would like to know how to do this with Ubuntu.

---

### Post by superprash2003 on 2008-07-02
go to places->network

---


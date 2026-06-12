---
title: "Problems with D-Link G624T and Synaptic"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by chinchillart on 2007-05-25
Hi all,
this is my first post.

I've a linux box with Ubuntu, cable connected to a D-Link G624T modem/router. 
The problem is simple, apt-get and synaptic don't work at all.
Instead, I can browse the web and use the mail service.

When I try to upgrade or installa a package I got these errors:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...0.7.04_all.deb](http://archive.ubuntu.com/ubuntu/poo...0.7.04_all.deb)
can't connect to 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu7.1_i386.deb](http://security.ubuntu.com/ubuntu/po...tu7.1_i386.deb)
Can't connect to 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)

...and so on..

Synaptic provides these errors when I try to reload the repository lists:

[http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:) Impossibile connettersi a 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)
[http://it.archive.ubuntu.com/ubuntu/...y/Release.gpg:](http://it.archive.ubuntu.com/ubuntu/...y/Release.gpg:) Impossibile connettersi a 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)
[http://it.archive.ubuntu.com/ubuntu/...lation-it.bz2:](http://it.archive.ubuntu.com/ubuntu/...lation-it.bz2:) Impossibile connettersi a 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)
[http://it.archive.ubuntu.com/ubuntu/...lation-it.bz2:](http://it.archive.ubuntu.com/ubuntu/...lation-it.bz2:) Impossibile connettersi a 192.168.1.1:8080 (192.168.1.1). - connect (111 Connection refused)

and so on..

It seems both synaptic and apt try to connect to the router, to the port 8080, as if it's a proxy.
Don't know how to solve this problem, so please, help me!

Roberto

---


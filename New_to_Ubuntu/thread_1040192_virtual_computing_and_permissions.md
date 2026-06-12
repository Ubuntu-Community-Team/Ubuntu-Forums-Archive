---
title: "virtual computing and permissions"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by csogilvie on 2009-01-15
I have a bit of an interesting problem for you folks out there.  I'm relatively new to ubuntu, but I slowly catching on.

I have a rather interesting problem that I'm hoping somebody might be able to help with...  Here's the situation:

I have a virtual installation of windows XP running on my ubuntu 8.04 64-bit server.  (Virtualbox 2.1, xp sp3)  But, for the life of me, I can't get it to connect properly to the shares on the network.

The network is entirely a windows network with an internal domain.  There is a master file server running win serv 2003.  (Not my choice... but this business is stuck with a windows accounting/inventory software... haven't tried to wine it yet... might give it a wirl soon)

Virtualbox will let you directly mount network shares or will let the virtual machine sit behind a virtual NAT firewall.

Anyway, either or... I have a share setup on the ubuntu machine to a specific folder on the win2003 server.  (The database folder)  But for some reason, the host OS (winxp) says the files are read-only and can't write to them.

I set up the share on the ubuntu machine with the instructions listed on : [http://industriousone.com/mounting-windows-shares-ubuntu](http://industriousone.com/mounting-windows-shares-ubuntu)

In Gnome, and at the bash, I can modify folders, add, edit, delete files no problem.

But when I share that to the virtual machine through virtualbox it can no longer write...  I've doubled checked the share settings and it says "FULL ACCESS"

When I tried to mount the virtual machine directly to the windows network, the same problem results.

The quirk of the situation: I tried installing virtualbox on a winxp machine in the office, and the shares work exactly as expected.

So, this means I'm missing some weird permission thing somewhere or somehow?

Any help on this matter would be greatly appreciated!

---

### Post by compiledkernel on 2009-01-16
This guide may help you. 

[http://gaming.gwos.org/doku.php/udsf:virtualbox](http://gaming.gwos.org/doku.php/udsf:virtualbox)

---


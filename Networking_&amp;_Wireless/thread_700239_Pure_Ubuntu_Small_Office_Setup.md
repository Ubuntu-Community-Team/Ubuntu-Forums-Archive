---
title: "Pure Ubuntu Small Office Setup"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by nami on 2008-02-18
I need to setup a small office network environment for myself which has (to start off with) 3 user computers.  All 3 computers should be able to access all files created by anyone on the network, I am assuming a server is required for that?

Most likely I need some sort of backup solution too for the server.

Also, all 3 pcs should be able to print to a central printer.  It should be a wireless network.

What kind of hardware and software will I need to do all that?

---

### Post by dmizer on 2008-02-18
for file sharing, configure your machines for nfs.  last link in my sig.  a server is not required for this, but it's nice (and safer) to have a central location for all shared files rather than to allow all computers to talk to eachother.

backup solution will be rsync.  howto here: [http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

you'll want to make sure you have a linux compatible printer.  look here: [http://www.cups.org/ppd.php](http://www.cups.org/ppd.php) (most, if not all, printers on that list are included in ubuntu by default).

you'll want a decent router (don't skimp here).  also, a network switch (not just a hub) will be useful for future network expantion (gigabit if you can afford it).  as far as software is concerned, everything can be had in ubuntu or gotten via aptitude (apt).

it will be loads easier for you to build and administrate your network if you configure it for static ip instead of dhcp.  that way you can use /etc/hosts for name resolution across your network. your other choices would be to set up netbios (windows ... yuck), or configure a dns server (painful).

---


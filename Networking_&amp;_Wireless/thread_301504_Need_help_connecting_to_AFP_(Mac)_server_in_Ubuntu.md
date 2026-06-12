---
title: "Need help connecting to AFP (Mac) server in Ubuntu"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2006-11-17
I am running a dual-boot Ubuntu 6.06 / WinXP (at this point only for printing reasons :rolleyes:) and at my workplace the server is an AFP (Apple file protocol, I believe). I have the afp://xx.x.x.x address, user name, password, all relevant info, but I can't figure out how to get Ubuntu to see the darn thing (even a "User-defined" entry with the afp address yields an "invalid location" error). The server is not going to change, so is there another way to connect to it? The server/networking stuff is relatively new to me, so please be explanatory. I've heard mention of samba, netatalk and nfs in some forums but that seems more along the lines of *setting up* a server, which is not what I am doing.

---

### Post by dennis1200 on 2006-12-03
still would be interested, though the post is a couple weeks old. don't let that discourage you, you mac-network person.

---

### Post by dennis1200 on 2006-12-17
Would STILL be interested. And for the foreseeable future.

---

### Post by utkjamie on 2007-02-02
If anyone has instructions for this, I'm definitely interested. I need to connect to an AFP server on campus from my Linux machine.

---

### Post by dennis1200 on 2007-02-17
bumping one final time, since I got a couple private messages expressing interest in this topic. Come on, all you server gurus!

---

### Post by dueyfinster on 2007-02-20
install Netatalk binaries, don't know how you connect from ubuntu, but from my Mac I can connect to my Ubuntu machines no problem

---

### Post by dennis1200 on 2007-02-21
I'll let you know how that works, but I had always thought that it was to create a server, not connect to one:

> Q: What is Netatalk for? What can I do with it?

A: Netatalk is an OpenSource software package, that can be used to turn an inexpensive *NIX machine into an extremely performant and reliable file and print server for Macintosh computers.
From the Netatalk FAQs.

---

### Post by Hiram on 2007-03-11
see 
[http://ubuntuforums.org/showthread.php?p=2283745](http://ubuntuforums.org/showthread.php?p=2283745)

you gotta use afpfs-ng

---

### Post by dennis1200 on 2007-03-12
Great! Thanks for pointing me in the right direction.

---

### Post by MaXqUE on 2007-03-17
Well, Samba is certainly not the way to go for Mac users! It will not deal with your Mac created files properly. The only package standard unix/linux package that does this is Netatlk. Netatalk has been aroudn for a while and really does work almost out of hte box. Its easier to set up than Samba. There is only one problem, the current pacakge was not compiled with the proper support for encrypted passwords so it sends them in clear text over the network.

There is some political problem with the use of SSL which I do not understand the details. The other package of interest is libavahi-compat-libdnssd1. Avahni implements Bounjour (formerly Rendezvous) which makes devides and computers easily discoverable over a network.

A friend of mine just installed Apple's Bonjour package for Windows on his machine and we had  his printer working (connected to his iBook) within mere minutes where any other way would have taken hours and lots of debugging.

Netalk does work and its easier to set up than Samba is.

Cheers,
MaX

---

### Post by alexthepuffin on 2007-10-08
I wrote afpfs-ng so that Linux clients can mount filesystems from Mac AFP volumes.  Check out afpfs-ng.sf.net.

- Alex

---


---
title: "Novell ConsoleOne"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Lord C on 2008-08-12
I'm using Ubuntu at work, on a new desktop machine.

Using the great tutorials found both here and on Novell's coolbits website, I have managed to successfully install the official ConsoleOne, GroupWise and the sourceforge novelclient.

I have managed to get GroupWise working and Novel Client working however, I cannot get any ConsoleOne to connect to my network.
ConsoleOne is the most important, pretty much everything else I can do via the iManager website.

ConsoleOne appears to have very, very few options if any. There is nowhere to enter a server address or anything.
Upon attempting to NDS Authenticate, I am obviously not seeing any servers in the Tree.
I type in the tree and context and click connect, this is when I'm faced with > (Error -632) Unexpected results have occurred

[Edit]
Finally got ConsoleOne to connect. I used the server IP as the tree, but the correct Context.

---

### Post by t2a on 2008-09-17
Hi,

I figured out the same stuff and setup ConsoleOne 1.3.6h
Also wrote it down, if your interested.....

Instead of typing the tree type in the ip address of a replica server.

[http://www.jirp.nl/2008/09/17/ubuntu-heron-novell-consoleone-136h/](http://www.jirp.nl/2008/09/17/ubuntu-heron-novell-consoleone-136h/)

Cheers,
Raymond.

---

### Post by tixetsal on 2009-02-13
Lord C,

   I also discovered what you did concerning using ConOne on Ubuntu.  Have you tried to install any snap-ins for ConsoleOne?  I am trying to get some Zen (rem mgmt, etc) snap-ins working today @ work.  If anyone has any tips, I would appreciate the guidance, and if I figure anything out today, I will post an update.  Thanks.

---


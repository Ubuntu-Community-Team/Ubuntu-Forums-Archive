---
title: "Must confirm remote connection--but I have that option turned off!"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2007-10-28
Very recently, I started playing with KRDC and KRFB to remotely control one Ubuntu box from another.  Everything's great...EXCEPT...

On the server box:
. I have checked "allow uninvited connections"
. I have checked "announce service on the network"
. I have definitely, positively, unequivocally UNCHECKED "confirm uninvited connections before accepting"
. I have checked "allow uninvited connections to control the desktop"
. and I have assigned a password for uninvited connections

Yet, without fail, when I connect to the remote (server) box, the confirmation modal comes up on it and the client computer is unable to complete its connection until I "OK" the confirmation modal on the server.  This is extremely frustrating. 

Although I'm using these tools purely for fun (I've already networked all my computers and can do everything I need from a command line), it's pissing me off that I can't get rid of that confirmation modal!  :roll:  Any ideas?

---

### Post by Old *ix Geek on 2007-10-29
No ideas, eh?  ](*,)

---

### Post by Old *ix Geek on 2008-01-12
Well, back in October when I posted this thread, no one had anything to offer in terms of help.  I thought the problem had [magically] solved itself, since I hadn't needed to confirm a connection in several months.  Until today, that is.

This morning, the power went out, causing the host computer to shut down; this was its first downtime, and its first restarting of KRFB, since before posting about the connection problem.  Once I brought it back up, I tried reconnecting to it from my laptop but had to...again...go to the host and confirm the connection.  As in my OP, I DEFINITELY have everything checked or unchecked in the manner that's supposed to make UNconfirmed connections possible, but it's not working.

Any chance that anyone might have some ideas about this now? :confused:

---


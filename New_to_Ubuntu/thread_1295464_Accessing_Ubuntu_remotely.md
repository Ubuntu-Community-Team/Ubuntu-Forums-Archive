---
title: "Accessing Ubuntu remotely"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by newport_j on 2009-10-19
I would like to use Ubuntu 8.04 Hardy Heron to access another system Ubuntu 9.04 remotely. The 9.04 system will be the host.
 
Where is this discussed in print so I can read how to do it?
 
Can this even be done accessing 9.04 from 8.04 remotely?
 
 
Respectfully,
 
Newport_j

---

### Post by -Zeus- on 2009-10-19
By remotely, do you mean console (SSH) or graphical (VNC)?

---

### Post by Sarmacid on 2009-10-19
Through terminal:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Remote desktop:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by hyperAura on 2009-10-19
i know SSH is pretty simple but u cant pass sound..

---

### Post by avidday on 2009-10-20
NX is by far the best system for remote access. Because it uses X11 protocol level compression, rather than IP compression, the latency and responsiveness is orders of magnitude better than VNC. There is an open source server implementation:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)


and the client (available for Linux, Solaris, Mac OS X and Windows) is free as in beer from the original commercial developer, NoMachine;

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

For a maladroit beginner, however, I would recommend sticking to plain ssh because NX requires some modicum of understanding of Linux, TCP/IP, ssh and an ounce of common sense.

---

### Post by carnagex420x on 2009-10-20
I have to agree that SSH is the better option. The command line rules and its faster and easier. Oh and did I mention secure?

---

### Post by qneill on 2009-10-23
> **avidday said:**
> NX is by far the best system for remote access....

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

...

For a maladroit beginner, however, I would recommend sticking to plain ssh because NX requires some modicum of understanding of Linux, TCP/IP, ssh and an ounce of common sense.

Man, I don't know.  I just apt-got the NX server, installed the win client, and in a matter of 5 minutes had a full Gnome desktop running in a window on Vista over a VPN.   I'm no beginner, but that was easier than configuring a putty connection.

(p.s. Thank you ubuntu for such a great community)

---

### Post by carnagex420x on 2009-10-24
nice. I haven't tried it, but I'm just a big fan of the command line.

---

### Post by qneill on 2009-10-24
In this case I needed it for an X11 app (running on a box at work).  Instead of installing an XServer in my winders box and trying one of the old LBX or other compression schemes, I found NX and gave it a shot.

Ditto fan of the command line.  As soon as I got NX opened I fired up a terminal window in the gnome session, then ran said X11 app from a bash prompt :).

---

### Post by carnagex420x on 2009-10-24
:lolflag: well if i need to run an X11 app I know what to use now.

---


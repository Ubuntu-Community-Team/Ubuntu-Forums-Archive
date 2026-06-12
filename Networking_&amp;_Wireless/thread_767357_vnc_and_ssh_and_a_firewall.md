---
title: "vnc and ssh and a firewall"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by tamman2000 on 2008-04-25
alright, I'll give some back ground first...

I have a Kubuntu box at work (lets call it desk.work.com) and a Ubuntu laptop at home (lets call it lap.home.org) and a mac laptop at home too (mac.home.org).  Between my desk.work.com and the outside world is login.work.com (a red hat box which does firewall duty on which I don't have sudo).

I usually don't have to do much work via ssh because I have almost everything I use regularly on at least one of my laptops, but I have recently taken on some new modeling tasks that involve software that can only be used on desk.work.com because of licensing...

I will be telecommuting for a week soon, and I would like to be able to use vnc as I have heard it is much faster than ssh -X.

Right now to run a X app on desk, displayed at lap or mac I 
ssh -X login.work.com, and then from login I ssh -X desk.work.com.

Can I do something similar with vnc?

Thanks,
Tamman2000

---

### Post by FrankT-Qc on 2009-04-21
There are some VNC options to forward only a "window" but it actually only forwards the "interesting" part of the window. You don't have X control as you do with X forwarding (ssh -X) nor do you have the possibility to, let's say, cut and paste between your remote app and local ones. 

Another (huge) problem is that if your other app opens another window, you will only see the part that's overlapping the original window.

If you really want to improve on speed, you might want to try NX (NoMachine has a nice client in deb packaging). Here's the repo for the server :

deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) intrepid main

---


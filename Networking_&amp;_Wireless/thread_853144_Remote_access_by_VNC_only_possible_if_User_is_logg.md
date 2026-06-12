---
title: "Remote access by VNC only possible if User is logged in"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by JUL2000 on 2008-07-08
Hi there,

my system is Ubuntu 7.10 Server with an additional Gnome.
This ist my first ubuntu system. Pls see my problem:

I have a vnc service running on that machine, and I can
login remotly via vnc client from a win-machine. I can
only do so, if a user is already logged in the ubuntu.

What I would like to do is logging in by the vnc remote, but not
always having an user already logged in at the ubuntu server.

Is there any way to fix this ?

Thanks for your help.

---

### Post by Chazaxl on 2008-07-08
I have the same question. Is it not possible to have the remote server start as a service as part of the boot / startup?

If my box is in my attic acting as a router / server - I dont want to have to go into the attic after a power cut or something and first login to allow a remote login session.

---

### Post by Chazaxl on 2008-07-08
Just got it working - need to find where. I basically told it to auto login and then also allowed a timed login option - that seemed to have done the trick.

System / Administration / Login Window ...... there you go.

---

### Post by Chazaxl on 2008-07-08
Under the security tab is where you should find those options.

---

### Post by JUL2000 on 2008-07-09
Hi,

thats what I did meanwhile, too. With auto login, it runs, but,
this means, you have 24 h per day a user logged in and
this is not a servers purpose.

Normaly, there should be no user logged in on a server which is offering services on a LAN.

Does anybody have some ideas ?

Thanks & Regards

---


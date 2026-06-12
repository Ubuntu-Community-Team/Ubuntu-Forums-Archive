---
title: "x11forward over ssh"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Wofl on 2007-04-14
hey guys

so here is the deal:
i have a desktop, "still shining" and "blazing fast" running ubuntu 6.10, soon to be 7.04
then i have a labtop, 7+ years old, super slow     running debian testing

now i have had this one book, telling me that i can have a remote xsession, allowing me to run programms displayed on the labtop to actually run on the desktop (blazingly fast)

now i have already installed ssh server on the desktop, and x11forwarding is on

but now i connect and run a programm, but i get "couldnt connect to display"

1) now what have i got to do?

2) would it be possible to run everything from boot up over the network (automatic ssh connection, etc...), and would firefox have the same bookmarks on both pc's?

3) would it be possible to extend this over the internet, to where i can connect to my home desktop from school?

---

### Post by Wofl on 2007-04-14
oh and is there like some minimal linux i can install that doesnt come with more then boot, ssh and ndiswrapper, just so that it doesnt load a lot on boot?

---

### Post by az on 2007-04-14
1. From your client machine, you need to connect with the -X switch

ssh -X wofl@192.168.0.100

That will enable X forwarding.

2.  You can run a thin client (LTSP).  You can even boot from your network.  Look it up on help.ubuntu.com/community

3.  Yes.

---

### Post by Wofl on 2007-04-15
ok, im getting close now

the "normal" deal works fine for now...

now im tring to do the entire thing (including xdm)

so the thing is, that the old, slow, crappy labtop tries to load the xorg.conf from the server, with aixgl enabled, causing it to give me the background and mouse, but no login

i copied the local xorg,conf over to the server as xorg-labtop.conf, but how do i tell it to pick that one instead?

currently using this

/usr/X11/bin/X -query 192.168.0.81 :1

---


---
title: "SSH always routing through a local address"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by Bryan_Eslinger on 2014-09-24
Has anyone come across this before, and been able to recover without wiping the whole system?

In a nut shell, when I am on my wifi at home on my dell laptop running ubuntu 14.04 and try to ssh to any host, I get redirected to a one-time virtual host I had running on a development server (separate box and the virtual host is gone, but the physical server is still running on the local network). For example, trying to connect to an external host goes like this:
```
ssh user@domain.com
```

response:
```
ssh: connect to host user@<now-deleted-virtual-host> port 22: connection refused
```

Now in, uh, the opposite of a nutshellf: Long-time listener, first-time caller, so to speak, but this is a weird one and I can't find examples of a similar issue. I have a straight-forward local network at home consisting chiefly of a desktop, a laptop, some shared storage and an old(ish) desktop pretending to be a development server. I'm working on a number of things right now and have been pretty chaotically (mis)managing some development server environments, working from both laptop and desktop, mostly on proof of concept-type stuff to inform proposals, etc. Somehow, and I'm really not sure in the midst of all the different things I've been trying-- for example, emulating a raspberry pi-style gpio output to test some ideas for a micro-controller project, to resurrecting Wordpress sites I haven't touched in a year to see how they play with the upcoming release (I know, ew, Wordpress, but it's pretty easy money to fund the more interesting work...right?). Anyway, point is, I've been beating both the dev server and the laptop up recently, booting into all sorts of different configurations and then going back to what it used to be, rinse and repeat, and somewhere in the midst of that, all of my attempts to ssh anywhere from the laptop (including via a git clone or similar) started getting redirected to what used to be a virtual host on the dev server. I finished that project a while ago and, as I usually do, removed the virtual host from the server and went about my business for a couple months. Now I can't actually make an ssh connection, because every single one tries to go to this now defunct address. I've tried all I can think of to get it pointing to the right places, but to no avail. Short of wiping the laptop completely, does anyone have any suggestions for how to get the laptop to make the right ssh connections again? I don't really know for sure, but I suspect the problem is either on the laptop or something that would affect a wifi connection but not a hard-wired connection, because my desktop has no problem ssh'ing into any of a number of external hosts I manage or the dev server (properly) that the laptop keeps trying to hit an old host on.

Any insight is greatly appreciated.

---

### Post by Lars Noodén on 2014-09-24
Did you put a shortcut in ~/.ssh/config for the old, missing VM?  If so, those lines need to be commented out or removed.

---


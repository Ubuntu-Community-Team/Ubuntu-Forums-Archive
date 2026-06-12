---
title: "netem / tc illegal latency issue"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by nicean on 2007-10-30
I've got a 'tc' / 'netem' question.

I've got a brand new install of ubuntu 7.10 here:

Linux mybox 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

on a 1.6 ghz P4 with 128 MB of RAM.  I'm trying to set up a few NICs with large delays for a small project I'm working on.  Nothing too complicated here; simply doing:

sudo tc qdisc add dev eth0 root netem delay 4000ms

Which should add a 4 sec delay to every outbound packet on that interface.  This works on gentoo 2007.0 and ubuntu 6.06.  However, on my ubuntu 7.10 box, I receive the following errors:

myuser@mybox:~$ sudo tc qdisc add dev eth0 root netem delay 4000ms
[sudo] password for myuser:
Illegal 4000000000 time (too large)
Illegal "latency"

I'm kinda thinking this is a bug, but before I did anything with it, I kinda wanted somebody with more experience with this kind of thing to take a look.  I didn't see this filed anywhere last time I checked, though.

I've tried searching these forums for tc and netem, but no joy there, either.

Anyway, ideas, suggestions, links, and/or (preferably constructive) criticism would be appreciated.  Thanks folks!

---

### Post by Lambert on 2007-10-30
Does look like a bug, have you tried using the s option instead of ms option.

sudo tc qdisc add dev eth0 root netem delay 4s

---

### Post by nicean on 2007-10-31
Yup, tried that too.  It accepted the command, but the delay introduced onto the interface was incorrect.  Also tried '4000000us' with no success.

Went ahead and put a version of fedora onto the thing just so that I could get stuff working.  Suppose it might be worth checking to see if it's a problem with the .6.22 kernel in general or only with ubuntu's distribution, but that'll have to wait for now.

In any case, appreciate the reply!

---


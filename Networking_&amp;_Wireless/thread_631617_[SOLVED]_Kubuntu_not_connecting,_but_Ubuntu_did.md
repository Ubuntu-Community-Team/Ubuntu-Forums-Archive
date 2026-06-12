---
title: "[SOLVED] Kubuntu not connecting, but Ubuntu did"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by lukeminus on 2007-12-04
Kiaora,

Okay I resisted posting my problem for so long, but I do need some help.

I recently did a clean install from Ubuntu 7.10 to Kubuntu 7.10 (I was bored), but now I have a few issues. The install was done off-line.

1) Internet is not working, which was fine on Ubuntu so it seems a bit odd to me. I use a Wired adsl connection. All the Windows computers at home are working fine also.

2) Updates are not working either.

I am not a completely techno-illiterate linux  user and can usually find a fix myself, but this is just beginning to exhaust me! It is probably something really simple, but can anyone help...PLEASE! :)

Chur,

Luke.

---

### Post by ectospasm on 2007-12-04
Let's start with the basics.  Are you receiving an IP address?  Do the following as root (or sudo it):

ifconfig

That should show you all of your network interfaces.  Most people just have eth0 and lo.  Make sure your eth0 (or other appropriate) interface has an IP address.  If you only see the lo interface, there's your problem.  If you don't have an IP address or the IP address is wrong, you may need to run dhclient (root or sudo).  You may find more information here:

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

---

### Post by raul_ on 2007-12-04
If you only see "lo" try a "sudo ifconfig eth0 up" or "sudo ifconfig eth1 up" just in case

---

### Post by lukeminus on 2007-12-05
Thanks all, I solved it... went back to Ubuntu! :guitar:

---

### Post by ectospasm on 2007-12-05
> **lukeminus said:**
> Thanks all, I solved it... went back to Ubuntu! :guitar:

That's not much of a solution, you still don't know what was wrong.  Oh, well, if you're satisfied...

---


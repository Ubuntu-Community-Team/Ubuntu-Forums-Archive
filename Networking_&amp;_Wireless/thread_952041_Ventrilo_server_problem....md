---
title: "Ventrilo server problem..."
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by pzhukke on 2008-10-18
Good evening!

I've got some network issues with my ventrilo server.
First of all, I want to tell you that I'm using a windows-version combined with wine to get it to run (the reason is because it's patched so it supports > 8 users).

You see, when I start it, this is the end of my output:
> 20081019 00:03:05 Accepting connections on these interface(s).
20081019 00:03:05   1: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 Accepting UDP Status/Control messages on these interface(s).
20081019 00:03:05   1: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 READY:


And this is what it says in Windows:
> 20081019 00:03:05 Accepting connections on these interface(s).
20081019 00:03:05 1: 192.168.0.195
20081019 00:03:05 2: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 Accepting UDP Status/Control messages on these interface(s).
20081019 00:03:05 1: 192.168.0.195
20081019 00:03:05 2: 127.0.0.1
20081019 00:03:05
20081019 00:03:05 READY: 

And when I run it under Windows, there's no problem to connect to it, but there is in ubuntu; I can't connect.

I have absolutely no idea of what could be wrong, but I'm pretty sure that it's something to do with my network, some setting somewhere.
That's why I'm asking you guys for some professional help!


Thank you for being polite and helpful! :)
Eric.

---

### Post by superprash2003 on 2008-10-19
well in the ubuntu version it doesnt seem to listen to the correct interface.. in windows it is listening to 127.0.0.1 which is your loopback and 192.168.0.195 .. whereas in ubuntu it only listens to loopback... everything may not work properly under wine..

---

### Post by pzhukke on 2008-10-19
Well.

I don't think it's wine since It works with another windows-version of ventrilo.
But I want to use this version if it's possible.

---

### Post by superprash2003 on 2008-10-19
you would have to look into its settings and see if you have an option wherein it shows which interfaces to listen to.. also please post output of ifconfig, to see the available interfaces..

---


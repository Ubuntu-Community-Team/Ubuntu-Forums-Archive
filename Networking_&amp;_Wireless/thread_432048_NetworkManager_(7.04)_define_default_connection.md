---
title: "NetworkManager (7.04): define default connection?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by DE255 on 2007-05-03
I upgraded to 7.04 and everything is fine.

the new NetworkManager which now is installed by default is nice but my PC is connected by cable with my DSL-router. No WiFi.

every time I want access the internet I have to leftclick on the NetworkManager and choose my LAN-connection.

isn't it possible to define any default connection? 
the NetworkManager should connect to this connection as long as it is available and I don't say something else... couldn't find something like this...:(

---

### Post by DE255 on 2007-05-06
here
[http://www.gnome.org/projects/NetworkManager/users/](http://www.gnome.org/projects/NetworkManager/users/)
is written

> NetworkManager will automatically connect to networks it knows about, but you will need to manually connect to a network at least once.

the only connection is my LAN (via cable). There is no other connection available (e.g. WiFi). Why do I have to choose/click/verify every time?

Any Ideas?

---

### Post by Cannaregio on 2007-05-07
I have a similar problem.
There are at least 6 wifi connections overlapping where I live, and Ubuntu 7.04, thanks network manager, always starts from the wrong one (dunnow if I did or not enable it at the beginning, anyway I don't want to connect to my neighbour per default anymore).
Maybe a developer should implement a possibility of "deselect" a given connection and / or to choose a 'default' connection. Which seems impossible at the moment (but I'm only beginning to look around, maybe, as usual, there's some hidden switch).

---

### Post by DE255 on 2007-05-07
there should be an option "default network".

every other network should require a click in die NetworkManager menu.

---

### Post by DE255 on 2007-05-09
reported it to the GNOME bugzilla
[http://bugzilla.gnome.org/show_bug.cgi?id=437220](http://bugzilla.gnome.org/show_bug.cgi?id=437220)

---

### Post by NilsE on 2007-05-09
You have the reverse problem that most people have and that is to use the system on only one network.

To do this you can disable NM by going into manual configuration and turning off roaming then select the one network and get connected. Try it it might work for you.

---

### Post by DE255 on 2007-05-10
the roaming mode was already turned off for my cable-connection. Manual config does not help.

I think deinstalling the complete NM-package should resolve it. But I would prefer to keep it and find another way! :mad:

---

### Post by DE255 on 2007-05-15
I deinstalled it with synaptic.

After a clean reboot everything was and is fine. It's like before the update (without NM). :KS

---


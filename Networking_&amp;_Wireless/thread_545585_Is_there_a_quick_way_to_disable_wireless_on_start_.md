---
title: "Is there a quick way to disable wireless on start up?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by Breathe on 2007-09-07
Is there a quick way to disable wireless on start up?

I would like to find a way to do this:

> $ sudo gedit /etc/network/interfaces

Comment lines that point to the network interface that i want to disable (My case: eth1)
Now any time I restart i don't have wireless.
If I want at any time to re-enable it

$ sudo gedit /etc/network/interfaces
Uncomment lines that point to the network interface
$ sudo /etc/init.d/networking


in a much more elegant way***, is there any way???

*** Elegant Way: Using NetworkManager (Default GNOME application for Ubuntu) ... XD

Thank you all...

---

### Post by K.Mandla on 2007-09-07
You could keep two backup copies of that file, one with wireless activated and one not, and then use a little script to copy one or the other as the correctly-named interfaces file. Does that make sense? :|

---

### Post by Breathe on 2007-09-07
HAHAHAHAHAHA!!!!! XD

Yes, it makes sense... Thanks for your  method, i'll use it till i find something better :D

If any one has any other way... I'd like to hear your suggestions...

---


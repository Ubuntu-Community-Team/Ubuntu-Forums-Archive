---
title: "new to ubuntu and need help"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by tweekavich on 2009-02-05
I have a Dell Inspiron 1520 laptop, recently crashed my hard drive and had to buy a new one, installed ubuntu 8.10 and am trying to keep windows/microsoft off of it, i am unable to connect to the internet wireless, tried installing some .deb packages that were supposed to help, can't remember where i got them, read a bunch of forums and help sites for it and am still unable to connect, any help would be appreciated.

---

### Post by avtolle on 2009-02-05
Which wireless card do you have? Please do, at the terminal```
lspci
```and post the results here.

---

### Post by cmnorton on 2009-02-05
Is the NetworkManager icon on the screen? Usually, it's on the upper right, and is in icon with vertical bars.

Can you start an X-term (command line), and enter cat /etc/network/interfaces ?

Does it look similar to this?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

Into which kind of network are you trying to connect, wired or wireless?

In the future, a subject like Cannot Connect to Network will probably cause more people to read and respond to your post.

---

### Post by IEKnight on 2009-02-05
It should be automatically detected. If not, try going to
system > administration > Hardware Drivers
enable the Broadcom B43 Wireless Driver, and disable any other wireless drivers that may be present.

If that doesn't work, this may help
_[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html ](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html )_

good luck ;)

---


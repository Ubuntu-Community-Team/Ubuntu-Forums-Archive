---
title: "Need some help"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by gloowee on 2009-12-17
I'm so new to Ubuntu that the paint is dripping.  I prefer to learn the command line server edition.  I've installed 9.04 on a vmware host.  Now what?  I'm behind a Microsoft Proxy that I don't manage.  When I run sudo apt-get update I can't connect to the net for updates.

in my smallest voice.........."help"?

:confused:

---

### Post by candtalan on 2009-12-17
> **gloowee said:**
> I'm so new to Ubuntu that the paint is dripping.  I prefer to learn the command line server edition.  I've installed 9.04 on a vmware host.  Now what?  I'm behind a Microsoft Proxy that I don't manage.  When I run sudo apt-get update I can't connect to the net for updates.

in my smallest voice.........."help"?

:confused:

Welcome!
I dont use the server version myself, and I think I would also use a gui to make my own life easier while I learned up on it all.
Have you seen the server information pages? A friend mentioned them to me recently, they look very useful
[http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation](http://www.ubuntu.com/products/whatisubuntu/serveredition/documentation)

hth

---

### Post by Temposs on 2009-12-17
I agree. I use both the Desktop and Server versions. You can do all the stuff with the Desktop version that you can do with Server. The only difference between them is what the default applications installed are. You can set up a server on the Desktop edition very easily.

But yes, starting out with a GUI will make things a lot easier on you.

---

### Post by gdonwallace on 2009-12-17
My first suggestion would be to try and ping an IP address outside your network.  If you can't get it to ping, then I would look at the settings for your host to make sure the networking is setup correctly.  Generally speaking, NAT is what works best.  You may have to experiment a little to get it to work.  

Also run **lfconfig** and find out what your IP address is and make sure that it is not being blocked.  Also could be that your IP has not been setup on the proxy server.  Of course to fix these issues you will need to talk with your IT guys and have them unblock / add to the proxy server that IP address.

good luck.

---


---
title: "help with remote networking."
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2007-12-14
I will be installing ubuntu on my mother's laptop this weekend. she lives in another state, so I will not be able to perform any maintenance directly. I would like to remotely connect to her laptop via GUI.

I have found some guides, but I am not exactly sure which one to use. I do not necessarily need something super-secure, just easy to use and efficient. 

What do you recommend? I see the Remote Desktop application in System>Preferences, but is that for remote connections or just local networking?

Thanks.

---

### Post by purdticker on 2007-12-14
** edit, realized this isn't as easy as I thought it was...

I like [http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

---

### Post by purdticker on 2007-12-14
This seemed to work locally for me, however I can't get it to work externally.

[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

---

### Post by bionnaki on 2007-12-17
anyone else have any recommendations?

---

### Post by el escocés on 2007-12-17
Just depends if you want screen sharing or simple command line access.

For screen sharing on your mother's laptop in Gusty go to System>Preferences>Remote Desktop and select 'allow users to view your desktop' there are other options as well, password, user confirmation etc. You need to forward port TCP 5900 to the internal IP of you mothers laptop to connect from the internet.

On your PC use the program 'Terminal Server Client' to connect, using the public IP of mothers laptop as the address, you can install a dyndns like service in her linux or just ask her to go to [http://whatismyip.com]("http://whatismyip.com/") every time she needs help ;)

The passwords are not encrypted in VNC so someone nasty could sniff them out.

If you just want command line access then just ssh into her machine, forwarding port 22 instead of 5900.

---


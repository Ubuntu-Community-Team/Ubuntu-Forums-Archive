---
title: "black screen vnc"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Artanis.ro on 2010-02-10
I want to connect from my ubuntu 8 computer to a Mac with Tiger. The mac has screen sharing enabled and allows VPN connections. When I try to connect to it, I insert the password and the window appears, but everything inside the window is black.
I have red this thread [http://ubuntuforums.org/showthread.php?p=8769413#post8769413](http://ubuntuforums.org/showthread.php?p=8769413#post8769413) and I have deactivated every desktop effect.

I have a ATI video card and I use compiz fusion.

Thnak you

btw, when I connect to windows computers using rdp or rdp5 works fine.

---

### Post by mwcrowley on 2010-02-10
The issue is probably your vnc client, the application you're using to connect to the mac box.  Try using xtightvnc.  you can install it using synaptic or just enter sudo aptitude install xtightvncviewer.  

[http://www.techanswerguy.com/2008/10/vnc-on-linux-wont-connect-to-mac.html](http://www.techanswerguy.com/2008/10/vnc-on-linux-wont-connect-to-mac.html)

and if you have to open the firewall on the mac to allow the connection
[http://homepage.mac.com/car1son/static_port_fwd_firewall.html](http://homepage.mac.com/car1son/static_port_fwd_firewall.html)

---


---
title: "VNC only gets terminal session"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by dsmithhfx on 2014-12-26
Hi,

I've installed vncserver on 13.04 server roughly following this guide: [http://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04](http://www.howtoforge.com/how-to-install-vnc-server-on-ubuntu-14.04) (basically apt-get install vnc4server and gnome-core)

Unfortunately when I connect over lan using Remina at [ubuntuserver ip]:5901, it is opening to a terminal session instead of xdesktop. If I exit the terminal, the vnc session is still running as a flat grey window.

Any tips on how to fix this so I can get to regular desktop?

Thanks!

---

### Post by slickymaster on 2014-12-26
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by steeldriver on 2014-12-26
You need to create a suitable ~/.vnc/xstartup file - this should get you started [https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

---

### Post by dsmithhfx on 2014-12-27
Thanks. I just needed to add one line to the end of vnc4server auto-generated .vnc/xstartup, "startxfce4 &" (probably didn't need gnome-core at all).

It's been a few years since I had to configure a vnc server :oops:

---


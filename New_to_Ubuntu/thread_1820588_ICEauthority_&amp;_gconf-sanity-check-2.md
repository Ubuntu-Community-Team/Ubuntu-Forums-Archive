---
title: "ICEauthority &amp; gconf-sanity-check-2"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by isa.dsouza on 2011-08-07
I would get the following 2 errors after logging in to Ubuntu Natty 

1) Could not update ICEauthority file /home/isa/.ICEauthority 
and 
2) There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

The OS was totally unresponsive & any application I would launch was not opening. The environment had also changed from unity to gnome.

I managed to launch terminal using CTRL+ALT+F1 have used some commands like sudo chown isa:isa .ICEauthority and sudo chmod 0644 .ICEauthority
but nothing was been fixed for Error 1. Also tried sudo chmod 755/elc/gconf/gconf.xml.* for Error 2. 

The only thing I did was change my user account profile from custom to administrator. I also removed Nautilus & replaced with Thunar, as the home folder Nautilus was not responding in Natty. 

These errors persisted until I re-installed Maverick over the Natty partition, with the Maverick usb installer. This was the only solution I could think of.

I have now upgraded to Natty using the alternate iso image & the upgrade completed successfully.

---

### Post by sando89 on 2011-10-28
did you have home folder encryption and auto login enabled at the same time?

---

### Post by isa.dsouza on 2011-11-14
no idea, but its done & dusted now

---


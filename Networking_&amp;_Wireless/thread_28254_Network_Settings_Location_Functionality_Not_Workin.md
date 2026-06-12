---
title: "Network Settings: Location Functionality Not Working"
date: 2005-04-19
forum: Networking &amp; Wireless
---

### Post by General_Tso on 2005-04-19
Hello, folks.

This is my first post here, because I seem to be getting blank stares on other boards.  Hopefully, you people will be able to help.

I just jumped onto the Ubuntu (5.04) bandwagon, and I'm really impressed. I do have one question though. When I open the Network Settings application (System -> Administration -> Networking), the "location" I set does not seem to affect the settings. I am trying to have one wireless configuration for work and one for home where it is just a matter of changing the Location pulldown menu. When I try to change "Home," it seems to overwrite the "Work" settings.

Is this a bug?  Anyone have any suggestions?

Lastly, I saw an application called whereami listed elsewhere on this site.  If the "location" functionality is not working, would this be a good solution?  This is a laptop for a non-Linux saavy user, so I want something easy for him to manage.

Thanks!

---

### Post by speedman on 2005-04-19
[QUOTE=General_Tso]Is this a bug?[/QUOTE]

Yes.

> Anyone have any suggestions?

I manually edited /etc/gnome-system-tools/network/profiles.xml, but some of the changes were still overwritten when changing profiles from within Gnome.

As such, I just set my laptop to DHCP, so it would function at home and at the office with no headaches.  I set my MAC address on the DHCP servers to always issue me the same address, but that may not be applicable in your situation.

> Lastly, I saw an application called whereami listed elsewhere on this site.  If the "location" functionality is not working, would this be a good solution?

I haven't used whereami, but it seems like a viable solution.


Regards,

SM

---

### Post by General_Tso on 2005-04-19
[QUOTE=speedman]Yes.
I manually edited /etc/gnome-system-tools/network/profiles.xml, but some of the changes were still overwritten when changing profiles from within Gnome.

As such, I just set my laptop to DHCP, so it would function at home and at the office with no headaches.  I set my MAC address on the DHCP servers to always issue me the same address, but that may not be applicable in your situation.

I haven't used whereami, but it seems like a viable solution.

Regards,

SM[/QUOTE]

Thank you very much for the tip on the profiles.xml file.  From my cursory editing, it doesn't seem to have made an impact.  (I'm trying to have the various locations remember SSID's and passwords to no avail.)  Is there some tutorial that explains each of the tags in and general syntax of the profiles.xml file so I can understand it better?

I may play with whereami, because it looks pretty cool.

Thanks again for your response!

---

### Post by speedman on 2005-04-19
The network-admin application is part of gnome-system-tools, which is not well documented.

There are some resources noted in this file:

/usr/share/doc/gnome-system-tools/README

HTH


Regards,

SM

---

### Post by General_Tso on 2005-04-19
Speedman,

Thanks again for useful information.  It is much appreciated!

---

### Post by speedman on 2005-04-19
My pleasure.  Best of luck.


Regards,

SM

---

### Post by joeljkp on 2005-05-13
Thank you for this thread. I just installed Ubuntu myself, and the wireless locations feature was a big reason for that. It's a bummer that it doesn't work right now, but at least it's a known bug, so maybe it'll get fixed soon.

---

### Post by General_Tso on 2005-05-13
[QUOTE=joeljkp]Thank you for this thread. I just installed Ubuntu myself, and the wireless locations feature was a big reason for that. It's a bummer that it doesn't work right now, but at least it's a known bug, so maybe it'll get fixed soon.[/QUOTE]

Aside from that, Ubuntu is pretty nice, isn't it?  I haven't given whereami a shot yet, but it seems like it'd be a good option.  For the time being, I'm just changing the settings manually.

---

### Post by Xama on 2006-12-11
This seems to be a long lingering bug ... it was talked about in 2005 and here we are wandering into 2007 ... is there/has there been a fix for this?

---


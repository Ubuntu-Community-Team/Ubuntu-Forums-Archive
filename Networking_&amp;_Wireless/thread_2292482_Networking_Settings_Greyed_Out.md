---
title: "Networking Settings Greyed Out"
date: 2015-08-28
forum: Networking &amp; Wireless
---

### Post by bfleishman on 2015-08-28
This should be an easy fix.

I am running Ubuntu 14.04 LTS . When I click on the settings applet --> Network --> Select Wired and click the options button, all the settings on all the tabs are greyed out or disabled. I can see all my static IP information but I am unable to change it.

What could be causing this and how can I enable the editing of the network details?

Thanks
-Brian

---

### Post by brad-bogar on 2015-08-28
Do you see a lock symbol near the bottom of the applet? Usually you can enable changing these settings with that - it asks for your root password to change settings.

---

### Post by bfleishman on 2015-08-28
No there is no lock sign. Here is a link to the screenshot.

[http://snag.gy/JW0ZB.jpg](http://snag.gy/JW0ZB.jpg)

---

### Post by bfleishman on 2015-08-28
Following this article actually help resolve my issue.

[http://askubuntu.com/questions/455736/remove-ifupdowneth0-connection](http://askubuntu.com/questions/455736/remove-ifupdowneth0-connection)

---

### Post by brad-bogar on 2015-08-28
Could be just the GUI messing up, you may need to edit manually in command line to fix it. 

Sudo nano [COLOR=#111111][FONT=Consolas]/etc/network/interfaces

then put in your info, etc.

[/FONT][/COLOR]auto eth0
    iface eth0 inet static
    address xx.xx.xx.xx
    netmask xx.xx.xx.xx
    gateway xx.xx.xx.xx
    dns-nameservers xx.xx.xx.xx
    dns-search xx

Save the file then:

sudo ifup eth0

---


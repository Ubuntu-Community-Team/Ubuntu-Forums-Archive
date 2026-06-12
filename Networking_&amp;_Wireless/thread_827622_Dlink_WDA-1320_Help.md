---
title: "Dlink WDA-1320 Help"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Mike.42 on 2008-06-12
I am trying to get a dlink wda-1320 card working in Hardy. I have looked at some trouble shooting guides and when I run the " sudo lshw" comand I do not even see my card. Any Ideas to try to get this to work?

---

### Post by Mike.42 on 2008-06-13
This guide

[http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/](http://blog.linuxoss.com/2008/05/08/ubuntu-804-enabling-atheros-ar5007-based-wireless/)

uses madwifi drivers, but madwifi.org seems to be down, can anyone confirm this?

---

### Post by chili555 on 2008-06-13
Yes, it's down. I hope, not for long. You could just wait or try the drivers in *linux-restricted-modules* that you can install in Synaptic. Did you try that and did it not work correctly?

---

### Post by Mike.42 on 2008-06-13
What madwifi drivers would I need for the dlink wda-1320?
Also, after I download the drivers, is there anything else I would  need to do?

---

### Post by Mike.42 on 2008-06-14
ARRRR all fixes I have found use madwifi which is still down! I have found the chipset for the dlink card, Atheros AR5005G.

---

### Post by Bubba64 on 2008-06-14
Have you tried ticking roam on the wired and wireless this is the method that works pretty good for me to get everything to link up. I then restart the router then restart the computer and look in the wireless to see if your personal network is showing. If everything gets going this way then switch to manual, choose your network input the password and choose DHCP if that is what your using and do another restart. I can never get my manual set up to work if I disconnect, but if I go to roam it always works. It always takes a restart to get the manual set up to work.  the manual always works when I turn the laptop on after the initial linking.

---


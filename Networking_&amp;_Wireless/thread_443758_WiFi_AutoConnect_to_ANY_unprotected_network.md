---
title: "WiFi AutoConnect to ANY unprotected network"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by BDwinsAlt on 2007-05-14
Is there an application that automatically connects to ANY unprotected network.  I have the roaming enabled.  When I ride around on my bike I have this signal tracker that beeps faster and louder as the signal gets stronger.  When I leave my house and I lose my signal, it doesn't connect to another unprotected network automatically.  What can I do to make it connect to ANY unprotected network as it disconnects from another one.  I have Fiesty 7.04.

Thanks

---

### Post by BDwinsAlt on 2007-05-15
Help? Áudame por favor? Helfen Sie mich?  What else must I say?  :(

---

### Post by BDwinsAlt on 2007-05-18
Thanks for the help.  :mad:

---

### Post by devnu11 on 2007-05-18
Have you tried wifi-radar?  **sudo apt-get install wifi-radar**  You just need to make a connection called **any** and set auto for type and channel and use dhcp.  I have had good luck with wifi-radar.  If the signal is strong enough to make a connection it usually will connect and be ready for you to use.  Good luck.

---

### Post by BDwinsAlt on 2007-05-19
After upgrading to feisty, I get this when I try to start it.

root@brad-laptop:/home/brad# wifi-radar
dhclient3 --version 2>&1
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1926, in <module>
    import gtk, gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from _gobject import *
ImportError: /usr/local/lib/python2.5/site-packages/gtk-2.0/gobject/_gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode
root@brad-laptop:/home/brad# 

I'm currently using wlassistant and some KNetworkManager.

---


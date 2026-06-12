---
title: "Removing an icon."
date: 2009-04-10
forum: New to Ubuntu
---

### Post by DUfire on 2009-04-10
I no longer use GNOME's default network manager applet, but even though I removed the applications, the applet still remains in the notification area. Is there any way I can get rid of it? 

[http://img105.imageshack.us/img105/2754/nmapplet.png](http://img105.imageshack.us/img105/2754/nmapplet.png)

---

### Post by Tim Sharitt on 2009-04-10
To prevent nm-applet from lading at start go to System > Preferences > Startup Applications and remove the entry for Network Manager.

To completely remove the applet from your system, you will need to remove the network-manager-gnome package.

---

### Post by DUfire on 2009-04-11
> **Tim Sharitt said:**
> To prevent nm-applet from lading at start go to System > Preferences > Startup Applications and remove the entry for Network Manager.

To completely remove the applet from your system, you will need to remove the network-manager-gnome package.

Worked like a charm. Thanks.

Took me awhile to realize Start-Up Applications is under the "Sessions" tab.

---

### Post by Tim Sharitt on 2009-04-11
> **DUfire said:**
> 
Took me awhile to realize Start-Up Applications is under the "Sessions" tab.

Sorry, It's labeled Startup Applications in Jaunty and I forgot that it was labeled sessions in previous versions :P

---


---
title: "ubuntu CE 7.05 will not work with my generic ethernet card"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Huggy on 2008-01-07
I've been through the other similar posts and none of them worked. I shrunk my windows partition and install ubuntu CE 7.05. My windows has internet and I have the disc with the windows driver for the ethernet card if that will help. I just couldn't figure out what to do with it. When I type ifconfig, I can see eth0 so I know it's there. It shows up in the devices. It just won't use it. Any advice or magical commands that might help. I'm a real noobie at this stuff.

---

### Post by lswest on 2008-01-08
if you have a GUI go to system-->administration-->network tools and go to your ethernet card right-click and choose "properties"  from the drop-down menu choose dhcp if you get your IP from a dhcp server, or else set up a static IP.

should work.

---

### Post by Huggy on 2008-01-08
I can no get a static IP to work, and I have the DHCP selected, but it shows I have an eth0 when I do ifconfig.

---

### Post by lswest on 2008-01-09
if you're connected with a cable, and if you do ifconfig eth0, does it show you an IP?  if not run ```
sudo dhclient eth0
``` which will request an IP from the dhcp server, which might fix your problem.  if it does, you can add it to the boot process so that you always get an IP when you boot.

---


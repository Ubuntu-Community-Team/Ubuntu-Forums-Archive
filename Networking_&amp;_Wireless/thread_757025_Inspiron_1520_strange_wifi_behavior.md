---
title: "Inspiron 1520 strange wifi behavior"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by bayonetblaha on 2008-04-16
Though my wifi works fine connecting to my Belkin router at home for long periods of time, I find that I have trouble keeping a connection at public locations, particularly at my university.  It's not that I lose the actual connection, just that pages don't load.  The firefox status bar reads "looking up google.com..." for example, and the page never changes, all while the network icon shows a nearly full-bars connection.  I then typically use the network icon to reconnect to the network, and it works for a few more seconds or minutes.  Under Vista my network card performs much more reasonably. I even typed this post into Gedit to paste to the forum because I knew I wouldn't be able to stay connected very long. Multiple fresh installs of Ubuntu have presented this same problem.

Dell Inspiron 1520 
Ubuntu Gutsy

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Restricted Drivers: Firmware for Broadcam 43xx chipset family

---

### Post by dstew on 2008-04-16
I have heard of this behavior with the native driver, which you are using. The other thing to try is to [use the Windows driver, with ndiswrapper.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29#head-b0e306f00ab3b4adea24f483a5dd5bf05fbdaf08")

---


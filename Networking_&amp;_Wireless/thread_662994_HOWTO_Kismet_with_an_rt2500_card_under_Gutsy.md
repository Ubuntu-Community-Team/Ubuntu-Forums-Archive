---
title: "HOWTO: Kismet with an rt2500 card under Gutsy"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by icheyne on 2008-01-09
If you are running the Gutsy-supplied rt2500 driver and kismet package, you will probably not be able to get kismet running. I got the following error:



FATAL: Failed to set monitor mode: Device or resource busy. This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it. Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README. 


I managed to fix this by installing the latest version of Kismet (2007-10).
 1. [http://kismetwireless.net/download.shtml](http://kismetwireless.net/download.shtml)
2. sudo aptitude install build-essentials libncurses-dev libpcap-dev
3. ./configure
4. make
5. sudo make suidinstall (do not do this on a shared PC)
6.  sudo nano /usr/local/etc/kismet.conf
7. change the source line to rt2500,wlan0,whatever
8. kismet (notice the lack of sudo)

---


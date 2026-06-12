---
title: "Wifi disconnects every day or so, shows two arrows instead of wifi symbol"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by eezacque on 2017-08-04
Every day or so, wifi disconnects, and instead of the wifi icon I get  the ethernet icon (two arrows), which makes no sense, as there is no  ethernet cable attached. When this happens, the entire gui slows down,  mouse becomes jittery. This can be fixed by switched wireless off and on  in the network control panel. This was reported as a bug ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1705269](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1705269) ), but response has been underwhelming so far, so it doesn't hurt to ask here. 

Anyone having the same problem? Any clue about a workaround/fix?
I also remember this has worked for me until, say, a year ago, so it looks like a bug introduced to a stable release.

---

### Post by BenginM on 2017-08-04
I figured it's a Broadcom from your description!  so which wireless card is it ..we see the driver in use is wl ,  maybe the free driver has support for that card.

see what dmesg | grep have to say! ,  in a sperate terminal tab/window run: $ tail -f /var/log/syslog , and $ tail -f /var/log/dmesg   .. then try to connect to the wifi

you'll be luck to have support responses from the community on launchpad , this should be reported against wl upstream.

---


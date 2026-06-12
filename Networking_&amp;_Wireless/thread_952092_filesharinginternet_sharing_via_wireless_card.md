---
title: "filesharing/internet sharing via wireless card?"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2008-10-18
Hey,

I'm wondering if this is possible to do on Ubuntu and how it would be done.

I live in halls at a uni, which has a connection to a main network which I use to connect to the internet. Since I have a spare wireless card which isn't used for anything else, I was wondering if it's possible to setup ubuntu to relay my internet connection from the main network through the wireless card, so that it's possible to use the internet connection with our laptops wirelessly.

An extra bonus would be if we could somehow connect our computers together for file sharing, either securely over the uni network or preferably over the wireless.

---

### Post by themusicalduck on 2008-10-19
bumpity

---

### Post by superprash2003 on 2008-10-19
well with a wifi card, you could share or connect to only one more pc.. wifi cards can connect to only one pc at a time in adhoc mode..
  It is very much possible to share with one pc at a time.. just follow this for internet connection sharing [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. and for file sharing.. if its a ubuntu only network you could use NFS , if there are windows pcs as well, then you could use samba

---

### Post by themusicalduck on 2008-10-19
Ok, well I tried out how-to, but then read in the comments that it was better to use firestarter to configure a shared connection.

I tried to undo as much as I could from that tutorial to try out firestarter, which seemed like an easier and safer option, but since rebooting, firestarter can't seem to use my wireless card anymore.

Error is:

Failed to star the firewall

The device wlan0 is not ready.

Please check your network device settings and make sure your internet connection is active.

Anyone know how to fix this?

---


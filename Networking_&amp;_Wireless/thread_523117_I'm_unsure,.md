---
title: "I'm unsure,"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by rinzy20 on 2007-08-11
I have a BCM4318 wireless card, with a working (I think) driver. It was a .deb package I found on the forum. I have my wireless light on when in Ubuntu and i am able to scan networks and find them (I.E. my card works) however when i try to connect to my internet, (WPA and WPA2, i have both setup,) it does not work. I cant even connect to a network without an encryption.  I am currently on my Vista partition and if I can get any help it would be great. I am an intermediate user who can't figure this out.

---

### Post by spd106 on 2007-08-13
Try looking through the /var/log/syslog for error messages, you should be able to identify the point at which connection fails. The process should be this, association -> handshake -> connected -> DHCP. It might be a good idea to post the significant parts here if you are unsure.

Sometimes when I have problems connecting I like to run this command in a terminal while clicking on nm-applet to rescan. It will follow the progress of NM and allow you to see what's going on as it happens.
```
tail -f /var/log/syslog
```

---


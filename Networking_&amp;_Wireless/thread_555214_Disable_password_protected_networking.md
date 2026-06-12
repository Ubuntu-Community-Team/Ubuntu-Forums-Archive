---
title: "Disable password protected networking"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by billyransier on 2007-09-19
I am the only one with Linux on a windows network, I'm on the network fine, I can see everyone and they can see me

however when they try to click on my computer it asks them for a user name and password, is there anyway to make it so they don't have to log in to my computer it is just not password protected?

---

### Post by Zorael on 2007-09-20
Try editing your /etc/samba/smb.conf file. Scroll down to the very bottom where you see your shares defined, and add 'guest ok = yes' to each.

---


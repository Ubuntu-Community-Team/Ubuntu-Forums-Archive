---
title: "trying to setup network printing....Help"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by dbrine on 2005-08-20
I am trying to print to the network printer but no luck. It's a stand alone printer. configured thru windows. I tried to connect using smb but nothing...?

---

### Post by dbrine on 2005-08-22
No one knows how to setup and network standalone printer

---

### Post by ape on 2005-08-23
Couple of things to check:

1. Your printer is in fact configured to be shared on the windows box.

2. What errors do you get when trying to set up the printer through the "Printer Connection" dialog?

3. What does the output of the `smbtree` command show?  This is part of the smbclient package.

---

### Post by Franko30 on 2005-08-23
Maybe this thread helps:

[http://www.ubuntuforums.org/showthread.php?t=27736&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27736&page=1&pp=10)

It did for me - entering guest (German: gast) as username and no password in the configuration dialogue (System -> Administration -> Printing) helped.

---


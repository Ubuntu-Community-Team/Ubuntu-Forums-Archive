---
title: "network printing help"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by JDee on 2007-04-12
I have a windows network and i have ubuntu on two of my computers and i wanted to know if it is posiible to use my printer on that network in ubuntu?

---

### Post by dbott67 on 2007-04-12
Absolutely.  You can share it in a few ways.

1. Connect it to a Windows computer & share it.  Then in Ubuntu, click **SYSTEM > ADMINISTRATION > PRINTERS** and add a new printer.  The *PRINTER TYPE* should be **NETWORK --- WINDOWS PRINTER (SMB)**.  The host addresss would be the IP of the Windows computer, and the printer name would be the "shared name".

See attached screenshot.

2. You can also connect it to an Ubuntu computer and use CUPS.  See my post here for info on setting it up:

[http://ubuntuforums.org/showthread.php?p=2413840&highlight=cups#post2413840](http://ubuntuforums.org/showthread.php?p=2413840&highlight=cups#post2413840)

-Dave

---


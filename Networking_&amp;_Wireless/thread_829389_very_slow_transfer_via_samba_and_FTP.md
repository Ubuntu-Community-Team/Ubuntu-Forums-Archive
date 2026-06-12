---
title: "very slow transfer via samba and FTP"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by vvlonghorn on 2008-06-14
I recently set up a fileserver on an old computer using gutsy gibbon, and i've been having problems with the transfer rates. Before i go any further, let me say that i have looked all over using google and going through forums and can't find a solution. I have a gigabit intel pci NIC (e1000) that is running on a 100Mb network.

Whenever i try to move large files to and from the server i get very poor performance (Windows -> server = ~300Kb, server ->windows = ~1200Kb)

I have made sure it is in 100baseT mode, and even tried using wii-tools to force it to 10Mb but the uploads still stayed at ~300Kb. Why is the transfer rate SO slow?

and it should be noted that i am running a minimal setup (command line, vsftpd, samba, sshserver)

-thanks

---


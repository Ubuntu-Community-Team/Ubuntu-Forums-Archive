---
title: "WG511 v2 (China) locking up PC"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by nothingxs on 2006-10-12
Ever since I used ndiswrapper to install my Netgear WG511 v2 (Marvell chipset), my computer will either hang on boot (hanging on 'Starting kernel log...' [ ok ]) if I have it plugged in, or will immediately crash the moment I plug it in to the computer. Curiously enough, plugging it into the computer also causes the little netapplet on my GNOME panel to vanish.

Anyone have any insight as to what's going on?

---

### Post by wieman01 on 2006-10-13
I have had similar experience (as well as others) in connection with "ndiswrapper" and my Linksys wusb54g v4. Solution was to compile "ndiswrapper" from source in order to have the latest version. You may take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=274485]("http://ubuntuforums.org/showthread.php?t=274485")

---


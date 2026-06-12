---
title: "Can't access Windows shares through TP-Link Archer A6 router."
date: 2023-02-05
forum: Networking &amp; Wireless
---

### Post by eddrap on 2023-02-05
I recently had to replace my old Buffalo router. With the old router, I could access Windows network shares through SMB4K with no problems. The replacement router is a TP-Link Archer A6 v2 router. With the new router, I can access the internet easily. However, when I try to connect to the shares on a windows computer, SMB4K cannot connect to the computer. Dolphin cannot connect to the computer. I tried a command line ping to the computer's IP address and it never responds.

I am trying to connect through wifi. Through wifi, I can connect using a windows computer and I can connect using an Android device. It is only any Computer running Ubuntu with the KDE desktop that has a problem. I tried two different laptops with the Ubuntu install and neither one will connect.

I am at a loss for anything else to try. Can someone help?

---

### Post by eddrap on 2023-02-06
Problem solved. It was my Nordvpn that was blocking access.

---


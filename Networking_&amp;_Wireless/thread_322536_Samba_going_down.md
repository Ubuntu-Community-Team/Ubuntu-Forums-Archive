---
title: "Samba going down"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by m1tnick on 2006-12-20
Hi everyone.

I have a problem that is driving me crazy!
When I'm copying movies or any type of data from ubuntu to XP, my network becomes crazy.
I have System Monitor showing the Graph of the usage of Network, and when I start copying the Graph shows that the network isn't always at 100%. It behaves like this 10%, 60%, 50%, 27%, 80%, xx%, xx%.... and after a seconds (or minutes) it says read/write error, and I have to restart the pc to connect to the network again.

With fedora 5 this things didn't happen, why is Ubuntu diiferent?.

Please help me. 
I really want to quit Windows, but with this problem I can't!

Thanks in advance!

---

### Post by linuchsan on 2006-12-20
What is your hardware configuration, especially your nic.

---

### Post by m1tnick on 2006-12-20
Its a Marvell Yukon 88E803X PCI Express Fast Ethernet Controller Family. My laptot is a LG lw20-44MP. Need more info?

---

### Post by linuchsan on 2006-12-20
Are you running edgy? what does lsmod |grep sk98lin say?

---

### Post by m1tnick on 2006-12-20
Yes, I'm running edgy.
 lsmod | grep sk98lin returns :
sk98lin               191700  0

---

### Post by linuchsan on 2006-12-20
Try the skge module

---


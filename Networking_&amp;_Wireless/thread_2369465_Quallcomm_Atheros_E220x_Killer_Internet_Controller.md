---
title: "Quallcomm Atheros E220x Killer Internet Controller: no LAN"
date: 2017-08-23
forum: Networking &amp; Wireless
---

### Post by punch3 on 2017-08-23
Hello,

Please find the output of my wireless-script below.

[https://paste.ubuntu.com/25376011/](https://paste.ubuntu.com/25376011/)

It seems alx is exiting repeatedly. How should I proceed?

I won't be able to take further diagnostic steps until after I return home from work some 9 hrs from now, but I should be able to answer any questions regarding the specs of this machine.

Thank you for your time.

Distro: Ubuntu 16.04

---

### Post by punch3 on 2017-08-23
It looks like this may be caused by IOMMU being enabled. I'll try this when I get home:

[https://askubuntu.com/questions/853881/killer-ethernet-e2400-not-connecting-16-04](https://askubuntu.com/questions/853881/killer-ethernet-e2400-not-connecting-16-04)

I'm still open to any other suggestions however.

---

### Post by jeremy31 on 2017-08-24
*Thread moved to **Networking & Wireless**.*

---

### Post by punch3 on 2017-08-28
Alright, so anyone else who happens to have this same issue: follow the information in [https://askubuntu.com/questions/853881/killer-ethernet-e2400-not-connecting-16-04](https://askubuntu.com/questions/853881/killer-ethernet-e2400-not-connecting-16-04)

It will tell you to use the grub script "iommu = soft", which works. You need to also disable IOMMU in BIOS if you happen to have the same motherboard that brings on this issue.

---


---
title: "Realtek RTL8187B problem (desktop pc not laptop)"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by vmanisme on 2008-08-04
I have a Gateway GT5694 Desktop PC.  It has Realtek RTL8187B Wireless 802.11b/g 54mbps USB2.0 wireless card (build in not a USB one i dont know why its named USB).  I installed Ubuntu (the latest one) on it through Dual-boot.  It cant find my card or any wireless cards, does not detect any wireless networks in range and i cant find the driver for it online.  If anyone can help me out please do... THANKS AHEAD!  Oh yeah if you do have a solution try to explain it in step-by-step mode because i'm new to Ubuntu.

---

### Post by pytheas22 on 2008-08-04
Please post the output of these commands:
```

lsmod | grep rtl
lspci
lspci -n
lshw -C Network
uname -n
```

That will help figure out what you need to do.  I may not be back till tomorrow but I'll reply when I can, or hopefully someone else can pick it up sooner.

---

### Post by vmanisme on 2008-08-05
K i'll reply in few hours gotta reinstall Ubuntu again i got rid of it since it didnt work the only reason why i want Ubuntu is to get rid of viruses and stuff other than that my Vista x64-bit roX

---


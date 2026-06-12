---
title: "Cannot get online with Airlink 101 usb card"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by brie987 on 2008-08-06
Hello.  I have been trying for a few days to get online with Xubuntu without any success.  Xubuntu cannot even detect ANY wireless networks and there are a lot in my building that my computers normally detect.  I use the latest Xubuntu distro and I am using an Airlink 101 usb card.  Do I need an appropriate driver?  If so where do I get it, i have been looking.  As you may tell I am very new and  this is very disconcerting and annoying but i am patient.  Please help with any advice or perhaps I'm doing something wrong.  Thanks in advance.

---

### Post by pytheas22 on 2008-08-06
Don't feel bad about being confused; wireless can be frustrating if you're new to Linux.  Please open a terminal and post the output of these commands:
```

lsusb
uname -m
lshw -C Network
```

With that, we can figure out which chipset your wireless card has and which driver it needs (if you're interested, see the link in my signature to read more about what a chipset is and how you should approach wireless-driver troubleshooting in Linux).

---


---
title: "Linksys WMP54GS v1.1 - Fiesty"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by XLostSpartanX on 2007-07-05
So I just got Ubuntu Fiesty installed and everything configured - except for the wireless.  I have a Linksys WMP54GS v1.1.  I just can't figure out how to get it to work.  It doesn't even show up that I have wireless on the network icon in the panel.  Thanks for any help!

---

### Post by sj3fk3 on 2007-07-05
> **XLostSpartanX said:**
> So I just got Ubuntu Fiesty installed and everything configured - except for the wireless.  I have a Linksys WMP54GS v1.1.  I just can't figure out how to get it to work.  It doesn't even show up that I have wireless on the network icon in the panel.  Thanks for any help!

It's a FAQ, searching the forum before posting does help... (sometimes)

See: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by kevdog on 2007-07-05
Could you do me a favor, I think your card may have the rt2500 chipset rather than the broadcom.  To verify this can type type at the command prompt the following and cut and paste the output:

lspci
lshw -C network

---


---
title: "can't establish wired connection"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Moe Z on 2009-07-06
Hi,
    The wired network connection icon on top right corner of screen always shows a cross sign though i can connect other PCs in my network and internet. What's going wrong with it. I have 2 NICs . 1st is built in NIC from motherboard and 2nd is a PCI slot NIC. Since built in NIC is dmaged, i used to connect through the PCI slot NIC.

---

### Post by candtalan on 2009-07-06
> **Moe Z said:**
> Hi,
    The wired network connection icon on top right corner of screen always shows a cross sign though i can connect other PCs in my network and internet. What's going wrong with it. I have 2 NICs . 1st is built in NIC from motherboard and 2nd is a PCI slot NIC. Since built in NIC is dmaged, i used to connect through the PCI slot NIC.

make sure the built in NIC is disabled or whatever in the bios screens  in the relevant options

---

### Post by anystupidname on 2009-07-06
Can we see these please?

sudo lspci -v
sudo ifconfig -a
/etc/network/interfaces
sudo /etc/init.d/networking restart

---

### Post by Iowan on 2009-07-06
Is machine set for DHCP or static address? If it's failing on DHCP attempt, [this]("http://ubuntuforums.org/showthread.php?t=1156441") one *might* help.

---


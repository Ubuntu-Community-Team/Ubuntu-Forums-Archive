---
title: "PLEASE help!"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by klunuts on 2009-02-24
I just bought [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041") wireless card for [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121342") motherboard. i installed it into the PCI slot, and turned on my computer. nothing happened. i tried running the install wizard disk that comes with, but it only runs with windows. i tried reinstalling ubuntu all together. NOTHING will work.  Please help me :/

---

### Post by llamabr on 2009-02-24
post the output of lspci

---

### Post by klunuts on 2009-02-24
shall do - hold on two minutes

---

### Post by klunuts on 2009-02-24
uh i tried just putting it in a txt document and putting it on a thumb drive to get it over to my laptop (which im on right now) but it says permission denied everytime i try to get the file onto the thumb drive...

---

### Post by halitech on 2009-02-24
sounds like the thumb drive is not mounted with permissions for your user. You will either need to get it mounted with your user or in this case where we want the info wuickly, you could carefully use sudo to open nautilus and copy it that way.

```
gksudo nautilus
```

---

### Post by klunuts on 2009-02-24
ah i see, thanks! kay, here it is:

klu@klu-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
klu@klu-desktop:~$

---

### Post by halitech on 2009-02-24
the only ethernet card I'm seeing is your wired connection

[color=red]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/color]

are you sure the card is inserted in the PCI slot properly?

---

### Post by klunuts on 2009-02-24
heh heh, probably not. let me go check.

---

### Post by halitech on 2009-02-24
ok, cause the 2 options I can think of are 1. card isn't seated properly or 2. card is defective.

---

### Post by klunuts on 2009-02-24
wowww, that was it. hahaha. thanks so much!

---

### Post by halitech on 2009-02-24
so all is working now?

---

### Post by llamabr on 2009-02-24
If so, change the subject line to include a solved tag.

---


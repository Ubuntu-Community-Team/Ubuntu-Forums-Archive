---
title: "3G on Acer Aspire One"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by willis575 on 2008-12-24
Has anybody gotten this to work? I haven't had any luck... if nobody has either lets figure it out here!

---

### Post by LowSky on 2008-12-24
This is a driver issue.

in a terminal type ```
lspci
```

so we can see what we are working with

---

### Post by willis575 on 2008-12-24
Great! I tried installing mad wifi to at least get wifi working, and now WIRED networking doesn't work! I used a thumb drive to get a copy of the lspci output over to a machine with a connection.... here it is


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by willis575 on 2008-12-24
Some more info....

3G - I used the little wizard in the network manager to add a mobile broadband connection, however looking at lspci I don't think it's recognizing the broadband modem.

Wired - In my attempt to get at least wifi working I tried this from a thread about the aspire one... and now the wired network doesn't work either!

> MadWifi: [http://snapshots.madwifi-project.org...0081105.tar.gz](http://snapshots.madwifi-project.org...0081105.tar.gz)
-uncompress the package with the package manager
-go to the terminal and type in "cd whatever_folder_you_just_extracted" and enter
-type "make" and enter
-type "sudo make install" and enter
-type "sudo gedit /etc/modules"
-add "ath_pci" to the very end
-reboot!

---

### Post by willis575 on 2008-12-24
Also, I followed this to try and detect which chipset I'm using, but nothing that could be the chipset id showed up. So would I be correct in assuming that Ubuntu isn't detecting it at all?

---

### Post by willis575 on 2008-12-24
Ok, reinstalled Intrepid to get wired networking back.

---


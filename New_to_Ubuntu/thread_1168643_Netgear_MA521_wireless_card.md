---
title: "Netgear MA521 wireless card"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by lmazonde on 2009-05-24
i bought a Netgear MA521 PC wireless card a while ago but i can't get it to work . i don't know which drivers to download and install. I would  be grateful if someone can give me step-by -step instructions , i'm quite new to this. i'm running on Ubuntu 8.10.

---

### Post by super.rad on 2009-05-25
Open a terminal (Applications > Accesories > Terminal) and type **lspci** then copy and paste the output here, if we know more information about your wireless card it will help

---

### Post by lmazonde on 2009-05-27
Here's what i got:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

---

### Post by mapes12 on 2009-05-28
Here are some links that may be helpful:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Good luck.

Mark

---


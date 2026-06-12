---
title: "help can't connect to internet"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by rob reza on 2008-01-11
Hi just installed ubunto 7.10 gutsy and i cant get online? I really need some help i have a 04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
And i cant see any wireless connection around me,and my speakers don't work?

---

### Post by ubutufan on 2008-01-11
Hi
Go to Applications>Accessories>Terminal
Type lspci
and post the results here

---

### Post by rob reza on 2008-01-11
> **ubutufan said:**
> Hi
Go to Applications>Accessories>Terminal
Type lspci
and post the results here

bash: ispci: command not found

---

### Post by m1k3uk on 2008-01-11
think you have entered the command wrong, the 1st letter is L not I.  lspci <------Try that and post again

---

### Post by rob reza on 2008-01-11
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by Reeva on 2008-01-11
The wireless networkcard is detected : 


04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


Do you see a network icon on the top rightside of your gnome screen? If yes, click once on it, and you should see the availible networks in the area.

Pherhaps you need a security-key?

Does it work if you use a wired connection?

grts

---

### Post by rob reza on 2008-01-11
no still didn't work,WHAT IS THIS ndiswapper i see every where?

---

### Post by Himie on 2008-01-11
hi im having the same problem and i think i need to input my modem security code for the internet so how do i do that?

---

### Post by rob reza on 2008-01-11
Someone please tell me what the ndiswapper is and where to find it? please i'm sruggling here:confused:

---

### Post by rob reza on 2008-01-11
I have toshiba satellite a135-s7403 don't have wireless in my network manger has buildin atheros ar5006eg need help :(:confused:someone please help

---


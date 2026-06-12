---
title: "Wireless router"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by mllelinotte on 2009-04-02
Can anyone tell me how to get my computer to connect to the internet via wireless router? I am using Ubuntu 8.10.

---

### Post by superprash2003 on 2009-04-02
does your PC have a wifi LAN card?

---

### Post by SpenceMakesSense on 2009-04-02
Are you saying taht you have a wireless lan card and it doesnt work? Because then you may need to use ndiswrapper or better yet ndisgtk. With these programs you can use your windows drivers under linux.

---

### Post by jigsaws on 2009-04-02
Try to click on network monitor icon on the bar and then select the network.

If you have problem, please be more specific.

---

### Post by mllelinotte on 2009-04-02
yes the computer has a Wifi LAN card. I used wireless internet on this computer when i had Windows. Now with Ubunut i have to use the cord. I do not know what to do to connect to wireless. i have only been using Ubuntu for about a week, so i still know very little about it. When i click on the monitor icon, no wireless connection is listed.

---

### Post by wolfen69 on 2009-04-02
see if there is a driver in system>administration>hardware drivers

also, post the output of
```
lspci
```

---

### Post by mllelinotte on 2009-04-02
Under drivers it says that "Support for the Atheros 802.11 wireless LAN cards" is active and in use.

and this is the output of the code you gave:


00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by superprash2003 on 2009-04-03
hope this helps [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by Kareeser on 2009-04-03
Please try the following:

System -> Administration -> Hardware Drivers

... and enable the wireless driver.

---

### Post by MPTony T on 2009-04-03
I had the same problem and had to use ndiswrapper. now all works fine. do a search for ndiswrapper and it will step by step you that's what i did. I was not able to even select the wireless at all.

---


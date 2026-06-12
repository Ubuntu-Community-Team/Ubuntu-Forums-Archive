---
title: "No wifi active on installation"
date: 2020-01-21
forum: Networking &amp; Wireless
---

### Post by tony482 on 2020-01-21
I have just co-installed Ubuntu 18.04, alongside windows 7 on a Lenovo G550 - 2958. On initial boot, no wifi was detected, although on windows it works fine, I am unable to get an icon to search for a wifi connection, I have re-installed in case there had been some corruption but still unable to detect or search for a wifi connection, I am not too technical, can anyone give any advice on getting the software to look for and connect to the wifi router. The software was downloaded from the internet and burnt to CD-ROM

---

### Post by gdesilva on 2020-01-21
Open a terminal (on your desktop not occupied by any application, type CTRL+ALT T to open a teminal) and then type 'lspci' at the prompt. This will give you a list of pci devices on your system. Go through the list and find the name of the wifi adapter or just post the output here.

---

### Post by jeremy31 on 2020-01-21
Moved to Networking and Wireless

---

### Post by tony482 on 2020-01-21
Thanks for your help,
screen shows
00:00.0 Host bridge: Intel Corporation Mobile 4 series chipset memory contoller hub (rev 09)
00:02.0 VGA compatible controller: intel corporation mobile 4 series chipset integrated graphics controller (rev 09)
00:02.1 Display controller: intel corporation mobile 4 series chipset integrated graphics controller (rev09)
00:1a.0 USB controller:intel corporation 82801I (ICH9 family) USB UHCI controller #4 (rev 03)
00:1a.1 USB controller: intel corporation 82801I (ICH9 family) USB UHCI controller  #5 (rev 03)
00:1a.2 USB controller: intel corporation 82801I (ICH9 family) usb UHCI controller #6 (rev 03)
00:1a.7 USB controller: intel corporation 82801I (ICH9 family) USB2 EHCI controller #2 (rev 03)
00:1b.0 Audio device: intel corporation 82801I (ICH9 family) HD audio controller (rev 03)
00:1c.0 PCI Bridge: intel corporation 82801I (ICH9 family) PCI express port 1 (rev 03)
00:1c.1 PCI Bridge: Intel corporation 82801I (ICH9 family) PCI Express port 2 (rev 03)
00:1c.2 PCI Bridge: Intel corporation 82801I (ICH9 family) PCI Express port 3 (rev 03)
00:1c.3 PCI Bridge: Intel corporation 82801I (ICH9 family) PCI Express port 4 (rev 03)
00:1c.5 PCI Bridge: Intel corporation 82801I (ICH9 family) PCI Express port 6 (rev 03)
00:1d.0 USB controller: Intel corporation 82801I (ICH9 family) USB UHCI controller #1 (rev 03)
00:1d.1 USB controller: Intel corporation 82801I (ICH9 family) USB UHCI controller #2 (rev 03)
00:1d.2 USB controller: Intel corporation 82801I (ICH9 family) USB UHCI controller #3 (rev 03)
00:1d.7 USB controller: Intel corporation 82801 (ICH9 family) USB2 UHCI controller #1 (rev 03)
00:1e.0 PCI bridge: Intel corporation 82801 mobile PCI bridge (rev 93)
00:1f.0 ISA bridge: Intel corporation ICH9M LPC interface controller (rev 03)
00:1f.2 SATA controller: Intel corporation 82801IBM/IEM (ICH9M -E) 4 port SATA controller [ACHI mode]  (rev 03)
00:1f.3 SMBus: Intel corporation 82801I (ICH9 family) SNBus controller  (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 family) thermal subsystem (rev 03)
04:00.0 Network controller broadcom Inc, and subsidiaries BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: broadcom Inc. and subsidiaries Netlink BCM5906M 802.11b/g LP-PHY (rev 01)
I could not copy and paste from the other computer, so had to type, so there might be a 'typo mistake'
Thanks
Tony

---

### Post by chili555 on 2020-01-21
> Network controller broadcom Inc, and subsidiaries BCM4312 802.11b/g LP-PHY (rev 01)Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by jeremy31 on 2020-01-22
If you have no internet connectivity to the computer see [https://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843](https://ubuntuforums.org/showthread.php?t=2098717&p=12426843#post12426843)

---

### Post by tony482 on 2020-01-22
Hi,
trying to unravel the problem, as one thread suggested 
interrogated lspci -nn -d 14e4
revealed
04:00.0 network controller [0280]: broadcom inc and subsiduaries BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
07:00.0 ethernet controller [0200]: broadcom inc and subsiduaries netlink BCM5906M fast ethernet PCI express [14e4:1713] (rev 02)

looking at the suggested threads, I cannot find BCM4312 on the info, any advice greatly received

---

### Post by CelticWarrior on 2020-01-22
```
04:00.0 network controller [0280]: broadcom inc and subsiduaries BCM4312 802.11b/g LP-PHY [**14e4:4315**] (rev 01)
```

Marked in **bold** above is the information you should be looking for in the mentioned thread [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

So, according to the table there, you need to install **firmware-b43-installer**:
```
sudo apt install firmware-b43-installer
```

---


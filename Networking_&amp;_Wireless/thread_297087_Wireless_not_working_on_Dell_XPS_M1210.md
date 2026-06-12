---
title: "Wireless not working on Dell XPS M1210"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by cnrus on 2006-11-10
Hello All,

I recently installed Kubuntu Edgy Eft (6.10) on my Dell XPS M1210. It looks great, but unfortunately my wireless does not work. I know M1210 uses the Intel ipw3945 card. When I ran lspci, it does not list the wireless card. I found some errors in the dmesg output. But, I am sure those errors are from running the script for ipw3945install found on these forums. I also see the LED for WIFI lit. Please let me know if there is any fix to this.

lspci output:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

dmesg output:
dmesg | grep 3945
[17180174.796000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[17180174.796000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[17180174.796000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[17180174.796000] ipw3945: Unknown symbol ieee80211_txb_free
[17180174.796000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[17180174.796000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[17180174.800000] ipw3945: Unknown symbol escape_essid
[17180174.800000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[17180174.800000] ipw3945: Unknown symbol ieee80211_set_geo
[17180174.800000] ipw3945: Unknown symbol ieee80211_rx
[17180174.800000] ipw3945: Unknown symbol ieee80211_get_channel
[17180174.800000] ipw3945: Unknown symbol ieee80211_channel_to_index
[17180174.800000] ipw3945: Unknown symbol ieee80211_rx_mgt
[17180174.800000] ipw3945: Unknown symbol ieee80211_get_geo
[17180174.800000] ipw3945: Unknown symbol free_ieee80211
[17180174.800000] ipw3945: Unknown symbol ieee80211_tx_frame
[17180174.800000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[17180174.800000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[17180174.800000] ipw3945: Unknown symbol alloc_ieee80211

Thanks in Advance.

---


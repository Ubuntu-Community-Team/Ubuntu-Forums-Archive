---
title: "Trouble setting up Atheros AR5005G"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by hoy_pogi on 2006-09-08
It seems that installing or not installing ndiswrapper doesn't make a difference.

I have followed the ndiswrapper guide in the unofficial ubuntu guide [http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

after running iwconfig, I still cannot see the mac address of my router. I tried configuring using the graphical network configuration tool (networking applet), disabled eth0, enabled ath0, entered the proper SSID and WEP key, tried using DHCP and manual IP, all to no avail. The signal bar is very low, and when double-clicked, indicates that there is no signal. What am I missing here?

I'm running ubuntu on an AOpen 2000 laptop- amd sempron cpu (s754), ati xpress 200m chipset, atheros ar5005g mini PCI wireless card. Everything works except my wireless card, card reader (TI PCIxx21 Integrated flashmedia controller), special keys (wireless on, load browser, fan speed adjuster), and card reader.

Thanks.

---

### Post by tturrisi on 2006-09-09
You don't need ndiswrapper for atheros chipset wlan cards.  You need the madwifi-ng drivers.  To install these drivers, run synaptic, then enable the universe & multi-universe repositories, reload the packages list, install the linux-restricted-modules that matches your kernel.  Reboot.

---

### Post by rw2007 on 2007-12-31
I did all of that on my Toshiba Satellite A55-S1063 because it has the same wireless chipset but it still didn't work.  The wired still works however.

---

### Post by marcocec on 2008-01-23
I try configuring my AR5005G with madwifi
After following the script process I put this command

#lspci  ---->
root@spud:/home/marco/madwifi-0.9.3.3# lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)


Can anyone help me??
Hurry please I use 

compatibilita SM BIOS, supporto HD Audio
ATI Xpress 200M
128 MB dedicata
fino a 256 MB con Hypermemory
Processore Intel Pentium Dual Core T2080
1, 73 GHz
Cache 1 MB
FSB 533 MHz
Ram	
1024 (512+512) MB
espansione max.: 2.048 MB
tecnologia: DDR2 RAM
2 slot di memoria occupati
80 GB
5.400 rpm
Serial ATA

---


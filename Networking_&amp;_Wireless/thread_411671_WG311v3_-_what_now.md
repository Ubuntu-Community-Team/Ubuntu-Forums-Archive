---
title: "WG311v3 - what now?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by Philistine on 2007-04-17
Trying to get WG311v3 card working... what do I do next?

Thanks in advance for your help!

Phil


phil@phil:~$ sudo iwconfig 
Password: 
lo no wireless extensions. 

eth0 no wireless extensions.



phil@phil:~$ sudo lspci 
Password: 
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] 
00:06.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0 
00:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) 
00:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) 
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)




phil@phil:~$ sudo modprobe -r ndiswrapper 
Password: 
phil@phil:~$ sudo ndiswrapper -i WG311v3.INF 
wg311v3 is already installed. Use -e to remove it 
phil@phil:~$ sudo modprobe ndiswrapper 
phil@phil:~$ ndiswrapper -l 
Installed ndis drivers: 
wg311v3 driver present, hardware present




What do I do now???

---

### Post by Kobalt on 2007-04-17
I think you need to compile the latest version of ndiswrapper and use your windows drivers in order to get that card working. See this for instructions : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb)

---


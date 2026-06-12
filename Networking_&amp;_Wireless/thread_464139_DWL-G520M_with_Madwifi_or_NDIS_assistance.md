---
title: "DWL-G520M with Madwifi or NDIS assistance"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by JoshuaRyan on 2007-06-04
Hello All,

I am currently trying to get my wireless card to work in Kubuntu 7.04 and have not been successful thus far.  I've checked the Madwifi site and it states that the device is not supported whereas the NDIS Wrapper site claims that it can work.  

1.       Card: D-Link DWL-G520M Wireless 108G MIMO Desktop Adapter (bought in UK)

o        Chipset: Atheros Communications, Inc. AR5005VL 802.11bg Wireless Chipset (rev 01)

o        pciid: 168c:0020 (rev 01)

o        Driver: ar5513.sys and net5513.inf from [ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip)

o        Other: Fedora Core 5 and ndiswrapper from livna repository (utils: 1.8, driver: 1.13, vermagic: 2.6.16-1.2122_FC5 686 REGPARM 4KSTACKS gcc-4.1). Works with WEP. Not tested beyond a few hours of continuous operation.


Now, when I run the LSPCI command, it does show that the device exists but that's as far as I get.  I've tried building the driver with NDIS wrapper and the drivers linked above however even after loading them I have no such luck. 

In network manager all I can find is my wired ethernet, not the wireless.  I've checked all the forums regarding this card but haven't found a working solution anywhere.  Any help would be appreciated.  

Thank you

---

### Post by JoshuaRyan on 2007-06-04
ndiswrapper-1.45# lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Contr          oller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset           Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev           08)
01:0a.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wire          less NIC (rev 01)
01:0b.0 USB Controller: VIA Technologies, Inc. Unknown device 3028 (rev 50)
01:0b.1 USB Controller: VIA Technologies, Inc. Unknown device 3028 (rev 50)
01:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)

---

### Post by JoshuaRyan on 2007-06-08
Hello, has anyone found any articles stating how to get this card to work?  I've tried all the commands that I know and am needing some additional advice.

---

### Post by navneets on 2007-07-03
no joke i have same wireless card just mines from australia but  im like having the same problems.

---

### Post by 150pilot on 2007-12-14
Any fix for this yet?

---

### Post by stchman on 2007-12-14
> **JoshuaRyan said:**
> Hello All,

I am currently trying to get my wireless card to work in Kubuntu 7.04 and have not been successful thus far.  I've checked the Madwifi site and it states that the device is not supported whereas the NDIS Wrapper site claims that it can work.  

1.       Card: D-Link DWL-G520M Wireless 108G MIMO Desktop Adapter (bought in UK)

o        Chipset: Atheros Communications, Inc. AR5005VL 802.11bg Wireless Chipset (rev 01)

o        pciid: 168c:0020 (rev 01)

o        Driver: ar5513.sys and net5513.inf from [ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip)

o        Other: Fedora Core 5 and ndiswrapper from livna repository (utils: 1.8, driver: 1.13, vermagic: 2.6.16-1.2122_FC5 686 REGPARM 4KSTACKS gcc-4.1). Works with WEP. Not tested beyond a few hours of continuous operation.


Now, when I run the LSPCI command, it does show that the device exists but that's as far as I get.  I've tried building the driver with NDIS wrapper and the drivers linked above however even after loading them I have no such luck. 

In network manager all I can find is my wired ethernet, not the wireless.  I've checked all the forums regarding this card but haven't found a working solution anywhere.  Any help would be appreciated.  

Thank you

Did you try enabling the Restricted Driver?  This should work.

---

### Post by conbe755 on 2008-01-19
I'm using Ubuntu 7.10 and Ndiswrapper-1.9 together with the D-Link DWL-G520M card 
and it works fine for me.

---

### Post by vlatkop on 2008-03-22
> I'm using Ubuntu 7.10 and Ndiswrapper-1.9 together with the D-Link DWL-G520M card
and it works fine for me.

I am also using this card and it is working perfect in Ubuntu 7.04 and 7.10
Can you tell me do you use TKIP for WPA-PSK? And if you use tell me how do you use. Do you use any GUI tool for "making the connection" or you set up the parameters manually?
In 7.04 I am using manual from:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_WPA_with_Ndiswrapper_driver](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_WPA_with_Ndiswrapper_driver)
And in 7.10 I am using gnome-network-manager to set up the connection. 
I have tried in 8.04 Beta but I was having problem with avahi daemon.
Regards

---


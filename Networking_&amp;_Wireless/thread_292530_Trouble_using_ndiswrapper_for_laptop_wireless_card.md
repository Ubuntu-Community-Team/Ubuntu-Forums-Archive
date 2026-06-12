---
title: "Trouble using ndiswrapper for laptop wireless card in Xubuntu"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by keefbeef on 2006-11-03
I am trying to resurrect an old laptop for word processing, email & internet. I have been reading through the archives but am having trouble with ndiswrapper.

The laptop:
Compaq Presario 1690
AMD-K2 400MHz
64Mb imbeded
SO-DIMM with 256Mb SO-DIMM (that's not being detected by Xubuntu but that's another post...)
6.5 Gb HDD
Xubuntu 6.10
Airlink101 802.11g PC card (AWLC3025)

I have tried doing the following:
cd dir/where_I_saved_the_driver
sudo -s
ndiswrapper -i WinXP_driver_for_my_card.INF
ndiswrapper -l
ndiswrapper -m
modprobe ndiswrapper

But here is where I am stuck.  I get the error message:
"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"


I also found this site ([http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)) and downloaded this file (FwRad16.bin_1.2.1.34) but I have no idea what to do with it.   According to this site, my card uses the Texas Inst. ACX111 chipset if that helps.  

Any help would be greatly appreciated.  Thanks.

---

### Post by amohanty on 2006-11-04
So after you did this

> cd dir/where_I_saved_the_driver
sudo -s
ndiswrapper -i WinXP_driver_for_my_card.INF
ndiswrapper -l
ndiswrapper -m

forget the modprobe stuff, its not necessary.

assuming your interface is called wlan0 and you use dhcp - and skip the '<' and '>'characters
in your /etc/network/interfaces, add the following:

auto wlan0
iface wlan0 inet dhcp
wireless-essid <your router SSID>
wireless-key   <your router WEP/WPA shared hex key>
wireless-channel <channel # - may have to comment it out - some cards dont suport it>
wireless-mode   managed

save it, then do a:
/etc/init.d/networking restart

If it still does not work, post the output of
ifconfig

HTH
AM

---


---
title: "wireless not working on Ubuntu 12.04.3 LTS"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by ykzh on 2014-01-05
Wireless not working after upgrading from 10.04 LTS to 12.04 LTS today.  I have tried the solution provided by chili555 in thread   [http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880). 

It seems to find the wireless signals after reboot, but I could not get connected using the previous wireless setting (DHCP and same WEP HEX key which worked for 10.04 LTS) 
The WEP index I used the default 1.  For the Authentication I chose "Shared key" instead of "open system". 

Could you provide some insight on why my correct HEX key is not working?    Thank you very much.

The following are some probing outputs 

~/wireless/ % sudo modprobe b43    (now returns no error)
~/wireless/ %  lspci -nn -d 14e4:
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
~/wireless/ %  dmesg | grep b43
[   28.953976] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   30.836600] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
~/wireless/ % dmesg | grep 0c:00
[    3.135924] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
~/wireless/ % rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by ykzh on 2014-01-05
silly me, the wireless router also needs to be rebooted in my case (although the wired connection worked fine without reboot),  also, the Authentication seems need to be "open system" instead of "shared key".

Thanks to chili555 for his simple but great solution in  [http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880)[COLOR=#000000]. [/COLOR]

---

### Post by Bucky Ball on 2014-01-05
Is this now solved? If so, please follow the link in my thread to mark it solved and help others. (Yes, chilli555 is a resident wireless guru and has helped many. ;))

---


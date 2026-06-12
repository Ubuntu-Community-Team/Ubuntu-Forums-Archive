---
title: "Ralink usb wifi RT2870/RT3070 , can't get connection"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by Frans_Thamura on 2014-07-16
i success register the .ko, but still cannot access wifi, any idea?

meruvian@baremerv:~/rt3573sta/sta$ sudo modprobe -v rt2800usb
insmod /lib/modules/3.13.0-30-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
install modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id 
insmod /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
meruvian@baremerv:~/rt3573sta/sta$ dmesg | grep rt28
[  286.583699] rtusb init rt2870 --->
[  286.583731] usbcore: registered new interface driver rt2870
[ 1772.474072] usbcore: registered new interface driver rt2800usb
meruvian@baremerv:~/rt3573sta/sta$ sudo iwlist scan
eth1      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

meruvian@baremerv:~/rt3573sta/sta$  dmesg | grep rt28
[  286.583699] rtusb init rt2870 --->
[  286.583731] usbcore: registered new interface driver rt2870
[ 1772.474072] usbcore: registered new interface driver rt2800usb
meruvian@baremerv:~/rt3573sta/sta$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation C206 Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
meruvian@baremerv:~/rt3573sta/sta$ lsmod | egrep 'rt28|rt55'
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              626557  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              12707  1 rt2800lib
meruvian@baremerv:~/rt3573sta/sta$ echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rt2800usb
meruvian@baremerv:~/rt3573sta/sta$ sudo echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
\blacklist rt2800usb
meruvian@baremerv:~/rt3573sta/sta$

---

### Post by slickymaster on 2014-07-17
I've moved this post to a thread of it's its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by varunendra on 2014-07-17
@Frans_Thamura,

Apart from what slickymaster said above, I don't think the proprietary driver mentioned in the [thread]("http://ubuntuforums.org/showthread.php?t=2193810") that your post is moved from, would compile on the newer kernels. That's why I requested to move your post to its own thread so we can determine if you need a newer solution and possibly find it.

To show us the current status of your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---


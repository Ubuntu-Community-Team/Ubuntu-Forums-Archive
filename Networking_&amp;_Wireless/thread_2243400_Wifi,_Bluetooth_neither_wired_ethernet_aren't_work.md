---
title: "Wifi, Bluetooth neither wired ethernet aren't working on my Dell Inspiron-7420"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by pratik4 on 2014-09-08
Desperate for Help.
Hello all.
I installed ubuntu 14.04 LTS a month back by the side of windows 8. All was good until a week ago when I was trying to shut down my computer via linux; it froze. So I forcefully shut it down by pressing the power button for a lengthy time. The next day when I turned on my computer ubuntu was not detecting any wireless connection. Bluetooth was there though. I tried fixing the problem by skimming through lots of blogs but I guess I made things even worse as now even bluetooth is gone. The kea on kea board that usually used to turn on and off wifi is no more functional. Strangely rest other keys are working normally.
Things in widows are good. There is no problem there at all with anything.
Please help as I totally novice to the world of Ubuntu. Through reading although I have learned a lot but still I don´t think that they are enough to get me out of this problem.[CENTER]x
[3 Update(s)]("http://ubuntuforums.org/usercp.php")[/CENTER]

---

### Post by pratik4 on 2014-09-08
here´s what I got after following your instructions. I can't even connect to the internet via ethernet. my system is dell inspiron -7420


########## wireless info START ##########


Report from: 08 Sep 2014 19:00 WEST +0100


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Dell Device [1028:055f]


##### lsusb #####


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:644b Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0000:0000  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


##### lsmod #####


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


##### iwconfig #####


lo        no wireless extensions.


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


nl80211 not found.


##### iwlist channels #####


lo        no frequency information.


##### iwlist scan #####


lo        Interface doesn't support scanning.


##### module infos #####


##### module parameters #####


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0887 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


########## wireless info END ############

---

### Post by pratik4 on 2014-09-08
Here´s what I got after following your instructions to get wireless report when you are not able to connect to internet via any means. My system is dell inspiron -7420. Please please please help


########## wireless info START ##########


Report from: 08 Sep 2014 19:00 WEST +0100


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Dell Device [1028:055f]


##### lsusb #####


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:644b Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0000:0000 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


##### lsmod #####


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


##### iwconfig #####


lo no wireless extensions.


##### route #####


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


nl80211 not found.


##### iwlist channels #####


lo no frequency information.


##### iwlist scan #####


lo Interface doesn't support scanning.


##### module infos #####


##### module parameters #####


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0887 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


########## wireless info END ############

---

### Post by sheldon-corey on 2014-09-09
lsmod | grep intel gives what and as both interfaces are default in the kernels that makes it odd that niether works.


Please install inxi if not already done and provide the following output please:

inxi -Sitcm20

---

### Post by varunendra on 2014-09-10
> **pratik4 said:**
> ....it froze. So I forcefully shut it down by pressing the power button for a lengthy time....
....which caused the installation of your brand new kernel broken halfway..

..Yes, it is most certainly a broken kernel issue. Please show us the output of -
```
uname -mr
```
..so we can try installing it again manually if required.

In the meanwhile, please also try -
```
sudo dpkg --configure -a
```
..and post back any errors it might give you. If there are none, all should again be good. If not, maybe try this additionally -
```
sudo apt-get install --reinstall $(uname -r)
```

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---


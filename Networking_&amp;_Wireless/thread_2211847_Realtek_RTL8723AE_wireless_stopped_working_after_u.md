---
title: "Realtek RTL8723AE: wireless stopped working after update"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by srdshardwood on 2014-03-18
Hi my wireless recently stopped working after i performed an update via update manager. im not sure why but i have re installed the firmware with no errors but still no wireless. on my laptop the wireless light is red and doesnt respond to the on/off button(which is in the fn keys). im not sure what steps next but help is much appreciated.

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux mars 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fb30]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
    Kernel driver in use: rtl8723ae

##### lsusb #####

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 03f0:2c24 Hewlett-Packard Logitech M-UAL-96 Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 04f2:b307 Chicony Electronics Co., Ltd 

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1
search gateway.2wire.net

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.100.117
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.254

    DNS:             192.168.100.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### lsmod #####

rtl8723ae              93211  0 
rtl_pci                27261  1 rtl8723ae
rtlwifi                64035  2 rtl8723ae,rtl_pci
mac80211              623607  3 rtl8723ae,rtl_pci,rtlwifi
cfg80211              499466  2 rtlwifi,mac80211

##### modinfo #####

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B27D28DF892890255CCDDBE
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7492FC488AD8A6D43075535
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9985D829F92712EC7AE7D4E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist nvidia_304_updates

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   11.500266] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   12.007751] rtlwifi: Firmware rtlwifi/rtl8723fw_B.bin not available

########## wireless info END ############

```

---

### Post by varunendra on 2014-03-18
The firmware is still missing -
> **srdshardwood said:**
> ```

[   11.500266] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   12.007751] rtlwifi: **[COLOR="#FF0000"]Firmware rtlwifi/rtl8723fw_B.bin not available[/COLOR]**

```

Either the firmware package (linux-firmware) didn't install properly, or it might have been broken. Assuming everything else in the system is working and there are no more (if any) broken packages, let's try a quick-fix.

Please download the attached zip file onto your Ubuntu Desktop > Right-click it > click "Extract here".

Then open a terminal and run the following commands (assuming the extracted file is on your Desktop) -
```
sudo mkdir -p /lib/firmware/rtlwifi
sudo cp Desktop/rtl8723fw_B.bin /lib/firmware/rtlwifi/
```

This will copy the file into your "/lib/firmware/rtlwifi" directory (creating the parent directory if it doesn't already exist) where the driver is looking for it.

After this, either reboot, or manually reload the driver with -
```
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae
```
Does the wifi work now? If not, please post back the output of -
```
dmesg | grep rtl
```

---

### Post by srdshardwood on 2014-03-18
Thanks this fixed the problem as my wireless does work now but a question i have is the wifi light on the laptop is still displaying red--off but it is definatly connected and working. im not concerned with it i was just curious why it still says off. anyhow thanks again. i am having a few other driver related issues and i will start new posts for them one has to do with my NVIDIA drivers, and the other was about the keyboard backlight, i would like to figure out how to turn it on.

---

### Post by srdshardwood on 2014-03-19
i wanted to mention to you that somehow the backlight on my keyboard has turned on..... can this be related to the fix we did or do you think its a ubuntu update that fixed this??

---

### Post by varunendra on 2014-03-19
> **srdshardwood said:**
> Thanks this fixed the problem as my wireless does work now but a question i have is the wifi light on the laptop is still displaying red--off but it is definatly connected and working. im not concerned with it i was just curious why it still says off.
Normally this shouldn't happen, but is not a big surprise either. Usually the wireless card and its status indicator have two related but independently controllable interfaces presented as two different interfaces to the system. It is possible that the switch that controls the switch is still "off", otherwise it maybe a firmware bug (which maybe fixed by an updated one).

To see the "rfkill switch" states (and possibly change it), please check or post back the output of -
```
rfkill list all
```

> **srdshardwood said:**
> i wanted to mention to you that somehow the backlight on my keyboard has turned on..... can this be related to the fix we did or do you think its a ubuntu update that fixed this??

It must be an update. The firmware I uploaded only deals with the wireless card, nothing else.

---

### Post by Carlo_Manuel_Molin on 2014-07-19
Hi,

I followed the fix in this thread (my wifi stopped working after kernel upgrade from 3.8.0-42 to 3.8.0-44). Here's my dmesg:

[   13.620539] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   14.396699] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.397207] rtlwifi: wireless switch is on

---

### Post by varunendra on 2014-07-19
> **Carlo_Manuel_Molin said:**
> I followed the fix in this thread....
Welcome to Ubuntu Forums! :)

The dmesg you posted contains no useful hints. To give us a detailed information about your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---


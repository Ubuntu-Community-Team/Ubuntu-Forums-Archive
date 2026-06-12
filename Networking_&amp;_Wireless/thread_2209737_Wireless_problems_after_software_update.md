---
title: "Wireless problems after software update"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by cahmadi26 on 2014-03-07
I am new to ubuntu and just recently downloaded it on my computer, had a friend install the drivers for me and everything was running flawlessly. Then i got a notification to "update software" and once the computer restarted I lost my ability to connect with the internet through wifi. I'm pretty sure that the computer wont even recognize that i have a wireless band. My computer is a lenovo yogapad 13


Any help is greatly appreciated. Thanks.

---

### Post by varunendra on 2014-03-07
Welcome to the forums cahmadi26 ! :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us all the relevant info to help determine and solve the problem.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by cahmadi26 on 2014-03-07
I wasn't sure if you wanted all of this but here it is. Thanks for the help.


The output of code:
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
```


*************** info trace ***************


***** uname -a *****


Linux cyrus-Lenovo-IdeaPad-Yoga-13 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****




***** lsusb *****


Bus 002 Device 004: ID 5986:029c Acer, Inc 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04f3:000a Elan Microelectronics Corp. 
Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** iw reg get *****


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         144.118.239.254 0.0.0.0         UG    0      0        0 eth0
144.118.224.0   0.0.0.0         255.255.240.0   U     1      0        0 eth0


***** lsmod *****


rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63229  2 rtl_usb,rtl8192cu
rtl8192c_common        49527  1 rtl8192cu
mac80211              597268  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              480503  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            asix
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         144.118.225.67
    Prefix:          20 (255.255.240.0)
    Gateway:         144.118.239.254


    DNS:             144.118.24.20
    DNS:             144.118.24.10






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1
search resnet.drexel.edu


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


***** modinfo *****


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     6BD4434FB2415C434F73006
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846pF001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp819Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     869111DAE2B855A98C64397
depends:        rtlwifi,mac80211
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


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D6221EBE7F9AFB5C639D02D
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 




***** udev rules *****


# USB device 0x:0x (rtl8723au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****




****************** done ******************

```

---

### Post by varunendra on 2014-03-07
Yes I do need the complete output, and if the above one IS the complete output, there is something seriously wrong with the update that happened.

The lspci part being empty (unless you missed it while 'selectively' copy-pasting) indicates a possible broken update.

As for the wireless part, you seem to have currently loaded a wrong driver "rtl8192cu" for it. Did you use an external USB adapter? If not, that is something that you or your friend may have done while trying random suggestions.

Anyway, from what I can see from the output, you need a very new driver which is neither in the kernel, nor on Realtek's official website. You'll have to follow this procedure to download and install it : [http://askubuntu.com/a/358479](http://askubuntu.com/a/358479) *(Thanks to **david**, @ askubuntu)*

And you'll have to repeat the installation part _EveryTime_ your kernel is upgraded, until the driver is included in kernel itself.

Try the procedure in the given link, and if you get any errors, post back the error you get.

If the installation goes smoothly, you may additionally need to remove the driver rtl8192cu if it is somehow forced to load automatically. Post back how it goes, and we'll sort it out as and if required.

---

### Post by cahmadi26 on 2014-03-07
It works again! thank you so much. Do you still recommend that I remove the other driver?

---

### Post by varunendra on 2014-03-08
You're welcome! :)

> **cahmadi26 said:**
> Do you still recommend that I remove the other driver?

Yes, please do so if you have done something to 'force' load it (like adding it to /etc/modules or /etc/rc.local files). If there are no devices that need it, it *may* conflict with the driver that is actually needed and is being used. Loading multiple drivers sharing same resources is never a good idea unless necessary.

And if a device really needs the other driver (rtl8192cu), it will load automatically when needed.

That being said, of course it is not necessary if things are working and you are not very sure of what you'd be doing to remove the other driver. But in case of problems, do it the first thing. :)

---

### Post by Murdoc_of_puts on 2014-03-11
Super helpful, thanks, also worked for me.

---

### Post by varunendra on 2014-03-11
All credits go to the nice post by David @ AskUbuntu. :)

---

### Post by Murdoc_of_puts on 2014-03-12
ok, so 1 problem though, now it seems to randomly drop the wifi connection, if I turn it off and back on it will work fine, until it drops again.  If I remove the rtl8192 module, the wifi goes with it.

---

### Post by varunendra on 2014-03-12
> **Murdoc_of_puts said:**
> ok, so 1 problem though, now it seems to randomly drop the wifi connection, if I turn it off and back on it will work fine, until it drops again.  If I remove the rtl8192 module, the wifi goes with it.

I wouldn't expect too much from an experimental driver, but perhaps you should post a new thread of your own with a detailed description of the problem and whatever you have tried. Along with the description, also post the "wireless_script" report for technical details.

Feel free to post a link to it here or PM me (or other potential helpers) to take a look at it. Maybe we could try some further tweaks to make it work better.

---

### Post by srdshardwood on 2014-03-17
hi i tried your method but still have no wireless!! im not sure how this happened everything has been good since i installed only a few weeks ago and simply did the updates from update manager. also i have been trying to get my NVIDIA drivers to work which also used to work before i did some updates and so after trying to repair my NVIDIA and doing updates at the same time i rebooted to find no wireless. any help is much appreciated !! :)

Here's the output of your wireless script<!>

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

[   10.731672] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   11.073205] rtlwifi: Firmware rtlwifi/rtl8723fw_B.bin not available

########## wireless info END ############

```

---

### Post by varunendra on 2014-03-17
Welcome to the forums srdshardwood!

It looks like you had a broken update, the required firmware that should have been part of default installation is missing -
> **srdshardwood said:**
> ```
##### dmesg #####

[   10.731672] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   11.073205] rtlwifi: **[COLOR="#FF0000"]Firmware rtlwifi/rtl8723fw_B.bin not available[/COLOR]**
```

Hoping you can complete the update now, without problems, please open a terminal (Ctrl-Alt-T) and run the following commands -
```
sudo apt-get update
sudo apt-get install --reinstall linux-firmware
```

Watch out for errors, and post back if there are any.

If you get any errors, or the wireless still doesn't work after the above successfully completing, please start a new thread and post the fresh wireless-info report and the errors (if any) along with a description of the problem there. Yours is a different card (RTL8723ae), which is different from the card discussed in this thread, so a new thread with relevant title would be better to address your problem.

Feel free to post its link here if you needed to start the new thread. :)

---

### Post by srdshardwood on 2014-03-18
thanks Varun i did the commands and they completed with no errors but after a reboot have no wireless, also i have tried these commands and still no luck..> i also started the new thread as you said

```

sudo apt-get install git build-essential && git clone https://github.com/lwfinger/rtl8723au.git && make && sudo make install

```

---

### Post by varunendra on 2014-03-18
> **srdshardwood said:**
> thanks Varun i did the commands and they completed with no errors but after a reboot have no wireless, also i have tried these commands and still no luck..> i also started the new thread as you said

```

sudo apt-get install git build-essential && git clone https://github.com/lwfinger/rtl8723au.git && make && sudo make install

```

Replied in your thread : [http://ubuntuforums.org/showthread.php?t=2211847](http://ubuntuforums.org/showthread.php?t=2211847)

Please continue there. By the way, the driver you tried to install above (rtl8723au) is for USB devices, not for your card which is a PCI one.

---


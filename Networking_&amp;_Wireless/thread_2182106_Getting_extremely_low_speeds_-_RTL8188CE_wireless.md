---
title: "Getting extremely low speeds - RTL8188CE wireless"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Cracky7 on 2013-10-20
I finished building my computer a day ago, and now I'm facing with this  problem. I have a wireless card (Asus PCIE N10) installed, and I'm  getting speeds of 0.77Mbps on speedtest.net. When I try the same test on  either my laptop or Windows 8, I get around x10 that speed (6-7Mbps).

After googling a bit, I logged into the router and tried to change the  channel to 11, it didn't work. I also tried to install the drivers that came with the card, but they can't be installed in Ubuntu versions older than 10.10. So I'll trust you guys with this one.  Thanks! I'm using latest Ubuntu 13.10.

Outputs for:

[iwconfig]("http://pastebin.com/hhatYteC")

[lspci -nnk | grep -iA2 net]("http://pastebin.com/AdDLZRQK")

[lsusb]("http://pastebin.com/qmq0P1LL")

[lsmod]("http://pastebin.com/xKxd4Pfp")

[cat /etc/resolv.conf]("http://pastebin.com/1ePZcgFg")

[ iwlist chan]("http://pastebin.com/2aa9Ki94")

[ sudo iwlist scan]("http://pastebin.com/UpHzqk97")

---

### Post by Cracky7 on 2013-10-20
Bump

---

### Post by Cracky7 on 2013-10-21
Bump again. Help please...

---

### Post by coffeecat on 2013-10-23
I've edited your thread title to include some detail about the wireless device, which would seem to be relevant. Googling suggests that the Linux driver might be problematic for this device. This link below refers to an older version of Ubuntu, but it seems to describe a similar problem.

[http://askubuntu.com/questions/205575/12-10-x64-rtl8188ce-intermittent-slow-internet-connection](http://askubuntu.com/questions/205575/12-10-x64-rtl8188ce-intermittent-slow-internet-connection)

Hopefully with RTL8188CE in the title, it will attract help from someone with experience of this chipset.

---

### Post by wildmanne39 on 2013-10-23
Hi, this driver is problematic but I will take a shot at it sometimes we can get it working, sometimes we have to compile a new driver, but I doubt there is one yet for 13.10.

Please post the output of:
```
grep -R [0-9a-zA-Z] /sys/module/rtl8192ce/parameters/
```
Thanks

---

### Post by Cracky7 on 2013-10-24
grep -R [0-9a-zA-Z] /sys/module/rtl8192ce/parameters/
```
zsh: no matches found: [0-9a-zA-Z]
```

---

### Post by wildmanne39 on 2013-10-24
Copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Cracky7 on 2013-10-24
It doesn't even find the wifi network now (well, it's been happening since a couple of days). I can get Internet with an old USB wifi card I have lying around, but it gives me much lower speeds. This is wireless-info.txt with the USB unplugged:

```



*************** info trace ***************


***** uname -a *****


Linux Energy 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
03:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller [1912:0015] (rev 02)
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7693]
	Kernel driver in use: r8169


***** lsusb *****


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 009 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






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




***** blacklist *****


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


***** modinfo *****




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[  146.045601] zd1211rw 6-1:1.0: firmware version 4725
[  146.070473] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  146.071085] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  147.766349] wlan1: authenticate with <MAC address removed>
[  147.782565] wlan1: send auth to <MAC address removed> (try 1/3)
[  147.784310] wlan1: authenticated
[  147.784542] zd1211rw 6-1:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[  147.784550] zd1211rw 6-1:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[  147.785453] wlan1: associate with <MAC address removed> (try 1/3)
[  147.787680] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  147.788088] wlan1: associated
[  147.788132] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  679.473415] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)


****************** done ******************



```

---

### Post by wildmanne39 on 2013-10-24
Well that information was not as helpful as it should have been because for some reason your driver is not loaded at all, please do:

```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
see if it connects and if it is still slow please run the script again and post the new results.
Thanks

---

### Post by Cracky7 on 2013-10-25
Well, it finds the network now, but back to the 0.80 Mbps speed. Ran the script again:

```


*************** info trace ***************


***** uname -a *****


Linux Energy 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
	Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7693]
	Kernel driver in use: r8169


***** lsusb *****


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 009 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"DARP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1783   Missed beacon:0




***** rfkill *****


1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8192ce              53550  0 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        48877  1 rtl8192ce
mac80211              596969  4 rtl_pci,rtlwifi,zd1211rw,rtl8192ce
cfg80211              479757  3 mac80211,rtlwifi,zd1211rw


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [DARP] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *DARP:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WPA2


  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"DARP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000136aa4d9d
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000444415250
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     69021F8FC8BF76DE7C8DD9C
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E94C1FCAB8071D430AC01C6
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   10.674806] zd1211rw 6-1:1.0: firmware version 4725
[   10.703915] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   10.704211] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   12.467898] wlan1: authenticate with <MAC address removed>
[   12.484491] wlan1: send auth to <MAC address removed> (try 1/3)
[   12.491332] wlan1: authenticated
[   12.491460] zd1211rw 6-1:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   12.491463] zd1211rw 6-1:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   12.491558] wlan1: associate with <MAC address removed> (try 1/3)
[   12.493745] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   12.493927] wlan1: associated
[   12.493952] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   73.054852] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  100.133593] rtl8192ce: rtl8192ce: Power Save off (module option)
[  100.133597] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  100.133607] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  100.139855] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  100.140142] rtlwifi: wireless switch is on
[  100.492306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  100.492566] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  102.241325] wlan0: authenticate with <MAC address removed>
[  102.260931] wlan0: send auth to <MAC address removed> (try 1/3)
[  102.262433] wlan0: authenticated
[  102.262658] rtl8192ce 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  102.262666] rtl8192ce 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  102.264698] wlan0: associate with <MAC address removed> (try 1/3)
[  102.266830] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  102.266897] wlan0: associated
[  102.266943] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by wildmanne39 on 2013-10-25
I see your usb adaptor was plugged in when you ran the wireless script, when you have it plugged in the driver will be in conflict with your internal wireless card, did you have the usb device unplugged when you tested the speed this last time?

Also this is in the dmesg:
```
disabling HT as WMM/QoS is not supported by the AP
```
Go into your router and find that setting and change it to enabled then save the router settings and reboot your computer.
Thanks

---

### Post by Cracky7 on 2013-10-27
But it was unplugged, I think. Okay, I enabled WMM inside QoS setup. Rebooting now.

Okay, I rebooted with the USB unplugged, loaded the drivers as you said in previous posts and then did the speedtest. I got slow speeds. Running wireless_script again:
```


*************** info trace ***************


***** uname -a *****


Linux Energy 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
	Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7693]
	Kernel driver in use: r8169


***** lsusb *****


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 009 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"DARP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1354   Missed beacon:0




***** rfkill *****


1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rtl8192ce              53550  0 
rtl_pci                26641  1 rtl8192ce
rtlwifi                63229  2 rtl_pci,rtl8192ce
rtl8192c_common        48877  1 rtl8192ce
mac80211              596969  4 rtl_pci,rtlwifi,zd1211rw,rtl8192ce
cfg80211              479757  3 mac80211,rtlwifi,zd1211rw


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [DARP] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *DARP:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2


  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"DARP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001661db12
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000444415250
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8F7DAD3B5887F2048AC7550
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     69021F8FC8BF76DE7C8DD9C
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E94C1FCAB8071D430AC01C6
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884E835120981A6FA10A621
depends:        
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   35.438078] zd1211rw 6-1:1.0: firmware version 4725
[   35.465440] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   35.465769] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   37.148687] wlan1: authenticate with <MAC address removed>
[   37.165159] wlan1: send auth to <MAC address removed> (try 1/3)
[   37.166620] wlan1: authenticated
[   37.168251] wlan1: associate with <MAC address removed> (try 1/3)
[   37.170445] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   37.170858] wlan1: associated
[   37.170887] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   97.328518] wlan1: deauthenticating from <MAC address removed> by local choice (reason=3)
[  130.412707] rtl8192ce: rtl8192ce: Power Save off (module option)
[  130.412713] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[  130.412733] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[  130.419496] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  130.419892] rtlwifi: wireless switch is on
[  130.772940] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  130.773180] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.521505] wlan0: authenticate with <MAC address removed>
[  132.541463] wlan0: send auth to <MAC address removed> (try 1/3)
[  132.542984] wlan0: authenticated
[  132.544819] wlan0: associate with <MAC address removed> (try 1/3)
[  132.547822] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  132.547883] wlan0: associated
[  132.547936] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************



```

---

### Post by Cracky7 on 2013-10-29
Bump

---

### Post by Cracky7 on 2013-11-01
Bump. Please?

---

### Post by wildmanne39 on 2013-11-01
Hi, we are going to compile a new driver that is suppose to work good with 13.10.

Go here: [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver) click on the download zip button, after it is finished downloading move the zip file to your desktop and click extract here.

Open the terminal (CTRL+ALT+T) Run the following commands one line at a time and watch for errors, (copy and paste for accuracy):
```
sudo apt-get install linux-headers-$(uname -r) build-essential git
cd Desktop/rtl8188ce-linux-driver-master
make
sudo make install
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce
```
When  there is a kernel upgrade you will have to do by changing into the directory of the driver:
```
sudo su
make clean
make
make install
modprobe -v rtl8192
exit

```
Thanks

---

### Post by Cracky7 on 2013-11-01
Okay, it compiled without errors. I can't tell you if it worked yet because I'm getting slow speeds on Windows too (my IPS's fault) so I'll let you know as soon as I can.

Also, in "sudo modprobe v rtl8192ce" you mean "sudo modprobe -v rtl8192ce" right?

---

### Post by wildmanne39 on 2013-11-01
Yes this is what I meant > sudo modprobe -v rtl8192ce
You may still need the parameters loaded that you loaded with the other driver but they should still be there unless you removed them.
Thanks

---

### Post by Cracky7 on 2013-11-02
Nope, I'm not. Still getting slow speeds and the connection drops from time to time. Most of the time, I run 

```
sudo modprobe -rv rtl8192ce

sudo modprobe -v rtl8192ce
```


and it's back up, but still with slow speeds.

---

### Post by wildmanne39 on 2013-11-02
Please run the script again so we can look at the settings of your router may be there is something that we can change to help.

Also post the results of:
```
modinfo rtl8192ce | grep version
```
Thanks

---

### Post by Cracky7 on 2013-11-02
wireless_info:

```


*************** info trace ***************


***** uname -a *****


Linux Energy 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b5]
    Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7693]
    Kernel driver in use: r8169


***** lsusb *****


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
Bus 009 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"DARP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:512   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8192ce             137725  0 
rtlwifi               110108  1 rtl8192ce
mac80211              596969  2 rtlwifi,rtl8192ce
cfg80211              479757  2 mac80211,rtlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [DARP] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *DARP:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DARP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000198c1cb622
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000444415250
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B140057BDC2D312F995749E
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     019F93BDB32F49BC7749C53
depends:        mac80211,cfg80211
vermagic:       3.11.0-12-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (zd1211rw)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   29.475699] rtl8192ce: unknown parameter 'debug' ignored
[   29.513274] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   29.513481] rtlwifi: wireless switch is on
[   29.858068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.858311] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.630411] wlan0: authenticate with <MAC address removed>
[   31.650246] wlan0: send auth to <MAC address removed> (try 1/3)
[   31.653127] wlan0: authenticated
[   31.653826] wlan0: associate with <MAC address removed> (try 1/3)
[   31.656394] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   31.656498] wlan0: associated
[   31.656514] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.530813] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   39.456545] wlan0: authenticate with <MAC address removed>
[   39.466518] wlan0: send auth to <MAC address removed> (try 1/3)
[   39.475489] wlan0: authenticated
[   39.476061] wlan0: associate with <MAC address removed> (try 1/3)
[   39.478549] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   39.478653] wlan0: associated
[   45.054177] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   45.873359] wlan0: authenticate with <MAC address removed>
[   45.883249] wlan0: send auth to <MAC address removed> (try 1/3)
[   45.887333] wlan0: authenticated
[   45.888887] wlan0: associate with <MAC address removed> (try 1/3)
[   45.893146] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   45.893240] wlan0: associated


****************** done ******************



```

modinfo rtl8192ce | grep version:
```
srcversion:     B140057BDC2D312F995749E
vermagic:       3.11.0-12-generic SMP mod_unload modversions 



```

---

### Post by wildmanne39 on 2013-11-02
Please set your wireless settings to match the screenshots:
Does that help?
Thanks

---

### Post by wildmanne39 on 2013-11-02
Please open this file and post the contents here:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
Thanks

---

### Post by Cracky7 on 2013-11-04
Changing those options and rebooting did not help.

```
options rtl8192ce swenc=1 ips=0
```

---

### Post by wildmanne39 on 2013-11-04
The last thing that I know to try thanks to chili555 reminding me is go into your router and change 802.11bgn to 802.11bg then save the settings and reboot your computer.

This driver has had many issuses and that has help with speed in many cases along with the other things we have done already.
Thanks

---

### Post by Cracky7 on 2013-11-05
I found the setting, it's set to:
```

802.11 Mode :	Mixed 802.11g and 802.11b

```

---

### Post by wildmanne39 on 2013-11-05
This is the last thing I know to try:
[http://askubuntu.com/questions/368693/wpa2-disconnects-at-intervals/368765?noredirect=1#comment475201_368765](http://askubuntu.com/questions/368693/wpa2-disconnects-at-intervals/368765?noredirect=1#comment475201_368765)

You did change your wireless settings to match the screenshots in my previous post?
Thanks

---

### Post by Cracky7 on 2013-11-06
I did change the IPv4 and v6 settings, and it didn't work. Same with the ofono thing. Well, I'll just wait. Maybe some update will magically resolve it.

Thanks for the help man.

---


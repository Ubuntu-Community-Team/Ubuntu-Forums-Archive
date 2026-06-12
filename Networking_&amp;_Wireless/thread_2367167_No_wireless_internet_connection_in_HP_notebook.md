---
title: "No wireless internet connection in HP notebook"
date: 2017-07-26
forum: Networking &amp; Wireless
---

### Post by vjsjith on 2017-07-26
I am using both Ubuntu 14.04 LTS and windows 10 Os In my HP laptop  I cant use wireless network in Ubuntu 14.04. wired connection is fine. If the system is very close with wireless modem antenna I am able to connect network. In windows both wireless and and wired connection work properly and very favourably, Please help me to solve this issues. wireless-info shown below.

```

########## wireless info START ##########

Report from: 26 Jul 2017 22:44 IST +0530

Booted last: 26 Jul 2017 21:56 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:81c1]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:81f1]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 275d:0ba6  
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 003: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              741376  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              552960  3 wl,mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25300827 (25.3 MB)  TX bytes:1807234 (1.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:475973 (475.9 KB)  TX bytes:475973 (475.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       857     1  0 21:56 ?        00:00:03 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=802-11-wireless
[802-11-wireless] ssid=D-Link | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Moto G (4) 3808]] (600 root)
[connection] id=Moto G (4) 3808 | type=802-11-wireless
[802-11-wireless] ssid=Moto G (4) 3808 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-35-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[rtl8723be]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     867B4080247A86ABBA59D17
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   20.310013] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.572674] r8169 0000:03:00.0 eth0: link down
[   20.572747] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.113490] r8169 0000:03:00.0 eth0: link up
[   22.113514] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  120.585691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  167.280531] r8169 0000:03:00.0 eth0: link down
[  249.971837] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  250.172096] r8169 0000:03:00.0 eth0: link down
[  250.172166] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  326.826968] r8169 0000:03:00.0 eth0: link up
[  326.827620] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  326.835064] r8169 0000:03:00.0 eth0: link up
[ 2770.576354] r8169 0000:03:00.0 eth0: link down

########## wireless info END ############
```

---

### Post by QIII on 2017-07-26
Hello!

Please enclose all long text and terminal commands and their output in code tags. This will preserve formatting (for instance: you won't get smilies) and make your posts much easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. The square brackets are required. 

Cheers!

---

### Post by Hadaka on 2017-07-26
Hi, from a working wired connection please copy and paste one line at a time.
```
sudo apt-get update
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
```
 then do..
```
sudo iw reg set IN
sudo sed -i 's/=.*/=IN/' /etc/default/crda
```
next..
```
echo "options rtl8723be ant_sel=2"  | sudo tee /etc/modprobe.d/rtl8723be.conf
```
*Boot and test wireless..if still no connect then do...
```
echo "options rtl8723be ant_sel=1"  | sudo tee /etc/modprobe.d/rtl8723be.conf
```
*Boot and test wireless
Thanks.

---

### Post by vjsjith on 2017-07-26
Thanks                           		  		 			 				 					[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1599436") 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=1599436"][B][COLOR=#000000]Hadaka
[/COLOR][/B]_[COLOR=#000000][/COLOR]_[COLOR=#000000]All are done , but issue still going on[/COLOR][U][COLOR=#000000]
[/COLOR][/U][/URL]

---

### Post by Hadaka on 2017-07-26
Hi, please post a new wireless-info report.
Thanks

---

### Post by praseodym on 2017-07-26
Try deactivating IPv6 in the network profile

---

### Post by johndough2 on 2017-07-27
Hi

Would you mind giving the parameters that are used in Windows 10 for your network, by pasting in some results from using the following (it is a .txt file that should be saved and run as a .bat ) and generating some text files.

It is a screen in command prompt with 16 choices, the safest is F to Finish, do nothing.  Other choices would be
3, 8, 9 and B (then exit with F).

```

:: Copy, Paste & Save As...NetFixed.bat.
:: Use a text editor (Notepad). Then when
:: it's run will create IP.txt & another 
:: file called NETSTAT.txt for posting.
:: Run as Administrator for best outcome.
@ECHO  THIS MAY HELP TO REPAIR / RECTIFY,
@ECHO  VERY, SIMPLE NETWORK DIFFICULTIES.
@ECHO................................... 
@ECHO  THE RESULTS MAY VARY ACCORDING TO 
@ECHO  YOUR CONFIGURATION AND USER LEVEL.
@ECHO  A RE-BOOT MUST BE DONE AFTER DOING
@ECHO  SOME OF THE CHECKS OPTIONED BELOW.
@ECHO....................................
:MENU
@ECHO  TYPE IN YOUR PREFERRED MENU CHOICE
@ECHO....................................
@ECHO.
@ECHO  0 - PING_LO Ping test to 127.0.0.1
@ECHO  1 - PING_MS Ping test to Microsoft
@ECHO  2 - GET_MAC Obtain MAC address(es)
@ECHO  3 - GET_IPs Lists all IP addresses
@ECHO  4 - IPvFOUR Reset to remove errors
@ECHO  5 - IP_RNEW Force/Renew IP address
@ECHO  6 - IPv_SIX Reset to remove errors
@ECHO  7 - NBTSTAT NETBIOS -Renew -Repair
@ECHO  8 - NETSTAT All Network Statistics
@ECHO  9 - SH_WLAN Display WLAN interface
@ECHO  A - ARP_TAB Displays ARP IP tables
@ECHO  B - NS_LKUP Shows your Name Server
@ECHO  C - SYS_SUM System Summary Windows
@ECHO  D - DNS_FIX Flush and Register DNS
@ECHO  E - WINSOCK Reset to remove errors
@ECHO  F - FINISHD Close this Command Box
@ECHO ...................................
@ECHO OFF
COLOR B1
SET /P M= Press 0-9, A-F, and then ENTER:
IF %M%==0 GOTO PING_LO
IF %M%==1 GOTO PING_MS
IF %M%==2 GOTO GET_MAC
IF %M%==3 GOTO GET_IPs
IF %M%==4 GOTO IPvFOUR
IF %M%==5 GOTO IP_RNEW
IF %M%==6 GOTO IPv_SIX
IF %M%==7 GOTO NBTSTAT
IF %M%==8 GOTO NETSTAT
IF %M%==9 GOTO SH_WLAN
IF /I %M%==A GOTO ARP_TAB
IF /I %M%==B GOTO NS_LKUP
IF /I %M%==C GOTO SYS_SUM
IF /I %M%==D GOTO DNS_FIX
IF /I %M%==E GOTO WINSOCK
IF /I %M%==F GOTO FINISHD
:PING_LO
ping LOOPBACK
GOTO MENU
:PING_MS
ping MICROSOFT.COM
GOTO MENU
:GET_MAC
getmac | more /c
getmac >> c:\GetMac.txt
Notepad c:\GetMac.txt
GOTO MENU
:GET_IPs
ipconfig -all | more /c
ipconfig -all >>IP.txt
Notepad IP.txt
GOTO MENU
:IPvFOUR
netsh int ipv4 reset reset.log
GOTO MENU
:IP_RNEW
ipconfig /release
ipconfig /renew
GOTO MENU
:IPv_SIX
netsh int ipv6 reset reset.log
GOTO MENU
:NBTSTAT
nbtstat -RR
GOTO MENU
:NETSTAT
netstat -e -r -s | more /c
netstat -e -r -s >> NetStat.txt
Notepad NetStat.txt
GOTO MENU
:SH_WLAN
netsh wlan show drivers | more /c
netsh wlan show interfaces | more /c
GOTO MENU
:ARP_TAB
arp /a
GOTO MENU
:NS_LKUP
nslookup /ns
GOTO MENU
:SYS_SUM
msinfo32
GOTO MENU
:DNS_FIX
ipconfig /flushdns
ipconfig /registerdns
GOTO MENU
:WINSOCK
netsh winsock reset catalog
GOTO MENU
:FINISHD
EXIT


```

---

### Post by vjsjith on 2017-07-28
HI Hadaka, 
This is new wireless-info report.
Output:

```

########## wireless info START ##########

Report from: 28 Jul 2017 22:44 IST +0530

Booted last: 28 Jul 2017 22:42 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:81c1]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:81f1]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 275d:0ba6  
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              741376  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              552960  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10784 (10.7 KB)  TX bytes:10784 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       791     1  2 22:42 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF2]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Moto G (4) 3808]] (600 root)
[connection] id=Moto G (4) 3808 | type=802-11-wireless
[802-11-wireless] ssid=Moto G (4) 3808 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     867B4080247A86ABBA59D17
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   10.357380] rtl8723be: unknown parameter 'ant_sel' ignored
[   10.372871] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   10.405210] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.414802] rtlwifi: rtlwifi: wireless switch is on
[   14.983591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.208360] r8169 0000:03:00.0 eth0: link down
[   15.208440] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.137396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  122.716576] r8169 0000:03:00.0 eth0: link down
[  122.716644] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

########## wireless info END ############
```

---

### Post by QIII on 2017-07-28
Please refer again to post #2.

Thanks.

---

### Post by praseodym on 2017-07-28
Your /etc/resolv.conf is empty. Please run
```

sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Hadaka on 2017-07-28
Hi, the dmesg error is showing..
```
##### dmesg #############################
[   10.357380] rtl8723be: unknown parameter 'ant_sel' ignored
```
You are missing the ability to select your antenna connection.
This is why it only works when you are sitting next to the router.
With a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then..
Please read carefully and copy and paste from this link.....post #3
[https://ubuntuforums.org/showthread.php?t=2327483&p=13502516#post13502516](https://ubuntuforums.org/showthread.php?t=2327483&p=13502516#post13502516)
Please post back an update when completed.
Thanks

---

### Post by praseodym on 2017-07-28
Hi,

the driver version shipped with kernel 4.2 lacks this parameter. You may upgrade the system using the LTS-enablement stack, or update the driver:

Test

```
sudo apt-get -s install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
```
Edit: Did you install Ubuntu with activated SecureBoot?

---

### Post by johndough2 on 2017-07-30
Hi

Your WiFi Hardware is installed and working.

Your setup is not.

Try more than 1 network manager, like wicd.

There are frequencies listed, but you are not using even 1 of them, so you need to go thru the network manager and choose an SSID and set the password etc, then you should see an improvement.

---

### Post by Hadaka on 2017-07-30
Hi, please use post # 11 or # 12 to correct the wifi configuration.
Everything else is correct including the use of Network Manager.



 #@johndough2
Your post has nothing to do with the wifi behavior
and will only compound the problem.  *see post #11 for reason this wifi is not working correctly.

---


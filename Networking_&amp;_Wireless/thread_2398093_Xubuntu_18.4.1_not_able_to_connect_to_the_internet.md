---
title: "Xubuntu 18.4.1 not able to connect to the internet"
date: 2018-08-07
forum: Networking &amp; Wireless
---

### Post by fr34kyfr34k on 2018-08-07
Hello Ubuntu forums!  I just recently installed Xubuntu on an old computer I had (it was my first time ever installing Linux), and it doesn't seem to be able to connect to the internet.

The first time I used it after I installed it I connected to the internet just fine.  But, for some reason, the second time I booted it up it disconnected and I have not been able to figure out why.  In the top right corner it shows two greyed out arrows, and when I click on them both "Enable Networking" and "Enable Wi-Fi" are checked, but everything but "Edit Conections..." is greyed out.  I know you probably need more information then this to help me, but I'm not sure what you need to know :P

Anyways, any help would be appreciated!

---

### Post by oldos2er on 2018-08-07
Moved to Networking and Wireless. 

Could you tell us if you're using a wired or wireless connection? And what make/model networking hardware,  please?

---

### Post by fr34kyfr34k on 2018-08-07
Thanks. I'm using a wireless connetion, and my router is a Netgear N6000 (not sure if that's specific enough or not :P)

---

### Post by ajgreeny on 2018-08-07
We need to know the wifi hardware of the computer, not your router as that is unlikely to have much effect on the wifi connection provided you are using wpa2 encryption.

If you're not sure about this please run command **lspci** in terminal and show us the output here.
It will also be useful for us if you go to Wireless-Info in my signature and follow the information there to run the script and report back here the output from that.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by fr34kyfr34k on 2018-08-07
Output from lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Limited BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```

Output from script:
```


########## wireless info START ##########

Report from: 07 Aug 2018 16:51 EDT -0400

Booted last: 07 Aug 2018 00:00 EDT -0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:37:27 UTC 2018 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell BCM4401-B0 100Base-TX [1028:01cb]
    Kernel driver in use: b44

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
    Subsystem: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:1020]
    Kernel driver in use: ipw2200

##### lsusb #############################

Bus 001 Device 003: ID 0781:5581 SanDisk Corp. Ultra
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

dell_laptop            20480  0
ipw2200               139264  0
libipw                 32768  1 ipw2200
dell_smbios            16384  2 dell_laptop,dell_smbios_smm
cfg80211              532480  2 ipw2200,libipw
ssb                    57344  1 b44
video                  40960  2 dell_laptop,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 93489  bytes 5615883 (5.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 93489  bytes 5615883 (5.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s3: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlp2s3    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       448     1  0 07:05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         wlp2s3
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 2915ABG [Calexico2] Network Connection
GENERAL.DRIVER:                         ipw2200
GENERAL.DRIVER-VERSION:                 1.2.2kmprq
GENERAL.FIRMWARE-VERSION:               ABG:9.0.5.27 (Dec 12 2007)
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/net/wlp2s3
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/DukeandT2]] (600 root)
[connection] id=DukeandT2 | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DukeandT2
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlp2s3    24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Channel=0

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlp2s3    No scan results

##### module infos ######################

[ipw2200]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/intel/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     CA4E969774051DEE5C3C6C6
depends:        cfg80211,libipw
retpoline:      Y
intree:         Y
name:           ipw2200
vermagic:       4.15.0-29-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/4.15.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-29-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     12D8BAB8F43573B88998E25
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       4.15.0-29-generic SMP mod_unload 686 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

##### module parameters #################

[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-acer.conf]
blacklist acer_wmi

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   24.687576] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   24.687579] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   24.687867] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   25.457420] ipw2200: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.
[   25.498103] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   25.513302] ipw2200 0000:02:03.0 wlp2s3: renamed from eth1
[   35.409041] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   35.530799] IPv6: ADDRCONF(NETDEV_UP): wlp2s3: link is not ready

########## wireless info END ############


```

Thanks for the reply!

---

### Post by wildmanne39 on 2018-08-07
That is a very old device but it says your wifi is turned off by the switch, find the switch, button or key combination and press it once and see if it comes on, you can check with.
```
rfkill list all
```

Thanks

---

### Post by fr34kyfr34k on 2018-08-07
Oh my gosh thank you so much, it worked! And yes, it is a very old machine. It had been laying around my church unused for the past 10 years, and I was finally able to snag it. Then, since I didn't know what else to do with it, I decided to try installing Linux on it :P

Thanks again for all the help guys!

---

### Post by wildmanne39 on 2018-08-07
Your welcome! Please use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by fr34kyfr34k on 2018-08-07
Already done ;)

Thanks again!

---


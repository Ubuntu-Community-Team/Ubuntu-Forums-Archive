---
title: "Dell Inspiron 5520 Dual Boot Ubuntu 12.04.3 LTS Wireless Keep Disconnecting"
date: 2014-01-24
forum: Networking &amp; Wireless
---

### Post by Jegul on 2014-01-24
Well, i am using Dell Inspiron 5520 (Wrong version in thread, which i wrote 5510) Windows 7,
and today i installed ubuntu 12.04.3 LTS on this laptop,
everything works fine except for the wireless connection,
it keeps disconnecting every 1 minute and i have to turn off the wireless and turn on again so it will connect
Can you help me solve this annoying problem?
I can't even update because of this problem

I am new to linux environment, so please help me,
it's even hard to post this thread

---

### Post by tripp98 on 2014-01-25
Hard wire to the on board wired connection.
open system settings
open software and updates
on the additional drivers tab
see if there is a proprietary driver available.

---

### Post by varunendra on 2014-01-26
And if installing a proprietary driver doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions in the linked post, and post back the report it generates.

While posting the outputs, please use 'Code' tags. To see a quick "How To" on using code tags, please follow the "Using Code Tags" link in my signature below.

**PS:**
Not sure how long it is allowed, but you can edit the title of your first post upto a certain amount of time to correct the thread title. If you can't, you may use the "Report Post" button at the bottom of your post to report it to the mods requesting to do that for you. I'm going to use that button to request the mods now. :)

---

### Post by Jegul on 2014-01-26
well, there is no proprietary driver when i checked it.
and so i used the wireless script and here is the code
```

*************** info trace ***************


***** uname -a *****


Linux ubuntu 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu

Description:    Ubuntu 12.04.3 LTS

Release:    12.04

Codename:    precise


***** lspci *****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

    Subsystem: Dell Device [1028:0569]

    Kernel driver in use: r8169

--

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)

    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4462]

    Kernel driver in use: iwlwifi


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

Bus 003 Device 002: ID 0781:5530 SanDisk Corp. Cruzer

Bus 003 Device 003: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 

Bus 001 Device 004: ID 064e:8125 Suyin Corp. 

Bus 002 Device 006: ID 8087:07da Intel Corp. 


***** PCMCIA Card Info *****


&#12288;

***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          


***** rfkill *****


1: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

4: hci0: Bluetooth

    Soft blocked: yes

    Hard blocked: no


***** lsmod *****


iwldvm                249093  0 

mac80211              630977  1 iwldvm

iwlwifi               183603  1 iwldvm

cfg80211              525244  3 iwldvm,mac80211,iwlwifi


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [IL'Dormnitory A16-17 3] --------------------------------------

  Type:              802.11 WiFi

  Driver:            iwlwifi

  State:             connected

  Default:           yes

  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties

    WEP Encryption:  yes

    WPA Encryption:  yes

    WPA2 Encryption: yes


  Wireless Access Points 

    UNIT-00:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2

    IL'Dormitory-A16-17-4: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2

    IL'Dormitory A16-17 Lt.2: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

    Medang_Hotspot:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 9 Mb/s, Strength 24 WPA WPA2

    SUPER BEJO AP2:  Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WEP

    PT. dwi global sentosa: Infra, <MAC address removed>, Freq 2412 MHz, Rate 48 Mb/s, Strength 22 WEP

    IL'Dormnitory A16-17 3: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2


  IPv4 Settings:

    Address:         192.168.1.48

    Prefix:          24 (255.255.255.0)

    Gateway:         192.168.1.1


    DNS:             192.168.1.1


&#12288;

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


&#12288;

&#12288;

***** NetworkManager.state *****


[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true

WimaxEnabled=true


***** NetworkManager.conf *****


&#12288;

[main]

plugins=ifupdown,keyfile

dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]

managed=false


***** interfaces *****


auto lo

iface lo inet loopback


&#12288;

***** iwlist *****


&#12288;

***** resolv.conf *****


nameserver 127.0.0.1


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


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko

license:        GPL

author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>

version:        in-tree:

description:    Intel(R) Wireless WiFi Link AGN driver for Linux

srcversion:     8FAC5D54523380931B0EE42

depends:        iwlwifi,mac80211,cfg80211

intree:         Y

vermagic:       3.8.0-29-generic SMP mod_unload modversions 


filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko

license:        GPL

author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>

version:        in-tree:

description:    Intel(R) Wireless WiFi driver for Linux

firmware:       iwlwifi-100-5.ucode

firmware:       iwlwifi-1000-5.ucode

firmware:       iwlwifi-135-6.ucode

firmware:       iwlwifi-105-6.ucode

firmware:       iwlwifi-2030-6.ucode

firmware:       iwlwifi-2000-6.ucode

firmware:       iwlwifi-5150-2.ucode

firmware:       iwlwifi-5000-5.ucode

firmware:       iwlwifi-6000g2b-6.ucode

firmware:       iwlwifi-6000g2a-5.ucode

firmware:       iwlwifi-6050-5.ucode

firmware:       iwlwifi-6000-4.ucode

firmware:       iwlwifi-3160-6.ucode

firmware:       iwlwifi-7260-6.ucode

srcversion:     010E5CFF9BB5A6F9A4CC4EC

alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*

alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*

alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*

alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*

alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*

alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*

alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*

alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*

alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*

alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*

alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*

alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*

alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*

alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*

alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*

alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*

alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*

alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*

alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*

alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*

alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*

alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*

alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*

alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*

alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*

alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*

alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*

alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*

alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*

alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*

alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*

alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*

alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*

alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*

alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*

alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*

alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*

alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*

alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*

alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*

alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*

alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*

alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*

alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*

alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*

alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*

alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*

alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*

alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*

alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*

alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*

alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*

alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*

alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*

alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*

alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*

alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*

alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*

alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*

alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*

alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*

alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*

alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*

alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*

alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*

alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*

alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*

alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*

alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*

alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*

alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*

alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*

alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*

alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*

alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*

alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*

alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*

alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*

alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*

alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*

alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*

alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*

alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*

alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*

alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*

alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*

alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*

alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*

alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*

alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*

alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*

alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*

depends:        cfg80211

intree:         Y

vermagic:       3.8.0-29-generic SMP mod_unload modversions 

parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)

parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)

parm:           amsdu_size_8K:enable 8K amsdu size (int)

parm:           fw_restart:restart firmware in case of error (int)

parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)

parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)

parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)

parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)

parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)

parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)

parm:           power_save:enable WiFi power management (default: disable) (bool)

parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)

parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)


&#12288;

***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (iwlwifi)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    8.054249] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X

[    8.214068] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1

[    8.269312] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)

[    8.699349] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled

[    8.699350] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled

[    8.699351] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled

[    8.699352] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled

[    8.699353] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled

[    8.699355] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8

[    8.699456] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[    8.785663] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

[   12.863708] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[   12.871098] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0

[   13.238962] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[   13.246351] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0

[   13.446883] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   13.447094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   16.060909] wlan0: authenticate with <MAC address removed>

[   16.069307] wlan0: send auth to <MAC address removed> (try 1/3)

[   16.071140] wlan0: authenticated

[   16.075151] wlan0: associate with <MAC address removed> (try 1/3)

[   16.077865] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)

[   16.079893] wlan0: associated

[   16.079913] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[   51.005969] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues

[   53.007428] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[   53.007433] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 163

[   53.007437] wlan0: failed to remove key (0, <MAC address removed>) from hardware (-110)

[   55.008782] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.

[   55.008786] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 164

[   55.008788] iwlwifi 0000:02:00.0: Failed to update QoS

[   57.006220] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[   57.006237] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 165

[   57.006240] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[   59.007670] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[   59.007675] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 166

[   59.007679] wlan0: failed to remove key (2, <MAC address removed>) from hardware (-110)

[   61.005069] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[   61.005083] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 167

[   61.005086] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[   63.010470] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues

[   65.007900] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.

[   65.007905] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 168

[   65.007908] iwlwifi 0000:02:00.0: set power fail, ret = -110

[   67.005318] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[   67.005323] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 169

[   67.005325] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[   69.002661] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   69.002665] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 170

[   71.998840] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   71.998845] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 171

[   74.994943] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   74.994955] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 172

[   76.992408] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   76.992421] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 173

[   78.989800] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   78.989818] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 174

[   81.985941] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   81.985950] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 175

[   84.981985] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   84.981990] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 176

[   84.982028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   87.978119] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   87.978124] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 177

[   90.974227] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   90.974232] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 178

[   93.970419] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   93.970433] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 179

[   96.966501] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   96.966510] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 181

[   99.962629] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[   99.962647] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 182

[  102.958748] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  102.958752] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 183

[  105.954843] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  105.954847] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 184

[  108.950993] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  108.950998] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 185

[  111.947091] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  111.947096] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 186

[  114.943273] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  114.943283] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 187

[  117.939376] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  117.939382] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 188

[  120.935461] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  120.935466] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 189

[  123.931653] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  123.931663] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 190

[  126.927708] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  126.927714] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 161 write_ptr 191

[  127.147633] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.

[  127.148373] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  127.148383] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  127.148387] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  127.148391] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  127.175458] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  127.175490] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  129.117289] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.

[  129.169904] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[  129.177414] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0

[  129.372623] WARNING: at /build/buildd/linux-lts-raring-3.8.0/drivers/net/wireless/iwlwifi/pcie/tx.c:1281 iwl_pcie_enqueue_hcmd+0x824/0x940 [iwlwifi]()

[  129.372626] Modules linked in: bnep(F) rfcomm(F) parport_pc(F) ppdev(F) snd_hda_codec_hdmi(F) snd_hda_codec_conexant(F) coretemp(F) arc4(F) kvm_intel(F) kvm(F) iwldvm(F) snd_hda_intel(F) snd_hda_codec(F) mac80211(F) joydev(F) ghash_clmulni_intel(F) snd_hwdep(F) uvcvideo(F) snd_pcm(F) aesni_intel(F) ablk_helper(F) snd_seq_midi(F) i915(F) cryptd(F) snd_rawmidi(F) lrw(F) snd_seq_midi_event(F) aes_x86_64(F) snd_seq(F) videobuf2_core(F) iwlwifi(F) snd_timer(F) rts5139(FC) videodev(F) xts(F) snd_seq_device(F) gf128mul(F) drm_kms_helper(F) videobuf2_vmalloc(F) drm(F) videobuf2_memops(F) snd(F) btusb(F) cfg80211(F) soundcore(F) snd_page_alloc(F) bluetooth(F) psmouse(F) i2c_algo_bit(F) mei(F) lpc_ich(F) microcode(F) dell_laptop(F) mac_hid(F) dell_wmi(F) serio_raw(F) dcdbas(F) sparse_keymap(F) wmi(F) video(F) lp(F) parport(F) hid_generic(F) usbhid(F) hid(F) usb_storage(F) r8169(F) ahci(F) libahci(F)

[  129.372689]  [<ffffffffa02e7044>] iwl_pcie_enqueue_hcmd+0x824/0x940 [iwlwifi]

[  129.372702]  [<ffffffffa02f0010>] ? perf_trace_iwlwifi_dev_ucode_wrap_event+0x140/0x1b0 [iwlwifi]

[  129.372709]  [<ffffffffa02e72f4>] iwl_pcie_send_hcmd_sync+0xd4/0x4d0 [iwlwifi]

[  129.372720]  [<ffffffffa02e89a3>] iwl_trans_pcie_send_hcmd+0x33/0x50 [iwlwifi]

[  129.372728]  [<ffffffffa0561133>] iwl_dvm_send_cmd+0x63/0x180 [iwldvm]

[  129.372734]  [<ffffffffa0562e97>] iwl_send_calib_results+0x77/0xb0 [iwldvm]

[  129.372740]  [<ffffffffa055cef1>] iwl_alive_notify+0x161/0x1f0 [iwldvm]

[  129.372746]  [<ffffffffa055d752>] iwl_load_ucode_wait_alive+0x182/0x210 [iwldvm]

[  129.372752]  [<ffffffffa055cbd0>] ? iwl_alloc_all+0x30/0x30 [iwldvm]

[  129.372757]  [<ffffffffa055bc8a>] __iwl_up+0xea/0x140 [iwldvm]

[  129.372762]  [<ffffffffa055bd39>] iwlagn_mac_start+0x59/0xf0 [iwldvm]

[  129.385617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  131.636929] wlan0: authenticate with <MAC address removed>

[  131.644712] wlan0: send auth to <MAC address removed> (try 1/3)

[  131.649612] wlan0: authenticated

[  131.653642] wlan0: associate with <MAC address removed> (try 1/3)

[  131.656391] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)

[  131.659005] wlan0: associated

[  131.659052] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[  157.796311] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.

[  157.796401] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

[  157.796433] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.796436] wlan0: failed to remove key (0, <MAC address removed>) from hardware (-5)

[  157.797068] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797076] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797078] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797080] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797082] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797084] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797086] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797088] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797090] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797092] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797094] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797095] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797097] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797099] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797101] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797103] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797104] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797106] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797108] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797110] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797112] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797114] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797116] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797118] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797120] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.797122] iwlwifi 0000:02:00.0: Tx flush command to flush out all frames

[  157.803912] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.803918] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.803926] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.803929] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.803947] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.803950] wlan0: failed to remove key (2, <MAC address removed>) from hardware (-5)

[  157.811956] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  157.811988] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  158.248907] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  160.634381] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.

[  160.644844] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[  160.652367] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0

[  160.867204] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  163.078059] wlan0: authenticate with <MAC address removed>

[  163.086546] wlan0: send auth to <MAC address removed> (try 1/3)

[  163.088607] wlan0: authenticated

[  163.088796] wlan0: associate with <MAC address removed> (try 1/3)

[  163.091546] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)

[  163.093331] wlan0: associated

[  163.093372] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[  197.789081] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues

[  199.790488] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[  199.790506] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 141 write_ptr 143

[  199.790512] wlan0: failed to remove key (0, <MAC address removed>) from hardware (-110)

[  201.791886] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.

[  201.791906] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 141 write_ptr 144

[  201.791911] iwlwifi 0000:02:00.0: Failed to update QoS

[  203.789332] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[  203.789336] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 141 write_ptr 145

[  203.789349] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[  205.790678] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[  205.790684] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 141 write_ptr 146

[  205.790688] wlan0: failed to remove key (2, <MAC address removed>) from hardware (-110)

[  207.664310] iwlwifi 0000:02:00.0: ACTIVATE a non DRIVER active station id 0 addr <MAC address removed>

[  207.664326] iwlwifi 0000:02:00.0: HCMD_ACTIVE already clear for command REPLY_QOS_PARAM

[  207.665110] iwlwifi 0000:02:00.0: Attempting to modify non-existing station 0

[  207.665122] iwlwifi 0000:02:00.0: HCMD_ACTIVE already clear for command REPLY_ADD_STA

[  207.665131] iwlwifi 0000:02:00.0: Error: Response NULL in 'REPLY_ADD_STA'

[  207.665136] iwlwifi 0000:02:00.0: Adding station <MAC address removed> failed.

[  207.665305] iwlwifi 0000:02:00.0: HCMD_ACTIVE already clear for command REPLY_RXON

[  207.665542] iwlwifi 0000:02:00.0: ACTIVATE a non DRIVER active station id 15 addr <MAC address removed>

[  207.665551] iwlwifi 0000:02:00.0: HCMD_ACTIVE already clear for command REPLY_ADD_STA

[  208.261516] wlan0: authenticate with <MAC address removed>

[  208.264327] wlan0: send auth to <MAC address removed> (try 1/3)

[  208.467222] wlan0: send auth to <MAC address removed> (try 2/3)

[  208.670985] wlan0: send auth to <MAC address removed> (try 3/3)

[  208.874731] wlan0: authentication with <MAC address removed> timed out

[  214.280551] wlan0: authenticate with <MAC address removed>

[  214.283465] wlan0: direct probe to <MAC address removed> (try 1/3)

[  214.483434] wlan0: direct probe to <MAC address removed> (try 2/3)

[  214.687213] wlan0: direct probe to <MAC address removed> (try 3/3)

[  214.890915] wlan0: authentication with <MAC address removed> timed out

[  222.341672] wlan0: authenticate with <MAC address removed>

[  222.344545] wlan0: direct probe to <MAC address removed> (try 1/3)

[  222.545000] wlan0: direct probe to <MAC address removed> (try 2/3)

[  222.748739] wlan0: direct probe to <MAC address removed> (try 3/3)

[  222.952484] wlan0: authentication with <MAC address removed> timed out

[  235.779816] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.

[  235.787878] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  235.787917] iwlwifi 0000:02:00.0: Not sending command - RF KILL

[  236.118940] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  238.563325] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.

[  238.582343] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S

[  238.589814] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0

[  238.816326] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  241.036228] wlan0: authenticate with <MAC address removed>

[  241.046060] wlan0: send auth to <MAC address removed> (try 1/3)

[  241.048833] wlan0: authenticated

[  241.049123] wlan0: associate with <MAC address removed> (try 1/3)

[  241.051963] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)

[  241.054301] wlan0: associated

[  241.054349] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[  275.670254] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues

[  277.671649] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[  277.671657] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 129

[  277.671665] wlan0: failed to remove key (0, <MAC address removed>) from hardware (-110)

[  279.673073] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.

[  279.673090] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 130

[  279.673098] iwlwifi 0000:02:00.0: Failed to update QoS

[  281.670463] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[  281.670471] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 131

[  281.670476] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[  283.671900] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.

[  283.671905] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 132

[  283.671909] wlan0: failed to remove key (2, <MAC address removed>) from hardware (-110)

[  285.669322] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[  285.669331] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 133

[  285.669336] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[  287.674691] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues

[  289.672053] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.

[  289.672058] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 134

[  289.672061] iwlwifi 0000:02:00.0: set power fail, ret = -110

[  291.669523] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.

[  291.669535] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 135

[  291.669541] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)

[  293.666903] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  293.666912] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 136

[  296.663098] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  296.663107] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 137

[  299.659197] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  299.659206] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 138

[  301.656634] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.

[  301.656643] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 127 write_ptr 139


****************** done ******************


&#12288;

```

thanks both of you for trying to help me :)

---

### Post by varunendra on 2014-01-26
```

  Wireless Access Points 

    UNIT-00:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2

    IL'Dormitory-A16-17-4: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2

    IL'Dormitory A16-17 Lt.2: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

    Medang_Hotspot:  Infra, <MAC address removed>, Freq 2427 MHz, Rate 9 Mb/s, Strength 24 WPA WPA2

    SUPER BEJO AP2:  Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WEP

    PT. dwi global sentosa: Infra, <MAC address removed>, Freq 2412 MHz, Rate 48 Mb/s, Strength 22 WEP

    IL'Dormnitory A16-17 3: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
```
Is your wireless access point one of those that are using WPA/WPA2 mixed mode? It is strongly recommended to use WPA2-PSK (AES) only. Avoid TKIP or WPA/WPA2 mixed mode as it is inefficient and often causes troubles for Linux drivers.

At the driver level, please try this for now -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi swcrypto=1 bt_coex_active=N
sudo modprobe -v iwldvm
```
This will be a temporary change, and will be lost at next boot. If it helps, it can be made permanent. If it doesn't help, try another parameter -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwlwifi swcrypto=1 bt_coex_active=N 11n_disable=1
sudo modprobe -v iwldvm
```

One more thing - Does your router/access-point support N-channel? Is it enabled? If yes, you may try disabling it (setting it to b/g mode only) to see if it helps. This is obviously a big compromise with speeds and is not guaranteed to help, so keep it as the last option to try with the current driver.

If none of these helps, try the last three modprobe commands, then post back the output of -
```
dmesg | grep iwlwifi
```

---

### Post by Jegul on 2014-01-27
well, one moment just now, the wifi was stable,
but after i restarted, the wifi keeps disconnecting again,
so i use the
```
dmesg | grep iwlwifi
```
command and got this result
```
[    9.838624] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X[   10.139451] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[   10.692211] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.692212] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.692213] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.692214] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.692215] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.692218] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   10.692321] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.910805] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.918224] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   15.285476] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   15.292889] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   52.988643] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   54.990075] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[   54.990097] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 200
[   56.991480] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.
[   56.991488] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 201
[   56.991493] iwlwifi 0000:02:00.0: Failed to update QoS
[   58.988878] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[   58.988886] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 202
[   58.988891] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[   60.990315] iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[   60.990331] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 203
[   62.987762] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[   62.987766] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 204
[   62.987769] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[   64.993113] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   66.990537] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.
[   66.990546] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 205
[   66.990559] iwlwifi 0000:02:00.0: set power fail, ret = -110
[   68.988001] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[   68.988005] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 206
[   68.988008] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[   70.985346] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   70.985350] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 207
[   73.981511] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   73.981515] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 208
[   76.977609] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   76.977623] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 209
[   78.975064] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   78.975087] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 210
[   80.972478] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   80.972487] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 211
[   83.968562] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   83.968568] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 212
[   86.964685] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   86.964689] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 213
[   89.960878] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   89.960888] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 214
[   92.957001] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   92.957010] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 215
[   95.953042] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   95.953051] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 216
[   98.949173] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[   98.949184] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 218
[  101.945309] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  101.945315] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 219
[  104.941408] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  104.941413] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 220
[  107.937586] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  107.937590] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 221
[  110.933738] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  110.933747] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 222
[  113.929794] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  113.929802] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 223
[  116.925907] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  116.925916] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 224
[  119.286930] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  119.286939] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 198 write_ptr 227
[  119.286944] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  124.540584] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[  124.541490] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[  124.551781] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  124.551788] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  124.551791] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  124.551794] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[  124.551797] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[  124.551800] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[  124.551924] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  124.575812] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  124.583287] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[  124.960103] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  124.967547] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[  162.859408] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  164.860824] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.
[  164.860834] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 120
[  164.860839] iwlwifi 0000:02:00.0: Failed to update QoS
[  166.858229] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  166.858243] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 121
[  166.858257] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  168.859588] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  168.859599] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 122
[  168.859606] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  170.865058] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  172.862484] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.
[  172.862494] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 123
[  172.862499] iwlwifi 0000:02:00.0: set power fail, ret = -110
[  174.859832] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  174.859844] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 124
[  174.859851] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  176.857284] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  176.857292] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 125
[  179.853418] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  179.853426] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 126
[  182.849479] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  182.849484] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 127
[  185.845612] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  185.845623] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 128
[  188.841740] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  188.841751] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 129
[  191.837879] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  191.837897] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 130
[  194.834055] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  194.834064] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 131
[  197.830137] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  197.830143] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 132
[  200.826262] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  200.826271] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 133
[  203.822363] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  203.822374] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 134
[  206.818473] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  206.818484] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 135
[  209.814630] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  209.814640] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 137
[  212.810788] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  212.810797] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 138
[  215.806900] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  215.806910] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 139
[  218.803007] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  218.803016] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 142
[  220.812354] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  220.812366] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 118 write_ptr 143
[  220.812374] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  239.693929] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[  239.694585] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[  239.706339] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  239.706348] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  239.706353] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  239.706357] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[  239.706362] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[  239.706367] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[  239.706500] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  239.736158] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  239.743646] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[  240.120343] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  240.127835] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[  277.685156] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  279.686575] iwlwifi 0000:02:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.
[  279.686580] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 124
[  279.686582] iwlwifi 0000:02:00.0: Failed to update QoS
[  281.684031] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  281.684040] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 125
[  281.684045] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  283.685381] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  283.685389] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 126
[  283.685394] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  285.690797] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  287.688255] iwlwifi 0000:02:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.
[  287.688271] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 127
[  287.688284] iwlwifi 0000:02:00.0: set power fail, ret = -110
[  289.685677] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  289.685687] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 128
[  289.685692] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  291.683065] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  291.683074] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 129
[  294.679188] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  294.679197] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 130
[  297.675261] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  297.675267] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 131
[  300.671479] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  300.671488] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 132
[  303.667550] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  303.667561] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 133
[  306.663689] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  306.663699] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 134
[  309.659839] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  309.659849] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 135
[  312.655950] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  312.655960] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 136
[  315.652053] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  315.652062] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 137
[  318.648163] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  318.648168] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 138
[  321.644297] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  321.644313] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 139
[  324.640458] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  324.640468] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 141
[  327.636580] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  327.636590] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 142
[  330.632698] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
[  330.632708] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 143
[  332.825867] iwlwifi 0000:02:00.0: Error sending REPLY_RXON: time out after 2000ms.
[  332.825876] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 122 write_ptr 146
[  332.825881] iwlwifi 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-110)
[  339.866542] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[  339.866989] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[  339.877449] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  339.877464] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  339.877467] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  339.877470] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[  339.877473] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[  339.877477] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[  339.877599] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  339.901750] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  339.909227] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[  340.284987] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  340.292460] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0



```

---

### Post by varunendra on 2014-01-27
> **Jegul said:**
> well, one moment just now, the wifi was stable,
but after i restarted, the wifi keeps disconnecting again

..was stable.. while the suggested modprobe parameters were applied or by itself?

Since the parameters were temporary, the changes will be lost at each new boot, as I mentioned already in my original post. If they seem to help, can be made permanent.

---

### Post by Jegul on 2014-01-27
well, the wifi was stable when i haven't use that parameter;
and when the wifi back to its disconnecting habit, i tried that parameter, and it kept disconnecting;
and what i saw from my router, the wifi connection uses "WPA 2-Personal AES"
sorry, it's my bad for the lack of info :(

---

### Post by varunendra on 2014-01-27
Posting in a hurry, not sure I'll get time today to follow up or not.

Please check under "QoS" settings in your router and make sure a feature called "WMM Support" (if it is or something similar with term "WMM" is there) is disabled. A couple of users reported a few days ago that it was causing this kind of problems.

If that is not applicable to your router, or doesn't help (make sure to restart both router and laptop to make sure the changes properly take effect), try compiling a newer driver -

First, make sure the basic requirements are installed beforehand (do this while being connected to internet via cable or while the wireless itself is connected, won't take long)-
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Then,

[INDENT]**1)** Download the backport package 3.12.8-1 from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Copy the downloaded package to your Desktop > Right-Click > Extract here

**3)** Open a terminal (Ctrl-Alt-T) and run the following commands to compile and install the driver -
```
cd Desktop/backports-3.12.8-1
make defconfig-iwlwifi
make
sudo make install
```
Keep an eye on the outputs in the terminal and post back if any of them fail with any errors. Should install smoothly though.

**4)** If installed successfully, reboot your laptop and retry to connect.[/INDENT]

Any better? If not, you may try the same process (1 to 4) with the latest backports package, although I doubt in that case the problem lies elsewhere.

Please post back a fresh report of the wireless_script if the above suggestions don't bring any joy to us.

---

### Post by Jegul on 2014-01-30
sorry for the late reply,
I've tried for a couple of days now, and the wireless seems to work fine now.
but I should choose "Previous Linux Version" than choose the ubuntu for the wireless to work fine.
If I choose the ubuntu without choose "Previous Linux Version" first, then the wireless keeps disconnecting;
Well, i don't know why, but i think my problem has been solved.
Thanks a lot for helping me.
Really appreciate it :)

---


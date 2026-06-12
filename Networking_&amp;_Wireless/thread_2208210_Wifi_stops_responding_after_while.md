---
title: "Wifi stops responding after while"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by Radek_Johanna on 2014-02-27
Hello,

I would like to ask you for help with my wifi connection. My problem looks like this:
- After I turn on my laptop or after reboot everything works fine. But after suspend my wifi works about 6 minutes and then stops responding. It looks like it`s connected but it doesn`t responde. It is happening in all networks. After I turn on/off wifi, it works next 6 minutes. After reboot all fine until the next suspend.

I`m on Ubuntu 13.10 and my HW is Dell Vostro 5470 with SSD. Wireless card is Intel 7260.

I have already tried to:

Turn off power management by adding this:
sleep 10
/sbin/iwconfig wlan0 power off
exit 0
into /etc/pm/power.d

Forbit wireless to sleep by adding this:
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
;;
*)
;;
esac
exit $?
into /etc/pm/sleep.d

and by adding this:

HOOK_BLACKLIST="wireless"
HOOK_BLACKLIST="$HOOK_BLACKLIST wireless"
into /etc/pm/config.d

Here are results of iwconfig:
vmnet8    no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Tomca"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 
          Bit Rate=1 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

vmnet1    no wireless extensions.

and from sudo lshw -C network:
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 73
       serial: fc:f8:ae:21:a2:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-15-generic firmware=22.0.7.0 ip=192.168.1.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:62 memory:f1c00000-f1c01fff

I`m gessig thaht something is suspending my wireless card, because it is quite regullar. Thanks for any advice, Radek.

---

### Post by varunendra on 2014-02-27
Welcome to Ubuntu Forums Radek !! :)

> **Radek_Johanna said:**
> 
I have already tried to:

Turn off power management by adding this:
....
Forbit wireless to sleep by adding this:
.....
and by adding this:
....
....
Here are results of iwconfig:
```
wlan0     IEEE 802.11bg  ESSID:"Tomca"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 
          Bit Rate=1 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
         ** Power Management:[COLOR="#006400"]off[/COLOR]**
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0
```
Congratulations!! You have finally, successfully turned to Power Management off ! (I had started looking for _that_ step when you would have handed a Gun to a script to point at the wireless card, whenever it tries to Sleep :P)

Anyway, clearly you still have the problem. So why not figure out which of the changes above did the trick, and revert the rest?

Apart from doing that, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags, just like I added to the quoted part of your original post. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Radek_Johanna on 2014-02-27
Hi, here is output of your program. Nice SW, by the way.

```


*************** info trace ***************

***** uname -a *****

Linux padouchuss-Vostro-5470 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Dell Device [1028:0616]
    Kernel driver in use: r8169
08:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:4462]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 0c45:6500 Microdia 
Bus 002 Device 002: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 002 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"ExPS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:182   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
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

Sm&#283;rovací tabulka v jádru pro IP
Adresát         Brána           Maska           P&#345;ízn Metrik Odkaz  Užt Rozhraní
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
172.16.142.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.59.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1

***** lsmod *****

iwlmvm                161339  0 
mac80211              597268  1 iwlmvm
iwlwifi               165636  1 iwlmvm
cfg80211              480503  3 iwlwifi,mac80211,iwlmvm

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ExPS] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    kotel:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 2 Mb/s, Strength 37
    *ExPS:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    PAVEL-PC_Network:Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 49 WPA2

  IPv4 Settings:
    Address:         192.168.1.124
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             82.150.185.1


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
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ExPS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000769b9fd6c9
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000445785053
                    IE: Unknown: 01088C9298A4B0C8E0EC
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"kotel"
                    Bit Rates:1 Mb/s; 2 Mb/s
                    Mode:Master
                    Extra:tsf=0000002493597da9
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 00056B6F74656C
                    IE: Unknown: 01028204
                    IE: Unknown: 030101
                    IE: Unknown: 050401020000
                    IE: Unknown: 851C08004C0D5700FF03010041502D50616E656C616B3135333900AC2B00


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

[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325

***** modinfo *****

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     0916A821F768F66B7252B54
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     90DCEBFC3CB64C8138032A1
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
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
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
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
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
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
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


***** udev rules *****

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.027359] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    2.134635] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    2.549267] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.549356] iwlwifi 0000:08:00.0: irq 61 for MSI/MSI-X
[    2.553395] iwlwifi 0000:08:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[    2.589367] iwlwifi 0000:08:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    2.589438] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    2.589587] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    2.815032] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.312726] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x361f05)
[    4.777793] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    4.777952] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[    4.795293] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.795570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.313969] wlan0: authenticate with <MAC address removed>
[    6.314713] wlan0: send auth to <MAC address removed> (try 1/3)
[    6.316140] wlan0: authenticated
[    6.316275] iwlwifi 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[    6.316279] iwlwifi 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[    6.316911] wlan0: associate with <MAC address removed> (try 1/3)
[    6.324466] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[    6.325181] wlan0: associated
[    6.325212] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.337165] bridge-wlan0: device is wireless, enabling SMAC
[    6.337168] bridge-wlan0: up
[    6.337782] bridge-wlan0: attached

****************** done ******************



```

---

### Post by varunendra on 2014-02-27
> **Radek_Johanna said:**
> Nice SW, by the way.
Yup, thanks to Wild Man and others who created and helped it. I am not one of those. :P

Anyway, looks like all your tricks failed -
```

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:"ExPS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:182   Missed beacon:0
```
How come? Did you revert ALL the scripts/modifications or is it turned on WITH all of them working? Do we really need a gunner to threaten it to stay awake?

For now, please try a parameter with the iwlmvm driver -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlmvm power_scheme=1
```

And if that doesn't help, please post back the outputs of (while the above parameter is applied) -
```
grep [[:alnum:]] /sys/module/iwl*/parameters/*
ls -l /etc/pm/power.d
ls -l /etc/pm/sleep.d
ls -l /etc/pm/config.d
```
If there are multiple custom (non-default) files in these locations, please also mention which ones are the ones you created and for what.

---

### Post by Radek_Johanna on 2014-02-27
Just when I wanted to post that it works is stopped working. Murphy`s lawworks, thats for sure. So, I deleted all files I created before, runed code you posted and reboot. Wifi kept working for few hours and than stopped in the same way as before. Here are outputs of commands you posted:

ls -l /etc/pm/power.d :
```

celkem 0

```

ls -l /etc/pm/sleep.d:
```

celkem 20
-rwxr-xr-x 1 root root 1260 kv&#283; 23  2012 novatel_3g_suspend
-rwxr-xr-x 1 root root   81 úno 20 10:31 wakenet.sh
-rwxr-xr-x 1 root root   81 úno 20 10:31 wakenet.sh~
-rwxr-xr-x 1 root root  210 &#345;íj 10 19:48 10_grub-common
-rwxr-xr-x 1 root root  581 zá&#345;  9 17:34 10_unattended-upgrades-hibernate

```

ls -l /etc/pm/config.d
```

celkem 0

```

grep [[:alnum:]] /sys/module/iwl*/parameters/*
```

/sys/module/iwlmvm/parameters/init_dbg:N
/sys/module/iwlmvm/parameters/power_scheme:2
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/11n_disable:1

```

As you probably figured out, celkem means total in english.
No more undefault files should be in these folders any more.
Thanks, Radek.

---

### Post by varunendra on 2014-02-27
Did you say it "kept working for a few hours"? Can we consider this as an improvement?

And..
> **Radek_Johanna said:**
> No more undefault files should be in these folders any more.
Looks like at least there is one (plus its automatic backup) -
> **Radek_Johanna said:**
> ls -l /etc/pm/sleep.d:
```

celkem 20
-rwxr-xr-x 1 root root 1260 kv&#283; 23  2012 novatel_3g_suspend
[B][COLOR="#FF0000"]-rwxr-xr-x 1 root root   81 úno 20 10:31 wakenet.sh
-rwxr-xr-x 1 root root   81 úno 20 10:31 wakenet.sh~[/COLOR][/B]
-rwxr-xr-x 1 root root  210 &#345;íj 10 19:48 10_grub-common
-rwxr-xr-x 1 root root  581 zá&#345;  9 17:34 10_unattended-upgrades-hibernate

```
Please move/delete these ones too.

Not saying that any of those files are/were creating problems, but it is best to work with defaults, especially when I know that this card works nicely on the kernel version you have.

Obviously, the parameters are back to defaults again, after a reboot -
> **Radek_Johanna said:**
> 
grep [[:alnum:]] /sys/module/iwl*/parameters/*
```

/sys/module/iwlmvm/parameters/init_dbg:N
/sys/module/iwlmvm/parameters/**power_scheme:[COLOR="#FF0000"]2[/COLOR]**
/sys/module/iwlwifi/parameters/amsdu_size_8K:0
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/fw_restart:Y
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/nvm_file:(null)
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/swcrypto:0
/sys/module/iwlwifi/parameters/wd_disable:1
/sys/module/iwlwifi/parameters/11n_disable:1

```
So AFTER removing those custom files from the /etc/pm/sleep.d directory, please restart the networking ("sudo service networking restart", or simply reboot) and reload the module iwlmvm with the same parameter again -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlmvm power_scheme=1
```

If this doesn't help, or doesn't help 'As nicely as you wish', try a few other parameters as well that are applicable to the iwlwifi driver -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlwifi **[COLOR="#800000"]bt_coex_active=N[/COLOR]** **[COLOR="#0000CD"]swcrypto=1[/COLOR]**
sudo modprobe -v iwlmvm **power_scheme=1**
```
(looks like you have already set the "11n_disable=1" parameter permanently ;))

Like before, these will be temporary changes, and will be reset to defaults on next boot, or when you reload the drivers without parameters.

And just because we are as stubborn as the Power Management on your card (and too optimistic), additionally try to turn it off once more -
```
sudo iwconfig wlan0 power off
```
Test the connection and see if it's any more stable now. If it is, we can pin point the change(s) that is/are helping, and make them permanent.

---

### Post by Radek_Johanna on 2014-02-28
Yes, you was right, I forgot to delete the last file. So I deleted it, thant rebooted, than used commands you posted. Now I`m testing and I will report you my progress in the evening (my evening, I have 7a.m. now). Yesterday I made mistake that I used commands and then reboot. So defaut state and the same problem. Thank you very much for advices. Radek.

---

### Post by Radek_Johanna on 2014-02-28
Applied all commands you posted, tested for 10 hours and all seems to be  working! So if I might please you to tell me the secret how to make  this changes permanent, I would be very graceful. Thank you, Radek.

---

### Post by varunendra on 2014-02-28
I thought you already knew the secret, since the "11n_disable=1" option seems to be already applied permanently. But probably you applied it following some post without understanding what it actually did and/or how. :)

So here's the long awaited Secret! :D

You simply create a .conf file in your /etc/modprobe.d directory, and put a line in it whose syntax should be exactly this -
```
options [driver's name] [parameter 1] [parameter2] .... [last parameter]
```

The name of the file doesn't matter, but its extension name should always be ".conf". Currently even that is not mandatory but in future releases it will be. And just for consistency, we always prefer to name the file same as the driver which it is for.

Now considering the above rules/conventions, here are the exact lines that can be placed in two .conf files to make the parameters permanent -
```
options iwlmvm **power_scheme=1**
options iwlwifi **bt_coex_active=N [COLOR="#0000CD"]swcrypto=1[/COLOR] [COLOR="#800000"]11n_disable=1[/COLOR]**
```

You can simply use your text editor to create two new files (or edit existing one, as there seems to be one), but make sure to open the text editor with root access (e.g. "gksu gedit <file name>") to be able to write/edit file in **/etc/modprobe.d** directory.

We prefer the command line instead of GUI text editor, since commands are quick and universal. So here's my preferred way -
```
echo "options iwlmvm **power_scheme=1**" | sudo tee /etc/modprobe.d/iwlmvm.conf
echo "options iwlwifi **bt_coex_active=N [COLOR="#0000CD"]swcrypto=1[/COLOR] [COLOR="#800000"]11n_disable=1[/COLOR]**" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

From your previous outputs, it seems you already have a file, most probably named "**iwlwifi.conf**", in you /etc/modprobe.d directory to enforce the 11n_disable parameter. If its name is indeed "iwlwifi.conf", it will be overwritten with the second command above which is perfectly okay. If it has a different name, you should manually delete it or use the same name in the second command above to overwrite it.


That being explained, I would strongly recommend (not necessary though, as long as everything is working nicely) to experiment with individual parameters and not use all of them at once. This will help determining which one(s) is/are helping and make only those permanent.

My personal understanding/assumption/interpretation of what each one we used does, to help you decide whether or not to do the experiments -

**power_scheme=[COLOR="#0000CD"]1[/COLOR] :** Applicable to the "iwlmvm" driver; sets the power management scheme to "1", which is for "active" scheme as per its modinfo. The other two possible values are 2 (balanced) and 3 (low power). 2 was the default, we changed it to 1 (active).

**bt_coex_active=[COLOR="#0000CD"]N[/COLOR] :** Applicable to the "iwlwifi" driver; disables a 'Feature' that allows co-existence of bluetooth and wifi signals. The bluetooth signals operate within the same frequency range as wifi (2.4 GHz), and so may cause mutual interference when both are used simultaneously. This technology (bt-coexistence) modifies the transmission/reception of wifi in such a way that is supposed to avoid this kind of interference. Unfortunately, it doesn't always work as expected and sometimes causes more trouble than helping anything. In such cases, turning it off with above parameter helps.

**swcrypto=[COLOR="#0000CD"]1[/COLOR] :** Applicable to the "iwlwifi" driver; shifts the task of packet encryption from hardware (wireless chip) to software (driver/OS). Helps when the hardware encryption can't keep up with the packet encryption for some reason (too fast traffic, inefficient encryption algorithm etc.).

**11n_disable=[COLOR="#0000CD"]1[/COLOR] :** Applicable to the "iwlwifi" driver; disables N-channel, which means trading speed for stability by limiting yourself to g-speeds (54 Mbps max).

**[SIZE=3]You can check the available parameters[/SIZE] with any driver by using the "[COLOR="#0000CD"]modinfo[/COLOR]" command. For example, *"[COLOR="#B22222"]modinfo iwlwifi[/COLOR]"*.**

To see ONLY the available parameters, not the other details : "modinfo -p iwlwifi" (btw, it loses formatting too, so the above one is better)

If you do the experiments, please let us know which one(s) help and which ones don't. Happy tweaking ! :)

---

### Post by Radek_Johanna on 2014-03-01
Thank you very much. I`m new in linux, so I usually mess something up or copy/paste something without 100% understanding. But I`m doing my best. So thank you one again for advices and explanation. You saved my wifi man.

---

### Post by varunendra on 2014-03-01
You're always welcome!

If it keeps working satisfactorily, please mark the thread as [SOLVED] using the "Thread Tools" link above the top post (or follow the link in my signature to see with screenshots). It helps others by indicating that the thread contains a possible solution to the problem stated in the topic. :)

---

### Post by Roelof_Berg on 2015-01-16
Great solution. Unfortunately this slows down my WiFi to about 25 MBit, so my 100 MBit internet connection is throttled by factor four now. Is there any alternative to the given solution (disabling 'n') that doesn't decrease the WiFi speed ? Thanks in advance.

---

### Post by jeremy31 on 2015-01-16
> **Roelof_Berg said:**
> Great solution. Unfortunately this slows down my WiFi to about 25 MBit, so my 100 MBit internet connection is throttled by factor four now. Is there any alternative to the given solution (disabling 'n') that doesn't decrease the WiFi speed ? Thanks in advance.

OK, so edit the file ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` and change the option from 11n_disable=1 to ```
11n_disable=8
``` Save, exit program, reboot and it should get the speed back as the 11n_disable=8 doesn't disable 11n in any way, it actually enables agg tx

---

### Post by Noman_Khan on 2015-06-27
Hi
I am have the same issue with my Dell Inspiron 15. Need help.

```


########## wireless info START ##########

Report from: 27 Jun 2015 15:46 PKT +0500

Booted last: 27 Jun 2015 14:27 PKT +0500

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0bda:5756 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
cfg80211              494362  1 wl
wmi                    19193  2 dell_led,dell_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.188  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76e6:e2ff:fe45:baf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12343297 (12.3 MB)  TX bytes:786280 (786.2 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.15.1  Bcast:172.16.15.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.18.1  Bcast:172.16.18.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e33:7aff:fefa:bd4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30597 errors:0 dropped:0 overruns:0 frame:39480
          TX packets:35449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21531641 (21.5 MB)  TX bytes:4469973 (4.4 MB)
          Interrupt:18 

##### iwconfig ##########################

eth0      no wireless extensions.

vmnet1    no wireless extensions.

virbr0    no wireless extensions.

vmnet8    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"ImranNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ImranNet' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
172.16.15.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.18.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1666     1  0 14:27 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.188
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0  [ImranNet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PTCL-BB:         Infra, <MAC 'PTCL-BB' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    PTCL-BB:         Infra, <MAC 'PTCL-BB' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    *ImranNet:       Infra, <MAC 'ImranNet' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
    PTCL:            Infra, <MAC 'PTCL' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    witribe_wifi:    Infra, <MAC 'witribe_wifi' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ImranNet]] (600 root)
[connection] id=ImranNet | type=802-11-wireless
[802-11-wireless] ssid=ImranNet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/0F-ZH]] (600 root)
[connection] id=0F-ZH | type=802-11-wireless
[802-11-wireless] ssid=0F-ZH | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Karachi (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

vmnet1    no frequency information.

virbr0    no frequency information.

vmnet8    no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ImranNet' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"ImranNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'PTCL' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"PTCL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'PTCL-BB' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"PTCL-BB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'PTCL-BB' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"PTCL-BB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'witribe_wifi' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"witribe_wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '0622123468' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"0622123468"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-41-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2810.799837] bridge-wlan0: device is wireless, enabling SMAC
[ 2810.799839] bridge-wlan0: up
[ 2810.800341] bridge-wlan0: attached
[ 2810.801347] bridge-wlan0: disabling the bridge
[ 2810.817582] bridge-wlan0: down
[ 2810.817599] bridge-wlan0: detached
[ 2811.445180] bridge-wlan0: device is wireless, enabling SMAC
[ 2811.445182] bridge-wlan0: up
[ 2811.445185] bridge-wlan0: attached
[ 3851.782527] bridge-wlan0: disabling the bridge
[ 3851.782578] bridge-wlan0: down
[ 3851.782589] bridge-wlan0: detached
[ 3855.844472] bridge-wlan0: device is wireless, enabling SMAC
[ 3855.844474] bridge-wlan0: up
[ 3855.844478] bridge-wlan0: attached
[ 3855.844505] bridge-wlan0: disabling the bridge
[ 3855.861129] bridge-wlan0: down
[ 3855.861138] bridge-wlan0: detached
[ 3856.481124] bridge-wlan0: device is wireless, enabling SMAC
[ 3856.481126] bridge-wlan0: up
[ 3856.481130] bridge-wlan0: attached
[ 3978.746291] bridge-wlan0: disabling the bridge
[ 3978.762492] bridge-wlan0: down
[ 3978.762501] bridge-wlan0: detached
[ 4368.135009] bridge-wlan0: device is wireless, enabling SMAC
[ 4368.135011] bridge-wlan0: up
[ 4368.135015] bridge-wlan0: attached
[ 4369.699541] bridge-wlan0: disabling the bridge
[ 4369.704536] bridge-wlan0: down
[ 4369.704552] bridge-wlan0: detached
[ 4690.490163] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)

########## wireless info END ############



```

---


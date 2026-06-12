---
title: "wireless speed slow, and signal weak"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by silvan514 on 2014-02-08
Hi everybody,

I am a bit desperate. Can anybody help me with my network problem. Whenever I want to connect to a network, it does so, the signal strength jumps up only to drop as quickly as it had gone up and then stays very weak. Firefox turns gray very often and I have to wait until it's good again. This happens repeatedly. I have a Toshiba Satellite A70-C (intel processor) and Ubuntu 13.04.

Thanks in advance

Ps: I have read several threads, but nothing worked.

---

### Post by TheFu on 2014-02-09
Welcome to the forums! Hope we can help.

WiFi networking is fickle. As soon as you leave the same room (for normal room sizes), all bets are off. The data you've provided so far doesn't explain enough to provide any real help.  If this is an issue from 5 ft away, that is very different than if it happens across the house, on a different level.

So - a few questions. Call it homework, please answer them all:
* Did it work fine on prior Ubuntu releases? 13.04 is not supported anymore. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
* Does it work fine on other operating systems?
* Is the wifi router under your control or is this a wifi service provider?
* What model wifi router?
* How far between the router and laptop? Any obstructions?
* Are you in the same room with the router?
* Which channel is being used?
* Are any other wifi routers using the same channel?
* Which frequencies (2.4/5.8?)
* Which wifi card does your Toshiba have?
* Which drivers are you using?
* What country are you in? Different countries have different laws and frequencies.

---

### Post by silvan514 on 2014-02-09
Ok, first of all, thanks for replying.

I actually made a mistake. I am using 13.10.

I will go through the questions in the same order;)

*I lived in Switzerland until beginning of last month and had my own router, and it worked fine there. Now, I am supposed to use a wifi by British Telecom (BT Fon). I have bought one months allowance. I am sure it is not a problem on the provider's side, as my girl-friend uses it with her Mac and it works fine.
* so, yes it does. On my girl-friend Mac.
* by British Telecom
* --
* --
* --
* I don't know what "channel" means in this context.
* I don't know.
* I don't know.
* I think it is an "Atheros" model. Is that possible? I read about that in an article ([http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)). By the way, none of these tips solved my problem.
* I am using the drivers that came with Ubuntu canonical package.
* I am currently in the UK (south of it).

Hope that's helpful. Sorry about the "I don't knows".

---

### Post by silvan514 on 2014-02-11
Also, here are my settings. I had this file created following another suggestion earlier...


FILEBASE="wireless-info"
MODMATCHES="(air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|8192cu|8192du|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** PCMCIA Card Info *****\n\n"
pccardctl info
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
        printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
    fi
    fi
done
printf "\n***** modinfo *****\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done
printf "\n***** udev rules *****\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

---

### Post by silvan514 on 2014-02-13
root@Ramada:/home/silvan# lshw -c network
  *-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 24:fd:52:22:ff:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.11.0-15-generic firmware=N/A ip=192.168.0.90 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:3000(size=256) memory:c0500000-c0503fff
  *-network
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 08:9e:01:be:28:b2
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:c0400000-c043ffff ioport:20

---

### Post by TheFu on 2014-02-13
a) Please find the answers to my earlier questions. Some are REALLY easy, but will prevent us from spinning our wheels over things that are not related.
b) the wifi-info that you posted is just a script - you need to run it AND post the output to be of any help. Posting the script itself isn't too useful.
c) Your last post is helpful, but not so much without the answers to the initial questions. Please use "*code*" tags in the future so things line up and are easier to read.

---

### Post by varunendra on 2014-02-13
> **silvan514 said:**
> 
       configuration: broadcast=yes driver=**[COLOR="#FF0000"]rtl8188ee[/COLOR]** driverversion=**3.11.0-15-generic** firmware=N/A ip=192.168.0.90 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

This driver/card are known to have some issues. A later version as suggested [here]("http://askubuntu.com/a/398749") may work better.

But like TheFu mentioned already, please 'Run' the script that you posted, and instead post the result file (wireless-info.txt or wireless-info.txt.tar.gz) that it creates. It will give us much more info to be precise in our recommendations.

Please follow the "Wireless Script" link in my signature below to see the detailed instructions on how to run it.

---

### Post by silvan514 on 2014-02-13
Ok, thanks for the patience, guys.

Here: I hope this is helpful:


```
*************** info trace ***************

***** uname -a *****

Linux Ramada 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
    Kernel driver in use: rtl8188ee
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:fa80]
    Kernel driver in use: alx

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b3b1 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"RoyalOak Wi-Fi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:782   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

rtl8188ee              89614  0 
rtl_pci                26641  1 rtl8188ee
rtlwifi                63229  2 rtl_pci,rtl8188ee
mac80211              597268  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              480503  2 mac80211,rtlwifi

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [RoyalOak Wi-Fi] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
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
    SKYDCFC3:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    SKY20303:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    RoyalOak Wi-Fi:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46
    TALKTALK-044F20: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    RoyalOak Wi-Fi:  Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 48
    Maintenance:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *RoyalOak Wi-Fi: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    BTOpenzone:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    BTWifi-with-FON: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27

  IPv4 Settings:
    Address:         192.168.0.90
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



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
                    Encryption key:off
                    ESSID:"RoyalOak Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005188e3bcf4
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000E526F79616C4F616B2057692D4669
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"RoyalOak Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f9f95f0f54
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000E526F79616C4F616B2057692D4669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504000D127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434E20010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B000500000000000000000000000000000000000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-044F20"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001971bed663b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D303434463230
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9C0050F204104A0001101044000102103B0001031047001063041253101920061228C8D15E044F221021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383637311024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100114144534C204D6F64656D2F526F75746572100800020082
                    IE: Unknown: DD1E00904C330E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051100000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018c0a48da8b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Maintenance"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018c0a587826
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000B4D61696E74656E616E6365
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D14
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C


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

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     3DC80AFBD6DC9B10E085376
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8363D6BED4EF1CF5A92482B
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     13B5FC2521B6DC5AB3F115C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.400127] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   11.727969] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.728139] rtlwifi: wireless switch is on
[   15.337006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.337341] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.109575] wlan0: authenticate with <MAC address removed>
[   17.129176] wlan0: send auth to <MAC address removed> (try 1/3)
[   17.130726] wlan0: authenticated
[   17.132882] wlan0: associate with <MAC address removed> (try 1/3)
[   17.135646] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=3)
[   17.135811] wlan0: associated
[   17.135820] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.270249] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   66.307075] wlan0: authenticate with <MAC address removed>
[   66.318145] wlan0: send auth to <MAC address removed> (try 1/3)
[   66.319983] wlan0: authenticated
[   66.323103] wlan0: associate with <MAC address removed> (try 1/3)
[   66.325990] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=3)
[   66.326153] wlan0: associated
[   68.540668] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   69.397628] wlan0: authenticate with <MAC address removed>
[   69.417921] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.422712] wlan0: authenticated
[   69.425323] wlan0: associate with <MAC address removed> (try 1/3)
[   69.529409] wlan0: associate with <MAC address removed> (try 2/3)
[   69.633495] wlan0: associate with <MAC address removed> (try 3/3)
[   69.635882] wlan0: RX AssocResp from <MAC address removed> (capab=0xc21 status=0 aid=1)
[   69.636058] wlan0: associated
[   97.793084] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  104.219737] wlan0: authenticate with <MAC address removed>
[  104.239341] wlan0: send auth to <MAC address removed> (try 1/3)
[  104.246301] wlan0: authenticated
[  104.246938] wlan0: associate with <MAC address removed> (try 1/3)
[  104.351047] wlan0: associate with <MAC address removed> (try 2/3)
[  104.455159] wlan0: associate with <MAC address removed> (try 3/3)
[  104.559226] wlan0: association with <MAC address removed> timed out
[  105.528863] wlan0: authenticate with <MAC address removed>
[  105.548463] wlan0: send auth to <MAC address removed> (try 1/3)
[  105.549919] wlan0: authenticated
[  105.552086] wlan0: associate with <MAC address removed> (try 1/3)
[  105.562067] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=45)
[  105.562251] wlan0: associated
[  109.058176] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  114.220113] wlan0: authenticate with <MAC address removed>
[  114.239822] wlan0: send auth to <MAC address removed> (try 1/3)
[  114.243916] wlan0: authenticated
[  114.247468] wlan0: associate with <MAC address removed> (try 1/3)
[  114.253082] wlan0: RX AssocResp from <MAC address removed> (capab=0xc21 status=0 aid=1)
[  114.253272] wlan0: associated
[  144.288203] wlan0: Connection to AP <MAC address removed> lost
[  145.651018] wlan0: authenticate with <MAC address removed>
[  145.660504] wlan0: send auth to <MAC address removed> (try 1/3)
[  145.762318] wlan0: send auth to <MAC address removed> (try 2/3)
[  145.866405] wlan0: send auth to <MAC address removed> (try 3/3)
[  145.970495] wlan0: authentication with <MAC address removed> timed out
[  159.348970] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.442914] wlan0: authenticate with <MAC address removed>
[  164.462590] wlan0: send auth to <MAC address removed> (try 1/3)
[  164.464657] wlan0: authenticated
[  164.466166] wlan0: associate with <MAC address removed> (try 1/3)
[  164.468971] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=3)
[  164.469149] wlan0: associated
[  164.469187] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  210.396256] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  214.445358] wlan0: authenticate with <MAC address removed>
[  214.455022] wlan0: send auth to <MAC address removed> (try 1/3)
[  214.457135] wlan0: authenticated
[  214.460745] wlan0: associate with <MAC address removed> (try 1/3)
[  214.464733] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=3)
[  214.464901] wlan0: associated
[  260.437777] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  264.480190] wlan0: authenticate with <MAC address removed>
[  264.499590] wlan0: send auth to <MAC address removed> (try 1/3)
[  264.504396] wlan0: authenticated
[  264.507342] wlan0: associate with <MAC address removed> (try 1/3)
[  264.511291] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=6)
[  264.511468] wlan0: associated
[  333.568470] wlan0: authenticate with <MAC address removed>
[  333.578622] wlan0: send auth to <MAC address removed> (try 1/3)
[  333.583752] wlan0: authenticated
[  333.586078] wlan0: associate with <MAC address removed> (try 1/3)
[  333.589499] wlan0: RX AssocResp from <MAC address removed> (capab=0x1 status=0 aid=3)
[  333.589661] wlan0: associated
[  396.636365] wlan0: authenticate with <MAC address removed>
[  396.636502] wlan0: send auth to <MAC address removed> (try 1/3)
[  396.640634] wlan0: authenticated
[  396.640848] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  396.640854] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  396.644018] wlan0: associate with <MAC address removed> (try 1/3)
[  396.646202] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[  396.646368] wlan0: associated
[  822.988722] wlan0: authenticate with <MAC address removed>
[  822.999102] wlan0: direct probe to <MAC address removed> (try 1/3)
[  823.697280] wlan0: send auth to <MAC address removed> (try 2/3)
[  823.698877] wlan0: authenticated
[  823.935369] wlan0: authenticate with <MAC address removed>
[  823.945574] wlan0: direct probe to <MAC address removed> (try 1/3)
[  824.147231] wlan0: send auth to <MAC address removed> (try 2/3)
[  824.149388] wlan0: authenticated
[  824.151222] wlan0: associate with <MAC address removed> (try 1/3)
[  824.154073] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[  824.154254] wlan0: associated
[  851.570635] wlan0: Connection to AP <MAC address removed> lost
[  851.767363] wlan0: authenticate with <MAC address removed>
[  851.787093] wlan0: send auth to <MAC address removed> (try 1/3)
[  851.788823] wlan0: authenticated
[  851.790792] wlan0: associate with <MAC address removed> (try 1/3)
[  851.894851] wlan0: associate with <MAC address removed> (try 2/3)
[  851.899113] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=3)
[  851.899302] wlan0: associated
[  857.590850] wlan0: Connection to AP <MAC address removed> lost
[  858.945594] wlan0: authenticate with <MAC address removed>
[  858.965225] wlan0: send auth to <MAC address removed> (try 1/3)
[  858.966676] wlan0: authenticated
[  858.966830] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  858.966832] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  858.968896] wlan0: associate with <MAC address removed> (try 1/3)
[  858.971050] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[  858.971213] wlan0: associated
[ 1423.496044] wlan0: authenticate with <MAC address removed>
[ 1423.506423] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1423.507859] wlan0: authenticated
[ 1423.509080] wlan0: associate with <MAC address removed> (try 1/3)
[ 1423.512533] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 1423.512699] wlan0: associated
[ 1505.954251] wlan0: Connection to AP <MAC address removed> lost
[ 1512.777684] wlan0: authenticate with <MAC address removed>
[ 1512.798628] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1512.800218] wlan0: authenticated
[ 1512.800358] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1512.800361] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1512.800922] wlan0: associate with <MAC address removed> (try 1/3)
[ 1512.803169] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 1512.803335] wlan0: associated
[ 1783.809939] wlan0: authenticate with <MAC address removed>
[ 1783.820181] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1783.822284] wlan0: authenticated
[ 1783.823424] wlan0: associate with <MAC address removed> (try 1/3)
[ 1783.826432] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=5)
[ 1783.826603] wlan0: associated
[ 2024.010425] wlan0: authenticate with <MAC address removed>
[ 2024.020729] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2024.023739] wlan0: authenticated
[ 2024.025604] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2024.025608] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2024.031745] wlan0: associate with <MAC address removed> (try 1/3)
[ 2024.033898] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=1)
[ 2024.034060] wlan0: associated

****************** done ******************
```

---

### Post by varunendra on 2014-02-14
How far you are from the WiFi router/access-point, and what is the signal strength in Mac from the same distance?

Please try setting your router to b/g only mode, which means - try disabling N-channel in it if it supports that (b/g/n) and is enabled.
If that alone doesn't help, we may also try some temporary workarounds with your current driver -

Open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee ips=0
```
This will be a temporary change that will be lost at next boot, so try connecting without rebooting after this. If it doesn't seem to help, try another parameter -
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee fwlps=0
```
Then test the connection again. If this doesn't help either, try them both together -
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee ips=0 fwlps=0
```

And if you are using encryption in the router (you should, not a good idea to keep the security open), then also try another parameter "swenc" (individually, or with above ones as in this example -)
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee swenc=1 ips=0 fwlps=0
```

All of these would be temporary changes, so try the connection without rebooting after applying them. If any of these seems to help, report back and we'd make that permanent.

But if none of the above work, try the suggestion I linked to before, that is, this one : [http://askubuntu.com/a/398749](http://askubuntu.com/a/398749)

**PS:**
If any of the parameters or the newer driver works better, you may try it with N-channel enabled again to see if you can get advantage of higher speeds without compromising connection quality.

---

### Post by TheFu on 2014-02-14
There are 3 other routers on the SAME CHANNEL!!!
You need to get the router to switch channels - 1, 6, 11 are the only 2.4Ghz channels that don't overlap and 4 routers nearby are using channel 11.
There are lots of wifi devices in your area, so there will always be interference.  Wifi-N devices handle this better, so if you can switch to a device that supports that, you'll be better off. Hopefully, you'll be able to use the 5.8Ghz frequencies, which are less busy.

For testing, the laptop should be 3-7 ft away from the router, not too close, but definitely in the same room AND with a clear line-of-sight between the antennas on the router AND the antenna built-into the laptop.  Different types of antennas have very different radiation patterns. Learn a little about those so any efforts to direct antennas is productive.

Also, turn off all other wifi devices. Every addition device halves the available bandwidth, approximately.

---

### Post by silvan514 on 2014-02-14
Thanks Varun,

I followed the steps on the link you sent me. I think it has worked because the connection speed is more stable. I also did the speed scan and it yielded 8.626Mbps download speed. Browsing seems okay now.

Also, there seems to be a misunderstanding. I don't have a router in my house. I bought one month's allowance from BT, so I can use their network. I guess there are wifi antennas all over the UK. That one worked fine with the MAC. The other connection (royal oak) had always been slow, but I used it because the others did not work at all. Now the BT connection is at a stable 3 out of 4 bars... could probably still get better. I really don't know what I did driver-wise. What do you think about the speed? The connection potential is 72mb/s... but I guess this is just the highest rate possible and it varies during different times of the day.

Did another scan and had 29.54 a second...

Thanks again for all the help, I really do appreciate it.

Silvan

---

### Post by TheFu on 2014-02-14
Answering the original questions could have saved time.
If you don't control the router, there isn't much you can do besides create a wifi "heat map" of the best places for your area to learn where the performance is best. Also, you won't have any control over the number of concurrent devices connected, which is bad.  The way that wifi signals propigate means that sometimes closer isn't better when the source is outside. [http://www.howtogeek.com/165614/how-to-create-a-wi-fi-heatmap-for-network-analysis-better-coverage-and-geek-cred-galore/](http://www.howtogeek.com/165614/how-to-create-a-wi-fi-heatmap-for-network-analysis-better-coverage-and-geek-cred-galore/) describes the steps. Note that different devices will have different properties and the heat map for each will be different.

Good wifi drivers matter as well. There isn't much that you or I can do about those besides ensure we have the best drivers available for our equipment. "Best" does not always mean "newest."

For WiFi-G and B devices, every added device connection approximately halves the bandwidth.  To keep it simple, assuming that every device connected has a perfect connection (which is NEVER the situation), and that 50Mbps is the theoretical max, then
Mbps	Devices
50.00	0
25.00	1
12.50	2
6.25	3
3.13	4
1.56	5
0.78	6
0.39	7
0.20	8
0.10	9
0.05	10

With 10 devices connected, dialup would be better.
Never believe the "72Mbps" crap. It is a lie.  In lab testing, we were never able to get the throughput our connection speed claimed.  BTW, I've designed wifi deployments for over 1200 locations.

---

### Post by silvan514 on 2014-02-14
You are right. I am a complete newbie to Ubuntu, so "sorry". Thanks for the information, your time and patience.

Silvan

---

### Post by varunendra on 2014-02-14
> **TheFu said:**
> "Best" does not always mean "newest."

A big **+1** !


@ silvan514,

Feel free to ask questions if you have more related ones, of course providing background details as TheFu asked.
But if the connection is satisfactory now and you think the current problem is solved, please mark the thread as [SOLVED] to help others looking for help on the same problem. :)

---


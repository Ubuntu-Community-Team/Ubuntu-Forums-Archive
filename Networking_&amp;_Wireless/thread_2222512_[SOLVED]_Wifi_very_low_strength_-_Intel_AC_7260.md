---
title: "[SOLVED] Wifi very low strength - Intel AC 7260"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by tony43 on 2014-05-06
Hi,
new to Linux here.


  Before completely formatting my computer I dual booted Ubuntu to try it out.
  Right now I am having wifi connectivity issues, my wifi strength is   extremely low but when I switch to Windows 7 I have full strength.

  I figured maybe its the driver. I downloaded and I am assuming I have   installed it, I see the ucode in the firmware folder in lib. At least I   believe I installed it correctly.
  
I have the Intel Wireless AC 7260 wifi card. I am trying to read others  questions with the same problem, either my  internet just stops on me or  the fix that worked for them wasn't valid  for myself.

  If anyone could shed some light on this that would be great, it appears to be my only problem at the moment.
  
Thanks in advance.

```

FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"

exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCannot write output file, aborting.\n\n"
    exit 1
fi

printf "\n########## wireless info START ##########\n"

printf "\n##### release #####\n\n"
lsb_release -idrc

printf "\n##### kernel #####\n\n"
uname -a

printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 net | sed 's/^--$//'

printf "\n##### lsusb #####\n\n"
lsusb

printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info

printf "\n##### rfkill #####\n\n"
rfkill list all

printf "\n##### iw reg get #####\n\n"
iw reg get

printf "\n##### interfaces #####\n\n"
sed 's/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### iwconfig #####\n\n"
iwconfig

printf "\n##### route #####\n\n"
route -n

printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### nm-tool #####\n"
nm-tool

printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### iwlist #####\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi

printf "\n##### iwlist channel #####\n\n"
iwlist chan

printf "\n##### lsmod #####\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"

printf "\n##### modinfo #####\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done

printf "\n##### modules #####\n\n"
grep -v '^#' /etc/modules

printf "\n##### blacklist #####\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
        printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
    fi
    fi
done

printf "\n##### udev rules #####\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules

printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"

printf "\n########## wireless info END ############\n\n"

exec 1>&3 3>&-
exec 2>&4 4>&-

RESULTS=$(cat -s $FILEBASE.txt)
sed 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' <<< "$RESULTS" > $FILEBASE.txt

if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

```

---

### Post by varunendra on 2014-05-07
Hi tony,

You have posted the wireless_script itself, not the report it generates. We need the report, not the script. Please follow the "Wireless Script" link in my signature below to see the detailed instructions.

---

### Post by tony43 on 2014-05-11
Hey Thnaks for the response, my apologies I must of missread something.
Also my bad for the late response, I had personal stuff to attend to.

Btw here is the Wifi Info.
I am still having issues with my connection using Ubuntu.

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux tony-N61Jq 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
    Kernel driver in use: atl1c

##### lsusb #####

Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 13d3:5122 IMC Networks 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11abgn  ESSID:"CICC-5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC address removed>   
          Bit Rate=24 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=17/70  Signal level=-93 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:23  Invalid misc:14   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [CICC-5] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Miller:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA
    BELL725:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    FibeTVM91351SA1BRR: Infra, <MAC address removed>, Freq 5540 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Johnny5:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    *CICC-5:         Infra, <MAC address removed>, Freq 5180 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Fast Lion:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    CICC:            Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    PACE491:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    bertdana:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    JOSEPH:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA
    Purplerose:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    GoldFinger:      Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Rogers14144:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    belkin.27c:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2
    belkin.27c.guests: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    Bel4:            Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    dhouse:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Bishua:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Kalulu:          Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 14 WEP

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.18 GHz (Channel 36)

##### lsmod #####

iwlmvm                189774  0 
mac80211              626489  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
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
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
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
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   20.332352] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X
[   20.682579] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   20.706566] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   20.706621] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.706856] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.914472] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   21.219231] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[   24.127261] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   24.127647] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   24.144416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.146246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.958117] wlan0: authenticate with <MAC address removed>
[   27.960867] wlan0: direct probe to <MAC address removed> (try 1/3)
[   28.165872] wlan0: direct probe to <MAC address removed> (try 2/3)
[   28.369454] wlan0: direct probe to <MAC address removed> (try 3/3)
[   28.572983] wlan0: authentication with <MAC address removed> timed out
[   32.269907] wlan0: authenticate with <MAC address removed>
[   32.271698] wlan0: direct probe to <MAC address removed> (try 1/3)
[   32.475979] wlan0: direct probe to <MAC address removed> (try 2/3)
[   32.680093] wlan0: direct probe to <MAC address removed> (try 3/3)
[   32.883607] wlan0: authentication with <MAC address removed> timed out
[   45.583720] wlan0: authenticate with <MAC address removed>
[   45.585366] wlan0: direct probe to <MAC address removed> (try 1/3)
[   45.788041] wlan0: direct probe to <MAC address removed> (try 2/3)
[   45.996217] wlan0: direct probe to <MAC address removed> (try 3/3)
[   46.199717] wlan0: authentication with <MAC address removed> timed out
[   60.756983] wlan0: authenticate with <MAC address removed>
[   60.758889] wlan0: direct probe to <MAC address removed> (try 1/3)
[   60.961612] wlan0: direct probe to <MAC address removed> (try 2/3)
[   61.165907] wlan0: direct probe to <MAC address removed> (try 3/3)
[   61.369165] wlan0: authentication with <MAC address removed> timed out
[   69.965838] wlan0: authenticate with <MAC address removed>
[   69.968231] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.968843] wlan0: authenticated
[   69.970343] wlan0: associate with <MAC address removed> (try 1/3)
[   69.983590] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   69.985042] wlan0: associated
[   69.985087] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1837.381638] wlan0: authenticate with <MAC address removed>
[ 1837.383475] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1837.384104] wlan0: authenticated
[ 1837.387768] wlan0: associate with <MAC address removed> (try 1/3)
[ 1837.400162] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1837.401613] wlan0: associated
[ 3567.674695] wlan0: authenticate with <MAC address removed>
[ 3567.677555] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3567.678185] wlan0: authenticated
[ 3567.682010] wlan0: associate with <MAC address removed> (try 1/3)
[ 3567.694388] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3567.695653] wlan0: associated
[ 3623.924223] wlan0: authenticate with <MAC address removed>
[ 3623.926104] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3623.926697] wlan0: authenticated
[ 3623.928620] wlan0: associate with <MAC address removed> (try 1/3)
[ 3623.940946] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3623.942317] wlan0: associated
[ 3645.753633] wlan0: authenticate with <MAC address removed>
[ 3645.755861] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3645.756534] wlan0: authenticated
[ 3645.757579] wlan0: associate with <MAC address removed> (try 1/3)
[ 3645.769938] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3645.771200] wlan0: associated
[ 3671.974298] wlan0: authenticate with <MAC address removed>
[ 3671.976465] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3671.977475] wlan0: authenticated
[ 3671.981585] wlan0: associate with <MAC address removed> (try 1/3)
[ 3671.993966] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3671.995357] wlan0: associated
[ 3738.795360] wlan0: authenticate with <MAC address removed>
[ 3738.797293] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3738.797866] wlan0: authenticated
[ 3738.798242] wlan0: associate with <MAC address removed> (try 1/3)
[ 3738.810652] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3738.812291] wlan0: associated
[ 3820.340490] wlan0: authenticate with <MAC address removed>
[ 3820.342691] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3820.343313] wlan0: authenticated
[ 3820.343959] wlan0: associate with <MAC address removed> (try 1/3)
[ 3820.356354] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3820.357953] wlan0: associated
[ 3850.569220] wlan0: authenticate with <MAC address removed>
[ 3850.571054] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3850.571925] wlan0: authenticated
[ 3850.574356] wlan0: associate with <MAC address removed> (try 1/3)
[ 3850.586763] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3850.588455] wlan0: associated
[ 3857.230439] wlan0: authenticate with <MAC address removed>
[ 3857.232563] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3857.233194] wlan0: authenticated
[ 3857.234419] wlan0: associate with <MAC address removed> (try 1/3)
[ 3857.246943] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3857.248682] wlan0: associated
[ 3878.762283] wlan0: authenticate with <MAC address removed>
[ 3878.764459] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3878.765174] wlan0: authenticated
[ 3878.767523] wlan0: associate with <MAC address removed> (try 1/3)
[ 3878.779945] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3878.781438] wlan0: associated
[ 3891.754754] wlan0: authenticate with <MAC address removed>
[ 3891.757040] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3891.757680] wlan0: authenticated
[ 3891.759551] wlan0: associate with <MAC address removed> (try 1/3)
[ 3891.772034] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3891.773849] wlan0: associated
[ 3971.580489] wlan0: authenticate with <MAC address removed>
[ 3971.582837] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3971.583518] wlan0: authenticated
[ 3971.584183] wlan0: associate with <MAC address removed> (try 1/3)
[ 3971.596608] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 3971.598355] wlan0: associated
[ 4164.706314] wlan0: authenticate with <MAC address removed>
[ 4164.708236] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4164.708882] wlan0: authenticated
[ 4164.709827] wlan0: associate with <MAC address removed> (try 1/3)
[ 4164.722240] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4164.724001] wlan0: associated
[ 4192.766466] wlan0: authenticate with <MAC address removed>
[ 4192.768527] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4192.774376] wlan0: authenticated
[ 4192.774918] wlan0: associate with <MAC address removed> (try 1/3)
[ 4192.787383] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4192.788985] wlan0: associated
[ 4199.305766] wlan0: authenticate with <MAC address removed>
[ 4199.307935] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4199.308629] wlan0: authenticated
[ 4199.310846] wlan0: associate with <MAC address removed> (try 1/3)
[ 4199.324037] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4199.325330] wlan0: associated
[ 4204.037322] wlan0: authenticate with <MAC address removed>
[ 4204.039354] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4204.045207] wlan0: authenticated
[ 4204.045720] wlan0: associate with <MAC address removed> (try 1/3)
[ 4204.058169] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4204.059466] wlan0: associated
[ 4430.712190] wlan0: authenticate with <MAC address removed>
[ 4430.714303] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4430.714978] wlan0: authenticated
[ 4430.715887] wlan0: associate with <MAC address removed> (try 1/3)
[ 4430.728209] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4430.729834] wlan0: associated
[ 4445.565888] wlan0: authenticate with <MAC address removed>
[ 4445.568095] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4445.568716] wlan0: authenticated
[ 4445.572975] wlan0: associate with <MAC address removed> (try 1/3)
[ 4445.585444] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4445.587195] wlan0: associated

########## wireless info END ############
```

Thanks again.

---

### Post by tony43 on 2014-05-25
Hello, I am having issues with my internet, I am on a windows 7 dual boot and the internet is working normally on my Windows. But for Ubunut I don't understand what the problem is.  If anyone can help that would be great.    ```
   ########## wireless info START ##########  ##### release #####  Distributor ID:	Ubuntu Description:	Ubuntu 14.04 LTS Release:	14.04 Codename:	trusty  ##### kernel #####  Linux tony-N61Jq 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  ##### lspci #####  03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73) 	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070] 	Kernel driver in use: iwlwifi  08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0) 	Subsystem: ASUSTeK Computer Inc. Device [1043:1820] 	Kernel driver in use: atl1c  ##### lsusb #####  Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc.  Bus 001 Device 004: ID 13d3:5122 IMC Networks  Bus 001 Device 003: ID 8087:07dc Intel Corp.  Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  ##### PCMCIA Card Info #####  ##### rfkill #####  0: hci0: Bluetooth 	Soft blocked: no 	Hard blocked: no 1: hci1: Bluetooth 	Soft blocked: no 	Hard blocked: no 2: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no  ##### iw reg get #####  country 00: 	(2402 - 2472 @ 40), (3, 20) 	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS 	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS 	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS 	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS  ##### interfaces #####  # interfaces(5) file used by ifup(8) and ifdown(8) auto lo iface lo inet loopback  ##### iwconfig #####  wlan0     IEEE 802.11abgn  ESSID:"CICC-5"             Mode:Managed  Frequency:5.18 GHz  Access Point:               Bit Rate=6 Mb/s   Tx-Power=16 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:on           Link Quality=38/70  Signal level=-72 dBm             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:364  Invalid misc:440   Missed beacon:0  ##### route #####  Kernel IP routing table Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0 192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0  ##### resolv.conf #####  nameserver 127.0.1.1  ##### nm-tool #####  NetworkManager Tool  State: connected (global)  - Device: eth0 -----------------------------------------------------------------   Type:              Wired   Driver:            atl1c   State:             unavailable   Default:           no   HW Address:            Capabilities:     Carrier Detect:  yes    Wired Properties     Carrier:         off  - Device: wlan0  [CICC-5] ------------------------------------------------------   Type:              802.11 WiFi   Driver:            iwlwifi   State:             connected   Default:           yes   HW Address:            Capabilities:     Speed:           32 Mb/s    Wireless Properties     WEP Encryption:  yes     WPA Encryption:  yes     WPA2 Encryption: yes    Wireless Access Points (* = current AP)     FibeTVM91351SA1BRR: Infra, , Freq 5560 MHz, Rate 54 Mb/s, Strength 74 WPA2     Miller:          Infra, , Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA     BELL725:         Infra, , Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2     Fast Lion:       Infra, , Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2     Johnny5:         Infra, , Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2     GoldFinger:      Infra, , Freq 2417 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2     JOSEPH:          Infra, , Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA     CICC:            Infra, , Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2     *CICC-5:         Infra, , Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2     BELL744:         Infra, , Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2     Bishua:          Infra, , Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2     Rogers14144:     Infra, , Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2    IPv4 Settings:     Address:         192.168.0.100     Prefix:          24 (255.255.255.0)     Gateway:         192.168.0.1      DNS:             192.168.0.1  ##### NetworkManager.state #####  [main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true  ##### NetworkManager.conf #####  [main] plugins=ifupdown,keyfile,ofono dns=dnsmasq  [ifupdown] managed=false  ##### iwlist #####  wlan0     Scan completed :           Cell 01 - Address:                      Channel:36                     Frequency:5.18 GHz (Channel 36)                     Quality=40/70  Signal level=-70 dBm                       Encryption key:on                     ESSID:"CICC-5"                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                               36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=000000003a952036                     Extra: Last beacon: 28ms ago                     IE: Unknown: 0006434943432D35                     IE: Unknown: 01088C129824B048606C                     IE: Unknown: 2D1A6E101FFFFF000000000000000000000000000000000000000000                     IE: Unknown: 3D1624050000000000000000000000000000000000000000                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: DD1E00904C336E101FFFFF000000000000000000000000000000000000000000                     IE: Unknown: DD1A00904C3424050000000000000000000000000000000000000000                     IE: Unknown: DD0700E04C02026004                     IE: Unknown: BF0C3040C103FAFF0C03FAFF0C03                     IE: Unknown: C005012A00F0FF                     IE: Unknown: DD820050F204104A0001101044000102103B00010310470010112233445566778899AAC8D3A3703D7610210006442D4C696E6B102300084449522D3832304C102400084449522D3832304C1042000830303030303030301054000800060050F2040001101100084449522D3832304C10080002208C103C0001031049000600372A000120           Cell 02 - Address:                      Channel:1                     Frequency:2.412 GHz (Channel 1)                     Quality=35/70  Signal level=-75 dBm                       Encryption key:on                     ESSID:"BELL725"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s; 54 Mb/s                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s                     Mode:Master                     Extra:tsf=0000007d8f206f2b                     Extra: Last beacon: 28ms ago                     IE: Unknown: 000742454C4C373235                     IE: Unknown: 010882848B961224486C                     IE: Unknown: 030101                     IE: Unknown: 2A0104                     IE: Unknown: 32040C183060                     IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000                     IE: Unknown: 3D1601050000000000000000000000000000000000000000                     IE: Unknown: 3E0100                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: 0B0500000A127A                     IE: Unknown: 4A0E14000A002C01C800140005001900                     IE: Unknown: 7F0101                     IE: Unknown: DD07000C4300000000                     IE: Unknown: 0706434120010B10                     IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A880D86CE921F93D1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101           Cell 03 - Address:                      Channel:1                     Frequency:2.412 GHz (Channel 1)                     Quality=19/70  Signal level=-91 dBm                       Encryption key:on                     ESSID:"Bishua"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                               36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=00000055e97051bc                     Extra: Last beacon: 4732ms ago                     IE: Unknown: 0006426973687561                     IE: Unknown: 010482848B96                     IE: Unknown: 030101                     IE: Unknown: 050400010000                     IE: Unknown: 2A0100                     IE: Unknown: 2F0100                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : CCMP TKIP                         Authentication Suites (1) : PSK                     IE: Unknown: 32080C1218243048606C                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000                     IE: Unknown: 3D1601080000000000000000000000000000000000000000                     IE: Unknown: DD090010180201F02C0000                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : CCMP TKIP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00           Cell 04 - Address:                      Channel:2                     Frequency:2.417 GHz (Channel 2)                     Quality=17/70  Signal level=-93 dBm                       Encryption key:on                     ESSID:"GoldFinger"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s; 54 Mb/s                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s                     Mode:Master                     Extra:tsf=0000000f08a9d15d                     Extra: Last beacon: 4684ms ago                     IE: Unknown: 000A476F6C6446696E676572                     IE: Unknown: 010882848B961224486C                     IE: Unknown: 030102                     IE: Unknown: 32040C183060                     IE: Unknown: 0706555320010B14                     IE: Unknown: 33082001020304050607                     IE: Unknown: 33082105060708090A0B                     IE: Unknown: 050400010002                     IE: Unknown: DD310050F204104A0001101044000102104700102880288028801880A880BC1401280208103C0001011049000600372A000120                     IE: Unknown: 2A0104                     IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000                     IE: Unknown: 3D1602000600000000000000000000000000000000000000                     IE: Unknown: 4A0E14000A002C01C800140005001900                     IE: Unknown: 7F0101                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: 0B05010014127A                     IE: Unknown: DD07000C4304000000           Cell 05 - Address:                      Channel:2                     Frequency:2.417 GHz (Channel 2)                     Quality=19/70  Signal level=-91 dBm                       Encryption key:on                     ESSID:""                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s; 54 Mb/s                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s                     Mode:Master                     Extra:tsf=0000000f08a9dc5f                     Extra: Last beacon: 4680ms ago                     IE: Unknown: 0000                     IE: Unknown: 010882848B961224486C                     IE: Unknown: 030102                     IE: Unknown: 32040C183060                     IE: Unknown: 0706555320010B14                     IE: Unknown: 33082001020304050607                     IE: Unknown: 33082105060708090A0B                     IE: Unknown: 050400010000                     IE: Unknown: 2A0104                     IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000                     IE: Unknown: 3D1602000600000000000000000000000000000000000000                     IE: Unknown: 4A0E14000A002C01C800140005001900                     IE: Unknown: 7F0101                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: 0B05010014127A                     IE: Unknown: DD07000C4304000000           Cell 06 - Address:                      Channel:3                     Frequency:2.422 GHz (Channel 3)                     Quality=29/70  Signal level=-81 dBm                       Encryption key:on                     ESSID:"Fast Lion"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s; 54 Mb/s                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s                     Mode:Master                     Extra:tsf=0000004399e3f4dd                     Extra: Last beacon: 28ms ago                     IE: Unknown: 000946617374204C696F6E                     IE: Unknown: 010882848B961224486C                     IE: Unknown: 030103                     IE: Unknown: 2A0104                     IE: Unknown: 32040C183060                     IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000                     IE: Unknown: 3D1603010400000000000000000000000000000000000000                     IE: Unknown: 3E0100                     IE: WPA Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: 0B0504000F127A                     IE: Unknown: 7F0101                     IE: Unknown: DD07000C4304000000                     IE: Unknown: 0706555320010B10                     IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A880BC1401576BE810210006484954524F4E1023000443474E321024000A313530333230303030311042000C3235303131373032323235351054000800060050F20400011011000652543333353210080002210C103C0001011049000600372A000120           Cell 07 - Address:                      Channel:3                     Frequency:2.422 GHz (Channel 3)                     Quality=29/70  Signal level=-81 dBm                       Encryption key:on                     ESSID:""                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s; 54 Mb/s                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s                     Mode:Master                     Extra:tsf=0000004399e3df6d                     Extra: Last beacon: 4668ms ago                     IE: Unknown: 0000                     IE: Unknown: 010882848B961224486C                     IE: Unknown: 030103                     IE: Unknown: 32040C183060                     IE: Unknown: 0706555320010B14                     IE: Unknown: 33082001020304050607                     IE: Unknown: 33082105060708090A0B                     IE: Unknown: 050400010000                     IE: Unknown: 2A0104                     IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000                     IE: Unknown: 3D1603010400000000000000000000000000000000000000                     IE: Unknown: 7F0101                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: 0B0504000F127A                     IE: Unknown: DD07000C4304000000           Cell 08 - Address:                      Channel:6                     Frequency:2.437 GHz (Channel 6)                     Quality=48/70  Signal level=-62 dBm                       Encryption key:on                     ESSID:"Miller"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                               36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=0000007af10fc4f3                     Extra: Last beacon: 28ms ago                     IE: Unknown: 00064D696C6C6572                     IE: Unknown: 010582848B962C                     IE: Unknown: 030106                     IE: Unknown: 2A0100                     IE: Unknown: 32080C1218243048606C                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (1) : TKIP                         Authentication Suites (1) : PSK           Cell 09 - Address:                      Channel:6                     Frequency:2.437 GHz (Channel 6)                     Quality=27/70  Signal level=-83 dBm                       Encryption key:on                     ESSID:"Johnny5"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                               9 Mb/s; 12 Mb/s; 18 Mb/s                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=00000001abff4626                     Extra: Last beacon: 28ms ago                     IE: Unknown: 00074A6F686E6E7935                     IE: Unknown: 010882848B960C121824                     IE: Unknown: 030106                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                        Preauthentication Supported                     IE: Unknown: 2A0100                     IE: Unknown: 32043048606C                     IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00                     IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000                     IE: Unknown: 3D1606001900000000000000000000000000000000000000                     IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259CF94CEB102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B3332393333351054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004                     IE: Unknown: DD0900037F01010000FF7F                     IE: Unknown: DD0A00037F04010000000000           Cell 10 - Address:                      Channel:10                     Frequency:2.457 GHz (Channel 10)                     Quality=45/70  Signal level=-65 dBm                       Encryption key:on                     ESSID:"CICC"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s                               9 Mb/s; 12 Mb/s; 18 Mb/s                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=000000003ab74176                     Extra: Last beacon: 4316ms ago                     IE: Unknown: 000443494343                     IE: Unknown: 010882848B960C121824                     IE: Unknown: 03010A                     IE: Unknown: 050400010100                     IE: Unknown: 2A0104                     IE: Unknown: 32043048606C                     IE: Unknown: 2D1A6E101EFFFF000000000000000000000000000000000000000000                     IE: Unknown: 3D160A000000000000000000000000000000000000000000                     IE: Unknown: 4A0E14000A00B400C800140005001900                     IE: Unknown: 7F0101                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) : TKIP CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00                     IE: Unknown: DD1E00904C336E101EFFFF000000000000000000000000000000000000000000                     IE: Unknown: DD1A00904C340A000000000000000000000000000000000000000000                     IE: Unknown: DD0600E04C020160                     IE: Unknown: DD310050F204104A000110104400010210470010112233445566778899AAC8D3A3703D76103C0001031049000600372A000120           Cell 11 - Address:                      Channel:11                     Frequency:2.462 GHz (Channel 11)                     Quality=25/70  Signal level=-85 dBm                       Encryption key:on                     ESSID:"JOSEPH"                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                               36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=0000008159054963                     Extra: Last beacon: 28ms ago                     IE: Unknown: 00064A4F53455048                     IE: Unknown: 010582848B962C                     IE: Unknown: 03010B                     IE: Unknown: 2A0100                     IE: Unknown: 32080C1218243048606C                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (1) : TKIP                         Authentication Suites (1) : PSK           Cell 12 - Address:                      Channel:112                     Frequency:5.56 GHz (Channel 112)                     Quality=53/70  Signal level=-57 dBm                       Encryption key:on                     ESSID:"FibeTVM91351SA1BRR"                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                               36 Mb/s; 48 Mb/s; 54 Mb/s                     Mode:Master                     Extra:tsf=0000007d91c8a3e7                     Extra: Last beacon: 28ms ago                     IE: Unknown: 00124669626554564D3931333531534131425252                     IE: Unknown: 01088C129824B048606C                     IE: Unknown: 030170                     IE: Unknown: 2D1A4F0017FFFFFFFFFEFFFFFFFF1F000001000000000018E6E71900                     IE: Unknown: 3D16700F0400000000000000000000000000000000000000                     IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00                     IE: IEEE 802.11i/WPA2 Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) : CCMP                         Authentication Suites (1) : PSK                     IE: Unknown: DD8E0050F204104A0001101044000102103B00010310470010848065899FCC586A8F344A4BC5651BF1102100095175616E74656E6E611023000452756279102400095148533731302E30301042000C4D39313335315341314252521054000800060050F2040001101100105265666572656E63652044657369676E100800020006103C0001021049000600372A000120                     IE: Unknown: DD0A002686010300DD000001  ##### iwlist channel #####  wlan0     32 channels in total; available frequencies :           Channel 01 : 2.412 GHz           Channel 02 : 2.417 GHz           Channel 03 : 2.422 GHz           Channel 04 : 2.427 GHz           Channel 05 : 2.432 GHz           Channel 06 : 2.437 GHz           Channel 07 : 2.442 GHz           Channel 08 : 2.447 GHz           Channel 09 : 2.452 GHz           Channel 10 : 2.457 GHz           Channel 11 : 2.462 GHz           Channel 12 : 2.467 GHz           Channel 13 : 2.472 GHz           Channel 36 : 5.18 GHz           Channel 40 : 5.2 GHz           Channel 44 : 5.22 GHz           Channel 48 : 5.24 GHz           Channel 52 : 5.26 GHz           Channel 56 : 5.28 GHz           Channel 60 : 5.3 GHz           Channel 64 : 5.32 GHz           Channel 100 : 5.5 GHz           Channel 104 : 5.52 GHz           Channel 108 : 5.54 GHz           Channel 112 : 5.56 GHz           Channel 116 : 5.58 GHz           Channel 120 : 5.6 GHz           Channel 124 : 5.62 GHz           Channel 128 : 5.64 GHz           Channel 132 : 5.66 GHz           Channel 136 : 5.68 GHz           Channel 140 : 5.7 GHz           Current Frequency:5.18 GHz (Channel 36)  ##### lsmod #####  iwlmvm                189774  0  mac80211              626489  1 iwlmvm iwlwifi               169932  1 iwlmvm cfg80211              484040  3 iwlwifi,mac80211,iwlmvm  ##### modinfo #####  filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko license:        GPL author:         Copyright(c) 2003-2013 Intel Corporation  version:        in-tree: description:    The new Intel(R) wireless AGN driver for Linux srcversion:     964B69F7EBC572BE39F5C50 depends:        iwlwifi,mac80211,cfg80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload modversions  signer:         Magrathea: Glacier signing key sig_key:        :D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0 sig_hashalgo:   sha512 parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool) parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)  filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko license:        GPL author:         Copyright(c) 2003-2013 Intel Corporation  version:        in-tree: description:    Intel(R) Wireless WiFi driver for Linux firmware:       iwlwifi-100-5.ucode firmware:       iwlwifi-1000-5.ucode firmware:       iwlwifi-135-6.ucode firmware:       iwlwifi-105-6.ucode firmware:       iwlwifi-2030-6.ucode firmware:       iwlwifi-2000-6.ucode firmware:       iwlwifi-5150-2.ucode firmware:       iwlwifi-5000-5.ucode firmware:       iwlwifi-6000g2b-6.ucode firmware:       iwlwifi-6000g2a-5.ucode firmware:       iwlwifi-6050-5.ucode firmware:       iwlwifi-6000-4.ucode firmware:       iwlwifi-3160-7.ucode firmware:       iwlwifi-7260-7.ucode srcversion:     1E6912E109D5A43B310FB34 alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i* alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i* alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i* alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i* alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i* alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i* alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i* alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i* alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i* alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i* alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i* alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i* alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i* alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i* alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i* alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i* alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i* alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i* alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i* alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i* alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i* alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i* alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i* alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i* alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i* alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i* alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i* alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i* alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i* alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i* alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i* alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i* alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i* alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i* alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i* alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i* alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i* alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i* alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i* alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i* alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i* alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i* alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i* alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i* alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i* alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i* alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i* alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i* alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i* alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i* alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i* alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i* alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i* alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i* alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i* alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i* alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i* alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i* alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i* alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i* alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i* alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i* alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i* alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i* alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i* alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i* alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i* alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i* alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i* alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i* depends:        cfg80211 intree:         Y vermagic:       3.13.0-24-generic SMP mod_unload modversions  signer:         Magrathea: Glacier signing key sig_key:        :D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0 sig_hashalgo:   sha512 parm:           swcrypto:using crypto in software (default 0 [hardware]) (int) parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint) parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int) parm:           fw_restart:restart firmware in case of error (default true) (bool) parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int) parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int) parm:           nvm_file:NVM file name (charp) parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool) parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int) parm:           power_save:enable WiFi power management (default: disable) (bool) parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)  ##### modules #####  lp rtc  ##### blacklist #####  [/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci  [/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac  [/etc/modprobe.d/fbdev-blacklist.conf] blacklist arkfb blacklist aty128fb blacklist atyfb blacklist radeonfb blacklist cirrusfb blacklist cyber2000fb blacklist gx1fb blacklist gxfb blacklist kyrofb blacklist matroxfb_base blacklist mb862xxfb blacklist neofb blacklist nvidiafb blacklist pm2fb blacklist pm3fb blacklist s3fb blacklist savagefb blacklist sisfb blacklist tdfxfb blacklist tridentfb blacklist viafb blacklist vt8623fb  ##### udev rules #####  # PCI device 0x1969:0x1063 (atl1c) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"  # PCI device 0x8086:0x08b1 (iwlwifi) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"  ##### dmesg #####  [    2.575817] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201) [   15.412882] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X [   15.441494] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2 [   15.441500] iwlwifi 0000:03:00.0: Falling back to user helper [   15.611292] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm [   15.629109] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144 [   15.629162] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S [   15.629377] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S [   15.852416] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs' [   19.204550] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S [   19.204778] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S [   19.219674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready [   19.220426] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready [   22.930961] wlan0: authenticate with  [   22.933198] wlan0: direct probe to  (try 1/3) [   23.136524] wlan0: direct probe to  (try 2/3) [   23.340936] wlan0: direct probe to  (try 3/3) [   23.544039] wlan0: authentication with  timed out [   79.678395] wlan0: authenticate with  [   79.679529] wlan0: send auth to  (try 1/3) [   79.680158] wlan0: authenticated [   79.682329] wlan0: associate with  (try 1/3) [   79.695361] wlan0: RX AssocResp from  (capab=0x411 status=0 aid=1) [   79.696419] wlan0: associated [   79.696447] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  ########## wireless info END ############ 
```  I don't understand why it is posting it in one giant line

---

### Post by varunendra on 2014-05-28
Hello Tony, sorry for not being able to reply on your [earlier thread]("http://ubuntuforums.org/showthread.php?t=2222512").., but you should rather bump your thread instead of posting new one.

Based on your previous report, which is more clear, here are a few suggestions -

1) In your router/access-point, change the encryption to pure WPA2-PSK with AES (CCMP). It was set to WPA/WPA2 mixed mode with TKIP (as per previous report) which should be avoided.

2) Run the following command in a terminal -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
..and make sure "Power Management" appears to be "off".

If these two don't help, please post back a fresh report of a new, experimental version of wireless_script mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by bapoumba on 2014-05-28
Threads merged.

---

### Post by tony43 on 2014-06-08
Hey there,
Sorry abot the double posted topics, I was not sure if bumping was aloud on the forums.

So I changed the security encryptions as you suggested, though it didn't do much improvement to the connection.

What really helped was turning off the Power Management. my 2.4Gz connection is 100% solid now Thanks!
I usually stay on the 5gz freqeuncy but that still isn't working even after these changes. Atleast I have a connection now.

Here is the info when connected to the 5gz.
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

tony-N61Jq 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
Memory : 3877 MB
Uptime : 16:59:11 up  1:19,  2 users,  load average: 0.41, 0.43, 0.38


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi
--
08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 13d3:5122 IMC Networks 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"CICC-5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC C-01 CICC-5>   
          Bit Rate=18 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:244  Invalid misc:387   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: hci1: Bluetooth         no            no
2: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626489  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=================o=============o=========o==============o=========o===========o==============o===========
 eth0            | Wired       | atl1c   | unavailable  | no      |           |              | <MAC eth0>
-----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0  [CICC-5] | 802.11 WiFi | iwlwifi | connected    | yes     | 12 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    FibeTVM91351SA1BRR: Infra, <MAC C-08 FibeTVM91351SA1BRR>, Freq 5540 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Miller:          Infra, <MAC C-03 Miller>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    BELL725:         Infra, <MAC C-07 BELL725>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Johnny5:         Infra, <MAC C-10 Johnny5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Fast Lion:       Infra, <MAC C-02 Fast Lion>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Rogers14144:     Infra, <MAC C-04 Rogers14144>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    JOSEPH:          Infra, <MAC C-12 JOSEPH>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA
    MINet:           Infra, <MAC C-NA MINet 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    BELL744:         Infra, <MAC C-NA BELL744 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    GoldFinger:      Infra, <MAC C-NA GoldFinger 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    *CICC-5:         Infra, <MAC C-01 CICC-5>, Freq 5180 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    Rogers303:       Infra, <MAC C-NA Rogers303 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

    Address:         192.168.0.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
-----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

CICC                 : ssid=CICC | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CICC-5               : ssid=CICC-5 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
FibeTVM91351SA1BRR   : ssid=FibeTVM91351SA1BRR | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.971/52.753/104.536/51.783 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.032/0.037/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)

          Current Frequency:5.18 GHz (Channel 36)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 CICC-5>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"CICC-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e03c027
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Fast Lion>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Fast Lion"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000305610ad6b
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Miller>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Miller"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002be037bdbb
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Rogers14144>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Rogers14144"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c6679eb15d
                    Extra: Last beacon: 4360ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 >
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c6673ddc17
                    Extra: Last beacon: 10708ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 CICC>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"CICC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000e1f6423
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 BELL725>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BELL725"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003055de9654
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 FibeTVM91351SA1BRR>
                    Channel:108
                    Frequency:5.54 GHz (Channel 108)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"FibeTVM91351SA1BRR"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000030582d4b46
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030525afc0b
                    Extra: Last beacon: 11064ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 Johnny5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Johnny5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029eaf5180
                    Extra: Last beacon: 10892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: <MAC C-11 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000305610fca3
                    Extra: Last beacon: 4528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 JOSEPH>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"JOSEPH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002b94498b
                    Extra: Last beacon: 4068ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
srcversion:     1E6912E109D5A43B310FB34
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
echo "2" > /sys/class/backlight/acpi_video0/brightness
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=0f94c6bc-5417-40f6-8a53-b7de4f75ce38 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.232828] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.233270] audit: initializing netlink socket (disabled)
[    2.566599] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[   19.282594] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X
[   19.421105] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   19.421111] iwlwifi 0000:03:00.0: Falling back to user helper
[   19.443908] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   19.603283] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   19.663700] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   19.685366] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   19.685426] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   19.685654] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   19.914986] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   22.944975] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.128423] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   24.128670] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   24.139526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.140302] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.592693] wlan0: authenticate with <MAC C-06 CICC>
[   31.593673] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[   31.595363] wlan0: authenticated
[   31.597179] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[   31.601315] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=2)
[   31.604125] wlan0: associated
[   31.604152] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.632742] wlan0: authenticate with <MAC ID removed>
[   31.633701] wlan0: direct probe to <MAC ID removed> (try 1/3)
[   31.837828] wlan0: direct probe to <MAC ID removed> (try 2/3)
[   32.041958] wlan0: direct probe to <MAC ID removed> (try 3/3)
[   32.245569] wlan0: authentication with <MAC ID removed> timed out
[   36.052053] wlan0: authenticate with <MAC C-06 CICC>
[   36.053524] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[   36.057034] wlan0: authenticated
[   36.060057] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[   36.067430] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=2)
[   36.074244] wlan0: associated
[  223.672902] wlan0: deauthenticating from <MAC C-06 CICC> by local choice (reason=3)
[  227.455109] wlan0: authenticate with <MAC C-01 CICC-5>
[  227.456201] wlan0: direct probe to <MAC C-01 CICC-5> (try 1/3)
[  227.657903] wlan0: direct probe to <MAC C-01 CICC-5> (try 2/3)
[  227.861771] wlan0: send auth to <MAC C-01 CICC-5> (try 3/3)
[  227.862274] wlan0: authenticated
[  227.864904] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[  227.877989] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[  227.879037] wlan0: associated
[  420.565842] wlan0: authenticate with <MAC C-01 CICC-5>
[  420.567382] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[  420.581885] wlan0: authenticated
[  420.585486] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[  420.597907] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[  420.600713] wlan0: associated
[  570.978217] wlan0: authenticate with <MAC C-01 CICC-5>
[  570.979578] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[  570.980188] wlan0: authenticated
[  570.981045] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[  570.993391] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[  570.995034] wlan0: associated
[  971.301780] wlan0: deauthenticating from <MAC C-01 CICC-5> by local choice (reason=3)
[  975.048763] wlan0: authenticate with <MAC C-01 CICC-5>
[  975.049892] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[  975.050395] wlan0: authenticated
[  975.051458] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[  975.063835] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[  975.065238] wlan0: associated
[ 2078.706990] wlan0: deauthenticating from <MAC C-01 CICC-5> by local choice (reason=3)
[ 2082.455518] wlan0: authenticate with <MAC C-06 CICC>
[ 2082.456493] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 2082.458807] wlan0: authenticated
[ 2082.460893] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[ 2082.465109] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=2)
[ 2082.467778] wlan0: associated
[ 2408.936343] wlan0: authenticate with <MAC C-06 CICC>
[ 2408.937422] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 2408.939149] wlan0: authenticated
[ 2408.942211] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[ 2408.946442] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=1)
[ 2408.949175] wlan0: associated
[ 2455.814542] wlan0: deauthenticating from <MAC C-06 CICC> by local choice (reason=3)
[ 2459.566560] wlan0: authenticate with <MAC C-01 CICC-5>
[ 2459.567927] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 2459.580597] wlan0: authenticated
[ 2459.581100] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 2459.593511] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[ 2459.594976] wlan0: associated
[ 2484.399573] wlan0: deauthenticating from <MAC C-01 CICC-5> by local choice (reason=3)
[ 2486.619225] wlan0: authenticate with <MAC C-06 CICC>
[ 2486.620348] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 2486.622151] wlan0: authenticated
[ 2486.624099] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[ 2486.629614] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=1)
[ 2486.632673] wlan0: associated
[ 2575.749282] wlan0: deauthenticating from <MAC C-06 CICC> by local choice (reason=3)
[ 2579.497255] wlan0: authenticate with <MAC C-01 CICC-5>
[ 2579.498514] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 2579.498997] wlan0: authenticated
[ 2579.499476] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 2579.511980] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[ 2579.513784] wlan0: associated
[ 2648.626875] wlan0: deauthenticating from <MAC C-01 CICC-5> by local choice (reason=3)
[ 2653.464370] wlan0: authenticate with <MAC C-06 CICC>
[ 2653.465487] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 2653.468710] wlan0: authenticated
[ 2653.470317] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[ 2653.480010] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=1)
[ 2653.483011] wlan0: associated
[ 2694.139037] wlan0: deauthenticated from <MAC C-06 CICC> (Reason: 3)
[ 2697.958439] wlan0: authenticate with <MAC C-06 CICC>
[ 2697.959429] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 2698.022856] wlan0: send auth to <MAC C-06 CICC> (try 2/3)
[ 2698.086760] wlan0: send auth to <MAC C-06 CICC> (try 3/3)
[ 2698.161661] wlan0: authentication with <MAC C-06 CICC> timed out
[ 2709.989635] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2711.061768] wlan0: authenticate with <MAC C-01 CICC-5>
[ 2711.062932] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 2711.063718] wlan0: authenticated
[ 2711.067373] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 2711.079867] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[ 2711.081703] wlan0: associated
[ 2711.081747] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3044.003573] wlan0: authenticate with <MAC C-01 CICC-5>
[ 3044.004705] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 3044.005275] wlan0: authenticated
[ 3044.006287] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 3044.018627] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[ 3044.020169] wlan0: associated
[ 3498.548911] wlan0: deauthenticated from <MAC C-01 CICC-5> (Reason: 6)
[ 3498.568320] wlan0: authenticate with <MAC C-01 CICC-5>
[ 3498.569538] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 3498.570045] wlan0: authenticated
[ 3498.571660] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 3498.584516] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=2)
[ 3498.585885] wlan0: associated
[ 4314.380134] wlan0: deauthenticating from <MAC C-01 CICC-5> by local choice (reason=3)
[ 4318.139270] wlan0: authenticate with <MAC C-06 CICC>
[ 4318.140459] wlan0: direct probe to <MAC C-06 CICC> (try 1/3)
[ 4318.344033] wlan0: send auth to <MAC C-06 CICC> (try 2/3)
[ 4318.366604] wlan0: authenticated
[ 4318.367538] wlan0: associate with <MAC C-06 CICC> (try 1/3)
[ 4318.374856] wlan0: RX AssocResp from <MAC C-06 CICC> (capab=0x411 status=0 aid=2)
[ 4318.386022] wlan0: associated
[ 4517.481502] wlan0: deauthenticated from <MAC C-06 CICC> (Reason: 3)
[ 4521.301958] wlan0: authenticate with <MAC C-06 CICC>
[ 4521.303328] wlan0: send auth to <MAC C-06 CICC> (try 1/3)
[ 4521.350928] wlan0: send auth to <MAC C-06 CICC> (try 2/3)
[ 4521.414022] wlan0: send auth to <MAC C-06 CICC> (try 3/3)
[ 4521.475686] wlan0: authentication with <MAC C-06 CICC> timed out
[ 4533.082497] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4534.378364] wlan0: authenticate with <MAC C-01 CICC-5>
[ 4534.380020] wlan0: send auth to <MAC C-01 CICC-5> (try 1/3)
[ 4534.380546] wlan0: authenticated
[ 4534.381625] wlan0: associate with <MAC C-01 CICC-5> (try 1/3)
[ 4534.394138] wlan0: RX AssocResp from <MAC C-01 CICC-5> (capab=0x411 status=0 aid=1)
[ 4534.396125] wlan0: associated
[ 4534.396169] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========

```

---

### Post by mohammad9 on 2014-06-11
Hi guys I have same problem on Sony Vaio Pro 13. here's some info + the report. Any help is appreciated.I've read about patching the kernel with the backports and that it might help but don't know how to it!

---

### Post by varunendra on 2014-06-11
> **tony43 said:**
> What really helped was turning off the Power Management. my 2.4Gz connection is 100% solid now Thanks!
I usually stay on the 5gz freqeuncy but that still isn't working even after these changes.
We know that the iwlwifi driver still works better at 2.4 GHz band if working at 'N' speeds (above 54 Mbps) or higher. However, we (at least I) don't yet know the exact reason or a fix in case of problems with 5GHz. So if the connection with 2.4 GHz band is stable and good, I can only suggest to just stick with it and consider it solved for now. May be keep trying the 5GHz with each new kernel upgrade. Or, if the problem is serious, consider filing a bug report (or add yourself to one, if already exists) about 5 GHz band to make sure developers know it and can address the issue.

> **mohammad9 said:**
> Hi guys I have same problem on Sony Vaio Pro 13. here's some info + the report. Any help is appreciated.I've read about patching the kernel with the backports and that it might help but don't know how to it!

Welcome to the forums mohammad9!

Did you try the "sudo iwconfig wlan0 power off" command? The script report shows it to be "on", so please try that, and confirm if it helps or not. If it is automatically turning back to "on", we may try a few tricks to attempt fixing it.

**PS:**
For reference, may or may not be relevant, here is a finding a user *(metaphysician)* at IRC shared with us (I haven't yet found time to verify it, nor have made sure how may it affect wireless, if at all) -
> <metaphysician> In 14.04, there is a bug in /usr/lib/pm-utils/power.d/wireless script at line 23. It should "enabled" at the end of path /sys/class/net/$1/device/enable. Wireless power saving does not get applied
....
<metaphysician> where $1 is the interface

---

### Post by tony43 on 2014-06-12
Hey man,

Ya I appreciate the help!
The fact that I have an actual working connecton now I can be productive and probably find out more about this.

I tend ot use the 5ghz frequency in my appartment because the 2.4ghz has too much disturbance (I think) and owkrs on no other devices either. But for some reason it holds its strength with Linux. 
But I am good to go now.

Thank you.

---


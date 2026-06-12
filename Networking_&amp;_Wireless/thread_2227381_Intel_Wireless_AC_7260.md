---
title: "Intel Wireless AC 7260"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by rafael10 on 2014-06-01
Hello i recently installed ubunut and my wifi keeps droppin i dont know why, is there anyway to fix this if there can you please help me?

---

### Post by varunendra on 2014-06-01
Welcome to the forums rafael10 !

Please follow the instructions in this post to download and run wireless_script, and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

This report shall help us find and fix the problem with your wireless.

---

### Post by Vladlenin5000 on 2014-06-01
Hi, welcome.

Without other info little can be done...
There are already many topics in the specialized section - [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) -. Perhaps you should search for issues specific to your wifi device and OS version in the Networking & Wireless section and/or post there with informations about your hardware, namely the WiFi of course, and Ubuntu version and whether it is 32 or 64-bit.

---

### Post by rafael10 on 2014-06-01
```
#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etwork)[^[:punct:] ]*"

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
```

---

### Post by lisati on 2014-06-01
*Thread moved to **Networking & Wireless**.*
@rafael10: it looks like you've posted the contents of the script, and not the results.

---

### Post by varunendra on 2014-06-01
This is the script, not the report I expected. Please read the instructions carefully, as well as the prompts that appear on the terminal while running it.

And please use 'Code' tags to post the outputs. It preserves the formatting, and makes the post more readable. Please follow the "Use Code Tags" link in my signature to see how to use it. :)

---

### Post by rafael10 on 2014-06-01
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-27-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 12:22:18 up  1:22,  2 users,  load average: 0.10, 0.18, 0.39


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 017: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
4: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626511  1 iwlmvm
iwlwifi               169932  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-03 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-02 MyCharterWiFi71-2G>, Freq 2427 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ATTd8bhWuI:      Infra, <MAC C-05 ATTd8bhWuI>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    2WIRE132:        Infra, <MAC C-NA 2WIRE132 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR60:       Infra, <MAC C-NA NETGEAR60 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    2WIRE247:        Infra, <MAC C-NA 2WIRE247 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    NETGEAR95:       Infra, <MAC C-NA NETGEAR95 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    EFD:             Infra, <MAC C-NA EFD 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    NETGEAR63:       Infra, <MAC C-NA NETGEAR63 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    2WIRE435:        Infra, <MAC C-NA 2WIRE435 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    2WIRE497:        Infra, <MAC C-NA 2WIRE497 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    2WIRE973:        Infra, <MAC C-04 2WIRE973>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ATT7M4u6A2:      Infra, <MAC C-NA ATT7M4u6A2 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2

    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.369/1.387/1.405/0.018 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.373/2.135/2.898/0.763 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.043/0.051/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c045e4fa7
                    Extra: Last beacon: 64ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 MyCharterWiFi71-2G>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi71-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eb853c3050
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000af1f7593a2
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 2WIRE973>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE973"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b51af9181
                    Extra: Last beacon: 4220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 ATTd8bhWuI>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ATTd8bhWuI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c3661cf469
                    Extra: Last beacon: 4172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B09A94F74DCA60EBD06A6B6
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-27-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.687052] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.687381] audit: initializing netlink socket (disabled)
[    0.836005] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.512555] wmi: Mapper loaded
[    5.964458] asus_wmi: ASUS WMI generic driver loaded
[    5.976754] asus_wmi: Initialization: 0x1
[    5.976821] asus_wmi: BIOS WMI version: 7.9
[    5.976905] asus_wmi: SFUN value: 0x4a0877
[    5.977802] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[    5.994647] asus_wmi: Backlight controlled by ACPI video driver
[    6.163127] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[    6.454266] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    6.522191] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[    6.633411] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    6.633461] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    6.633677] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    6.924523] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.183670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.645103] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.645351] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.656564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.656833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.106694] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   19.242118] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   26.699345] wlan0: authenticate with <MAC C-01 belkin.986>
[   26.701482] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   26.710106] wlan0: authenticated
[   26.711043] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   26.720789] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[   26.726629] wlan0: associated
[   26.726658] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.916079] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[   27.967013] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   27.967228] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   27.978128] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.868064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.032851] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.033081] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.044800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.794590] wlan0: authenticate with <MAC C-01 belkin.986>
[   32.796155] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   32.798336] wlan0: authenticated
[   32.799740] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   32.805177] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[   32.807540] wlan0: associated
[   32.807559] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  807.060722] wlan0: authenticate with <MAC C-01 belkin.986>
[  807.062408] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  807.065057] wlan0: authenticated
[  807.068644] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  807.082888] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[  807.085473] wlan0: associated
[  814.368268] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[  814.425696] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  814.425928] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  814.437439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  814.717708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  818.154977] wlan0: authenticate with <MAC C-01 belkin.986>
[  818.156553] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  818.162662] wlan0: authenticated
[  818.168880] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  818.174721] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[  818.177689] wlan0: associated
[  818.177712] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  824.998805] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[  825.042996] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  825.043230] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  825.055601] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  825.397246] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  825.397481] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  825.410130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  827.772501] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  831.624760] wlan0: authenticate with <MAC C-01 belkin.986>
[  831.626322] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  831.628049] wlan0: authenticated
[  831.630649] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  831.634459] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[  831.636895] wlan0: associated
[  831.636924] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2167.325691] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2167.327292] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2167.329035] wlan0: authenticated
[ 2167.332221] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2167.336142] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2167.341125] wlan0: associated
[ 2170.713795] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2170.758597] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2170.758830] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2170.771822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2171.034012] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2174.484855] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2174.486414] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2174.488152] wlan0: authenticated
[ 2174.492201] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2174.498137] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2174.500641] wlan0: associated
[ 2174.500667] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2181.375372] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2181.415174] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2181.415408] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2181.428104] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2181.687061] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2181.780864] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2181.781085] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2181.794449] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2185.474466] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2185.475989] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2185.478571] wlan0: authenticated
[ 2185.482230] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2185.486043] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2185.488436] wlan0: associated
[ 2185.488460] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3308.474025] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3309.856066] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3309.856284] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3309.868142] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3309.922077] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3309.922306] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3309.934788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3310.328837] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3310.329052] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3310.340876] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3311.089524] (NULL device *): Direct firmware load failed with error -2
[ 3314.549699] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3314.549912] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3314.575576] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 3314.702535] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 3320.539818] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3320.541388] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3320.543090] wlan0: authenticated
[ 3320.546638] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3320.550499] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3320.552917] wlan0: associated
[ 3320.552947] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3320.761492] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3320.800008] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3320.800227] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3320.811516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3321.061568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3321.109980] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3321.110199] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3321.121759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3324.785453] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3324.786955] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3324.788713] wlan0: authenticated
[ 3324.792296] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3324.796154] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3324.798612] wlan0: associated
[ 3324.798638] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3659.370640] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3659.372510] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3659.374363] wlan0: authenticated
[ 3659.375453] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3659.379339] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3659.385174] wlan0: associated
[ 3661.750838] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3661.791303] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3661.791525] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3661.803846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3662.083335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3669.275985] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3669.277607] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3669.279287] wlan0: authenticated
[ 3669.280936] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3669.284843] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3669.287326] wlan0: associated
[ 3669.287350] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3669.303627] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 3669.307071] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3669.308515] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3669.601769] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3669.601989] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3669.614769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3669.978589] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3669.978804] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3669.991200] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3687.684299] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3687.686053] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3687.687844] wlan0: authenticated
[ 3687.689408] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3687.693359] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3687.696072] wlan0: associated
[ 3687.696131] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3687.706809] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 3687.710226] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3687.711774] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3687.717073] wlan0: authenticated
[ 3687.721355] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3687.725218] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 3687.729581] wlan0: associated

    ======== Done ========
```

---

### Post by rafael10 on 2014-06-01
in installed the wicd network manager to see if it would fix it but it didnt

---

### Post by rafael10 on 2014-06-01
it got worst when i installed wicd network manager

---

### Post by rafael10 on 2014-06-01
[COLOR=#ff0000]if anyone could help me fix this i would greatly appreciate it,, im getting annoyed of it diconecting and reconnecting[/COLOR].

---

### Post by varunendra on 2014-06-01
Please do not bump the thread in less than 24 hrs unless there is a real good reason. Other peoples' threads deserve the same level of attention as yours does.

For the problem, please try this -

[INDENT]**1)** In your router, change the encryption type from WPA/WPA2 mixed mode to pure **WPA2-PSK with AES (CCMP)**. Avoid the mixed mode and TKIP.

**2)** In Ubuntu, please open a terminal, and run the following command -
```
sudo iwconfig wlan0 power off
```[/INDENT]

Do these changes fix the problem? Or at least make the stability any better? Keep watching every 10-20 minutes the output of -
```
iwconfig
```
..and make sure "Power Management" in the output remains "off". If it turns "on" automatically after sometime, the connection may suffer again and we'll need to make it permanently "off" using other ways.

---

### Post by rafael10 on 2014-06-02
sorry for bumping the thread and is there anyway i could remove wicd network manager and install the default one??

---

### Post by varunendra on 2014-06-02
> **rafael10 said:**
> is there anyway i could remove wicd network manager and install the default one??

Sure. While being connected to internet via any means, please run the following commands in a terminal -
```
sudo apt-get install network-manager-gnome
sudo apt-get purge wicd
```
The first command will install the default network manager, the second one will purge (completely remove) wicd, so they don't conflict with each other. The sequence of commands is important.

---

### Post by rafael10 on 2014-06-02
power management came back online

---

### Post by varunendra on 2014-06-03
And the problem too? If yes, please try -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
sudo iwconfig wlan0 power off
```
Then reboot and check the output of "iwconfig" again to see if the power management remains off. If it turns back on, try -
```
sudo touch /etc/pm/power.d/wireless
sudo iwconfig wlan0 power off
```
Does it remain off now? Only one of the above two tricks should be sufficient to keep it off. We need to determine which one. If none of these can keep it off, we may have only one more trick left, but let's try the above two first.

---

### Post by rafael10 on 2014-06-04
i still get kicked offline from time to time

---

### Post by varunendra on 2014-06-04
And does 'Power Management' (in the output of 'iwconfig') also turn "on" ? If yes, please try this -
```
echo "iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
sudo iwconfig wlan0 power off
```
Then see if we have any more stability. If not, please post a fresh report of the 'wireless_script' you used earlier.

---

### Post by rafael10 on 2014-06-05
```
########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux Alpha 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
	Kernel driver in use: iwlwifi


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 015: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
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


wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=135 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:137   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [belkin.986] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           121 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    2WIRE951:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 47 WPA2
    2WIRE000:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    NETGEAR63:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    2WIRE497:        Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    ATTd8bhWuI:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR60:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    NETGEAR95:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    2WIRE973:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE771:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ATT7gCM46a:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *belkin.986:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2


  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005c10f679e
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A62656C6B696E2E393836
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050300000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA50050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F08863B2AA9861021001442656C6B696E20496E7465726E6174696F6E616C102300144E31353020576972656C65737320526F757465721024000746394B313030311042000E32303131323147313131353737391054000800060050F20400011011001B42656C6B696E204E31353020576972656C65737320526F75746572100800020086
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi71-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005bf937180
                    Extra: Last beacon: 4720ms ago
                    IE: Unknown: 00124D79436861727465725769466937312D3247
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403001900000000000000000000000000000000000000
                    IE: Unknown: 3D1603001900000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f3cab767fe
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00083257495245393531
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
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
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR60"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005bd0e6a10
                    Extra: Last beacon: 19624ms ago
                    IE: Unknown: 00094E4554474541523630
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B0001031047001032839F6D36D254F39896008EF2FD086B102100044E54475210230008574E4452343330301024000256311042000C3030386566326664303836621054000800060050F204000110110015574E44523433303028576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 05 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"2WIRE000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005bffaf8bb
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00083257495245303030
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
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
          Current Frequency:2.412 GHz (Channel 1)


##### lsmod #####


iwlmvm                189774  0 
mac80211              626511  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm


##### modinfo #####


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.903256] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   13.269363] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   13.502755] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   13.502756] iwlwifi 0000:03:00.0: Falling back to user helper
[   13.526346] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   13.539590] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   13.539637] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.539849] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.772166] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   20.322488] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.322727] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.334750] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.335045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.351815] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   21.492780] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   29.688237] wlan0: authenticate with <MAC address removed>
[   29.689152] wlan0: send auth to <MAC address removed> (try 1/3)
[   29.766644] wlan0: send auth to <MAC address removed> (try 2/3)
[   29.768490] wlan0: authenticated
[   29.769561] wlan0: associate with <MAC address removed> (try 1/3)
[   29.860874] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   29.863354] wlan0: associated
[   29.863379] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.009477] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   30.058866] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.059085] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.070789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.351327] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.384527] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.384760] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.395927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.193142] wlan0: authenticate with <MAC address removed>
[   34.193774] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.195509] wlan0: authenticated
[   34.199012] wlan0: associate with <MAC address removed> (try 1/3)
[   34.202861] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   34.205971] wlan0: associated
[   34.206001] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  828.730025] wlan0: authenticate with <MAC address removed>
[  828.730795] wlan0: send auth to <MAC address removed> (try 1/3)
[  828.733652] wlan0: authenticated
[  828.735289] wlan0: associate with <MAC address removed> (try 1/3)
[  828.746364] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  828.776815] wlan0: associated
[  829.039744] iwlwifi 0000:03:00.0: Time Event end notification failure
[  836.550235] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  836.588072] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  836.588293] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  836.599445] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  836.869957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  840.336443] wlan0: authenticate with <MAC address removed>
[  840.337599] wlan0: send auth to <MAC address removed> (try 1/3)
[  840.339323] wlan0: authenticated
[  840.340822] wlan0: associate with <MAC address removed> (try 1/3)
[  840.344853] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  840.347077] wlan0: associated
[  840.347114] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1171.127842] wlan0: authenticate with <MAC address removed>
[ 1171.128717] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1171.131028] wlan0: authenticated
[ 1171.135050] wlan0: associate with <MAC address removed> (try 1/3)
[ 1171.138930] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1171.141973] wlan0: associated
[ 1204.493120] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1204.634728] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 1207.026920] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 1207.028483] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1207.028702] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1207.039607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1207.409309] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1207.409537] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1207.421532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1214.835396] wlan0: authenticate with <MAC address removed>
[ 1214.836333] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1214.838042] wlan0: authenticated
[ 1214.838742] wlan0: associate with <MAC address removed> (try 1/3)
[ 1214.842615] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1214.845028] wlan0: associated
[ 1214.845056] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1214.855201] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1214.856596] wlan0: authenticate with <MAC address removed>
[ 1214.857148] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1214.858839] wlan0: authenticated
[ 1214.862803] wlan0: associate with <MAC address removed> (try 1/3)
[ 1214.869179] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1214.871649] wlan0: associated
[ 1224.840259] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1224.890012] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1224.890230] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1224.901301] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1225.176002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1225.272483] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1225.272699] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1225.284414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1228.980205] wlan0: authenticate with <MAC address removed>
[ 1228.981156] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1228.982900] wlan0: authenticated
[ 1228.986857] wlan0: associate with <MAC address removed> (try 1/3)
[ 1228.992584] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 1228.995203] wlan0: associated
[ 1228.995230] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2905.463875] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2905.464111] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2905.475214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2905.783650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2913.051393] wlan0: authenticate with <MAC address removed>
[ 2913.053524] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2913.055277] wlan0: authenticated
[ 2913.059131] wlan0: associate with <MAC address removed> (try 1/3)
[ 2913.064818] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2913.070123] wlan0: associated
[ 2913.070189] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2913.086967] wlan0: authenticate with <MAC address removed>
[ 2913.088674] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2913.092790] wlan0: authenticated
[ 2913.092928] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2913.092931] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2913.095165] wlan0: associate with <MAC address removed> (try 1/3)
[ 2913.097139] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[ 2913.098149] wlan0: associated
[ 2913.538232] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2913.581785] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2913.582007] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2913.593304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2913.946671] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2913.946888] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2913.958117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2931.525084] wlan0: authenticate with <MAC address removed>
[ 2931.526174] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2931.527873] wlan0: authenticated
[ 2931.528862] wlan0: associate with <MAC address removed> (try 1/3)
[ 2931.532757] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2931.535387] wlan0: associated
[ 2931.535463] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2931.547063] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 2931.548455] wlan0: authenticate with <MAC address removed>
[ 2931.549048] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2931.550754] wlan0: authenticated
[ 2931.554045] wlan0: associate with <MAC address removed> (try 1/3)
[ 2931.558462] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[ 2931.560895] wlan0: associated


########## wireless info END ############
```

---

### Post by varunendra on 2014-06-05
Since it is connected in the above report, there may be clues that don't exist in it, but would appear only when the connection fails. When it gets disconnected, does the 'Power Management' appear to be turned "on" in 'iwconfig' output?

You can try this in Ubuntu -
```
echo "options iwlwifi bt_coex_active=N" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
This will disable a driver feature that modifies the signal when bluetooth and wifi are enabled simultaneously. This modification may sometimes cause problems, although I'm not sure if it has improved in current versions or not.

Another thing to check in the router/access-point is a feature called 'WMM'. It is usually located under 'QoS' settings in the router, and is known to cause disconnection or slow speed problems sometimes. So if it exists in your router, make sure it is disabled.

If these don't help, next time when it disconnects, please run the script that I mentioned in post #2 (I always like to see more info, not the limited ones), and post the report of that one.

---

### Post by rafael10 on 2014-06-08
```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux Alpha 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
	Kernel driver in use: iwlwifi


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 013: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
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


wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC address removed>   
          Bit Rate=135 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [belkin.986] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    2WIRE951:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    2WIRE497:        Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    NETGEAR95:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    NETGEAR63:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    NETGEAR60:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    ATTd8bhWuI:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WPA2
    2WIRE000:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    2WIRE132:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    EFD:             Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
    2WIRE648:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    *belkin.986:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 62 WPA2


  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001fb549110b
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A62656C6B696E2E393836
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602050300000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA50050F204104A0001101044000102103B00010310470010775B6680BFDE11D38D2F08863B2AA9861021001442656C6B696E20496E7465726E6174696F6E616C102300144E31353020576972656C65737320526F757465721024000746394B313030311042000E32303131323147313131353737391054000800060050F20400011011001B42656C6B696E204E31353020576972656C65737320526F75746572100800020086
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402050300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004eb903e183
                    Extra: Last beacon: 4740ms ago
                    IE: Unknown: 00094E4554474541523633
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700100EB8191946AC6C9DE95C15C5786CBAD9103C0001031049000600372A000120
                    IE: Unknown: DD090010180208001C0000
                    IE: Unknown: DD180050F2020101880003A4000027A400004243BC0062326600
          Cell 03 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"2WIRE000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004eb6c03181
                    Extra: Last beacon: 4564ms ago
                    IE: Unknown: 00083257495245303030
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013cc1c8228f
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00083257495245393531
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
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
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ATTd8bhWuI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004eb8b7ffd5
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A41545464386268577549
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d60776bf0
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00094E4554474541523935
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010CDF8753B6A035F5DA79A4494FC717FAD102100044E54475210230008574E4452343330301024000256311042000C3434393466633731376661641054000800060050F204000110110015574E44523433303028576972656C65737320415029100800022008103C0001011049000600372A000120


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
          Current Frequency:2.417 GHz (Channel 2)


##### lsmod #####


iwlmvm                189774  0 
mac80211              626511  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm


##### modinfo #####


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    1.937298] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   13.499587] iwlwifi 0000:03:00.0: irq 62 for MSI/MSI-X
[   13.603519] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   13.603523] iwlwifi 0000:03:00.0: Falling back to user helper
[   13.693707] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   13.707077] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   13.707127] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.707342] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   13.928425] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   16.981026] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.981242] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.992186] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.992622] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.165716] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   17.280232] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   20.723506] wlan0: authenticate with <MAC address removed>
[   20.724348] wlan0: send auth to <MAC address removed> (try 1/3)
[   20.727347] wlan0: authenticated
[   20.730405] wlan0: associate with <MAC address removed> (try 1/3)
[   20.738177] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   20.741991] wlan0: associated
[   20.742015] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.021188] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   29.053491] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.053707] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.065549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.340453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.360593] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.360800] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   29.372343] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.150517] wlan0: authenticate with <MAC address removed>
[   33.151183] wlan0: send auth to <MAC address removed> (try 1/3)
[   33.157108] wlan0: authenticated
[   33.159481] wlan0: associate with <MAC address removed> (try 1/3)
[   33.188112] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   33.190674] wlan0: associated
[   33.190702] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1015.138906] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1015.139123] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1015.150148] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1015.443499] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1019.339445] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1019.339667] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1019.350799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1019.717012] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1019.717228] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1019.728016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1037.151193] wlan0: authenticate with <MAC address removed>
[ 1037.152816] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1037.155392] wlan0: authenticated
[ 1037.156531] wlan0: associate with <MAC address removed> (try 1/3)
[ 1037.160446] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1037.163502] wlan0: associated
[ 1037.163529] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1037.173966] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1037.176615] wlan0: authenticate with <MAC address removed>
[ 1037.177718] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1037.180318] wlan0: authenticated
[ 1037.184510] wlan0: associate with <MAC address removed> (try 1/3)
[ 1037.190078] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 1037.192613] wlan0: associated
[ 4046.522625] wlan0: authenticate with <MAC address removed>
[ 4046.523382] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4046.526258] wlan0: authenticated
[ 4046.528823] wlan0: associate with <MAC address removed> (try 1/3)
[ 4046.542205] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4046.545905] wlan0: associated
[ 4054.267059] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4054.267277] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4054.278134] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4054.559271] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4061.800262] wlan0: authenticate with <MAC address removed>
[ 4061.801260] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4061.802981] wlan0: authenticated
[ 4061.804379] wlan0: associate with <MAC address removed> (try 1/3)
[ 4061.809846] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4061.810465] wlan0: associated
[ 4061.810493] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4061.821145] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 4061.827936] wlan0: authenticate with <MAC address removed>
[ 4061.828531] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4062.135329] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 4062.135345] wlan0: Connection to AP <MAC address removed> lost
[ 4065.787390] wlan0: authenticated
[ 4065.790169] wlan0: associate with <MAC address removed> (try 1/3)
[ 4065.795151] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4065.797094] wlan0: associated
[ 4066.234412] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4066.278838] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4066.279061] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4066.290128] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4066.640479] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4066.640695] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4066.653312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4067.145855] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4070.853620] wlan0: authenticate with <MAC address removed>
[ 4070.854377] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4070.856095] wlan0: authenticated
[ 4070.859258] wlan0: associate with <MAC address removed> (try 1/3)
[ 4070.863120] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 4070.865556] wlan0: associated
[ 4070.865579] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

### Post by rafael10 on 2014-06-10
its still disconnecting me

---

### Post by varunendra on 2014-06-11
I may not be able to help anyway, because I would almost certainly be short of time throughout this month, but you have posted the results of the old script again. Please read **[This Post]("http://ubuntuforums.org/showpost.php?p=13024222")** VERY CAREFULLY, and post back the report of the new script mentioned there.

The more info that script would present would give you better chance of getting proper help.

---

### Post by rafael10 on 2014-06-12
the script i posted was a new one i didnt copy the old one 

```
loggikwolf@Alpha:~$ sudo lshw -C network  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: bc:ee:7b:2e:23:52
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:61 ioport:e000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 6b
       serial: fc:f8:ae:7c:67:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-27-generic firmware=22.1.7.0 ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:63 memory:f7c00000-f7c01fff
```

---

### Post by varunendra on 2014-06-12
> **rafael10 said:**
> the script i posted was a new one i didnt copy the old one 
You posted this -
> **rafael10 said:**
> ```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux Alpha 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####
....
....
```

While the report generated by the new script looks like this : [http://ubuntuforums.org/showpost.php?p=13044737](http://ubuntuforums.org/showpost.php?p=13044737)

Can you notice the difference in the report's layout and style? If yes, please re-read the post I linked to, to know where the difference comes from. :)

---

### Post by rafael10 on 2014-06-12
i do notice the diffrence between the 2 post but when ever i do a wireless script mine dont come out like that

---

### Post by rafael10 on 2014-06-12
whenever i run the command to get the script i get this ```
loggikwolf@Alpha:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-06-12 17:07:36--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 54.235.138.14
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.138.14|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-06-12 17:07:36--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.23.104.199, 54.225.68.143, 54.235.166.243, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.23.104.199|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4352 (4.2K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-06-12 17:07:37--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Reusing existing connection to dl.dropboxusercontent.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 4352 (4.2K) [text/plain]
Saving to: &#8216;wireless_script&#8217;

100%[======================================>] 4,352       --.-K/s   in 0s      

2014-06-12 17:07:37 (290 MB/s) - &#8216;wireless_script&#8217; saved [4352/4352]

[sudo] password for loggikwolf: 
[sudo] password for loggikwolf: 

Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.
```

---

### Post by varunendra on 2014-06-14
> **rafael10 said:**
> whenever i run the command to get the script i get this ```
loggikwolf@Alpha:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/**[COLOR="#FF0000"]u/57264241[/COLOR]**/wireless_script && chmod +x wireless_script && ./wireless_script
....
```

You are not using the command suggested in the post I linked to. The one you are using downloads and runs the older script. For newer one, the command is -
```
wget -N -t 5 -T 10 https://dl.dropbox.com/**[COLOR="#0000CD"]s/qjc87hzk1z5x6z0[/COLOR]**/wireless_script && chmod +x wireless_script && ./wireless_script
```
Not that it is guaranteed to get your problem solved, but I am wondering if you even read the post a second time.

---

### Post by rafael10 on 2014-06-14
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 17:58:49 up 39 min,  2 users,  load average: 2.27, 1.79, 1.39


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 028: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=120 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:58  Invalid misc:8798   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: phy0: Wireless LAN             no            no
1: asus-wlan: Wireless LAN        no            no
2: asus-bluetooth: Bluetooth      no            no
3: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
video                  19476  2 i915,asus_wmi
wmi                    19177  1 asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 120 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-04 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-03 MyCharterWiFi71-2G>, Freq 2427 MHz, Rate 54 Mb/s, Strength 45 WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    ATTd8bhWuI:      Infra, <MAC C-06 ATTd8bhWuI>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR63:       Infra, <MAC C-02 NETGEAR63>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    2WIRE132:        Infra, <MAC C-NA 2WIRE132 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR95:       Infra, <MAC C-08 NETGEAR95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    2WIRE648:        Infra, <MAC C-07 2WIRE648>, Freq 2457 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.009/2.154/3.299/1.145 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.043/0.045/0.048/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017ffe9aa3b
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 NETGEAR63>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb4d8086e6
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 MyCharterWiFi71-2G>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi71-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb4b2c3344
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b95627e3e6
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 NETGEAR60>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR60"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb66efa869
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 ATTd8bhWuI>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ATTd8bhWuI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb4d46ebaa
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 2WIRE648>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE648"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001055b7f1
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 NETGEAR95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca077eb32b
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlmvm.conf       : sudo tee /etc/modprobe.d/iwlmvm.conf
                    sudo iwconfig wlan0 power off
                    iwconfig
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.694686] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.695016] audit: initializing netlink socket (disabled)
[    1.841800] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.785053] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   26.903807] wmi: Mapper loaded
[   26.971353] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   27.048142] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   27.048146] iwlwifi 0000:03:00.0: Falling back to user helper
[   27.244571] asus_wmi: ASUS WMI generic driver loaded
[   27.246014] asus_wmi: Initialization: 0x1
[   27.246058] asus_wmi: BIOS WMI version: 7.9
[   27.246110] asus_wmi: SFUN value: 0x4a0877
[   27.247077] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   27.346479] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   27.358580] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   27.358628] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   27.358841] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   27.577181] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   27.752005] asus_wmi: Backlight controlled by ACPI video driver
[   28.730614] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   28.832057] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   29.935079] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.840935] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.841168] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   30.851828] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.852045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.221653] wlan0: authenticate with <MAC C-01 belkin.986>
[   38.222832] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   38.224543] wlan0: authenticated
[   38.225050] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   38.230952] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[   38.233586] wlan0: associated
[   38.233607] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.252783] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[   38.254242] wlan0: authenticate with <MAC C-01 belkin.986>
[   38.254817] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   38.257155] wlan0: authenticated
[   38.261024] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   38.266885] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[   38.269651] wlan0: associated

    ======== Done ========
```

---

### Post by varunendra on 2014-06-15
The contents of 'iwlmvm.conf' file are all wrong -
> **rafael10 said:**
> ```
[/etc/modprobe.d]
**iwlmvm.conf       :** [COLOR="#FF0000"]sudo tee /etc/modprobe.d/iwlmvm.conf
                    sudo iwconfig wlan0 power off
                    iwconfig[/COLOR]
```
Not sure if you put that content there manually or some kind of mistake in executing commands did it, but let's try correcting it to what needs to be in the file.

Please run this command (the whole line at once, you may copy-paste it to avoid any typing mistake) in a terminal -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
Then reboot and see if the connection is stable now. If not, please post back a freshly generated report to confirm if the change was applied correctly this time.

We may have only one or two more shots to try after this. But if the above change did the trick, most of the other suggestions I offered later may not be needed at all.

---

### Post by rafael10 on 2014-06-15
its still kicking me offline ```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 11:11:18 up  2:17,  2 users,  load average: 1.66, 1.52, 1.50


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 014: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=150 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:521   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
3: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 120 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-02 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    NETGEAR63:       Infra, <MAC C-06 NETGEAR63>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2
    2WIRE132:        Infra, <MAC C-04 2WIRE132>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    ATTd8bhWuI:      Infra, <MAC C-03 ATTd8bhWuI>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    2WIRE648:        Infra, <MAC C-NA 2WIRE648 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE497:        Infra, <MAC C-NA 2WIRE497 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA2
    NETGEAR95:       Infra, <MAC C-05 NETGEAR95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2

    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 52.336/89.614/126.893/37.279 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.052/121.336/240.620/119.284 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.024/0.034/0.045/0.012 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000266c59c025
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c7c29735ec
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 ATTd8bhWuI>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ATTd8bhWuI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9b8bda47e
                    Extra: Last beacon: 17032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 2WIRE132>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE132"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000018be6fa44d81
                    Extra: Last beacon: 4360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 NETGEAR95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d8751649ed
                    Extra: Last beacon: 17032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 NETGEAR63>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9b9f54a69
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.694623] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.694959] audit: initializing netlink socket (disabled)
[    0.847669] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.915697] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   11.265234] wmi: Mapper loaded
[   11.310108] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   11.439215] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   11.439219] iwlwifi 0000:03:00.0: Falling back to user helper
[   11.444612] asus_wmi: ASUS WMI generic driver loaded
[   11.445811] asus_wmi: Initialization: 0x1
[   11.445840] asus_wmi: BIOS WMI version: 7.9
[   11.445871] asus_wmi: SFUN value: 0x4a0877
[   11.446689] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[   11.466301] asus_wmi: Backlight controlled by ACPI video driver
[   11.515867] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   11.533457] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   11.533505] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.533720] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.751367] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   14.015003] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.676869] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   14.788686] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   15.321456] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.321688] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.332492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.332783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.040290] wlan0: authenticate with <MAC C-01 belkin.986>
[   19.041122] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   19.042805] wlan0: authenticated
[   19.043506] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   19.047371] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[   19.049830] wlan0: associated
[   19.049853] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4131.237718] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4131.237950] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4131.249423] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4131.552334] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4135.349143] wlan0: authenticate with <MAC C-01 belkin.986>
[ 4135.349826] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 4135.351533] wlan0: authenticated
[ 4135.352154] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 4135.359773] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 4135.362160] wlan0: associated
[ 4135.362195] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4141.346305] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 4141.390749] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4141.390979] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4141.402553] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4141.708717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4141.780095] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4141.780311] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4141.791342] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4142.113267] init: network-manager main process (793) killed by SEGV signal
[ 4142.113313] init: network-manager main process ended, respawning
[ 4145.904863] wlan0: authenticate with <MAC C-01 belkin.986>
[ 4145.905586] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 4145.907264] wlan0: authenticated
[ 4145.910257] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 4145.914096] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 4145.916609] wlan0: associated
[ 4145.916642] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7421.768556] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7421.916944] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 7424.507922] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 7424.509431] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7424.509654] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7424.520649] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7426.196226] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7426.196606] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7426.207705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7433.717028] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7433.717938] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7433.719653] wlan0: authenticated
[ 7433.721228] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7433.725158] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 7433.727618] wlan0: associated
[ 7433.727667] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7433.738578] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 7433.740988] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7433.743665] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7433.745373] wlan0: authenticated
[ 7433.749235] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7433.753202] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 7433.757938] wlan0: associated
[ 7440.878164] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7440.935900] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7440.936207] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7440.947129] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7441.249147] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7441.328845] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7441.329070] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7441.340143] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7441.556979] init: network-manager main process (7835) killed by SEGV signal
[ 7441.556999] init: network-manager main process ended, respawning
[ 7445.038166] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7445.038925] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7445.040642] wlan0: authenticated
[ 7445.042828] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7445.047768] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 7445.052218] wlan0: associated
[ 7445.052228] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8171.703543] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8171.703780] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8171.715585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8171.987992] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8179.290812] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8179.292619] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8179.294846] wlan0: authenticated
[ 8179.296186] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8179.302172] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8179.303960] wlan0: associated
[ 8179.304005] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8179.315247] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 8179.316411] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8179.317090] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8179.623888] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8179.623911] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8183.275968] wlan0: authenticated
[ 8183.278753] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8183.288214] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8183.290912] wlan0: associated
[ 8183.656332] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 8183.709045] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8183.709350] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8183.720730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8184.034247] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8184.177308] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8184.177758] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8184.189117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8187.892157] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8187.892918] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8187.895160] wlan0: authenticated
[ 8187.899460] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8187.903707] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8187.906335] wlan0: associated
[ 8187.906369] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by varunendra on 2014-06-15
Are you manually killing network-manager process as displayed here or is it happening automatically -
> **rafael10 said:**
> ```
[ 4142.113267] init: [COLOR="#FF0000"]network-manager main process (793) killed by SEGV signal[/COLOR]
[ 4142.113313] init: network-manager main process ended, respawning
....<snip>....
[ 7421.916944] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 7424.507922] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
....
[ 7433.757938] wlan0: associated
[ 7440.878164] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
....
[ 7441.556979] init: network-manager main process (7835) killed by SEGV signal
[ 7441.556999] init: network-manager main process ended, respawning
....
[ 8179.303960] wlan0: associated
[ 8179.304005] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8179.315247] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 8179.316411] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8179.317090] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8179.623888] iwlwifi 0000:03:00.0: **No association and the time event is over already...**
[ 8179.623911] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8183.275968] wlan0: authenticated
....
```

If happening automatically, I wonder if the culprit is the firmware that the driver is trying to use -
```
[   11.310108] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   11.439215] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   11.439219] iwlwifi 0000:03:00.0: Falling back to user helper
```
I know there is a quiet confusing progress going on at the firmware development part of the Intel AC 7260 cards, and only some particular combinations of the driver+firmware work smoothly.

I am not yet sure (others who are more consistent on the forums than me may know better) which combination is best for your kernel version, so let's try our remaining shots on the regular tricks first, and start fiddling with driver/firmware versions later if regular shots don't work.

[INDENT]**1)** Please try -
```
sudo sed -i '/options/ s/.*/& swcrypto=1 11n_disable=1/' /etc/modprobe.d/iwlwifi.conf
```
This will change the line *"options iwlwifi bt_coex_active=N"* to *"options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1"* in the /etc/modprobe.d/iwlwifi.conf file. The "11n_disable=1" parameter will disable the 'N' speeds, limiting the speed to 54 Mbps, but that is just to see if the limited speed can help stabilizing the connection. We can later choose to remove that parameter to return to full speed again, depending on whether it helps or whether the compromise is acceptable or not.

**2)** Set "IPv6" from "auto" to "Ignore" for the wireless connection in Network Manager.

**3)** In the router, if the channel bandwidth is set to 20/40 MHz auto mode, set it to 20 MHz only mode. Of course reboot the router after saving the change, and also reboot the notebook if required.

**4)** Run the following commands to update the firmware pack -
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-firmware
```[/INDENT]

For now, please try the above and post back the result, as well as the outputs of -
```
sudo lshw -C network | grep firmware
ls -1 /lib/firmware/iwl*7260*
```

---

### Post by rafael10 on 2014-06-17
it worked fine for one day but i started getting disconnected again today ```
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.1.7.0 ip=192.168.2.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
```

---

### Post by varunendra on 2014-06-18
> **rafael10 said:**
> ....```
.. **firmware=22.[COLOR="#FF0000"]1.7.0[/COLOR]** ..
```

As per [Intel Linux Support page]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm"), the firmware version for kernels 3.13+ should be newer than what you have. Please download it from here (direct download link copied from the same support page) : [http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.15.8.0.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-7260-ucode-22.15.8.0.tgz)

Then replace the current firmware with this new one as follows :

[INDENT]**1)** Copy the downloaded file onto your Desktop > Right-click > Extract here

**2)** Open a terminal (Ctrl-Alt-T) and run the following commands in it to backup the current firmware, and copy the new one -
```
sudo mv /lib/firmware/iwlwifi-7260-7.ucode iwlwifi-7260-7.ucode.bak
cd Desktop/iwlwifi-7260-ucode-22.15.8.0
sudo cp iwl* /lib/firmware/iwlwifi-7260-7.ucode
```[/INDENT]

Reboot the system after copying the file, test connectivity and let us know the outcome. If the error persists, please post back a fresh wireless_script report, plus the following outputs -
```
sudo lshw -C network | grep firmware
ls -l /lib/firmware/iwlwifi-7260*
```

---

### Post by rafael10 on 2014-06-18
i dont know if i did something wrong but its not letting me connect to any network not even ethenet.

ok this is what i did i downloaded the new firmware frome the link you gave me and extracted it on my desktop, then right after i did that i ran the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mv /lib/firmware/iwlwifi-7260-7.ucode iwlwifi-7260-7.ucode.bak[/FONT][/COLOR]cd Desktop/iwlwifi-7260-ucode-22.15.8.0
sudo cp iwl* /lib/firmware/iwlwifi-7260-7.ucode
```and after that i rebooted and once it came back up it didnt let me connect to anything your instructions say something about copy the new firmware i dont know where tho. or is it cause i ran all those commands u posted at once

---

### Post by varunendra on 2014-06-19
> **rafael10 said:**
> or is it cause i ran all those commands u posted at once

Could be. Suggested commands should always be run one at a time > let it complete > run the next one. For now, please post the wireless_script report, plus the output of commands I asked so we know where we are currently. Blindly repeating the process may further confuse the situation.

Also check your Home directory. If there is a file named 'iwlwifi-7260-7.ucode.bak', keep it in some safe location (in another directory or flash drive etc.), so we can easily restore it if required. If there is no such file there, most probably you have overwritten it with the new one. The report + command outputs I asked above should make the picture clearer.

---

### Post by rafael10 on 2014-06-19
ok i ran those commands one by one again and i did the new wireless script ```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 15:23:49 up 1 min,  2 users,  load average: 0.87, 0.41, 0.15




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 025: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 005: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 026: ID 154b:0048 PNY 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abg  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-NA *belkin.986 1>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
3: hci0: Bluetooth                no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=1 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    2WIRE951:        Infra, <MAC C-NA 2WIRE951 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-NA MyCharterWiFi71-2G 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA2
    NETGEAR63:       Infra, <MAC C-NA NETGEAR63 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE132:        Infra, <MAC C-NA 2WIRE132 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR60:       Infra, <MAC C-NA NETGEAR60 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    EFD:             Infra, <MAC C-NA EFD 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    2WIRE247:        Infra, <MAC C-NA 2WIRE247 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ATTd8bhWuI:      Infra, <MAC C-NA ATTd8bhWuI 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *belkin.986:     Infra, <MAC C-NA *belkin.986 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 73 WPA2
    2WIRE497:        Infra, <MAC C-NA 2WIRE497 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2


    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------




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


belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.062/1.107/1.153/0.056 ms


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.022/99.238/197.454/98.216 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.030/0.034/0.039/0.007 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
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


          Current Frequency:2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.698625] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.698957] audit: initializing netlink socket (disabled)
[    1.330640] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.305004] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   41.538755] wmi: Mapper loaded
[   41.576457] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   41.720723] asus_wmi: ASUS WMI generic driver loaded
[   41.722220] asus_wmi: Initialization: 0x1
[   41.722264] asus_wmi: BIOS WMI version: 7.9
[   41.722316] asus_wmi: SFUN value: 0x4a0877
[   41.723795] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   41.748120] asus_wmi: Backlight controlled by ACPI video driver
[   41.767414] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   41.767415] iwlwifi 0000:03:00.0: Falling back to user helper
[   41.846534] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   41.859010] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   41.859058] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   41.859274] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   42.066712] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   44.027486] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.246562] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   45.246778] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   45.258216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.258571] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.869221] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   46.983881] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   55.676589] wlan0: authenticate with <MAC C-NA *belkin.986 1>
[   55.678110] wlan0: send auth to <MAC C-NA *belkin.986 1> (try 1/3)
[   55.680007] wlan0: authenticated
[   55.683284] wlan0: associate with <MAC C-NA *belkin.986 1> (try 1/3)
[   55.685997] wlan0: RX AssocResp from <MAC C-NA *belkin.986 1> (capab=0x411 status=0 aid=4)
[   55.689844] wlan0: associated
[   55.689868] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.154695] wlan0: deauthenticating from <MAC C-NA *belkin.986 1> by local choice (reason=3)
[   56.186699] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   56.186935] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   56.198013] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.504975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.537698] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   56.537917] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   56.548877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.330646] wlan0: authenticate with <MAC C-NA *belkin.986 1>
[   60.331252] wlan0: send auth to <MAC C-NA *belkin.986 1> (try 1/3)
[   60.332940] wlan0: authenticated
[   60.336619] wlan0: associate with <MAC C-NA *belkin.986 1> (try 1/3)
[   60.343334] wlan0: RX AssocResp from <MAC C-NA *belkin.986 1> (capab=0x411 status=0 aid=4)
[   60.349968] wlan0: associated
[   60.349998] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


    ======== Done ========
```

```
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.1.7.0 ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
``` i also ran those commands again and my internet is up again, it probably wasnt working cause i ran all the commands at once but today i ran them all one by one,and m internet is working but it still disconnects me and its doing it faster than it used to.

---

### Post by WinEunuchs2Unix on 2014-06-19
Sorry to but in but the first msg "I recently installed Ubuntu but my wifi...".  It was not mentioned if it was installed with dual boot and the Windows wifi works perfectly.  I always check both platforms first to help isolate problems.

Secondly I considered the 7260 but 802.11ac is pretty much useless for me and the Wi-Direct-to-TV thingy requires to much horse power so I went with the N-6235 which has 802.11N like the telephone company's router and the Wi-Direct-to-TV thingy (which I'll probably never use having purchased Chromecast and ordered a hard wired XVGA to TV PC Input cable) supports my chipset.  Both include bluetooth which is rumoured to be flakey (and I'll probably never use).  The Intel N-6235 seems to be well received in Ubuntu whereas the Intel 7260 seems to be a lesser welcomed guest.

As far as "probably never use" keep in mind when I bought the laptop it came with a GPU (Graphical Processing Unit) which I started using 7 years later after Flash Player caused the CPU to run at 100% and fry my wrists.

I spent about four hours researching the N-6235 vs. 7260 before making my $18 USD purchasing decision and hope at least one other person can benefit from the time.

---

### Post by varunendra on 2014-06-20
First of all, since the parameter '11n_disable=1' didn't help, let's remove it so at least we can revert to full speed the adapter supports. Please run the following code to do so -
```
sudo sed -i 's/ 11n_disable=1//' /etc/modprobe.d/iwlwifi.conf
```
Note that there is a blank space before "11n...". Copy-paste the command using mouse cursor to avoid typo.

Verify that the parameter is removed -
```
cat /etc/modprobe.d/iwlwifi.conf
```
..you should see the contents of the 'iwlwifi.conf' file, in which there should be no "11n_disable=1" parameter anywhere.

Next -
> **rafael10 said:**
> ```
.. driver=iwlwifi driverversion=3.13.0-29-generic **firmware=[COLOR="#FF0000"]22.1.7.0[/COLOR]**
``` i also ran those commands again and my internet is up again, it probably wasnt working cause i ran all the commands at once but today i ran them all one by one,and m internet is working but it still disconnects me and its doing it faster than it used to.
It doesn't look like the firmware was replaced. If you ran the commands to get the above outputs right after running the previously suggested commands (to copy the firmware), then the change will take effect after a reboot. So run the "lshw.." command again after a reboot, and see if the firmware version is changed to "**22.15.8.0**". If it is, does it make the connection any better?

If the firmware version remains unchanged, please post the complete outputs of the commands you are running to copy the firmware, plus the output of "lshw..." command again.

If the version is changed, but the problem is still still there, please post a fresh wireless_script report, plus the output of the "lshw.." command.

---

### Post by rafael10 on 2014-06-20
this is the lshw ```
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.15.8.0 ip=192.168.2.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
``` and when i run those commands to install the new version nothing happens ```
loggikwolf@Alpha:~$ sudo cp iwl* /lib/firmware/iwlwifi-7260-7.ucode
[sudo] password for loggikwolf:
``` i also run the commands before that and i get this```
loggikwolf@Alpha:~$ cd Desktop/iwlwifi-7260-ucode-22.15.8.0
loggikwolf@Alpha:~/Desktop/iwlwifi-7260-ucode-22.15.8.0$ sudo get-install iwl/lib/firmware/iwlwifi-7260-7.ucoe
```

---

### Post by varunendra on 2014-06-21
> **rafael10 said:**
> ```
driver=iwlwifi driverversion=3.13.0-29-generic **firmware=22.15.8.0**
```

So the firmware version is changed now. I don't understand the command in your last post. There is no command, as far as I know, like "get-install....", and if you meant "apt-get install...", then you simply can't install a firmware like that (nor do you need, since the manual copying did the job as per lshw output).

Is the problem still there? If yes, pleas post a fresh wireless_script report like I asked in my previous post. Also post the output of the 'lshw ...' command simultaneously so I can be sure that your 'unwanted' experiments didn't replace the firmware again.

And please don't try things on your own if you are following what I am suggesting, especially if you are not sure what you are doing.

---

### Post by rafael10 on 2014-06-21
hers the lshw ```
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.1.7.0 ip=192.168.2.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
``` and heres the wireless script ```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 17:48:05 up  7:03,  2 users,  load average: 0.12, 0.22, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 027: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=135 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:5   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
3: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 135 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-02 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-03 MyCharterWiFi71-2G>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA2
    NETGEAR63:       Infra, <MAC C-04 NETGEAR63>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    ATTd8bhWuI:      Infra, <MAC C-06 ATTd8bhWuI>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    2WIRE132:        Infra, <MAC C-NA 2WIRE132 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    2WIRE000:        Infra, <MAC C-05 2WIRE000>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.465/2.515/3.565/1.050 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.975/1.064/1.154/0.095 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.032/0.037/0.042/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003808a8eb42
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002460020da65
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 MyCharterWiFi71-2G>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi71-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000157f548f681
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 NETGEAR63>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157f79f17b2
                    Extra: Last beacon: 4716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 2WIRE000>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"2WIRE000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000157f409e181
                    Extra: Last beacon: 4612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 ATTd8bhWuI>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ATTd8bhWuI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000157f779994d
                    Extra: Last beacon: 4476ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N swcrypto=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.694699] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.695036] audit: initializing netlink socket (disabled)
[    1.325882] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.295523] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   28.393126] wmi: Mapper loaded
[   28.439514] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   28.562086] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   28.562091] iwlwifi 0000:03:00.0: Falling back to user helper
[   28.571974] asus_wmi: ASUS WMI generic driver loaded
[   28.573532] asus_wmi: Initialization: 0x1
[   28.573577] asus_wmi: BIOS WMI version: 7.9
[   28.573630] asus_wmi: SFUN value: 0x4a0877
[   28.576486] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   28.588771] asus_wmi: Backlight controlled by ACPI video driver
[   28.605179] iwlwifi 0000:03:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   28.618026] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   28.618073] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   28.618287] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   28.836560] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   31.348859] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.280372] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   32.280588] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   32.294065] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.294380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.059724] wlan0: authenticate with <MAC C-01 belkin.986>
[   36.060439] wlan0: direct probe to <MAC C-01 belkin.986> (try 1/3)
[   36.262750] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[   36.264464] wlan0: authenticated
[   36.266129] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   36.269973] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[   36.272519] wlan0: associated
[   36.272546] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.024885] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[   44.053627] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   44.053859] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   44.065984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.943561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.060646] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   45.060863] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   45.074816] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.191631] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   45.287942] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   48.770494] wlan0: authenticate with <MAC C-01 belkin.986>
[   48.771146] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   48.772841] wlan0: authenticated
[   48.775175] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   48.779023] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[   48.781624] wlan0: associated
[   48.781653] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  529.822908] wlan0: authenticate with <MAC C-01 belkin.986>
[  529.823873] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  529.825614] wlan0: authenticated
[  529.829156] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  529.833016] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[  529.835479] wlan0: associated
[  877.177407] wlan0: authenticate with <MAC C-01 belkin.986>
[  877.178433] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  877.180208] wlan0: authenticated
[  877.183858] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  877.187894] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[  877.192524] wlan0: associated
[  885.581297] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[  885.620712] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  885.620948] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  885.633476] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  885.924157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  893.182379] wlan0: authenticate with <MAC C-01 belkin.986>
[  893.183244] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  893.184975] wlan0: authenticated
[  893.186947] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  893.190876] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[  893.193851] wlan0: associated
[  893.193911] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  893.202669] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[  893.204088] wlan0: authenticate with <MAC C-01 belkin.986>
[  893.204717] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  893.511603] iwlwifi 0000:03:00.0: No association and the time event is over already...
[  893.511668] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[  897.163759] wlan0: authenticated
[  897.168769] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  897.173145] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[  897.175926] wlan0: associated
[  897.463311] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[  897.517455] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  897.517687] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  897.529499] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  897.814602] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  897.883610] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  897.883837] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[  897.895403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  901.591600] wlan0: authenticate with <MAC C-01 belkin.986>
[  901.592473] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[  901.594175] wlan0: authenticated
[  901.598220] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[  901.603954] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[  901.607977] wlan0: associated
[  901.608002] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1227.501302] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1227.502166] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1227.503884] wlan0: authenticated
[ 1227.507225] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1227.511189] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1227.514030] wlan0: associated
[ 1229.573635] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 1229.613892] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1229.614118] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1229.625823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1229.881411] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1233.396445] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1233.397126] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1233.398802] wlan0: authenticated
[ 1233.399897] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1233.403726] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1233.406406] wlan0: associated
[ 1233.406429] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1240.218756] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 1240.254749] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1240.254976] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1240.267134] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1240.535472] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1240.599139] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1240.599367] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1240.610653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1240.887897] init: network-manager main process (764) killed by SEGV signal
[ 1240.887910] init: network-manager main process ended, respawning
[ 1248.285973] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1248.286908] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1248.288651] wlan0: authenticated
[ 1248.293213] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1248.298469] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1248.301002] wlan0: associated
[ 1248.301035] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1248.308065] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 1248.310446] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1248.311148] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1248.312868] wlan0: authenticated
[ 1248.316044] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1248.319946] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1248.322471] wlan0: associated
[ 1401.698087] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1401.698912] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1401.700617] wlan0: authenticated
[ 1401.702001] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1401.705905] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1401.710569] wlan0: associated
[ 1411.284688] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 1411.324641] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1411.324857] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1411.336157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1411.603019] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1415.708107] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1415.708331] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1415.720177] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1416.069438] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1416.069658] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1416.080471] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1433.429495] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1433.430287] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1433.431983] wlan0: authenticated
[ 1433.432324] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1433.436645] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1433.439159] wlan0: associated
[ 1433.439183] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1433.445910] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 1433.447571] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1433.448105] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1433.451546] wlan0: authenticated
[ 1433.452304] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1433.458412] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1433.462736] wlan0: associated
[ 1925.198136] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1925.199145] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1925.200981] wlan0: authenticated
[ 1925.202252] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1925.206162] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1925.208911] wlan0: associated
[ 1932.062826] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 1932.110538] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1932.110757] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1932.123093] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1932.408561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1939.682867] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1939.683738] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1939.685830] wlan0: authenticated
[ 1939.686155] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1939.692249] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1939.700734] wlan0: associated
[ 1939.700782] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1939.714385] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 1939.717710] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1939.718596] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1940.025941] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 1940.025984] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 1943.678098] wlan0: authenticated
[ 1943.679951] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1943.687742] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1943.697461] wlan0: associated
[ 1943.970666] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 1944.020127] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1944.020348] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1944.032048] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1944.306099] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1944.354094] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1944.354309] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 1944.365545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1948.170682] wlan0: authenticate with <MAC C-01 belkin.986>
[ 1948.171312] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 1948.172993] wlan0: authenticated
[ 1948.173393] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 1948.177214] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 1948.179643] wlan0: associated
[ 1948.179668] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2098.251488] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2098.252433] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2098.254215] wlan0: authenticated
[ 2098.257925] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2098.265662] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2098.268447] wlan0: associated
[ 2101.207572] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2101.247054] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2101.247288] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2101.259786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2101.555780] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2108.822107] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2108.823274] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2108.824990] wlan0: authenticated
[ 2108.827998] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2108.831897] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2108.834451] wlan0: associated
[ 2108.834504] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2108.842315] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2108.844087] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2108.844647] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2109.151486] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 2109.151529] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 2112.803648] wlan0: authenticated
[ 2112.805783] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2112.810180] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2112.812635] wlan0: associated
[ 2113.109107] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2113.154004] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2113.154229] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2113.165985] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2113.424444] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2113.655983] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2113.656214] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2113.668205] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2117.464436] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2117.465041] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2117.466712] wlan0: authenticated
[ 2117.467175] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2117.472223] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2117.474621] wlan0: associated
[ 2117.474642] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2971.148283] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2971.150255] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2971.151977] wlan0: authenticated
[ 2971.154231] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2971.158093] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2971.160595] wlan0: associated
[ 2974.544773] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2974.581858] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2974.582077] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2974.594615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2974.878552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2982.129539] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2982.130504] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2982.132208] wlan0: authenticated
[ 2982.136126] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2982.140014] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2982.142541] wlan0: associated
[ 2982.142574] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2982.150272] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2982.151674] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2982.152303] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2982.459168] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 2982.459208] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 2986.214187] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[ 2986.215890] wlan0: authenticated
[ 2986.217864] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2986.221691] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2986.224167] wlan0: associated
[ 2986.404794] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2986.443930] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2986.444166] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2986.455527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2986.725307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2986.846596] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2986.846818] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2986.858551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2990.651799] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2990.652507] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2990.654197] wlan0: authenticated
[ 2990.655369] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2990.659216] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 2990.661585] wlan0: associated
[ 2990.661606] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3319.738666] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3319.739645] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3319.741440] wlan0: authenticated
[ 3319.745178] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3319.749172] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 3319.751982] wlan0: associated
[ 3323.341717] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3323.372049] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3323.372285] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3323.385387] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3323.672964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3327.591698] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3327.591928] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3327.604070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3327.969112] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3327.969334] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3327.981348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3345.392658] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3345.393559] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3345.395278] wlan0: authenticated
[ 3345.398832] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3345.403602] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 3345.408485] wlan0: associated
[ 3345.408526] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3345.416248] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 3345.417542] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3345.418319] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3345.420035] wlan0: authenticated
[ 3345.422798] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3345.430475] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 3345.433124] wlan0: associated
[ 5762.084297] wlan0: authenticate with <MAC C-01 belkin.986>
[ 5762.085201] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 5762.086938] wlan0: authenticated
[ 5762.090865] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 5762.094824] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 5762.097731] wlan0: associated
[ 6110.474208] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6110.475026] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6110.476887] wlan0: authenticated
[ 6110.480871] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6110.485435] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6110.488211] wlan0: associated
[ 6117.862767] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6117.898890] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6117.899113] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6117.911646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6118.188544] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6125.458520] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6125.459465] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6125.461866] wlan0: authenticated
[ 6125.464545] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6125.468411] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6125.470963] wlan0: associated
[ 6125.470997] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6125.481488] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 6125.485533] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6125.486158] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6125.793609] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 6125.793652] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 6129.445722] wlan0: authenticated
[ 6129.450284] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6129.458892] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6129.461567] wlan0: associated
[ 6129.745559] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6129.784213] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6129.784439] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6129.795725] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6130.061434] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6130.289303] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6130.289523] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6130.301088] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6134.082906] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6134.083644] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6134.085353] wlan0: authenticated
[ 6134.087794] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6134.091642] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6134.099489] wlan0: associated
[ 6134.099526] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6647.877175] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6647.878234] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6647.880012] wlan0: authenticated
[ 6647.884141] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6647.888122] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6647.890774] wlan0: associated
[ 6656.469137] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6656.469359] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6656.482385] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6656.749927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6664.014768] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6664.015757] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6664.017517] wlan0: authenticated
[ 6664.019152] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6664.023179] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6664.027013] wlan0: associated
[ 6664.027046] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6664.041630] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 6664.043181] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6664.043812] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6664.350657] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 6664.350695] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 6668.002789] wlan0: authenticated
[ 6668.004986] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6668.009358] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6668.011975] wlan0: associated
[ 6668.261739] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6668.305649] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6668.305868] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6668.317601] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6668.606910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6668.679898] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6668.680117] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6668.691977] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6672.388392] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6672.389002] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6672.390691] wlan0: authenticated
[ 6672.394438] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6672.406716] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6672.409445] wlan0: associated
[ 6672.409470] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6769.060080] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6769.060995] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6769.062904] wlan0: authenticated
[ 6769.066840] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6769.070721] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6769.073251] wlan0: associated
[ 6774.277196] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6774.278754] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6774.280486] wlan0: authenticated
[ 6774.283919] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6774.287842] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6774.290637] wlan0: associated
[ 6779.294225] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6779.295288] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6779.297073] wlan0: authenticated
[ 6779.301197] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6779.305141] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6779.307967] wlan0: associated
[ 6786.354680] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6786.355653] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6786.357431] wlan0: authenticated
[ 6786.361244] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6786.365341] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6786.368192] wlan0: associated
[ 6793.826631] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6793.827610] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6793.829386] wlan0: authenticated
[ 6793.833083] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6793.837078] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6793.839849] wlan0: associated
[ 6795.403805] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6795.404020] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6795.416272] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6795.690563] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6802.943260] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6802.944384] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6802.946098] wlan0: authenticated
[ 6802.948181] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6802.952047] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6802.954557] wlan0: associated
[ 6802.954595] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6802.961859] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 6802.963576] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6802.964111] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6803.270934] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 6803.270969] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 6807.026060] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[ 6807.028335] wlan0: authenticated
[ 6807.029698] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6807.033529] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6807.036161] wlan0: associated
[ 6807.262084] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6807.305621] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6807.305847] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6807.318184] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6807.580116] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6807.656610] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6807.656837] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6807.668144] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6811.367613] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6811.368221] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6811.371947] wlan0: authenticated
[ 6811.379255] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6811.387504] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6811.390078] wlan0: associated
[ 6811.390102] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6825.548753] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6825.549746] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6825.556029] wlan0: authenticated
[ 6825.559485] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6825.565206] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6825.567819] wlan0: associated
[ 6834.360702] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6834.402223] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6834.402459] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6834.415611] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6834.689850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6841.919830] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6841.921213] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6841.922943] wlan0: authenticated
[ 6841.927202] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6841.931108] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6841.934011] wlan0: associated
[ 6841.934066] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6841.942123] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 6841.943418] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6841.944060] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6842.250870] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 6842.250903] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 6845.903022] wlan0: authenticated
[ 6845.904973] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6845.909406] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6845.911790] wlan0: associated
[ 6846.239604] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 6846.276075] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6846.276303] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6846.288788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6846.582699] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6846.815101] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6846.815331] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 6846.828083] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6850.641098] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6850.641723] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6850.643583] wlan0: authenticated
[ 6850.646304] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6850.651682] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6850.654300] wlan0: associated
[ 6850.654323] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6856.048031] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6856.049028] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6856.051403] wlan0: authenticated
[ 6856.055349] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6856.059272] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6856.062110] wlan0: associated
[ 6860.450129] wlan0: authenticate with <MAC C-01 belkin.986>
[ 6860.451248] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 6860.453233] wlan0: authenticated
[ 6860.456905] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 6860.462480] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 6860.464960] wlan0: associated
[ 7025.529299] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7025.530184] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7025.531893] wlan0: authenticated
[ 7025.535811] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7025.539797] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 7025.542619] wlan0: associated
[ 7028.633441] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7028.666446] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7028.666670] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7028.678229] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7028.936803] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7032.404668] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7032.405330] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7032.407009] wlan0: authenticated
[ 7032.407922] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7032.411764] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 7032.414330] wlan0: associated
[ 7032.414354] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7040.856686] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7040.896887] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7040.897120] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7040.909773] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7041.193270] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7041.258444] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7041.258663] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7041.270151] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7041.463061] init: network-manager main process (3971) killed by SEGV signal
[ 7041.463073] init: network-manager main process ended, respawning
[ 7045.236920] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7045.237602] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7045.239289] wlan0: authenticated
[ 7045.240796] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7045.244615] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 7045.247162] wlan0: associated
[ 7045.247186] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8900.799481] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8900.800631] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8900.802324] wlan0: authenticated
[ 8900.806252] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8900.810159] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 8900.812763] wlan0: associated
[ 9771.338420] wlan0: authenticate with <MAC C-01 belkin.986>
[ 9771.339244] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 9771.341272] wlan0: authenticated
[ 9771.341748] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 9771.346320] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 9771.348868] wlan0: associated
[ 9780.697252] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 9780.736985] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9780.737211] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9780.749440] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9781.035182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9788.305100] wlan0: authenticate with <MAC C-01 belkin.986>
[ 9788.305981] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 9788.310454] wlan0: authenticated
[ 9788.312324] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 9788.316345] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 9788.319095] wlan0: associated
[ 9788.319130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9788.327314] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 9788.328816] wlan0: authenticate with <MAC C-01 belkin.986>
[ 9788.329456] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 9788.636298] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 9788.636334] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 9792.288502] wlan0: authenticated
[ 9792.290136] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 9792.294414] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 9792.297072] wlan0: associated
[ 9792.587300] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 9792.619570] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9792.619801] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9792.631022] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9792.901718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9792.976626] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9792.976842] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 9792.988433] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9796.791893] wlan0: authenticate with <MAC C-01 belkin.986>
[ 9796.792517] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 9796.794201] wlan0: authenticated
[ 9796.795554] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 9796.800341] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[ 9796.805191] wlan0: associated
[ 9796.805217] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10120.124566] wlan0: authenticate with <MAC C-01 belkin.986>
[10120.125457] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10120.127215] wlan0: authenticated
[10120.131185] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10120.135445] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10120.138291] wlan0: associated
[10124.983240] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10125.034903] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10125.035137] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10125.048113] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10125.335308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10132.604954] wlan0: authenticate with <MAC C-01 belkin.986>
[10132.605922] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10132.607629] wlan0: authenticated
[10132.608175] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10132.612122] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10132.614680] wlan0: associated
[10132.614727] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10132.622293] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[10132.623991] wlan0: authenticate with <MAC C-01 belkin.986>
[10132.625865] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10132.931616] iwlwifi 0000:03:00.0: No association and the time event is over already...
[10132.931640] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[10136.583781] wlan0: authenticated
[10136.586003] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10136.591964] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10136.596004] wlan0: associated
[10136.921606] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10136.970263] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10136.970509] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10136.982393] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10137.256991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10137.325135] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10137.325342] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10137.336941] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10141.036184] wlan0: authenticate with <MAC C-01 belkin.986>
[10141.036869] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10141.040103] wlan0: authenticated
[10141.043447] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10141.048045] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10141.051913] wlan0: associated
[10141.051938] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10683.027326] wlan0: authenticate with <MAC C-01 belkin.986>
[10683.028132] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10683.030996] wlan0: authenticated
[10683.031984] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10683.042130] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10683.046199] wlan0: associated
[10688.365776] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10688.406067] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10688.406289] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10688.418576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10688.707555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10695.979279] wlan0: authenticate with <MAC C-01 belkin.986>
[10695.980074] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10695.981797] wlan0: authenticated
[10695.988844] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10695.993060] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10695.995937] wlan0: associated
[10695.996007] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10696.004354] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[10696.006605] wlan0: authenticate with <MAC C-01 belkin.986>
[10696.007241] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10696.314104] iwlwifi 0000:03:00.0: No association and the time event is over already...
[10696.314127] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[10699.966914] wlan0: authenticated
[10699.970640] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10699.976009] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10699.978783] wlan0: associated
[10700.266448] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10700.315682] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10700.315905] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10700.327181] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10700.612810] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10700.693597] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10700.693824] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10700.705329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10704.507798] wlan0: authenticate with <MAC C-01 belkin.986>
[10704.508437] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10704.510121] wlan0: authenticated
[10704.512027] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10704.515979] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10704.518233] wlan0: associated
[10704.518242] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10817.397365] wlan0: authenticate with <MAC C-01 belkin.986>
[10817.398155] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10817.399897] wlan0: authenticated
[10817.400447] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10817.404440] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10817.407561] wlan0: associated
[10827.139876] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10827.175448] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10827.175683] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10827.187559] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10827.466083] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10834.717977] wlan0: authenticate with <MAC C-01 belkin.986>
[10834.718859] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10834.720597] wlan0: authenticated
[10834.723603] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10834.730351] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10834.732858] wlan0: associated
[10834.732892] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10834.741832] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[10834.743788] wlan0: authenticate with <MAC C-01 belkin.986>
[10834.744617] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10835.051408] iwlwifi 0000:03:00.0: No association and the time event is over already...
[10835.051468] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[10838.703571] wlan0: authenticated
[10838.708583] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10838.714480] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10838.715628] wlan0: associated
[10839.043383] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[10839.103040] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10839.103263] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10839.114582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10839.403824] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10839.487614] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10839.487833] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[10839.500183] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10843.298815] wlan0: authenticate with <MAC C-01 belkin.986>
[10843.299442] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[10843.301122] wlan0: authenticated
[10843.301998] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[10843.306120] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[10843.308822] wlan0: associated
[10843.308847] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11166.801852] wlan0: authenticate with <MAC C-01 belkin.986>
[11166.802551] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[11166.804275] wlan0: authenticated
[11166.804509] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[11166.808477] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[11166.811400] wlan0: associated
[11175.948284] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[11175.984229] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11175.984456] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11175.996322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11176.266121] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11179.740563] wlan0: authenticate with <MAC C-01 belkin.986>
[11179.741220] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[11179.742890] wlan0: authenticated
[11179.745315] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[11179.751295] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[11179.753883] wlan0: associated
[11179.753907] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11186.843991] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[11186.878023] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11186.878258] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11186.890742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11187.152132] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11187.240530] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11187.240750] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[11187.252155] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11191.044887] wlan0: authenticate with <MAC C-01 belkin.986>
[11191.045515] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[11191.047213] wlan0: authenticated
[11191.051023] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[11191.054875] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[11191.060150] wlan0: associated
[11191.060174] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12213.587864] wlan0: authenticate with <MAC C-01 belkin.986>
[12213.588634] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12213.590315] wlan0: authenticated
[12213.591080] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12213.596831] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12213.600055] wlan0: associated
[12218.401458] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[12218.446699] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12218.446931] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12218.459792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12218.715098] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12222.197260] wlan0: authenticate with <MAC C-01 belkin.986>
[12222.198532] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12222.200209] wlan0: authenticated
[12222.202272] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12222.206154] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12222.209583] wlan0: associated
[12222.209609] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12229.457827] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[12229.484070] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12229.484286] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12229.495900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12229.788209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12229.895027] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12229.895244] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12229.910489] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12233.608161] wlan0: authenticate with <MAC C-01 belkin.986>
[12233.609008] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12233.610720] wlan0: authenticated
[12233.611910] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12233.618107] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12233.620632] wlan0: associated
[12233.620654] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12388.700724] wlan0: authenticate with <MAC C-01 belkin.986>
[12388.701578] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12388.703295] wlan0: authenticated
[12388.707378] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12388.711253] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12388.713771] wlan0: associated
[12396.257194] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[12396.289657] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12396.289877] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12396.302539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12396.590806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12403.868120] wlan0: authenticate with <MAC C-01 belkin.986>
[12403.869058] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12403.872377] wlan0: authenticated
[12403.874950] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12403.878822] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12403.881344] wlan0: associated
[12403.881392] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12403.889471] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[12403.890760] wlan0: authenticate with <MAC C-01 belkin.986>
[12403.891497] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12404.198350] iwlwifi 0000:03:00.0: No association and the time event is over already...
[12404.198375] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[12407.850479] wlan0: authenticated
[12407.852732] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12407.858015] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12407.860456] wlan0: associated
[12408.186608] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[12408.235063] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12408.235286] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12408.246905] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12408.527592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12408.639532] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12408.639748] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[12408.651222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12412.454928] wlan0: authenticate with <MAC C-01 belkin.986>
[12412.456093] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[12412.457760] wlan0: authenticated
[12412.458135] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[12412.463453] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[12412.465833] wlan0: associated
[12412.465854] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15178.300453] wlan0: authenticate with <MAC C-01 belkin.986>
[15178.301400] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15178.303122] wlan0: authenticated
[15178.307296] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15178.311186] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15178.313629] wlan0: associated
[15528.525421] wlan0: authenticate with <MAC C-01 belkin.986>
[15528.526397] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15528.528128] wlan0: authenticated
[15528.536413] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15528.540411] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15528.542428] wlan0: associated
[15533.738882] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[15533.781319] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15533.781607] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15533.793816] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15534.083836] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15537.994200] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15537.994422] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15538.006786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15538.333670] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15538.333900] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15538.346330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15552.011963] wlan0: authenticate with <MAC C-01 belkin.986>
[15552.012616] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15552.015359] wlan0: authenticated
[15552.019275] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15552.023130] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15552.023757] wlan0: associated
[15552.023924] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15701.997934] wlan0: authenticate with <MAC C-01 belkin.986>
[15701.999058] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15702.000815] wlan0: authenticated
[15702.004712] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15702.008722] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15702.011516] wlan0: associated
[15704.478873] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[15704.512513] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15704.512741] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15704.525318] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15704.817899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15712.087925] wlan0: authenticate with <MAC C-01 belkin.986>
[15712.088885] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15712.090601] wlan0: authenticated
[15712.091158] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15712.095059] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15712.097549] wlan0: associated
[15712.097614] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15712.107068] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[15712.110315] wlan0: authenticate with <MAC C-01 belkin.986>
[15712.110986] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15712.417863] iwlwifi 0000:03:00.0: No association and the time event is over already...
[15712.417925] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[15716.069912] wlan0: authenticated
[15716.072957] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15716.077262] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15716.079766] wlan0: associated
[15716.408402] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[15716.454944] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15716.455165] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15716.466822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15716.768526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15716.871733] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15716.871952] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15716.884130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15720.686334] wlan0: authenticate with <MAC C-01 belkin.986>
[15720.687384] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15720.689056] wlan0: authenticated
[15720.690258] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15720.694090] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15720.696486] wlan0: associated
[15720.696510] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15875.682494] wlan0: authenticate with <MAC C-01 belkin.986>
[15875.683427] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15875.685201] wlan0: authenticated
[15875.689376] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15875.694855] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15875.697509] wlan0: associated
[15878.457431] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[15878.496002] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15878.496228] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15878.508333] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15878.798834] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15886.064882] wlan0: authenticate with <MAC C-01 belkin.986>
[15886.065784] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15886.067547] wlan0: authenticated
[15886.071506] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15886.075366] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15886.077903] wlan0: associated
[15886.077932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15886.085604] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[15886.086863] wlan0: authenticate with <MAC C-01 belkin.986>
[15886.087548] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15886.394376] iwlwifi 0000:03:00.0: No association and the time event is over already...
[15886.394419] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[15890.046541] wlan0: authenticated
[15890.049358] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15890.053769] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15890.058344] wlan0: associated
[15890.388570] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[15890.435824] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15890.436050] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15890.448525] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15890.724361] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15890.852249] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15890.852468] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[15890.863915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15894.671072] wlan0: authenticate with <MAC C-01 belkin.986>
[15894.671688] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[15894.675480] wlan0: authenticated
[15894.678759] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[15894.684952] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[15894.691556] wlan0: associated
[15894.691582] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17097.882266] wlan0: authenticate with <MAC C-01 belkin.986>
[17097.883000] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17097.884713] wlan0: authenticated
[17097.885474] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17097.889435] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17097.892051] wlan0: associated
[17101.891026] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[17101.931997] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17101.932234] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17101.945102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17102.221814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17109.486206] wlan0: authenticate with <MAC C-01 belkin.986>
[17109.487255] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17109.488941] wlan0: authenticated
[17109.490996] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17109.494861] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17109.497333] wlan0: associated
[17109.497383] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17109.504300] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[17109.505926] wlan0: authenticate with <MAC C-01 belkin.986>
[17109.506529] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17109.813336] iwlwifi 0000:03:00.0: No association and the time event is over already...
[17109.813355] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[17113.569086] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[17113.571384] wlan0: authenticated
[17113.572735] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17113.576626] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17113.579082] wlan0: associated
[17113.824445] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[17113.856347] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17113.856581] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17113.867999] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17114.131896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17114.203574] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17114.203791] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17114.215227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17121.640877] wlan0: authenticate with <MAC C-01 belkin.986>
[17121.641836] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17121.643598] wlan0: authenticated
[17121.644254] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17121.648154] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17121.650765] wlan0: associated
[17121.650807] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17121.658055] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[17121.659871] wlan0: authenticate with <MAC C-01 belkin.986>
[17121.660435] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17121.662184] wlan0: authenticated
[17121.664232] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17121.668107] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17121.670525] wlan0: associated
[17448.924469] wlan0: authenticate with <MAC C-01 belkin.986>
[17448.925386] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17448.927127] wlan0: authenticated
[17448.930907] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17448.934942] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17448.937589] wlan0: associated
[17450.501491] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[17450.534167] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17450.534386] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17450.545806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17450.817164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17458.087213] wlan0: authenticate with <MAC C-01 belkin.986>
[17458.088102] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17458.089818] wlan0: authenticated
[17458.093767] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17458.097642] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17458.100177] wlan0: associated
[17458.100225] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17458.110445] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[17458.111660] wlan0: authenticate with <MAC C-01 belkin.986>
[17458.112425] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17458.419223] iwlwifi 0000:03:00.0: No association and the time event is over already...
[17458.419279] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[17462.071351] wlan0: authenticated
[17462.075601] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17462.079914] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17462.082578] wlan0: associated
[17462.369283] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[17462.426365] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17462.426593] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17462.438427] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17462.734400] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17462.798569] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17462.798788] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[17462.810719] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17466.603681] wlan0: authenticate with <MAC C-01 belkin.986>
[17466.604395] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[17466.606089] wlan0: authenticated
[17466.609015] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[17466.617921] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[17466.620336] wlan0: associated
[17466.620359] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[18320.283569] wlan0: authenticate with <MAC C-01 belkin.986>
[18320.284651] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[18320.286396] wlan0: authenticated
[18320.290439] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[18320.294497] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[18320.297183] wlan0: associated
[18324.239895] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[18324.276633] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18324.276848] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18324.288837] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18324.580618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18331.822263] wlan0: authenticate with <MAC C-01 belkin.986>
[18331.823221] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[18331.825673] wlan0: authenticated
[18331.827940] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[18331.836470] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[18331.838918] wlan0: associated
[18331.838963] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[18331.847419] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[18331.848967] wlan0: authenticate with <MAC C-01 belkin.986>
[18331.849670] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[18332.156593] iwlwifi 0000:03:00.0: No association and the time event is over already...
[18332.156656] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[18335.808750] wlan0: authenticated
[18335.809937] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[18335.814743] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[18335.817319] wlan0: associated
[18336.139716] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[18336.189491] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18336.189722] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18336.202447] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18336.496122] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18336.608719] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18336.608947] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[18336.621398] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18340.432012] wlan0: authenticate with <MAC C-01 belkin.986>
[18340.432637] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[18340.434319] wlan0: authenticated
[18340.435216] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[18340.439039] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[18340.443337] wlan0: associated
[18340.443361] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20239.555521] wlan0: authenticate with <MAC C-01 belkin.986>
[20239.556605] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20239.558432] wlan0: authenticated
[20239.561770] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20239.567625] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20239.570272] wlan0: associated
[20246.931005] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[20246.974053] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20246.974272] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20246.986570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20247.260624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20254.524276] wlan0: authenticate with <MAC C-01 belkin.986>
[20254.525174] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20254.526887] wlan0: authenticated
[20254.529606] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20254.533528] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20254.543568] wlan0: associated
[20254.543612] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20254.550644] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[20254.552371] wlan0: authenticate with <MAC C-01 belkin.986>
[20254.552900] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20254.859792] iwlwifi 0000:03:00.0: No association and the time event is over already...
[20254.859855] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[20258.511947] wlan0: authenticated
[20258.515213] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20258.521041] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20258.523568] wlan0: associated
[20258.930584] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[20258.992607] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20258.992821] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20259.003906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20259.301394] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20259.529358] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20259.529588] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20259.541606] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20263.342457] wlan0: authenticate with <MAC C-01 belkin.986>
[20263.343794] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20263.345481] wlan0: authenticated
[20263.348458] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20263.353300] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20263.354669] wlan0: associated
[20263.354695] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20412.311790] wlan0: authenticate with <MAC C-01 belkin.986>
[20412.312807] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20412.314594] wlan0: authenticated
[20412.318539] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20412.324417] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20412.326997] wlan0: associated
[20415.977846] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[20416.012597] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20416.012822] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20416.024914] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20416.310628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20423.575218] wlan0: authenticate with <MAC C-01 belkin.986>
[20423.576071] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20423.577839] wlan0: authenticated
[20423.580450] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20423.584373] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20423.586966] wlan0: associated
[20423.587012] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20423.596541] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[20423.598330] wlan0: authenticate with <MAC C-01 belkin.986>
[20423.599102] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20423.905909] iwlwifi 0000:03:00.0: No association and the time event is over already...
[20423.905947] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[20427.558075] wlan0: authenticated
[20427.562082] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20427.566971] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20427.571618] wlan0: associated
[20428.091984] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[20428.133075] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20428.133301] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20428.144584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20428.416079] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20428.492956] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20428.493176] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[20428.504638] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20432.319144] wlan0: authenticate with <MAC C-01 belkin.986>
[20432.320200] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20432.321896] wlan0: authenticated
[20432.323346] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20432.327153] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20432.329578] wlan0: associated
[20432.329603] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20764.166680] wlan0: authenticate with <MAC C-01 belkin.986>
[20764.167670] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[20764.169483] wlan0: authenticated
[20764.173726] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[20764.177759] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[20764.181229] wlan0: associated
[21285.100505] wlan0: authenticate with <MAC C-01 belkin.986>
[21285.101406] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[21285.103163] wlan0: authenticated
[21285.103803] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[21285.107690] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[21285.112658] wlan0: associated
[21294.341674] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[21294.382614] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21294.382851] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21294.394912] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21294.681274] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21301.941741] wlan0: authenticate with <MAC C-01 belkin.986>
[21301.942620] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[21301.945197] wlan0: authenticated
[21301.947247] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[21301.951134] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[21301.953574] wlan0: associated
[21301.953599] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21301.961847] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[21301.970848] wlan0: authenticate with <MAC C-01 belkin.986>
[21301.971482] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[21302.278366] iwlwifi 0000:03:00.0: No association and the time event is over already...
[21302.278406] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[21305.930465] wlan0: authenticated
[21305.932268] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[21305.937483] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[21305.941829] wlan0: associated
[21306.227238] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[21306.266123] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21306.266347] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21306.277683] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21306.552658] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21306.618903] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21306.619128] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[21306.630794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21310.419909] wlan0: authenticate with <MAC C-01 belkin.986>
[21310.420833] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[21310.422520] wlan0: authenticated
[21310.425648] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[21310.429489] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[21310.431904] wlan0: associated
[21310.431927] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23377.742194] wlan0: authenticate with <MAC C-01 belkin.986>
[23377.743242] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23377.745031] wlan0: authenticated
[23377.749093] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23377.755777] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23377.759440] wlan0: associated
[23387.156065] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23387.196299] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23387.196524] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23387.208066] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23387.470295] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23394.710043] wlan0: authenticate with <MAC C-01 belkin.986>
[23394.710806] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23394.712552] wlan0: authenticated
[23394.715726] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23394.721579] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23394.724107] wlan0: associated
[23394.724141] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23394.736255] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[23394.738183] wlan0: authenticate with <MAC C-01 belkin.986>
[23394.738951] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23395.045755] iwlwifi 0000:03:00.0: No association and the time event is over already...
[23395.045793] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[23398.697942] wlan0: authenticated
[23398.701452] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23398.705813] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23398.710744] wlan0: associated
[23398.996222] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23399.038582] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23399.038808] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23399.049736] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23399.356811] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23399.456052] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23399.456267] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23399.467951] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23403.271154] wlan0: authenticate with <MAC C-01 belkin.986>
[23403.271804] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23403.273484] wlan0: authenticated
[23403.274944] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23403.279612] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23403.282114] wlan0: associated
[23403.282136] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23551.828893] wlan0: authenticate with <MAC C-01 belkin.986>
[23551.829644] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23551.832019] wlan0: authenticated
[23551.835992] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23551.839988] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23551.842719] wlan0: associated
[23556.316434] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23556.363437] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23556.363672] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23556.375265] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23556.664121] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23563.896117] wlan0: authenticate with <MAC C-01 belkin.986>
[23563.897066] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23563.899287] wlan0: authenticated
[23563.901395] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23563.908837] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23563.911292] wlan0: associated
[23563.911324] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23563.918609] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[23563.920286] wlan0: authenticate with <MAC C-01 belkin.986>
[23563.920900] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23564.227732] iwlwifi 0000:03:00.0: No association and the time event is over already...
[23564.227768] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[23567.879836] wlan0: authenticated
[23567.883089] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23567.888939] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23567.891809] wlan0: associated
[23568.184980] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23568.228084] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23568.228301] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23568.239379] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23568.509478] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23568.589661] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23568.589885] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23568.601991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23576.017744] wlan0: authenticate with <MAC C-01 belkin.986>
[23576.018788] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23576.020527] wlan0: authenticated
[23576.022489] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23576.026395] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23576.028831] wlan0: associated
[23576.028866] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23576.038487] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[23576.040593] wlan0: authenticate with <MAC C-01 belkin.986>
[23576.041363] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23576.043125] wlan0: authenticated
[23576.046498] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23576.050384] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23576.053005] wlan0: associated
[23726.640490] wlan0: authenticate with <MAC C-01 belkin.986>
[23726.641453] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23726.643159] wlan0: authenticated
[23726.647193] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23726.651036] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23726.653503] wlan0: associated
[23730.215032] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23730.253803] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23730.254040] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23730.266195] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23730.532136] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23737.798167] wlan0: authenticate with <MAC C-01 belkin.986>
[23737.799279] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23737.801004] wlan0: authenticated
[23737.804881] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23737.808782] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23737.811375] wlan0: associated
[23737.811428] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23737.821899] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[23737.823291] wlan0: authenticate with <MAC C-01 belkin.986>
[23737.823899] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23738.130788] iwlwifi 0000:03:00.0: No association and the time event is over already...
[23738.130853] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[23741.782901] wlan0: authenticated
[23741.786717] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23741.791055] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23741.793621] wlan0: associated
[23742.109040] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[23742.153289] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23742.153520] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23742.165965] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23742.455855] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23742.529043] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23742.529258] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[23742.541202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23749.968702] wlan0: authenticate with <MAC C-01 belkin.986>
[23749.969613] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23749.971332] wlan0: authenticated
[23749.974108] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23749.978016] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23749.988748] wlan0: associated
[23749.988804] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23749.997749] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[23749.999597] wlan0: authenticate with <MAC C-01 belkin.986>
[23750.000334] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[23750.002143] wlan0: authenticated
[23750.006134] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[23750.009992] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=4)
[23750.012584] wlan0: associated

    ======== Done ========
``` AND it still kicks me offline

---

### Post by varunendra on 2014-06-23
> **rafael10 said:**
> AND it still kicks me offline
Perhaps because the older firmware is _still there_, somehow back -
> **rafael10 said:**
> hers the lshw ```
      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic **[COLOR="#FF0000"]firmware=22.1.7.0[/COLOR]** ip=192.168.2.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
```

I don't know how it returned, but I do know that it can't happen by itself. Either an update installed/updated the "linux-firmware" package again, or it could be a result of a repeated attempt by you.

Just to make it clear, again, this is what we are trying to do - remove (backup) the current firmware file **(version [COLOR="#FF0000"]22.1.7.0[/COLOR])** and copy the newer version **[COLOR="#006400"](22.15.8.0)[/COLOR]** in place of it.

The procedure to do so is to simply extract the newer file from the downloaded archive, and use 'cp' command to copy it in the right place (/lib/firmware).

Let me know if you want a way other than commands to achieve that. Or if you understand it already, please try again and confirm that the newer version _Remains_ there even across reboots. Then confirm the performance with the _newer_ firmware.

---

### Post by rafael10 on 2014-06-23
which one of these do i delete and replace with the new firmware. [http://gyazo.com/d2e8781641729e1e4d5642fd10129e35](http://gyazo.com/d2e8781641729e1e4d5642fd10129e35)

---

### Post by varunendra on 2014-06-24
The screenshot is only showing a few kernel directories. The file you need to replace (iwlwifi-7260-7.ucode) should be within the /lib/firmware directory, not in any subfolder. I don't know any way other than the 'lshw' command to determine the version of the firmware files.

The file you would originally extract from the downloaded archive would be named "iwlwifi-7260-8.ucode". You must rename it to "iwlwifi-7260-7.ucode" before copying it in the /lib/firmware directory, otherwise the driver won't pick it up.

So the basic steps are -
Move (backup) the current firmware file > Extract the downloaded one > Rename the extracted one > Copy (or move) it to /lib/firmware directory > Reboot > check the version with the command "sudo lshw -C network | grep firmware" > make sure it is "22.15.8.0"

---

### Post by rafael10 on 2014-06-24
it doesnt let me delete the old firmware file

---

### Post by varunendra on 2014-06-25
Nor will it let you copy the new file without root privileges. These system directories need root privilege to make any changes to them. That's why we used 'sudo' with the 'mv' commands. You can also gain root access in GUI by opening the file manager ("nautilus" in default Ubuntu) with 'gksu', but running the GUI file manager as root can be risky (system would do ANYTHING you want without any warnings, no matter how disastrous the action may be). So [COLOR="#FF0000"]try this at your own risk![/COLOR]

First, install package 'gksu' (it is installed by default in 12.04, but not in later releases) -
```
sudo apt-get install gksu
```

Then to open the file manager with root access -
Press "Alt+F2" > type "gksu nautilus" > press 'Enter' > provide your login password > press 'Enter'

This will open the file manager "nautilus" in "root's" home. Anything you do in this file browser will be done with root access - no restrictions, no warnings either.

But be very careful in this mode and close the file manager as soon as you are done doing what you need it for. Otherwise you may end up breaking your installation.

---

### Post by jeremy31 on 2014-06-25
> **varunendra said:**
> The screenshot is only showing a few kernel directories. The file you need to replace (iwlwifi-7260-7.ucode) should be within the /lib/firmware directory, not in any subfolder. I don't know any way other than the 'lshw' command to determine the version of the firmware files.

The file you would originally extract from the downloaded archive would be named "iwlwifi-7260-8.ucode". You must rename it to "iwlwifi-7260-7.ucode" before copying it in the /lib/firmware directory, otherwise the driver won't pick it up.

So the basic steps are -
Move (backup) the current firmware file > Extract the downloaded one > Rename the extracted one > Copy (or move) it to /lib/firmware directory > Reboot > check the version with the command "sudo lshw -C network | grep firmware" > make sure it is "22.15.8.0"

I tried this same thing last night trying to get a 7620 AC working with a booted ISO and it did not work.  iwlwifi realized it was a unsupported ucode file

Somewhere I found a patch that would change what iwlwifi-7260 ucode files iwlwifi would accept and the patch might already be in a newer kernel

---

### Post by rafael10 on 2014-06-25
ok my wifi hasnt dropped and its been a few hours i was wondering if i were to install kubuntu would it effect my firmware in any way

---

### Post by rafael10 on 2014-06-25
it started to disconnect me again heres the new wireless script ```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 18:04:39 up  4:02,  2 users,  load average: 0.84, 0.94, 1.12


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 012: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=120 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
4: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 135 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-02 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    2WIRE000:        Infra, <MAC C-NA 2WIRE000 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-NA MyCharterWiFi71-2G 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA2
    NETGEAR63:       Infra, <MAC C-NA NETGEAR63 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2447 MHz, Rate 54 Mb/s, Strength 63 WPA2

    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 1.127/1.128/1.130/0.033 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.002/6.282/11.563/5.281 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.015/0.028/0.042/0.014 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
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

          Current Frequency:2.447 GHz (Channel 8)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002055985ba9
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000021905d3dc
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N swcrypto=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.690452] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.690784] audit: initializing netlink socket (disabled)
[    0.843266] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.921057] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   11.034116] wmi: Mapper loaded
[   11.060467] iwlwifi 0000:03:00.0: irq 62 for MSI/MSI-X
[   11.182511] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   11.182512] iwlwifi 0000:03:00.0: Falling back to user helper
[   11.339948] asus_wmi: ASUS WMI generic driver loaded
[   11.341040] asus_wmi: Initialization: 0x1
[   11.341085] asus_wmi: BIOS WMI version: 7.9
[   11.341140] asus_wmi: SFUN value: 0x4a0877
[   11.341866] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[   11.349587] asus_wmi: Backlight controlled by ACPI video driver
[   11.416056] iwlwifi 0000:03:00.0: loaded firmware version 22.15.8.0 op_mode iwlmvm
[   11.428027] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   11.428085] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.428307] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.626757] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   13.869802] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.845696] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   14.845917] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   14.856738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.857041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.906800] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   16.009935] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   22.160389] wlan0: authenticate with <MAC C-01 belkin.986>
[   22.161164] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   22.163322] wlan0: authenticated
[   22.165792] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   22.169906] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[   22.172276] wlan0: associated
[   22.172298] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.191194] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[   22.192577] wlan0: authenticate with <MAC C-01 belkin.986>
[   22.193080] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   22.195220] wlan0: authenticated
[   22.197789] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   22.201604] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[   22.203918] wlan0: associated
[ 4744.951232] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4744.951453] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 4744.961881] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4745.273439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4749.096358] wlan0: authenticate with <MAC C-01 belkin.986>
[ 4749.097184] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 4749.103583] wlan0: authenticated
[ 4749.104829] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 4749.119996] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[ 4749.124165] wlan0: associated
[ 4749.124196] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7384.000761] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7385.409770] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.409990] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.421107] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7385.475544] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.475764] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.486936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7385.871559] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.871788] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7385.884549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7390.083323] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7390.083535] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7390.107964] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 7390.216970] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 7395.910317] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7395.910999] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7395.918042] wlan0: authenticated
[ 7395.922047] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7395.925874] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[ 7395.928217] wlan0: associated
[ 7395.928240] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7396.101257] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 7396.150210] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7396.150426] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7396.161669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7396.459432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7396.568156] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7396.568373] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7396.580141] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7400.244178] wlan0: authenticate with <MAC C-01 belkin.986>
[ 7400.244799] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 7400.246683] wlan0: authenticated
[ 7400.247659] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 7400.251518] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[ 7400.253988] wlan0: associated
[ 7400.254011] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8053.166138] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8053.166357] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8053.177842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8053.442222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8060.618081] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8060.619274] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8060.621061] wlan0: authenticated
[ 8060.622055] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8060.625990] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=5)
[ 8060.631581] wlan0: associated
[ 8060.631619] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8061.366673] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 8061.419011] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8061.419227] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8061.430560] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8061.804474] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8061.804706] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8061.815351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8079.169156] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8079.169885] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8079.171616] wlan0: authenticated
[ 8079.172948] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8079.176824] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8079.179315] wlan0: associated
[ 8079.179339] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8079.187534] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 8079.189338] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8079.190040] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8079.196938] wlan0: authenticated
[ 8079.201235] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8079.205069] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8079.209595] wlan0: associated
[ 8098.258390] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8098.259554] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8098.278702] wlan0: authenticated
[ 8098.279853] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8098.566311] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8098.566344] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8099.703792] wlan0: associate with <MAC C-01 belkin.986> (try 2/3)
[ 8100.010948] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8100.010972] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8100.679780] wlan0: associate with <MAC C-01 belkin.986> (try 3/3)
[ 8100.722054] wlan0: association with <MAC C-01 belkin.986> timed out
[ 8108.144573] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8108.144794] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8108.155740] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8108.409761] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8111.845431] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8111.846978] wlan0: direct probe to <MAC C-01 belkin.986> (try 1/3)
[ 8112.047587] wlan0: direct probe to <MAC C-01 belkin.986> (try 2/3)
[ 8112.255508] wlan0: send auth to <MAC C-01 belkin.986> (try 3/3)
[ 8112.257685] wlan0: authenticated
[ 8112.259078] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8112.263773] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8112.267021] wlan0: associated
[ 8112.268347] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8119.274057] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 8119.328020] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8119.328239] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8119.339487] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8119.719414] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8119.719649] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 8119.730508] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8121.855207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8125.578159] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8125.579248] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8125.586203] wlan0: authenticated
[ 8125.590340] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8125.886039] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8125.886074] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8125.966310] wlan0: associate with <MAC C-01 belkin.986> (try 2/3)
[ 8125.989903] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8125.990686] wlan0: associated
[ 8125.990734] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8126.280657] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 8126.282751] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8126.283422] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8126.590282] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8126.590308] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8130.210920] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[ 8130.271716] wlan0: authenticated
[ 8130.274125] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8130.279583] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8130.282442] wlan0: associated
[ 8135.172660] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8135.173301] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8135.196663] wlan0: authenticated
[ 8135.197783] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8135.481069] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 8135.481100] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 8135.561770] wlan0: associate with <MAC C-01 belkin.986> (try 2/3)
[ 8135.591621] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8135.594372] wlan0: associated
[ 8140.503442] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8140.505535] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8140.507269] wlan0: authenticated
[ 8140.509526] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8140.513429] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8140.516038] wlan0: associated
[ 8149.927439] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8149.928088] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8149.979250] wlan0: authenticated
[ 8149.981120] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8150.009701] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8150.013753] wlan0: associated
[ 8159.223833] wlan0: authenticate with <MAC C-01 belkin.986>
[ 8159.224611] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 8159.229892] wlan0: authenticated
[ 8159.232453] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 8159.242621] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=1)
[ 8159.244957] wlan0: associated

    ======== Done ========
```
heres the lswh ```
loggikwolf@Alpha:~$ sudo lshw -C network | grep firmware
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.15.8.0 ip=192.168.2.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
```

---

### Post by varunendra on 2014-06-26
> **jeremy31 said:**
> I tried this same thing last night trying to get a 7620 AC working with a booted ISO and it did not work.  iwlwifi realized it was a unsupported ucode file
I also suspect that the firmware may not work with all versions of the driver. But since rafaes10's dmesg doesn't spit out any error messages, and he is able to connect even if intermittently, it means the firmware was accepted by his version of driver.

> **rafael10 said:**
> it started to disconnect me again heres the new wireless script ```
(Region : "en_US.UTF-8")
**country [COLOR="#FF0000"]00[/COLOR]**:
....
<snip>
....
iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    **[COLOR="#FF0000"]Channel:8[/COLOR]**
```
Everything looks good except the above two settings. The country code for regdomain settings is something I have been ignoring so far, but let's see if explicitly defining it helps..

Assuming you are in 'US', please run the following code in a terminal -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Reboot and check -
```
iw reg get
```
You should see "country US:" instead of "00". If so, does it help keeping the connection stable?

Regarding the router/access-point's channel, it seems you are using "auto" mode for channel in the router, because the channel has been changing in your different reports. Please log into your router's web interface, and FIX the channel to 1 or 11. Apart from that, also fix the channel bandwidth to 20 MHz instead of 20/40 MHz auto mode (if the router has the option to change this setting). Reboot the router after saving the changes, also reboot the laptop to be extra sure, and let us know if it helped.

---

### Post by rafael10 on 2014-06-26
its still kicking me offline

---

### Post by varunendra on 2014-06-28
Then I guess it's time for me to give up. I have nothing more to suggest. :(

---

### Post by rafael10 on 2014-07-02
heres my final wireless script if u see something new just reply ```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Alpha 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7869 MB
Uptime : 19:19:06 up 56 min,  2 users,  load average: 1.85, 1.43, 1.39


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4170]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 025: ID 04f3:010c Elan Microelectronics Corp. 
Bus 001 Device 004: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 027: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"belkin.986"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 belkin.986>   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: hci0: Bluetooth                no            no
1: asus-wlan: Wireless LAN        no            no
2: asus-bluetooth: Bluetooth      no            no
3: phy0: Wireless LAN             no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189774  0 
mac80211              626557  1 iwlmvm
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=1
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=N | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=1 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=====================o=============o=========o==============o=========o===========o==============o===========
 wlan0  [belkin.986] | 802.11 WiFi | iwlwifi | connected    | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    2WIRE951:        Infra, <MAC C-03 2WIRE951>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    NETGEAR95:       Infra, <MAC C-05 NETGEAR95>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    MyCharterWiFi71-2G: Infra, <MAC C-02 MyCharterWiFi71-2G>, Freq 2422 MHz, Rate 54 Mb/s, Strength 42 WPA2
    2WIRE000:        Infra, <MAC C-04 2WIRE000>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    2WIRE497:        Infra, <MAC C-NA 2WIRE497 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE771:        Infra, <MAC C-NA 2WIRE771 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    *belkin.986:     Infra, <MAC C-01 belkin.986>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA2

    Address:         192.168.2.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                | Wired       | r8169   | unavailable  | no      |           |              | <MAC eth0>
---------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

belkin.986           : ssid=belkin.986 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.086/1.370/1.654/0.284 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.163/1.170/1.178/0.035 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.024/0.025/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
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
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 belkin.986>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"belkin.986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000363936d7
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 MyCharterWiFi71-2G>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MyCharterWiFi71-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ecfd43ab8
                    Extra: Last beacon: 3824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 2WIRE951>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"2WIRE951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007b519f9e
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 2WIRE000>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"2WIRE000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003eb494a46d
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 NETGEAR95>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR95"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000338b57efa
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     964B69F7EBC572BE39F5C50
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
filename:       /lib/modules/3.13.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlmvm.conf       : options iwlmvm power_scheme=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi bt_coex_active=N swcrypto=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=1bac92c1-18ae-4b7a-8223-d2adad876efd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.698465] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.698799] audit: initializing netlink socket (disabled)
[    0.873536] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.928715] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   11.057896] wmi: Mapper loaded
[   11.106378] iwlwifi 0000:03:00.0: irq 63 for MSI/MSI-X
[   11.283013] asus_wmi: ASUS WMI generic driver loaded
[   11.285684] asus_wmi: Initialization: 0x1
[   11.285729] asus_wmi: BIOS WMI version: 7.9
[   11.285783] asus_wmi: SFUN value: 0x4a0877
[   11.288223] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[   11.293694] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   11.293695] iwlwifi 0000:03:00.0: Falling back to user helper
[   11.306232] asus_wmi: Backlight controlled by ACPI video driver
[   11.382514] iwlwifi 0000:03:00.0: loaded firmware version 22.15.8.0 op_mode iwlmvm
[   11.395304] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   11.395355] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.395568] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   11.419781] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   11.512715] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   11.617107] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   14.074051] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.205589] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.205798] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   15.216984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.217308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.185468] wlan0: authenticate with <MAC C-01 belkin.986>
[   18.186184] wlan0: direct probe to <MAC C-01 belkin.986> (try 1/3)
[   18.388382] wlan0: direct probe to <MAC C-01 belkin.986> (try 2/3)
[   18.592334] wlan0: send auth to <MAC C-01 belkin.986> (try 3/3)
[   18.637248] wlan0: authentication with <MAC C-01 belkin.986> timed out
[   21.692949] wlan0: authenticate with <MAC C-01 belkin.986>
[   21.693598] wlan0: direct probe to <MAC C-01 belkin.986> (try 1/3)
[   21.894540] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[   21.952736] wlan0: send auth to <MAC C-01 belkin.986> (try 3/3)
[   21.954434] wlan0: authenticated
[   21.957917] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   22.201299] iwlwifi 0000:03:00.0: No association and the time event is over already...
[   22.201333] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[   25.100164] wlan0: associate with <MAC C-01 belkin.986> (try 2/3)
[   25.104467] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[   25.107117] wlan0: associated
[   25.107144] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.548341] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[   25.584872] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   25.585092] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   25.595969] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.886111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.930183] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   25.930398] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   25.941046] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.996197] wlan0: authenticate with <MAC C-01 belkin.986>
[   28.996805] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   29.000863] wlan0: authenticated
[   29.001956] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   29.005781] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[   29.008558] wlan0: associated
[   29.008588] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   74.167877] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[   77.071824] wlan0: authenticate with <MAC C-01 belkin.986>
[   77.072732] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[   77.074470] wlan0: authenticated
[   77.075260] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[   77.079117] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[   77.081721] wlan0: associated
[ 2220.588982] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2220.589949] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2220.591743] wlan0: authenticated
[ 2220.595239] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2220.611900] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2220.616727] wlan0: associated
[ 2233.789778] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2233.791498] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2233.793895] wlan0: authenticated
[ 2233.795917] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2233.810383] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2233.813631] wlan0: associated
[ 2238.283588] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2238.284417] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2238.286196] wlan0: authenticated
[ 2238.289496] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2238.293438] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2238.295779] wlan0: associated
[ 2241.031615] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2241.079719] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2241.080044] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2241.090731] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2241.376338] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2244.805335] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2244.806407] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2244.808164] wlan0: authenticated
[ 2244.809905] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2244.814681] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2244.817081] wlan0: associated
[ 2244.817132] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2251.164399] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2251.165110] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2251.169987] wlan0: authenticated
[ 2251.174252] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2251.181442] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2251.187420] wlan0: associated
[ 2266.944481] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2266.944705] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2266.955304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2267.249246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2270.286134] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2270.286826] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2270.288608] wlan0: authenticated
[ 2270.288796] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2270.297270] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2270.300424] wlan0: associated
[ 2270.300455] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2274.315944] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2274.316803] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2274.320428] wlan0: authenticated
[ 2274.322760] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2274.354764] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2274.357243] wlan0: associated
[ 2286.176692] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2286.221521] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2286.221741] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2286.232495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2286.533896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2286.591143] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2286.591355] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2286.601707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2287.027643] init: network-manager main process (822) killed by SEGV signal
[ 2287.027655] init: network-manager main process ended, respawning
[ 2292.950767] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2292.951505] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2292.953587] wlan0: authenticated
[ 2292.956202] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2292.964374] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2292.968404] wlan0: associated
[ 2292.968457] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2292.977916] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2292.979454] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2292.980062] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2292.981755] wlan0: authenticated
[ 2292.984175] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2292.988043] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2292.990469] wlan0: associated
[ 2300.391745] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2300.392545] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2300.394259] wlan0: authenticated
[ 2300.396066] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2300.400088] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2300.402522] wlan0: associated
[ 2303.081656] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2303.130661] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2303.130954] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2303.141845] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2303.413169] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2306.843940] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2306.844671] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2306.848213] wlan0: authenticated
[ 2306.849315] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2306.853154] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2306.855637] wlan0: associated
[ 2306.855665] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2310.904536] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2310.905345] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2310.907049] wlan0: authenticated
[ 2310.911059] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2310.915308] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2310.921962] wlan0: associated
[ 2323.341789] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2323.342786] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2323.344518] wlan0: authenticated
[ 2323.349790] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2323.361742] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2323.364234] wlan0: associated
[ 2327.019451] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2327.020277] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2327.021979] wlan0: authenticated
[ 2327.026079] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2327.031472] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2327.033866] wlan0: associated
[ 2333.897649] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2333.897865] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2333.908432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2334.165110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2337.308431] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2337.320355] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2337.322900] wlan0: authenticated
[ 2337.324384] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2337.329321] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2337.332144] wlan0: associated
[ 2337.332172] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2341.452029] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2341.453171] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2341.454908] wlan0: authenticated
[ 2341.458060] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2341.461934] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2341.464346] wlan0: associated
[ 2350.302137] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2350.357533] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2350.357768] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2350.368795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2350.628105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2350.772331] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2350.772553] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2350.786637] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2353.845065] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2353.845688] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2353.847448] wlan0: authenticated
[ 2353.851766] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2353.858972] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2353.863450] wlan0: associated
[ 2353.863478] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2402.762393] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2402.763347] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2402.765083] wlan0: authenticated
[ 2402.768242] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2402.772122] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2402.777049] wlan0: associated
[ 2407.458533] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2407.459734] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2407.461560] wlan0: authenticated
[ 2407.465635] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2407.469479] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2407.471905] wlan0: associated
[ 2411.924256] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2411.924485] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2411.935304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2412.238921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2417.977348] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2417.978166] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2417.979973] wlan0: authenticated
[ 2417.983785] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2417.987667] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2417.989664] wlan0: associated
[ 2417.989690] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2417.999468] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2418.001175] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2418.001851] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2418.308789] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 2418.308828] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 2421.207602] wlan0: authenticated
[ 2421.210045] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2421.214379] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2421.216836] wlan0: associated
[ 2421.572770] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2421.612837] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2421.613061] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2421.624244] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2421.887133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2422.322685] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2422.322907] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2422.333538] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2435.597126] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2435.598294] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2435.600041] wlan0: authenticated
[ 2435.601948] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2435.607254] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2435.609629] wlan0: associated
[ 2435.609656] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2444.486960] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2444.487787] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2444.490139] wlan0: authenticated
[ 2444.493574] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2444.499106] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2444.501535] wlan0: associated
[ 2448.092768] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2448.094153] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2448.096549] wlan0: authenticated
[ 2448.099937] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2448.103827] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2448.106270] wlan0: associated
[ 2453.109659] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2453.110369] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2453.112098] wlan0: authenticated
[ 2453.113258] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2453.117120] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2453.119611] wlan0: associated
[ 2466.495875] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2466.496737] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2466.498485] wlan0: authenticated
[ 2466.502276] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2466.506175] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2466.508658] wlan0: associated
[ 2470.097504] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2470.098227] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2470.099957] wlan0: authenticated
[ 2470.103788] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2470.107685] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=3)
[ 2470.111137] wlan0: associated
[ 2493.125019] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2493.129728] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2493.203224] wlan0: send auth to <MAC C-01 belkin.986> (try 2/3)
[ 2493.270606] wlan0: send auth to <MAC C-01 belkin.986> (try 3/3)
[ 2493.354732] wlan0: authentication with <MAC C-01 belkin.986> timed out
[ 2496.807096] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2496.808643] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2496.810486] wlan0: authenticated
[ 2496.812395] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2496.816291] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=2)
[ 2496.824303] wlan0: associated
[ 2497.912143] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2497.950545] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2497.950783] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2497.961952] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2498.238167] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2503.970285] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2503.971070] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2503.972848] wlan0: authenticated
[ 2503.976596] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2503.981075] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2503.983605] wlan0: associated
[ 2503.983657] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2503.994394] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2503.995988] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2503.996576] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2504.303434] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 2504.303456] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 2507.202228] wlan0: authenticated
[ 2507.206843] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2507.211092] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2507.213656] wlan0: associated
[ 2507.510375] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 2507.549172] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2507.549399] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2507.560564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2507.830808] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2507.961112] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2507.961342] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 2507.972631] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2524.424721] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2524.425730] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2524.428331] wlan0: authenticated
[ 2524.429032] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2524.433296] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2524.435700] wlan0: associated
[ 2524.435728] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2524.444581] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 2524.446945] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2524.447679] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2524.449415] wlan0: authenticated
[ 2524.453026] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2524.457054] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2524.459298] wlan0: associated
[ 2662.462207] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2662.463043] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2662.464764] wlan0: authenticated
[ 2662.468846] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2662.480836] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2662.483313] wlan0: associated
[ 2837.138744] wlan0: authenticate with <MAC C-01 belkin.986>
[ 2837.139619] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 2837.142749] wlan0: authenticated
[ 2837.143401] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 2837.147266] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 2837.147707] wlan0: associated
[ 3011.148053] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3011.148789] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3011.150519] wlan0: authenticated
[ 3011.154586] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3011.164084] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3011.166619] wlan0: associated
[ 3013.831211] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3013.866908] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3013.867130] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3013.878036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3014.149079] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3017.597273] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3017.598020] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3017.599724] wlan0: authenticated
[ 3017.603389] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3017.607251] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3017.612320] wlan0: associated
[ 3017.612395] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3184.432469] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3184.432705] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3184.443590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3184.736803] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3187.783648] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3187.785092] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3187.786819] wlan0: authenticated
[ 3187.788578] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3187.792442] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3187.795046] wlan0: associated
[ 3187.795093] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3193.321960] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3193.357281] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3193.357537] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3193.368435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3193.668328] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3193.793392] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3193.793612] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3193.805658] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3210.054659] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3210.055404] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3210.057139] wlan0: authenticated
[ 3210.060210] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3210.064209] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3210.066345] wlan0: associated
[ 3210.066434] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3210.080102] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 3210.081846] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3210.082435] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3210.084957] wlan0: authenticated
[ 3210.088183] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3210.092678] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3210.094474] wlan0: associated
[ 3360.337890] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3360.339736] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3360.347584] wlan0: authenticated
[ 3360.352185] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3360.359288] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3360.364080] wlan0: associated
[ 3365.747047] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3365.797946] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3365.798163] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3365.808966] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3366.108599] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3371.847257] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3371.847967] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3371.849718] wlan0: authenticated
[ 3371.853796] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3371.868086] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3371.871973] wlan0: associated
[ 3371.872053] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3371.887168] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=2)
[ 3371.889172] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3371.890238] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3372.196918] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3372.196953] wlan0: Connection to AP <MAC C-01 belkin.986> lost
[ 3375.816218] wlan0: authenticated
[ 3375.819595] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3375.824627] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3375.827507] wlan0: associated
[ 3376.195282] wlan0: deauthenticating from <MAC C-01 belkin.986> by local choice (reason=3)
[ 3376.237987] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3376.238210] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3376.249259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3376.521388] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3376.636036] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3376.636253] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 3376.646813] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3379.589641] wlan0: authenticate with <MAC C-01 belkin.986>
[ 3379.590313] wlan0: send auth to <MAC C-01 belkin.986> (try 1/3)
[ 3379.592024] wlan0: authenticated
[ 3379.593494] wlan0: associate with <MAC C-01 belkin.986> (try 1/3)
[ 3379.607149] wlan0: RX AssocResp from <MAC C-01 belkin.986> (capab=0x411 status=0 aid=7)
[ 3379.607772] wlan0: associated
[ 3379.608008] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

### Post by jeremy31 on 2014-07-03
A bug report indicates that this is fixed in a newer kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315202/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315202/comments/7)

---

### Post by rafael10 on 2014-07-03
How do I upgrade to that kernel?

---

### Post by varunendra on 2014-07-04
> **rafael10 said:**
> How do I upgrade to that kernel?

As per [comment #8]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315202/comments/8") on the bug report page, kernel 3.13.0.24 was also working as good as the kernel in comment #7 for the bug reporter. You already have a kernel newer than that. If you still wish to try a newer kernel (sometimes helps), you must manually download and install the required packages from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

You currently have a 64 bit installation, so you'll have to download ...x86_64.deb packages for the kernel version you want. Proper installation requires both the kernel image (linux-image-<version>) and related headers (linux-headers-<version>). Installation can be done via either double-click or with 'sudo dpkg -i <package name>' command.

---

### Post by rafael10 on 2014-07-04
when i try installing the header i get this [http://gyazo.com/3c2b51bd9ca4489e92fcb7ac98d5803e](http://gyazo.com/3c2b51bd9ca4489e92fcb7ac98d5803e)

---

### Post by varunendra on 2014-07-04
You need to install the "linux-headers-<version>....._all.deb" package first, which has also been provided there, this link : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-headers-3.15.0-031500rc3_3.15.0-031500rc3.201404280035_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-rc3-utopic/linux-headers-3.15.0-031500rc3_3.15.0-031500rc3.201404280035_all.deb)

---

### Post by rafael10 on 2014-07-04
how can i check to make sure it instaled correctly

---

### Post by jeremy31 on 2014-07-04
reboot and see if ```
uname -r
``` reflects the kernel being 3.15.....

---


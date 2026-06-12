---
title: "HP Pavilion wifi soft disable"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by joefunsch on 2016-08-20
My neighbor just bought a new HP Pavilion notebook with Windows10home  installed.  They had me put Ubuntu on it as a dual boot system and all  has gone very well there with the exception that the WiFi doesn't work.   I used my USB WiFi adapter to get connected to the internet as the  computer does not have a LAN port, so WiFi is your only way of getting  out.

Once connected, I went to system and allowed 3rd party updates and then  updated.  The system says it's "Up to date".  Reboot.  After the reboot,  I was able to configure the on board WiFi radio and again all seemed  well.  Rebooted.

Neither of the WiFi radios work; well most of the time.  Some times I  can get the USB adapter to connect but it is through much trouble,  enabling, disabling the WiFi, etc.

I noticed in Network manager, If I turn the switch on for Either of the  WiFi radios, the switches automatically turn back off.  I'm sure there  is something in Ubuntu 16 that is messing with this.  Here's some more  data:
[INDENT=2]iwconfig
lo        no wireless extensions.

wlx801f029bea88  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
wlo1      IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ken@kens-pavilion:~$ sudo iwconfig wlx801f029bea88 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlx801f029bea88 ; Operation not supported.


ken@kens-pavilion:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/INDENT]



I've tried to force the "power on" for the wlx801f029bea88 but it  replies "Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlx801f029bea88 ; Operation not supported." as you can see above.

Any ideas?

Thanks,

---

### Post by joefunsch on 2016-08-20
wifi script results:

']0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n########## wireless info START ##########\n\n"

########## wireless info START ##########

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %  z")
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[   ]\+\(.\+\) - .*$/\1/p')
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")  [A
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 20 Aug 2016 21:24 EDT -0400

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 20 Aug 2016 00:00 EDT -0400

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 08 Jul 2016 02:16 UTC +0000
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### release ###########################\n\n"

##### release ###########################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### kernel ############################\n\n"

##### kernel ############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ uname -srvmpio
Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ echo

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parame  ters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### desktop ###########################\n\n"

##### desktop ###########################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.deskto  p")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Ubuntu
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### lspci #############################\n\n"

##### lspci #############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d  ; /^[^[:space:]]/ i\\'

01:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
    DeviceName: Intel WLAN Intel 3165NGWG Stone Peak 1 ac 1x1 + BT 4 LE PCIe+USB NGFF 2230 WW
    Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### lsusb #############################\n\n"

##### lsusb #############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b56d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 007: ID 2d42:5200  
Bus 001 Device 005: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### PCMCIA card info ##################\n\n"

##### PCMCIA card info ##################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### rfkill ############################\n\n"

##### rfkill ############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### lsmod #############################\n\n"

##### lsmod #############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODM  ATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ echo "$LSMOD"
rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
iwlmvm                311296  0
mac80211              737280  5 rtl8xxxu,rtl_usb,rtlwifi,iwlmvm,rtl8192cu
iwlwifi               200704  1 iwlmvm
hp_wmi                 16384  0
acer_wmi               20480  0
cfg80211              565248  4 iwlwifi,mac80211,rtlwifi,iwlmvm
sparse_keymap          16384  3 acer_wmi,hp_wmi,intel_hid
wmi                    20480  2 acer_wmi,hp_wmi
video                  40960  2 i915_bpo,acer_wmi
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### interfaces ########################\n\n"

##### interfaces ########################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key remove  d>/' /etc/network/interfaces
auto lo
iface lo inet loopback
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### ifconfig ##########################\n\n"

##### ifconfig ##########################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ IFCONFIG=$(ifconfig -a)
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ sed '/^lo /,/^$/d' <<< "$IFCONFIG"
wlo1      Link encap:Ethernet  HWaddr ac:2b:6e:dd:b8:cd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.  */\1/p' <<< "$IFCONFIG"))
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if (( ${#IFACESETH[@]} > 0 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### iwconfig ##########################\n\n"

##### iwconfig ##########################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ iwconfig
lo        no wireless extensions.

wlo1      IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### route #############################\n\n"

##### route #############################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### resolv.conf #######################\n\n"

##### resolv.conf #######################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ grep -v '^#' /etc/resolv.conf
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### network managers ##################\n\n"

##### network managers ##################

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "Installed:\n\n"
Installed:

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ for NETMGRNR in "${!NETMGRPATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
> NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
    NetworkManager
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRMATCHES// |/|}
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ NETMGRMATCHES="(${NETMGRMATCHES#|})"
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\nRunning:\n\n"

Running:

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone   found.\n"
root      2700     1  0 21:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### NetworkManager info ###############\n\n"

##### NetworkManager info ###############

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -x /usr/bin/nm-tool ]; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0  -9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE   device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-manager\")."
> fi
GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3165 (Dual Band Wireless AC 3165)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         AC:2B:6E:DD:B8:CD
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlo1
GENERAL.IP-IFACE:                       
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### NetworkManager.state ##############\n\n"

##### NetworkManager.state ##############

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### NetworkManager.conf ###############\n\n"

##### NetworkManager.conf ###############

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then  [A
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ 
]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ printf "\n##### NetworkManager profiles ###########\n\n"

##### NetworkManager profiles ###########

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ if [ -d /etc/NetworkManager/system-connections ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -  exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT"   --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     ORIGIFS="$IFS"
>     IFS=$'\n'
>     for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/  \1/p' <<< "$NMPROFILES"); do
> 
Display all 2406 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
> 
Display all 2406 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPR  OFILES"))
> 
Display all 2406 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\  n'
>     done
>     IFS="$ORIGIFS"
>     sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^  ]]*\]$/d'
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi
Sorry, try again.
Sorry, try again.

]0;ken@kens-pavilion: ~[01;32mken@kens-pavilion[00m:[01;34m~[00m$ '

---

### Post by chili555 on 2016-08-20
> My neighbor just bought a new HP Pavilion notebook But then we see:> 1: [COLOR="#FF0000"]acer[/COLOR]-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: noI don't think it is both an Acer and an HP, do you?

Please open a terminal and do:```
sudo -i
echo "blacklist acer-wmi"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot, detach the USB wireless and let us know how the internal wireless is working.

---

### Post by joefunsch on 2016-08-20
Thanks Chili-5^3!!

works perfectly.

I saw the "acer-wireless" thing, but didn't know if that was just the driver that was being used for this board.  Again, thanks.

regards,
Joe F.

---

### Post by chili555 on 2016-08-20
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---


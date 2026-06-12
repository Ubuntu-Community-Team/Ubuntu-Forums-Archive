---
title: "Netgear WNDA3100V2 installation problems"
date: 2016-10-08
forum: Networking &amp; Wireless
---

### Post by alann on 2016-10-08
I have been trying for two weeks to get the Netgear USB adaptor working in 16.04. (Works fine in XP and Win 10). I have just decided to try Linux after many years with xp win7 and win10 without problems but I am stuck with this one!
I ran the wireless info program and have attached the results. I cannot easily get a network connection by cable. Hope someone can help please.

```
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n########## wireless info START ##########\n\ 
n"


########## wireless info START ##########

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M 
 %Z %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system b 
oot[ ]\+\(.\+\) - .*$/\1/p')
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z 
 %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 08 Oct 2016 17:23 BST +0100

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 08 Oct 2016 00:00 BST +0100

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 08 Jul 2016 02:16 UTC +0000
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### release ###########################\n\ 
n"

##### release ###########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### kernel ############################\n\ 
n"

##### kernel ############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ uname -srvmpio
Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ echo

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/P 
arameters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### desktop ###########################\n\ 
n"

##### desktop ###########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
>  DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.deskto 
p")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Ubuntu
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lspci #############################\n\ 
n"

##### lspci #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^ 
--$/d; /^[^[:space:]]/ i\\'

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lsusb #############################\n\ 
n"

##### lsusb #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lsusb
Bus 002 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 005: ID 0e8f:0012 GreenAsia Inc. Joystick/Gamepad
Bus 002 Device 004: ID 04b8:084a Seiko Epson Corp. PX-501A [Stylus NX400]
Bus 002 Device 003: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### PCMCIA card info ##################\n\ 
n"

##### PCMCIA card info ##################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### rfkill ############################\n\ 
n"

##### rfkill ############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ rfkill list all
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lsmod #############################\n\ 
n"

##### lsmod #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$L 
SMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ echo "$LSMOD"

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### interfaces ########################\n\ 
n"

##### interfaces ########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key r 
emoved>/' /etc/network/interfaces
auto lo
iface lo inet loopback
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### ifconfig ##########################\n\ 
n"

##### ifconfig ##########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ IFCONFIG=$(ifconfig -a)
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed '/^lo /,/^$/d' <<< "$IFCONFIG"
enp3s0    Link encap:Ethernet  HWaddr 20:cf:30:01:c4:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethe 
rnet.*/\1/p' <<< "$IFCONFIG"))
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if (( ${#IFACESETH[@]} > 0 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### iwconfig ##########################\n\ 
n"

##### iwconfig ##########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### route #############################\n\ 
n"

##### route #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### resolv.conf #######################\n\ 
n"

##### resolv.conf #######################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ grep -v '^#' /etc/resolv.conf
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### network managers ##################\n\ 
n"

##### network managers ##################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Installed:\n\n"
Installed:

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ for NETMGRNR in "${!NETMGRPATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
>  NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
    NetworkManager
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES=${NETMGRMATCHES// |/|}
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES="(${NETMGRMATCHES#|})"
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\nRunning:\n\n"

Running:

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\ 
tNone found.\n"
root      2619     1  0 17:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager info ###############\n\ 
n"

##### NetworkManager info ###############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -x /usr/bin/nm-tool ]; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0 
-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE 
 device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-manager\")."
> fi
GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         20:CF:30:01:C4:B0
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/enp3s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager.state ##############\n\ 
n"

##### NetworkManager.state ##############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager.conf ###############\n\ 
n"

##### NetworkManager.conf ###############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; 
 then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager profiles ###########\n\ 
n"

##### NetworkManager profiles ###########

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -d /etc/NetworkManager/system-connections ]; then 
[A
>     if [ -n "$SUDO" ]; then
>  trap "" 2 3
>  NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f - 
exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT"  
--} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
>  trap 2 3
>  if [ "$SUDOSUCCESS" = "yes" ]; then
>      ORIGIFS="$IFS"
>      IFS=$'\n'
>      for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/ 
\1/p' <<< "$NMPROFILES"); do
>  
Display all 2408 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
>  
Display all 2408 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPR 
OFILES"))
>  
Display all 2408 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\ 
n'
>      done
>      IFS="$ORIGIFS"
>      sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^ 
]]*\]$/d'
>  else
>      printf "\nAcquisition of admin privileges failed.\n"
>  fi
>     else
>  echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi
Sorry, try again.
Sorry, try again.

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 

I have been trying for two weeks to get the netgear USB adaptor working in 16.04. (Works fine in XP and Win 10) I am new to Linux .
I ran the wireless info program and have attached the results. I cannot easily get a network connection by cable. Hope someone can help please.
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n########## wireless info START ##########\n\ 
n"

########## wireless info START ##########

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M 
 %Z %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system b 
oot[ ]\+\(.\+\) - .*$/\1/p')
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z 
 %z")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 08 Oct 2016 17:23 BST +0100

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 08 Oct 2016 00:00 BST +0100

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 08 Jul 2016 02:16 UTC +0000
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### release ###########################\n\ 
n"

##### release ###########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### kernel ############################\n\ 
n"

##### kernel ############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ uname -srvmpio
Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ echo

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/P 
arameters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### desktop ###########################\n\ 
n"

##### desktop ###########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
>  DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.deskto 
p")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Ubuntu
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lspci #############################\n\ 
n"

##### lspci #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^ 
--$/d; /^[^[:space:]]/ i\\'

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lsusb #############################\n\ 
n"

##### lsusb #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ lsusb
Bus 002 Device 006: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 005: ID 0e8f:0012 GreenAsia Inc. Joystick/Gamepad
Bus 002 Device 004: ID 04b8:084a Seiko Epson Corp. PX-501A [Stylus NX400]
Bus 002 Device 003: ID 04d9:048e Holtek Semiconductor, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### PCMCIA card info ##################\n\ 
n"

##### PCMCIA card info ##################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### rfkill ############################\n\ 
n"

##### rfkill ############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ rfkill list all
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### lsmod #############################\n\ 
n"

##### lsmod #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$L 
SMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ echo "$LSMOD"

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### interfaces ########################\n\ 
n"

##### interfaces ########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key r 
emoved>/' /etc/network/interfaces
auto lo
iface lo inet loopback
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### ifconfig ##########################\n\ 
n"

##### ifconfig ##########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ IFCONFIG=$(ifconfig -a)
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ sed '/^lo /,/^$/d' <<< "$IFCONFIG"
enp3s0    Link encap:Ethernet  HWaddr 20:cf:30:01:c4:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethe 
rnet.*/\1/p' <<< "$IFCONFIG"))
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if (( ${#IFACESETH[@]} > 0 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### iwconfig ##########################\n\ 
n"

##### iwconfig ##########################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### route #############################\n\ 
n"

##### route #############################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### resolv.conf #######################\n\ 
n"

##### resolv.conf #######################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ grep -v '^#' /etc/resolv.conf
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### network managers ##################\n\ 
n"

##### network managers ##################

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "Installed:\n\n"
Installed:

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ for NETMGRNR in "${!NETMGRPATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
>  NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
    NetworkManager
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES=${NETMGRMATCHES// |/|}
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ NETMGRMATCHES="(${NETMGRMATCHES#|})"
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\nRunning:\n\n"

Running:

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\ 
tNone found.\n"
root      2619     1  0 17:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager info ###############\n\ 
n"

##### NetworkManager info ###############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -x /usr/bin/nm-tool ]; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0 
-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE 
 device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-manager\")."
> fi
GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         20:CF:30:01:C4:B0
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/enp3s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager.state ##############\n\ 
n"

##### NetworkManager.state ##############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ cat -s /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager.conf ###############\n\ 
n"

##### NetworkManager.conf ###############

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; 
 then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ 
]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ printf "\n##### NetworkManager profiles ###########\n\ 
n"

##### NetworkManager profiles ###########

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$ if [ -d /etc/NetworkManager/system-connections ]; then 
[A
>     if [ -n "$SUDO" ]; then
>  trap "" 2 3
>  NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f - 
exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT"  
--} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
>  trap 2 3
>  if [ "$SUDOSUCCESS" = "yes" ]; then
>      ORIGIFS="$IFS"
>      IFS=$'\n'
>      for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/ 
\1/p' <<< "$NMPROFILES"); do
>  
Display all 2408 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
>  
Display all 2408 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPR 
OFILES"))
>  
Display all 2408 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\ 
n'
>      done
>      IFS="$ORIGIFS"
>      sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^ 
]]*\]$/d'
>  else
>      printf "\nAcquisition of admin privileges failed.\n"
>  fi
>     else
>  echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi
Sorry, try again.
Sorry, try again.

]0;alan@radioroom: ~/Desktop [01;32malan@radioroom[00m:[01;34m~/Desktop[00m$
```

---

### Post by jeremy31 on 2016-10-08
This older thread should work [https://ubuntuforums.org/showthread.php?t=2221251](https://ubuntuforums.org/showthread.php?t=2221251)

---

### Post by alann on 2016-10-09
Thanks for your quick reply. I have tried to install ndisgtk and ndiswrapper but have not had any success in getting then to install. I get a variety of error messages all of which i try to hunt down and address but so far I have not been able to install those programs. I have just ordered a couple of different USB wireless sticks to see if any of them will work. Any other help gratefully received.

---

### Post by jeremy31 on 2016-10-09
I have a TP-Link TL-WN722N 150Mbps that works well in Ubuntu.  I would avoid the smaller usb cards as people complain about poor signal strength

---

### Post by praseodym on 2016-10-09
Try this way:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
```

---

### Post by alann on 2016-10-09
Thanks Jeremy I have ordered a couple of small usb cards and if they work in Linux (which they claim in their specs) then at least i will know that  a more expensive one of the same make should work and then worth getting.

I have a post from praseodym with some more information on how to install and have just tried that but it still doesn't work. It seems as though it can't find the package files and keeps trying to go on the web to a repository. I will reply to him and see what he suggests.
Many thanks again for your help.

---

### Post by alann on 2016-10-09
Thanks for your reply. I have tried your code but i now get an error message saying it can't find the files. I think it is still trying to get the files via the repository. I tried putting the files into downloads and then ran your script from there and also tried other locations.  Below is the copy from the terminal.

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms


alan@radioroom:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndisgtk
E: Unable to locate package ndiswrapper-dkms
alan@radioroom:~$

---


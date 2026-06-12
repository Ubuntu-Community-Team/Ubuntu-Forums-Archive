---
title: "Slow internet Atheros AR242x driver ath5k with Ubuntu 16 lts"
date: 2017-10-28
forum: Networking &amp; Wireless
---

### Post by 12gimatuy on 2017-10-28
After two days on this forum searching for a solution, I need help to solve this painfully slow internet on my hp pavillion dv5 , with qualcomm atheros 242x/542x driver ath5k.
Tried to install driver ath9k, madwifi, nothing worked, with problem alog the path.
So, in the end, HELP

---

### Post by ajgreeny on 2017-10-28
See **Wireless-Info** in my signature below and follow the instructions there to run the Wifi-Info-Script.	 Post back the output you get in code tags please, (see below for a how-to), which will show us a lot more about your system's wifi setup.

---

### Post by 12gimatuy on 2017-10-29
Here the script, i hope, PS thanx for the time
[COLOR=#000000] [/COLOR][B]```

[/B]]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n########## wirel 
ess info START ##########\n\n"


########## wireless info START ##########


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ REPORTDATE=$(date +"%d %b  
%Y %H:%M %Z %z")
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ SCRIPTDATE=$(date -u -d "$ 
SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ LASTBOOTDT=$(last -FRn 1 r 
eboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*/\1/p')
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ LASTBOOTDT=$(date -d "$LAS 
TBOOTDT" +"%d %b %Y %H:%M %Z %z")
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "Report from: %s\n\ 
n" "$REPORTDATE"
Report from: 29 Oct 2017 10:15 CET +0100


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "Booted last: %s\n\ 
n" "$LASTBOOTDT"
Booted last: 29 Oct 2017 00:00 CEST +0200


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "Script from: %s\n" 
 "$SCRIPTDATE"
Script from: 25 Mar 2017 07:04 UTC +0000
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### release ## 
#########################\n\n"


##### release ###########################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ lsb_release -idrc
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### kernel ### 
#########################\n\n"


##### kernel ############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ uname -srvmpio
Linux 4.10.0-37-generic #41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ echo


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ sed 's/root=[^ ]*//;s/[ ]\ 
+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline
Parameters: ro, quiet, splash, vt.handoff=7
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### desktop ## 
#########################\n\n"


##### desktop ###########################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -n "$DESKTOP_SESSION" 
 ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -n "$DESKTOP" ]; then 
[A
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$D 
ESKTOP.desktop")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Ubuntu
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### lspci #### 
#########################\n\n"


##### lspci #############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ lspci -nnk | grep -iA 2 '^ 
[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'


08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company AR242x / AR542x Wireless Network Adapter (PCI-Express) [103c:137b]
	Kernel driver in use: ath5k


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:3600]
	Kernel driver in use: r8169
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### lsusb #### 
#########################\n\n"


##### lsusb #############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0408:03ba Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### PCMCIA car 
d info ##################\n\n"


##### PCMCIA card info ##################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -x /sbin/pccardctl ]; 
 then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\"). 
"
> fi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### rfkill ### 
#########################\n\n"


##### rfkill ############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ rfkill list all
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no
11: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### lsmod #### 
#########################\n\n"


##### lsmod #############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ LSMOD=$(lsmod | egrep "(^| 
[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ] 
|$)")
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ echo "$LSMOD"
ath5k                 147456  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k,ath9k_common
wl                   6447104  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ath                    28672  4 ath9k_hw,ath9k,ath5k,ath9k_common
mac80211              782336  2 ath9k,ath5k
cfg80211              602112  6 wl,mac80211,ath9k,ath,ath5k,ath9k_common
wmi                    16384  1 hp_wmi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### interfaces 
 ########################\n\n"


##### interfaces ########################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ sed '/^#/d;s/^wpa-psk [[:g 
raph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces
auto lo
iface lo inet loopback
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### ifconfig # 
#########################\n\n"


##### ifconfig ##########################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -x /sbin/ifconfig ];  
then
>     IFCONFIG=$(ifconfig -a)
> else
>     IFCONFIG=$(ip address show)
> fi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ echo "$IFCONFIG"
enp9s0    Link encap:Ethernet  HWaddr 00:1e:68:e6:0a:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:410986 (410.9 KB)  TX bytes:410986 (410.9 KB)


wlp8s0    Link encap:Ethernet  HWaddr 00:23:4d:2e:0c:f6  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe2e:cf6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:310613636 (310.6 MB)  TX bytes:18228937 (18.2 MB)
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ IFCONFIG=$(sed -n '1h; 1!H 
; ${g;s/\n /\\ /g;p}' <<< "$IFCONFIG")
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ IFACESETH=($(sed -n 's/^\( 
[^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p; s#^[0-9]\+: \([^ :]\+\):.* 
 link/ether.*#\1#p' <<< "$IFCONFIG"))
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if (( ${#IFACESETH[@]} > 0 
 )); then
>     IFETHMATCHES=${IFACESETH[@]}
>     IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
> fi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### iwconfig # 
#########################\n\n"


##### iwconfig ##########################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ iwconfig
lo        no wireless extensions.


enp9s0    no wireless extensions.


wlp8s0    IEEE 802.11  ESSID:"TIM-47577502"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 78:81:02:38:E9:5B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:20   Missed beacon:0


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### route #### 
#########################\n\n"


##### route #############################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -x /sbin/route ]; the 
n
>     route -n
> else
>     ip route show
> fi
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp8s0
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### resolv.con 
f #######################\n\n"


##### resolv.conf #######################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ grep -v '^#' /etc/resolv.c 
onf
nameserver 127.0.1.1
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### network ma 
nagers ##################\n\n"


##### network managers ##################


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "Installed:\n\n"
Installed:


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ for NETMGRNR in "${!NETMGR 
PATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
> NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\t%s\n" "${NETMGRI 
NST[@]:-None found.}"
	NetworkManager
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRPATH 
S[@]/#*\//|}
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ NETMGRMATCHES=${NETMGRMATC 
HES// |/|}
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ NETMGRMATCHES="(${NETMGRMA 
TCHES#|})"
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\nRunning:\n\n"


Running:


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ ps -ef | egrep "( |/)$NETM 
GRMATCHES($| )" || printf "\tNone found.\n"
root     18103     1  0 Oct28 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### NetworkMan 
ager info ###############\n\n"


##### NetworkManager info ###############


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -x /usr/bin/nm-tool ] 
; then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^ 
$/d; /^AP\[[0-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY, 
ACTIVE,IN-USE device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-mana 
ger\")."
> fi
GENERAL.DEVICE:                         wlp8s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR242x / AR542x Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.10.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         00:23:4D:2E:0C:F6
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:08:00.0/net/wlp8s0
GENERAL.IP-IFACE:                       wlp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TIM-47577502
GENERAL.CON-UUID:                       a2d22ce7-5109-4161-bc4d-99821d9b8ad0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a2d22ce7-5109-4161-bc4d-99821d9b8ad0 | TIM-47577502
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1509289988
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = homenet.telecomitalia.it
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 21600
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::223:4dff:fe2e:cf6/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         00:1E:68:E6:0A:84
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/0000:09:00.0/net/enp9s0
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




SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
TIM-47577502       78:81:02:38:E9:5B  Infra  1     2412 MHz  54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA2         yes     * 
Alice-95403789     00:1D:8B:5D:45:E0  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2    no        
Casa               00:04:ED:9F:4B:88  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
WOW FI - FASTWEB   A6:B1:E9:DE:4D:4B  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA2 802.1X  no        
TNCAPDE4D4A        A4:B1:E9:DE:4D:4A  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2    no        
DLINK              EC:08:6B:9F:09:70  Infra  7     2442 MHz  54 Mbit/s  17      &#9602;___  WPA2         no        
Vodafone-WiFi      BC:15:AC:64:9B:CB  Infra  1     2412 MHz  54 Mbit/s  12      &#9602;___  --           no        
Vodafone-34751047  BC:15:AC:64:9B:C9  Infra  1     2412 MHz  54 Mbit/s  9       &#9602;___  WPA2         no        
gointernet-N84D2   F8:35:DD:C2:84:2F  Infra  5     2432 MHz  54 Mbit/s  9       &#9602;___  WPA1 WPA2    no        
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### NetworkMan 
ager.state ##############\n\n"


##### NetworkManager.state ##############


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ cat -s /var/lib/NetworkMan 
ager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### NetworkMan 
ager.conf ###############\n\n"


##### NetworkManager.conf ###############


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ grep -v '^#' /etc/NetworkM 
anager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -f /etc/NetworkManage 
r/nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\ 
n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ printf "\n##### NetworkMan 
ager profiles ###########\n\n"


##### NetworkManager profiles ###########


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ if [ -d /etc/NetworkManage 
r/system-connections ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdept 
h 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment 
 "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="y 
es" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     ORIGIFS="$IFS"
>     IFS=$'\n'
>     for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireles 
s\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
> 
Display all 2480 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
> 
Display all 2480 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |; 
p" <<< "$NMPROFILES"))
> 
Display all 2480 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROF 
ILE[@]}"$'\n\n'
>     done
>     IFS="$ORIGIFS"
>     sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT"  
| sed '/^\[[^]]*\]$/d'
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


]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ unoduetre
unoduetre: command not found
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
]0;gima@gima-HP-Pavilion-dv5-Notebook-PC: ~[01;32mgima@gima-HP-Pavilion-dv5-Notebook-PC[00m:[01;34m~[00m$ 
**
```**

---


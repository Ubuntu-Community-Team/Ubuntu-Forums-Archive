---
title: "Lubuntu 15.04 Won’t see wireless connections"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by NathanPremo on 2015-07-18
Ok so I am working on a computer for a friend and they could not get on the internet. The issues was the CMOS batter was dead so I swapped out the CMOS battery and they bought another netbook battery to replace the one they had. However with all that done I do not feel ok with letting them using an older windows XP system online, even more so when they tell me they might use it to check their bank accounts. So I was looking for light weight OS’s because this being a netbook it does not have lot going for it. I heard about Lubuntu and how it was similar to windows and I thought it would be good. I downloaded 15.04 and used rufus to make a bootable flash drive. I tried it on my desktop with the live boot and it worked fine. I tried it on another actual laptop and it worked fine. When I first tried it on the netbook it would not boot. Turn out I need to use nomodeset. So after I get all this done I am finally able to boot. 

Now other laptop was able to see and connect to wireless point, the netbook is not. The nearest I can figure is a driver issue but I am unsure of where to find the drivers for this netbook and I do not want to install lubuntu until I can find them. I had a physical wireless shut off but trying to turn it on from there does nothing.

The netbook is a HSTNN-157C HP Mini. It is a intel ® Atom™ CPU N270 @ 1.60GHz. 504 MB of RAM, Windows XP Home Edition Version 2002 Service Pack 3.

I am still new to Linux and I am still learning about it so I do not know where to find these drivers. I am hesitant on install this Linux distro until I am able to find drivers for the wireless. If you could help me finding them or give me some idea on where to look that would be much appreciated.

---

### Post by slickymaster on 2015-07-18
Hi NathanPremo, welcome to the forums.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by NathanPremo on 2015-07-18
What information am I looking for in the wireless-info.txt

---

### Post by weatherman2 on 2015-07-18
Try to post all of it here, and use code tags if you can.

---

### Post by NathanPremo on 2015-07-18
Code tags?

I am posting this from another linux machine because windows messed up all the spacing when it is opened in notepad.


]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n########## wirele  ss info START ##########\n\n"

########## wireless info START ##########

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ REPORTDATE=$(date +"%d %b %  Y %H:%M %Z %z")
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ SCRIPTDATE=$(date -u -d "$S  CRIPTDATE" +"%d %b %Y %H:%M %Z %z")
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ LASTBOOTDT=$(last -FRn 1 re  boot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ LASTBOOTDT=$(date -d "$LAST  BOOTDT" +"%d %b %Y %H:%M %Z %z")
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "Report from: %s\n\n  " "$REPORTDATE"
Report from: 18 Jul 2015 15:38 UTC +0000

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "Booted last: %s\n\n  " "$LASTBOOTDT"
Booted last: 18 Jul 2015 15:21 UTC +0000

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "Script from: %s\n"   "$SCRIPTDATE"
Script from: 14 Jul 2015 17:04 UTC +0000
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### release ###  ########################\n\n"

##### release ###########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### kernel ####  ########################\n\n"

##### kernel ############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ uname -srvmpio
Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:01 UTC 2015 i686 i686 i686 GNU/Linux
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ echo

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ sed 's/root=[^ ]*//;s/[ ]\+  /, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline
file=/cdrom/preseed/lubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, ---, nomodeset
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### desktop ###  ########################\n\n"

##### desktop ###########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -n "$DESKTOP_SESSION"   ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/  $DESKTOP.desktop")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     printf "\nCould not be determined.\n"
> fi
Lubuntu
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### lspci #####  ########################\n\n"

##### lspci #############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ lspci -nnk | grep -iA 2 '^[  ^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
    Subsystem: Hewlett-Packard Company Device [103c:361a]
    Kernel driver in use: sky2
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### lsusb #####  ########################\n\n"

##### lsusb #############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ lsusb
Bus 001 Device 003: ID 10f1:1a08 Importek Internal Webcam
Bus 001 Device 004: ID 1e3d:2096 Chipsbank Microelectronics Co., Ltd 
Bus 001 Device 002: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### PCMCIA card   info ##################\n\n"

##### PCMCIA card info ##################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -x /sbin/pccardctl ];   then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\"  )."
> fi
'pccardctl' is not installed (package "pcmciautils").
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### rfkill ####  ########################\n\n"

##### rfkill ############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ rfkill list all
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### lsmod #####  ########################\n\n"

##### lsmod #############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ LSMOD=$(lsmod | egrep "(^|[  [:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:]   ]|$)")
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ echo "$LSMOD"
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
b43                   401408  0 
bcma                   49152  1 b43
mac80211              626688  1 b43
cfg80211              462848  2 b43,mac80211
ssb                    57344  1 b43
wmi                    20480  1 hp_wmi
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### interfaces   ########################\n\n"

##### interfaces ########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ sed '/^#/d;s/^wpa-psk [[:gr  aph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces
auto lo
iface lo inet loopback
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### ifconfig ##  ########################\n\n"

##### ifconfig ##########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ ifconfig -a | sed '/^lo /,/  ^$/d'
eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### iwconfig ##  ########################\n\n"

##### iwconfig ##########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### route #####  ########################\n\n"

##### route #############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### resolv.conf   #######################\n\n"

##### resolv.conf #######################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ grep -v '^#' /etc/resolv.co  nf
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### network man  agers ##################\n\n"

##### network managers ##################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "Installed:\n\n"
Installed:

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ for NETMGRNR in "${!NETMGRP  ATHS[@]}"; do
>     if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
> NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
>     fi
> done
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\t%s\n" "${NETMGRIN  ST[@]:-None found.}"
    NetworkManager
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ NETMGRMATCHES=${NETMGRPATHS  [@]/#*\//|}
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ NETMGRMATCHES=${NETMGRMATCH  ES// |/|}
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ NETMGRMATCHES="(${NETMGRMAT  CHES#|})"
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\nRunning:\n\n"

Running:

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ ps -ef | egrep "( |/)$NETMG  RMATCHES($| )" || printf "\tNone found.\n"
root      1247     1  0 15:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### NetworkMana  ger info ###############\n\n"

##### NetworkManager info ###############

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -x /usr/bin/nm-tool ];   then
>     nm-tool
> elif [ -x /usr/bin/nmcli ]; then
>     nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,  /^$/d; /^AP\[[0-9]\+\]\./d'
>     echo
>     nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURIT  Y,ACTIVE,IN-USE device wifi list
> else
>     echo "NetworkManager is not installed (package \"network-ma  nager\")."
> fi
GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8040 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### NetworkMana  ger.state ##############\n\n"

##### NetworkManager.state ##############

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ cat -s /var/lib/NetworkMana  ger/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### NetworkMana  ger.conf ###############\n\n"

##### NetworkManager.conf ###############

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ grep -v '^#' /etc/NetworkMa  nager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -f /etc/NetworkManager  /nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04)  :\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### NetworkMana  ger profiles ###########\n\n"

##### NetworkManager profiles ###########

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -d /etc/NetworkManager  /system-connections ]; then
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> NMPROFILES=$(find /etc/NetworkManager/system-connections -maxde  pth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --com  ment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCC  ESS="yes" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     ORIGIFS="$IFS"
>     IFS=$'\n'
>     for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wirel  ess\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
> 
Display all 1946 possibilities? (y or n)
> MWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
> 
Display all 1946 possibilities? (y or n)
> MWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1   |;p" <<< "$NMPROFILES"))
> 
Display all 1946 possibilities? (y or n)
> MWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPR  OFILE[@]}"$'\n\n'
>     done
>     IFS="$ORIGIFS"
>     sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT  " | sed '/^\[[^]]*\]$/d'
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "No NetworkManager profiles found."
> fi

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### iw reg get   ########################\n\n"

##### iw reg get ########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -x /sbin/iw ]; then
>     if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; the  n
> REGION=$(cat /etc/timezone)
> printf "Region: %s (based on set time zone)\n\n" "$REGION"
>     fi
>     echo "$IWREGGET"
> else
>     echo "'iw' is not installed (package \"iw\")."
> fi
Region: Etc/UTC (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### iwlist chan  nels ###################\n\n"

##### iwlist channels ###################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -x /sbin/iwlist ]; the  n
>     iwlist chan
> else
>     echo "'iwlist' is not installed (package \"wireless-tools\"  )."
> fi
lo        no frequency information.

eth0      no frequency information.

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### iwlist scan   #######################\n\n"

##### iwlist scan #######################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ if [ -x /sbin/iwlist ]; the  n
>     if [ -n "$SUDO" ]; then
> trap "" 2 3
> IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="y  es" || SUDOSUCCESS="no"
> trap 2 3
> if [ "$SUDOSUCCESS" = "yes" ]; then
>     if [[ $IWLISTSCAN = *Frequency:* ]]; then
> 
Display all 1946 possibilities? (y or n)
> tf "Channel occupancy:\n\n"
> 
Display all 1946 possibilities? (y or n)
:
!
./
[
[[
]]
{
}
2to3
2to3-2.7
2to3-3.4
a2p
aa-exec
aa-status
abiword
accept
accessdb
aconnect
acpi_available
add-apt-repository
addgroup
--More-- [K addpart
addr2line
add-shell
adduser
agetty
alert
alias
_allowed_groups
_allowed_users
alsa
alsactl
alsaloop
alsamixer
alsaucm
amidi
amixer
amuFormat.sh
anacron
anacron.distrib
aplay
aplaymidi
--More-- [K > uency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ]  [0-9]\+\)[ ]\+/     \1   APs on   /'
> 
40 Studies in Psychology/
Book for intro to business/
Books for business ethics/
Communication Skills for the  Processing of Words.pdf
Cyberethics Morality And Law In Cyberspace , 5th Edition.pdf
Effective Help Desk Specialist Skills, Gibson.pdf
Ethics on the Job.pdf
Fast Food Nation/
Hacking with Kali Preactical Penetraction Testing Techniques/
Hands-On Ethical Hacking and Network Defense, 2nd Edition/
.HPIMAGE.VFS
Infants Toddlers and Caregivers/
Jurassic Park.pdf
Lunsford-Everything's an Argument with Readings, 6e.zip
LW 220_Barber 6041-5 F14.pdf
Moral Issues in Business.pdf
MS Word 2013/
Network Guide to Networks.pdf
New Perspectives On Microsoft Excel 2013.pdf
New Perspectives on Microsoft PowerPoint 2013, Comprehensive, 1st Edition.pdf
OS X Support Essentials.pdf
--More-- [K Positive Child Guidance/
--More-- [K Programming Logic and Design, Comprehensive, 7th Edition.pdf
Psychology/
Records Management.pdf
Records Managment/
Walking for Fitness/
Windows 2000 MS-DOS Cammand Line.pdf
Windows 2000 MS-DOS Command Line/
wireless_info.sh
wireless-info.txt
>    fi
>     grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
> else
>     printf "\nAcquisition of admin privileges failed.\n"
> fi
>     else
> echo "No way to acquire admin privileges found."
>     fi
> else
>     echo "'iwlist' is not installed (package \"wireless-tools\"  )."
> fi
> 
> printf "\n##### module infos ######################\n\n"
> MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
> for MODULE in $MODULES; do
>     MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
>     printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
> done
> 
> printf "\n##### module parameters #################\n\n"
> for MODULE in $MODULES; do
>     if [ -d /sys/module/$MODULE/parameters ]; then
> MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/paramete  rs/* | sed 's#^.*/##;s/:/: /')
> printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
>     fi
> done
> 
> printf "\n##### /etc/modules ######################\n\n"
> grep -v '^#' /etc/modules
> 
> printf "\n##### modprobe options ##################\n\n"
> for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf  " -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/n  ull | sort); do
>     MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
bash: syntax error near unexpected token `('
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$     if [ -n "$MODPROBEOPTS"   ]; then
> printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
>     fi
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ done
bash: syntax error near unexpected token `done'
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### rc.local ##  ########################\n\n"

##### rc.local ##########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ grep -v '^#' /etc/rc.local

exit 0
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### pm-utils ##  ########################\n\n"

##### pm-utils ##########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ for PMUTILSFILE in $(find /  etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -  regex "$PMUTILSEXCL" | sort); do
>     PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
>     if [ -n "$PMUTFLCONT" ]; then
> PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
> printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUT  FLCONT"
>     fi
> done
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### udev rules   ########################\n\n"

##### udev rules ########################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ for UDEVRLFILE in /etc/udev  /rules.d/*net*.rules; do
>     UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?  $')
>     if [ -n "$UDEVRULES" ]; then
> printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
>     fi
> done
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n##### dmesg #####  ########################\n\n"

##### dmesg #############################

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ dmesg | tail -n 100 | egrep   "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:]   ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;  s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'
[   42.351046] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   42.423426] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   42.423452] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2062, Revision 2, Version 0
[   42.448227] b43 ssb0:0: Direct firmware load for b43/ucode15.fw failed with error -2 (repeated 2 times)
[   42.448383] b43 ssb0:0: Direct firmware load for b43-open/ucode15.fw failed with error -2 (repeated 2 times)
[   42.448444] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   42.448476] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   42.448505] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ printf "\n########## wirele  ss info END ############\n\n"

########## wireless info END ############

]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ 
]0;lubuntu@lubuntu: /media/lubuntu/BOOKSlubuntu@lubuntu:/media/lubuntu/BOOKS$ exec 2>&4 4>&-

---

### Post by weatherman2 on 2015-07-18
This is probably the relevant piece:

```

##### lspci #############################
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
Kernel driver in use: b43-pci-bridge

```

The Broadcom BCM4312 wireless chipset is know to have issues in Ubuntu.  I think it's a matter of the open source drivers not working or not existing.  (Ubuntu tries to load only open source software by default, not proprietary stuff.)  But there should be a proprietary driver available for this card.  It may help a lot if you can temporarily plug the netbook into a wired ethernet connection to get the wireless working, though.

It may be as easy as looking for "Additional Drivers" (when you are wired in temporarily) and installing any proprietary driver it finds.  But there is a driver already in use - it's just not working.

You may also do a web search for "BCM4312 ubuntu" and look for the recommended solutions.  I don't remember what works for that card these days.  Someone else here may just jump in with the right answer.

FYI, before you get too far along, did you realize that with Ubuntu, only LTS versions (released every two years, like 12.04 and 14.04) are supported for longer than nine months?  Lubuntu 15.04 will be supported only until January 2016 - then you will have to upgrade to get continued support.  By contrast, 14.04 will be supported until April 2019.  For an old netbook, I see no reason not to go with 14.04 myself especially if you are new to Ubuntu.

---

### Post by NathanPremo on 2015-07-18
"when you are wired in temporarily" 

Easier said than done. This Netbook doesn't actually have an RJ-45 Ethernet port. The additional drivers section does show information about a Broadcom driver but when I try to turn it on and apply the changes nothing happens.

---

### Post by weatherman2 on 2015-07-18
> **NathanPremo said:**
> "when you are wired in temporarily" 

Easier said than done. This Netbook doesn't actually have an RJ-45 Ethernet port. The additional drivers section does show information about a Broadcom driver but when I try to turn it on and apply the changes nothing happens.

That's surprising, given that an ethernet driver is listed in your output:

```

##### lspci #############################
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
Kernel driver in use: b43-pci-bridge


02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
Subsystem: Hewlett-Packard Company Device [103c:361a]
Kernel driver in use: sky2

```

---

### Post by NathanPremo on 2015-07-18
I do not know why it is list one but aren't any one the case.

---

### Post by weatherman2 on 2015-07-18
There should still be ways to install the driver without a direct internet connection.  Do some web sleuthing with that chipset "BCM4312" - that's what I would do.  You'll probably need to download a few files onto a thumbdrive with another working computer.

---


---
title: "Lan and wifi not working on ubuntu boot session but works from generic image boot"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by nolive721 on 2017-12-03
sorry in advance because not sure its an easy problem to explain and I am not a Linux expert at all[/FONT]
[FONT=inherit]I built few weeks ago a new rig, dual OS with Ubuntu 16.4LTS.Mobo is an ASROCK B350 PRO4 and comes with a Realtek RTL8111GR Lan. some time ago, I bought a USB Wifi dongle to connect my PC to my Chromecast devices, the dongle uses also a REALTEK chipset but wasn't recognized so I followed this tutorial to get the drivers to work and card to be recognized, it was quite painful but it worked in the end[/FONT]
[FONT=inherit][How do I get a Realtek RTL8723BE wireless card to work?]("https://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work")[/FONT]
[FONT=inherit]now since some recent Ubuntu software update, after a normal boot, there is no LAN and Wifi access anymore on my desktop, networking as a whole just dont work[/FONT]
[FONT=inherit]I have to launch a session from a generic image in the bootloader, one at the time I had installed the Wifi dongle, and both LAN and Wifi work as they should[/FONT]
[FONT=inherit]now Ubuntu is creating generic images since then and those also exhibit the same problem as the normal boot, no Networking at all[/FONT]
[FONT=inherit]any idea about what would have happened and how to troubleshoot this?[/FONT]
[FONT=inherit]thanks so much[/FONT]

---

### Post by mörgæs on 2017-12-05
Hi, welcome to the fora.

We get many posts from people running old software on new hardware, like yours. As a first step to prevent trouble in general I suggest that you begin with a fresh install of 17.10.

From 18.04 onwards you can probably take the LTS track.

---

### Post by nolive721 on 2017-12-05
thank you, I appreciate the welcome and reply

but what puzzles me is that network connection both lan and wifi works on a previous image of my 16.04LTS so considering I have installed quite few apps, media streaming softwares and all that on top of desktop customization,I would like to avoid ditching all that all that whenever possible

---

### Post by jeremy31 on 2017-12-05
What is the newest kernel you have?  Post results from terminal for ```
ls /lib/modules
```

---

### Post by nolive721 on 2017-12-05
4.10.0-37-generic  4.10.0-40-generic  4.4.0-97-generic
4.10.0-38-generic  4.4.0-101-generic  4.4.0-98-generic

currently logged in from 4.10.0-37-generic image where lan&wifi work

anything above network doesnt work

---

### Post by nolive721 on 2017-12-06
I have to correct myself, both  4.4.0-101-generic 4.4.0-98-generic dont have network working either, same as recent ones

any idea how I could troubleshoot this issue? any command to verify networking feature is active or not for example?

reinstall lan card and wifi usb dongle drivers entirely maybe?

Its set "enabled"in network settings but as I mentioned, no lan or wifi access whatsoever

why only this particular image 4.10.0-37-generic is working is  really puzzling me.

thanks in advance

---

### Post by jeremy31 on 2017-12-06
Post results for ```
lsusb; dkms status
```
I am still puzzled on how that RTL8723BE answer helped any as that is a PCI wifi not USB

---

### Post by nolive721 on 2017-12-06
to avoid a confusion, the link I sent about this RTL8723BE was a method I used to install my USB wifi dongle nothing else

this is what returns from both commands you asked me to run

Bus 004 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003:ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002:ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001:ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005:ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 001 Device 004:ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003:ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002:ID 045e:0772 Microsoft Corp. LifeCam Studio
Bus 001 Device 006:ID 152d:0539 JMicron Technology Corp. / JMicron USA Technology Corp.JMS539/567 SuperSpeed SATA II/III 3.0G/6.0G Bridge
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub


bbswitch, 0.8,4.10.0-37-generic, x86_64: installed
bbswitch, 0.8,4.10.0-38-generic, x86_64: installed
bbswitch, 0.8,4.10.0-40-generic, x86_64: installed
bbswitch, 0.8,4.4.0-101-generic, x86_64: installed
nvidia-384, 384.90,4.10.0-37-generic, x86_64: installed
nvidia-384, 384.90,4.10.0-38-generic, x86_64: installed
nvidia-384, 384.90,4.10.0-40-generic, x86_64: installed
nvidia-384, 384.90,4.4.0-101-generic, x86_64: installed
rtlwifi-new, 0.10,4.4.0-101-generic, x86_64: installed
rtlwifi-new, 0.10,4.4.0-97-generic, x86_64: installed
rtlwifi-new, 0.10,4.4.0-98-generic, x86_64: installed

---

### Post by jeremy31 on 2017-12-07
Try this
```
sudo apt install git
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2
```

Reboot

---

### Post by nolive721 on 2017-12-07
thank you again for your help.

just a sanity check before I proceed. It seems my ASROCK PRO4 Mobo LAN chipset is [COLOR=#CCCCCC][FONT=arial]RTL8111GR[/FONT][/COLOR]

and my WIFI USB one is as listed below  RTl8811AU(sorry about Japanese language, I live in Japan so I bought it here) but you are mentioning RTL8812AU. Does that mean both drivers are compatible?

_*&#20181;&#27096;*_
[COLOR=#333333][FONT=verdana]&#12481;&#12483;&#12503;&#65306;RTL8811AU[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]&#12481;&#12515;&#12531;&#12493;&#12523;&#65306;[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]2.4GHz&#24111; :1~13ch[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]5GHz&#24111; :   13/36/40/44/48/149/153/157/161/165ch[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]&#35373;&#23450;&#26041;&#24335;&#65306;WPS (&#12477;&#12501;&#12488; / &#12508;&#12479;&#12531;&#26041;&#24335;)[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]&#22806;&#24418;&#23544;&#27861; (&#24133;×&#39640;&#12373;)&#12288;&#32004;12.5&#65357;&#65357; × &#32004;140&#65357;&#65357;[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]&#36074;&#37327;&#65306;&#32004;50g[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-12-08
I can't be sure about the ethernet driver but your USB wifi is supported by the github source, the drivers aren't related for ethernet and wifi.  Check results for ```
lspci -nnk | grep -iA3 net
```
See if the ethernet uses r8169 module

---

### Post by nolive721 on 2017-12-08
no it uses r8168 since thats what shown from the cmd you suggested

any harm then to try install teh drivers as per your previous message?

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8168
	Kernel modules: r8168

---

### Post by jeremy31 on 2017-12-09
Are the results of the command the same with the kernels that don't have working ethernet?  The r8168 module is not a in tree kernel module in 4.4.0

You can install the driver from gihub for your USB wifi

---

### Post by nolive721 on 2017-12-09
the r8168 is with kernel 4.10.0-37-generic where both LAN and WIFI work

lspci -nnk | grep -iA3 net
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8168
	Kernel modules: r8168




r8169 module is with all other kernels and since dont have internet access,obviously, when running such Offline session , I cant run the commands you are advising

basically I am stuck

---

### Post by jeremy31 on 2017-12-09
How was the r8168 module installed, post results for ```
modinfo r8168
```

With a kernel that does have working ethernet do
```
sudo apt install git
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2 --all
```
That should install the module to all installed kernels

---

### Post by nolive721 on 2017-12-10
results output for modinfo cmd and trying to install module from network available kernel

> modinfo r8168filename:       /lib/modules/4.10.0-37-generic/kernel/drivers/net/ethernet/realtek/r8168.koversion:        8.045.08-NAPI
license:        GPL
description:    RealTek RTL-8168 Gigabit Ethernet driver
author:         Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion:     83F0B464A28DB94AB899112
alias:          pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
alias:          pci:v000010ECd00008161sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:        
vermagic:       4.10.0-37-generic SMP mod_unload 
parm:           speed_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           duplex_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           autoneg_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           aspm:Enable ASPM. (int)
parm:           s5wol:Enable Shutdown Wake On Lan. (int)
parm:           s5_keep_curr_mac:Enable Shutdown Keep Current MAC Address. (int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           timer_count:Timer Interrupt Interval. (int)
parm:           eee_enable:Enable Energy Efficient Ethernet. (int)
parm:           hwoptimize:Enable HW optimization function. (ulong)
parm:           s0_magic_packet:Enable S0 Magic Packet. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)


> nolive721@nolive721-desktop:~$git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
fatal: destinationpath 'rtl8812au' already exists and is not an empty directory.
nolive721@nolive721-desktop:~$sudo dkms add -m rtl8812au -v 4.2.2
Error! Could notfind module source directory.
Directory:/usr/src/rtl8812au-4.2.2 does not exist.
nolive721@nolive721-desktop:~$sudo dkms install -m rtl8812au -v 4.2.2
Error! Could notfind module source directory.
Directory:/usr/src/rtl8812au-4.2.2 does not exist.

---

### Post by jeremy31 on 2017-12-10
You already had the source, do
```
sudo dkms add ./rtl8812au
sudo dkms install -m rtl8812au -v 4.2.2 --all
```

---

### Post by nolive721 on 2017-12-11
both commands didnt do anything I am afraid.I am now in an internet session with access through my Iphone tethering and I see its called "Auto ethernet"

I am copying here the wirelessinfo.txt if that can help...

```
#!/bin/bash#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
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


SCRIPTDATE="2017-12-05 04:13 +0100"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"


MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|8(188|189|192|723|812)[acde][esu]|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
IFACEMATCHES="(wlan[0-9]|eth[0-9])"
DMESGMATCHES="(firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"


DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"


NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")
DEC2BI=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
DEC2HEX=($(printf "%02x " {0..255}))


export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"


if [ -t 0 ]; then
    DIALOGAPP="terminal"
    DIALOGBREAK=" "
    TERMOUT="yes"
elif [ -x /usr/bin/zenity ]; then
    DIALOGAPP="zenity"
    DIALOGBREAK="\n"
elif [ -x /usr/bin/kdialog ]; then
    DIALOGAPP="kdialog"
    DIALOGBREAK="\n"
else
    exit 1
fi


if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
    GKSUDO="yes"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
    KDESUDO="yes"
    KDESUDOCMT=" needs administrative privileges. Please enter your password."
fi


dialog_info () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1"
	    ;;
	zenity)
	    zenity --info --text="$1"
	    ;;
	kdialog)
	    kdialog --msgbox "$1"
	    ;;
    esac
}


dialog_error () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1" >&2
	    ;;
	zenity)
	    zenity --error --text="$1"
	    ;;
	kdialog)
	    kdialog --error "$1"
	    ;;
    esac
}


dialog_question () {
    case $DIALOGAPP in
	terminal)
	    local INPUT
	    read -r -p "$1 [Y/n]: " INPUT
	    echo "${INPUT,,}"
	    ;;
	zenity)
	    zenity --question --text="$1" || echo "no"
	    ;;
	kdialog)
	    kdialog --yesno "$1" || echo "no"
	    ;;
    esac
}


ip6-mac () {
    for MAC in "$@"; do
	OCT1BI=${DEC2BI[0x${MAC:0:2}]}
	OCT1BI7=$((${OCT1BI:6:1} - 1))
	OCT1BIM="${OCT1BI:0:6}${OCT1BI7#-}${OCT1BI:7}"
	IP6S+=${IP6S:+$'\n'}"${DEC2HEX[2#$OCT1BIM]}${MAC:3:2}:${MAC:6:2}ff:fe${MAC:9:2}:${MAC:12:2}${MAC:15:2}"
    done
    sed 's/\(^\|:\)0\+\([[:alnum:]]\)/\1\2/g;s/^\([0:]\+\)/\\(::\\|\1\\)/' <<< "$IP6S"
}


exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
	dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
	exit 1
    }
}
exec 2>&1


printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*/\1/p')
LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Booted last: %s\n\n" "$LASTBOOTDT"
printf "Script from: %s\n" "$SCRIPTDATE"


printf "\n##### release ###########################\n\n"
lsb_release -idrc


printf "\n##### kernel ############################\n\n"
uname -srvmpio
echo
sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline


printf "\n##### desktop ###########################\n\n"
if [ -n "$DESKTOP_SESSION" ]; then
    DESKTOP="$DESKTOP_SESSION"
else
    DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
	DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    printf "\nCould not be determined.\n"
fi


printf "\n##### lspci #############################\n\n"
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'


printf "\n##### lsusb #############################\n\n"
lsusb


printf "\n##### PCMCIA card info ##################\n\n"
if [ -x /sbin/pccardctl ]; then
    pccardctl info
else
    echo "'pccardctl' is not installed (package \"pcmciautils\")."
fi


printf "\n##### rfkill ############################\n\n"
rfkill list all


printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"


printf "\n##### interfaces ########################\n\n"
sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces


printf "\n##### ifconfig ##########################\n\n"
if [ -x /sbin/ifconfig ]; then
    IFCONFIG=$(ifconfig -a)
else
    IFCONFIG=$(ip address show)
fi
echo "$IFCONFIG"
IFCONFIG=$(sed -n '1h; 1!H; ${g;s/\n /\\ /g;p}' <<< "$IFCONFIG")
IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p; s#^[0-9]\+: \([^ :]\+\):.* link/ether.*#\1#p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi


printf "\n##### iwconfig ##########################\n\n"
iwconfig


printf "\n##### route #############################\n\n"
if [ -x /sbin/route ]; then
    route -n
else
    ip route show
fi


printf "\n##### resolv.conf #######################\n\n"
grep -v '^#' /etc/resolv.conf


printf "\n##### network managers ##################\n\n"
printf "Installed:\n\n"
for NETMGRNR in "${!NETMGRPATHS[@]}"; do
    if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
	NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
    fi
done
printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
NETMGRMATCHES=${NETMGRMATCHES// |/|}
NETMGRMATCHES="(${NETMGRMATCHES#|})"
printf "\nRunning:\n\n"
ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"


printf "\n##### NetworkManager info ###############\n\n"
if [ -x /usr/bin/nm-tool ]; then
    nm-tool
elif [ -x /usr/bin/nmcli ]; then
    nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
    echo
    nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
else
    echo "NetworkManager is not installed (package \"network-manager\")."
fi


printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state


printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi


printf "\n##### NetworkManager profiles ###########\n\n"
if [ -d /etc/NetworkManager/system-connections ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    ORIGIFS="$IFS"
	    IFS=$'\n'
	    for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
		NMWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
		NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
		NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
	    done
	    IFS="$ORIGIFS"
	    sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "No NetworkManager profiles found."
fi


printf "\n##### Netplan config ####################\n\n"
for NPLANFILE in $(find /{lib,etc,run}/netplan -name "*.yaml" 2> /dev/null | sort); do
    NPLANFLCNT=$(egrep -v '^(#|$)' $NPLANFILE)
    if [ -n "$NPLANFLCNT" ]; then
	printf "[%s]\n%s\n\n" "$NPLANFILE" "$NPLANFLCNT"
    fi
done


printf "\n##### iw reg get ########################\n\n"
if [ -x /sbin/iw ]; then
    if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
	REGION=$(cat /etc/timezone)
	printf "Region: %s (based on set time zone)\n\n" "$REGION"
    fi
    echo "$IWREGGET"
else
    echo "'iw' is not installed (package \"iw\")."
fi


printf "\n##### iwlist channels ###################\n\n"
if [ -x /sbin/iwlist ]; then
    iwlist chan
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi


printf "\n##### iwlist scan #######################\n\n"
if [ -x /sbin/iwlist ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    if [[ $IWLISTSCAN = *Frequency:* ]]; then
		printf "Channel occupancy:\n\n"
		grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
		echo
	    fi
	    grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi


printf "\n##### module infos ######################\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done


printf "\n##### module parameters #################\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
	MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
	printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done


printf "\n##### /etc/modules ######################\n\n"
grep -v '^#' /etc/modules


printf "\n##### modprobe options ##################\n\n"
for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
    MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
    if [ -n "$MODPROBEOPTS" ]; then
	printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
    fi
done


printf "\n##### rc.local ##########################\n\n"
grep -v '^#' /etc/rc.local


printf "\n##### pm-utils ##########################\n\n"
for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
    PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
    if [ -n "$PMUTFLCONT" ]; then
	PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
	printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
    fi
done


printf "\n##### udev rules ########################\n\n"
for UDEVRLFILE in $(find /etc/udev/rules.d -name "*net*.rules" | sort); do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
	printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done


printf "\n##### dmesg #############################\n\n"
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$IFACEMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'


printf "\n########## wireless info END ############\n\n"


exec 2>&4 4>&-
exec 1>&3 3>&-


##### MAC address masking #####


RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'


ORIGIFS="$IFS"
IFS=$'\n'


IFACESIDS=($(sed -n "/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/ {/\(00:\)\{5\}00/! {s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1'/p; s/^[0-9]\+: \([^ :]\+\):.*/'\1'/p}}" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n '/\(00:\)\{5\}00/! s#.*\(HWaddr\|link/[^ ]\+\) \(\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}\).*#\2#p' <<< "$IFCONFIG"))
IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))


WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))


WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{print "'\''" $1 "'\''"}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))


IFS="$ORIGIFS"


for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
    MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]} [IF$(($IFACENR + 1))]>;I;"
    IFACEMACC=${IFACESMACS[$IFACENR]//:/}
    if [[ ${IFACESIDS[$IFACENR],,} =~ ${IFACEMACC,,} ]]; then
	MACMASKSED+="s;\(${IFACESIDS[$IFACENR]:1:3}\)$IFACEMACC;\1<IF from MAC [IF$(($IFACENR + 1))]>;Ig;"
    fi
done


for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
    MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]}>;I;"
done


for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
    MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]} [AN$(($WLAPNMNR + 1))]>;I;"
done


sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"


##### The End #####


dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"


if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
	dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
	dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
fi


if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
    PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
    if [[ ! $PASTEBIN =~ ^no?$ ]]; then
	PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
	if [ "$PASTESUCCESS" = "yes" ]; then
	    dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
	else
	    if [ -n "$PASTERESULT" ]; then
		dialog_error "${TERMOUT+\n}Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
	    else
		dialog_error "${TERMOUT+\n}Pastebin failed, no error message given.${TERMOUT+\n}"
	    fi
	fi
    else
	echo
    fi
fi
```

---

### Post by jeremy31 on 2017-12-12
That is the wireless-info file not the wireless-info.txt that contains the results

---

### Post by nolive721 on 2017-12-13
apologies for showing my ignorance here.

this is the txt file output generated from the script but I can only run it from network enabled generic 4.10.0-37 kernel

---

### Post by jeremy31 on 2017-12-13
Boot into a kernel where nothing works, and in terminal ```
./wireless-info
```
Boot into a working kernel and post the new wireless-info.txt

---

### Post by nolive721 on 2017-12-14
voila

I have noticed the file is much smaller and seems to contain much less information than the one from a working kernel.

```
########## wireless info START ##########

Report from: 14 Dec 2017 20:46 JST +0900


Booted last: 14 Dec 2017 00:00 JST +0900


Script from: 05 Dec 2017 03:13 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel modules: r8169


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:a811 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 045e:0772 Microsoft Corp. LifeCam Studio
Bus 001 Device 006: ID 152d:0539 JMicron Technology Corp. / JMicron USA Technology Corp. JMS539/567 SuperSpeed SATA II/III 3.0G/6.0G Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


wmi                    16384  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261939 (261.9 KB)  TX bytes:261939 (261.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1231     1  0 20:45 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########
```

---

### Post by jeremy31 on 2017-12-14
Post results for ```
ls | grep '8168|8812'
```

---

### Post by nolive721 on 2017-12-15
that cmd didnt return anything, just nothing in the terminal or a generated file I could find sorry, still stuck here

---

### Post by jeremy31 on 2017-12-15
From your results in [https://ubuntuforums.org/showthread.php?t=2379250&p=13719527#post13719527](https://ubuntuforums.org/showthread.php?t=2379250&p=13719527#post13719527) 
It showed that you had rtl8812au in your home directory

Try booting into the newest kernel and do
```
cd rtl8812au
make clean
make
sudo make install
```
If you see any errors, copy the terminal output to a text file and post the contents from the working kernel, if no errors reboot back into the same kernel and see if wifi works

---

### Post by praseodym on 2017-12-15
Install the LAN driver:

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-1_all.deb)

Save it in /home and run

```
sudo dpkg -i *.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. LAN should work now

---

### Post by nolive721 on 2017-12-15
thanks both of you! both lan and wifi connectivity are back on the latest kernel.

only problem left is on cold boot, the wifi connection is not automatic, I need to unplug my USB dongle and replug then it works

I could live with that but any help to fix that very last problem is appreciated

---

### Post by nolive721 on 2017-12-15
i have just rebooted my machine and loaded the kernel where lan&wifi were working normally before and both adapters (lan and wireless) connect automatically actually

as I mentioned, ok to leave as it is but if I could fix that one, would be completely happy with my Ubuntu OS

thanks so much for your help

---

### Post by nolive721 on 2017-12-15
apologies I did bit more research and found a cmd to load wireless at boot and its all good now

again thank you so much for your help

---


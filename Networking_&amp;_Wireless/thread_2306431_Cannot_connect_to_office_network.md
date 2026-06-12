---
title: "Cannot connect to office network"
date: 2015-12-15
forum: Networking &amp; Wireless
---

### Post by nasser3 on 2015-12-15
Hello, 

I'm new to Ubuntu and this is my first time in forums.

I had an issue with office network .. Sometimes it get connected and i can access the internet but most of the time it fails to connect or very slow. I'm sure it's not a hardware issue because i can connect to any other network and it works fine.

I don't know what information to post .. any help?

Thanks,

---

### Post by Hadaka on 2015-12-15
Hi, It sounds like your office internet configuration is conflicting with your settings
or your office may have security set to block outside access. Please be attached
to your office network then go here...
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
follow the directions and post your wireless-info.text file so we may
help you find a solution.
thanks

---

### Post by nasser3 on 2015-12-16
Thanks for the replay

Unfortunately I got connected for few minutes yesterday and then I couldn't connect to the network at all. I copied the script from the link and I created the file but while being connected to other network. 

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


SCRIPTDATE="2015-09-27 02:34 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"


MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
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
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
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
IFCONFIG=$(ifconfig -a)
sed '/^lo /,/^$/d' <<< "$IFCONFIG"
IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi


printf "\n##### iwconfig ##########################\n\n"
iwconfig


printf "\n##### route #############################\n\n"
route -n


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
for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
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


IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFCONFIG"))
IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))


WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))


WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))


IFS="$ORIGIFS"


for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]-address}>;I;"
    MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]-from MAC}>;I;"
done


for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]-from MAC}>;I;"
done


for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]-from MAC}>;I;"
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

### Post by Hadaka on 2015-12-16
Hi, you posted the actual wireless script,we need the wireless-info.txt file
please try again.
thanks

---

### Post by slickymaster on 2015-12-16
> **Hadaka said:**
> Hi, you posted the actual wireless script,we need the wireless-info.txt file
please try again.
thanks

This ^^^
In order to do it, open a terminal window (Ctrl+Alt+T) and run the following```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by SeijiSensei on 2015-12-16
Can you connect to the office network with an Ethernet cable?  That's always much simpler and more reliable than wifi.

---

### Post by nasser3 on 2015-12-16
Hello .. Sorry for the stupid mistake .. The name of the office network is GuestNetwork

```


########## wireless info START ##########


Report from: 16 Dec 2015 19:12 GST +0400


Booted last: 16 Dec 2015 00:00 GST +0400


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380a]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lenovo Device [17aa:4026]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 001 Device 004: ID 5986:055d Acer, Inc 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 413c:2501 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
ath3k                  20480  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
bluetooth             516096  32 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
mac80211              733184  1 ath9k
cfg80211              548864  4 ath,ath9k_common,ath9k,mac80211
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
video                  36864  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.43.247  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59038926 (59.0 MB)  TX bytes:5124650 (5.1 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'AndroidAP' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:66   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       730     1  0 16:45 ?        00:00:10 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     AndroidAP
GENERAL.CON-UUID:                       1630c482-16ae-42b7-ab9b-d30c09c5e459
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/79
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{13,7,11,16,14}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   129cedfb-d74e-4696-890e-1a1fd27745a0 | GlobComp
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   1630c482-16ae-42b7-ab9b-d30c09c5e459 | AndroidAP
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   c0f833a9-c032-4466-ae4e-c4dac99fec99 | SAS-guest
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   19a35cc3-d3fd-4513-8789-b6b8f3781ef3 | GuestNetwork
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   d3a995a8-f00c-46b8-8940-b97e2c5f66a7 | SAS
IP4.ADDRESS[1]:                         192.168.43.247/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.247
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1450282337
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = nasser
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
GlobComp                   <MAC 'GlobComp' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1         no        
SAS                        <MAC 'SAS' [AC15]>  Infra  2     2417 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Ooredoo-B310-5BCD          <MAC 'Ooredoo-B310-5BCD' [AC8]>  Infra  9     2452 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        
Huawei-Employee            <MAC 'Huawei-Employee' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2 802.1X  no        
WirelessNet                <MAC 'WirelessNet' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
WirelessNet                <MAC 'WirelessNet' [AC6]>  Infra  4     2427 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  --           no        
HP-Print-DD-LaserJet 1102  <MAC 'HP-Print-DD-LaserJet 1102' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
SAS-guest                  <MAC 'SAS-guest' [AC5]>  Infra  2     2417 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
ITA-CONSULTANT             <MAC 'ITA-CONSULTANT' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2 802.1X  no        
GuestNetwork               <MAC 'GuestNetwork' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
ITA-MOBILE 2               <MAC 'ITA-MOBILE 2' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2 802.1X  no        
Ooredoo-B310-90A7          <MAC 'Ooredoo-B310-90A7' [AC11]>  Infra  13    2472 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2         no        
wlanaccessv2.0             <MAC 'wlanaccessv2.0' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2 802.1X  no        
Huawei-Employee            <MAC 'Huawei-Employee' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
AndroidAP                  <MAC 'AndroidAP' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2         yes     * 


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/dlink-BD74 1]] (600 root)
[connection] id=dlink-BD74 1 | type=wifi
[wifi] ssid=dlink-BD74 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SAS]] (600 root)
[connection] id=SAS | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=SAS
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Chromecast5770]] (600 root)
[connection] id=Chromecast5770 | type=wifi
[wifi] ssid=Chromecast5770 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AMJ Tech]] (600 root)
[connection] id=AMJ Tech | type=wifi
[wifi] ssid=AMJ Tech | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AkkasaWLAN]] (600 root)
[connection] id=AkkasaWLAN | type=wifi
[wifi] ssid=AkkasaWLAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Chromecast8784.b]] (600 root)
[connection] id=Chromecast8784.b | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=Chromecast8784.b
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GuestNetwork]] (600 root)
[connection] id=GuestNetwork | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=GuestNetwork
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=wifi
[wifi] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dlink-BD74]] (600 root)
[connection] id=dlink-BD74 | type=wifi
[wifi] ssid=dlink-BD74 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/oman]] (600 root)
[connection] id=oman | type=wifi
[wifi] ssid=oman | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DDS.om]] (600 root)
[connection] id=DDS.om | type=wifi
[wifi] ssid=DDS.om | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/costa]] (600 root)
[connection] id=costa | type=wifi
[wifi] ssid=costa | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=wifi
[wifi] ssid=D-Link | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/extender]] (600 root)
[connection] id=extender | type=wifi
[wifi] ssid=extender | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi
[wifi] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GlobComp]] (600 root)
[connection] id=GlobComp | type=wifi
[wifi] ssid=GlobComp | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SAS-guest]] (600 root)
[connection] id=SAS-guest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=SAS-guest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Al-Sabla]] (600 root)
[connection] id=Al-Sabla | type=wifi
[wifi] ssid=Al-Sabla | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GlobComCloud]] (600 root)
[connection] id=GlobComCloud | type=wifi
[wifi] ssid=GlobComCloud | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Muscat (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'AndroidAP' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"AndroidAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004bdccff
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'GlobComp' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"GlobComp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000355a7b41323
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Huawei-Employee' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Huawei-Employee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3200000f0dd0cfde
                    Extra: Last beacon: 192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'WirelessNet' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"WirelessNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000612ad4bdf37
                    Extra: Last beacon: 8ms ago
          Cell 05 - Address: <MAC 'SAS-guest' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"SAS-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032ef6f5160
                    Extra: Last beacon: 25752ms ago
          Cell 06 - Address: <MAC 'WirelessNet' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"WirelessNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000038ca17412
                    Extra: Last beacon: 8ms ago
          Cell 07 - Address: <MAC 'HP-Print-DD-LaserJet 1102' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-DD-LaserJet 1102"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e5e3071eaf
                    Extra: Last beacon: 8ms ago
          Cell 08 - Address: <MAC 'Ooredoo-B310-5BCD' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Ooredoo-B310-5BCD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001975afc8d0
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ITA-MOBILE 2' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ITA-MOBILE 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043a5a9f97c
                    Extra: Last beacon: 3504ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 10 - Address: <MAC 'GuestNetwork' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"GuestNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043a61882de
                    Extra: Last beacon: 1504ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: <MAC 'Ooredoo-B310-90A7' [AC11]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Ooredoo-B310-90A7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018b5559ebe
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'wlanaccessv2.0' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"wlanaccessv2.0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000048563f6d7
                    Extra: Last beacon: 28380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'Huawei-Employee' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Huawei-Employee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000048596f980
                    Extra: Last beacon: 25280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'wlanaccessv2.0' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"wlanaccessv2.0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f0ff37180
                    Extra: Last beacon: 960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC 'SAS' [AC15]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"SAS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032f0d84160
                    Extra: Last beacon: 2140ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'ITA-CONSULTANT' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"ITA-CONSULTANT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005e6e339ca
                    Extra: Last beacon: 628ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
                       Preauthentication Supported


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     681B59FC4C4EB63D7B98108
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 8463.881400] wlan0: authentication with <MAC 'GuestNetwork' [AC10]> timed out
[ 8476.219773] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8477.018252] wlan0: authenticate with <MAC 'GuestNetwork' [AC10]>
[ 8477.036321] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 1/3)
[ 8477.157570] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 2/3)
[ 8477.357662] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 3/3)
[ 8477.461783] wlan0: authentication with <MAC 'GuestNetwork' [AC10]> timed out
[ 8494.072776] wlan0: authenticate with <MAC 'GuestNetwork' [AC10]>
[ 8494.090994] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 1/3)
[ 8494.195997] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 2/3)
[ 8494.312090] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 3/3)
[ 8494.428113] wlan0: authentication with <MAC 'GuestNetwork' [AC10]> timed out
[ 8501.236472] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8503.078166] wlan0: authenticate with <MAC 'GuestNetwork' [AC10]>
[ 8503.096453] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 1/3)
[ 8503.257569] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 2/3)
[ 8503.369636] wlan0: send auth to <MAC 'GuestNetwork' [AC10]> (try 3/3)
[ 8503.473702] wlan0: authentication with <MAC 'GuestNetwork' [AC10]> timed out
[ 8514.289277] wlan0: authenticate with <MAC 'GuestNetwork' [AC10]>
[ 8514.307339] wlan0: direct probe to <MAC 'GuestNetwork' [AC10]> (try 1/3)
[ 8514.508485] wlan0: direct probe to <MAC 'GuestNetwork' [AC10]> (try 2/3)
[ 8514.712593] wlan0: direct probe to <MAC 'GuestNetwork' [AC10]> (try 3/3)
[ 8514.916663] wlan0: authentication with <MAC 'GuestNetwork' [AC10]> timed out
[ 8526.250749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 8812.219650] wlan0: authenticate with <MAC 'AndroidAP' [AC1]>
[ 8812.238251] wlan0: send auth to <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8812.242299] wlan0: authenticated
[ 8812.242901] wlan0: associate with <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8812.248231] wlan0: RX AssocResp from <MAC 'AndroidAP' [AC1]> (capab=0x411 status=0 aid=1)
[ 8812.248344] wlan0: associated
[ 8812.248366] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8851.854222] wlan0: deauthenticating from <MAC 'AndroidAP' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 8853.466881] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 8854.399960] wlan0: authenticate with <MAC 'AndroidAP' [AC1]>
[ 8854.412524] wlan0: send auth to <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8854.414477] wlan0: authenticated
[ 8854.417528] wlan0: associate with <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8854.423142] wlan0: RX AssocResp from <MAC 'AndroidAP' [AC1]> (capab=0x411 status=0 aid=1)
[ 8854.423251] wlan0: associated
[ 8854.423282] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8861.098780] wlan0: deauthenticating from <MAC 'AndroidAP' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 8865.924325] wlan0: authenticate with <MAC 'AndroidAP' [AC1]>
[ 8865.937335] wlan0: send auth to <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8865.939295] wlan0: authenticated
[ 8865.940324] wlan0: associate with <MAC 'AndroidAP' [AC1]> (try 1/3)
[ 8865.943847] wlan0: RX AssocResp from <MAC 'AndroidAP' [AC1]> (capab=0x411 status=0 aid=1)
[ 8865.943951] wlan0: associated


########## wireless info END ############



```

---

### Post by Hadaka on 2015-12-16
Hi, there are a couple things we can do that need to be done anyway
but with the exception of the country code correction, im not sure it
will make a difference. Let's do these, then i will attempt to explain why.
please open a terminal,ctrl/alt/t then COPY and paste. one line at a time.
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo iw reg set OM
sudo sed -i 's/^REG.*=$/&OM/' /etc/default/crda
```
**See attached:

[ATTACH=CONFIG]266197[/ATTACH][ATTACH=CONFIG]266198[/ATTACH]
You connect to AndroidAP without issue. GuestNetwork, you do not, side by side you can see they
are pretty much the same, with the exception of channel and possibly ISP, but the distinctive difference is
Preauthentication Supported definition. I have no experience with this,but did research it and it's a bit involved
and somewhat confusing. I do however think this is what the major reason is for your difficulties. Perhaps you
can get that definition removed by the network admin. Do a search on "wifi Preauthentication" for a better understanding.
It's sorta like a secret knock pattern on a door before the guy opens the little peek-a-boo hole and asks for the password
before opening the door to let you in.
thanks.

---


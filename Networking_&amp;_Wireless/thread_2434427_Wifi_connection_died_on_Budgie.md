---
title: "Wifi connection died on Budgie"
date: 2020-01-06
forum: Networking &amp; Wireless
---

### Post by mugento on 2020-01-06
I did a search for this topic but came up empty-handed so please direct me if this has already been solved elsewhere. 

We have Budgie 18.04.3 LTS running on our ancient Dell Inspiron N7110N. It was all running fine until a few days ago, when the internet connection suddenly ground to a halt. I am not sure exactly when the change happened because we were out of town for the holidays but I am pretty sure that it has been in the last week. Anyway, I have run a line test on the Dell sitting next to my work laptop (running on Windows) and our laptop is getting 0.1 Mbps while the work laptop gets ~30 Mbps download/5 Mbps upload. I tried restarting with an older kernel and I thought that fixed it at first but now it doesn't make any difference. 

I have seen on this forum where other people installed a different driver (mine is a Realtek RTL810xE) or switched to a different antenna but I don't want to go off half-cocked and make things worse. A team member over on the Budgie forum suggested that I ask here and post the text below. 

You may have gathered that I am not a developer/programmer so I can do basic stuff in Tilex but most likely need a bit more guidance than most of your other users. I would really appreciate any help in getting this going again. Thank you!

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


SCRIPTDATE="2018-10-22 05:34 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"


MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|8(188|189|192|723|812)[acde][esu]|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
IFACEMATCHES="(wlan[0-9]|eth[0-9])"
DMESGMATCHES="(firmware|[nN]etwork|sdio|SDIO)"
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


printf "\n##### secure boot #######################\n\n"
if [ -x /usr/bin/mokutil ]; then
    mokutil --sb-state
else
    echo "'mokutil' is not installed (package \"mokutil\")."
fi


printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"


printf "\n##### interfaces ########################\n\n"
for IFACESFILE in $(find /etc/network/interfaces{,.d} -type f 2> /dev/null | sort); do
    IFACESFLCNT=$(sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' $IFACESFILE)
    if [ -n "$IFACESFLCNT" ]; then
    printf "[%s]\n%s\n\n" "$IFACESFILE" "$IFACESFLCNT"
    fi
done


printf "\n##### ifconfig ##########################\n\n"
if [ -x /bin/ip ]; then
    IFCONFIG=$(ip address show)
elif [ -x /sbin/ifconfig ]; then
    IFCONFIG=$(ifconfig -a)
else
    echo "'ip' is not installed (package \"iproute2\")."
fi
echo "$IFCONFIG"
IFCONFIG=$(sed -n '1h; 1!H; ${g;s/\n /\\ /g;p}' <<< "$IFCONFIG")
IFACESETH=($(sed -n 's#^[0-9]\+: \([^ :]\+\):.* link/ether.*#\1#p; s/^\([^ :]\+\):\?.* \(Link encap:Ethernet\|ether\).*/\1/p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi


printf "\n##### iwconfig ##########################\n\n"
iwconfig


printf "\n##### route #############################\n\n"
if [ -x /bin/ip ]; then
    ip route show
elif [ -x /sbin/route ]; then
    route -n
else
    echo "'ip' is not installed (package \"iproute2\")."
fi


printf "\n##### resolv.conf #######################\n\n"
stat -c "[%a %U %N]" /etc/resolv.conf
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


printf "\n##### NetworkManager config #############\n\n"
for NMCONFFILE in $(find /{etc,usr/lib}/NetworkManager/{NetworkManager.conf,conf.d} -name "*.conf" 2> /dev/null | sort); do
    NMCONFCNT=$(egrep -v '^(#|$)' $NMCONFFILE)
    if [ -n "$NMCONFCNT" ]; then
    printf "[[%s]]\n%s\n\n" "$NMCONFFILE" "$NMCONFCNT"
    fi
done


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


IFACESIDS=($(sed -n "/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/ {/\(00:\)\{5\}00/! {s/^[0-9]\+: \([^ :]\+\):.*/'\1'/p; s/^\([^ :]\+\):\? .*/'\1'/p}}" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n '/\(00:\)\{5\}00/! s#.*\(HWaddr\|link/[^ ]\+\|ether\) \(\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}\).*#\2#p' <<< "$IFCONFIG"))
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


sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/g" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"


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

### Post by QIII on 2020-01-06
Hello!

You have posted the text of the script, not the results.

---

### Post by mugento on 2020-01-06
Oops. I found the results but it is giving me an error because there are 22 images in the message. I am going to try to post it in parts, sorry if this is a nightmare to read.
```

########## wireless info START ##########


Report from: 06 Jan 2020 17:57 NZDT +1300


Booted last: 06 Jan 2020 00:00 NZDT +1300


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Budgie Desktop


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:04d8]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2b80 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


dell_laptop            20480  0
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_hda_codec_realtek,dell_laptop
iwldvm                233472  0
mac80211              819200  1 iwldvm
iwlwifi               315392  1 iwldvm
dell_wmi               20480  0
sparse_keymap          16384  1 dell_wmi
dell_smbios            28672  2 dell_wmi,dell_laptop
wmi_bmof               16384  0
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
cfg80211              679936  3 iwldvm,iwlwifi,mac80211
wmi                    28672  4 dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor
video                  49152  3 dell_wmi,dell_laptop,i915


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
3: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF2]> brd <MAC address>
    inet 192.168.1.5/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp1s0
       valid_lft 86059sec preferred_lft 86059sec
    inet6 fe80::e8dc:8299:8f7e:5605/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


enp3s0    no wireless extensions.


lo        no wireless extensions.


wlp1s0    IEEE 802.11  ESSID:"Your New Wi-Fi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Your New Wi-Fi' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:10055   Missed beacon:0


##### route #############################


default via 192.168.1.1 dev wlp1s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
192.168.1.0/24 dev wlp1s0 proto kernel scope link src 192.168.1.5 metric 600 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       908     1  0 Jan05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 1030 [Rainbow Peak] (Centrino Wireless-N 1030 BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 5.0.0-37-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Your New Wi-Fi
GENERAL.CON-UUID:                       66675c4d-ec64-4773-8946-0011021027a4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1578372700
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       requested_netbios_scope = 1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_wpad = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_lease_time = 86400
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[28]:                       domain_name_servers = 192.168.1.1 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e8dc:8299:8f7e:5605/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   66675c4d-ec64-4773-8946-0011021027a4 | Your New Wi-Fi


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID            BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
Your New Wi-Fi  <MAC 'Your New Wi-Fi' [AC1]>  Infra  1     2412 MHz  270 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      yes     *

##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-changetypo-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Mike&#8217;s iPhone]] (600 root)
[connection] id=Mike&#8217;s iPhone | type=wifi | autoconnect=false | permissions=user:lyn:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=77;105;107;101;226;128;153;115;32;105;80;104;111;110;101;
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Your New Wi-Fi]] (600 root)
[connection] id=Your New Wi-Fi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=Your New Wi-Fi
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Pacific/Auckland (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp3s0    no frequency information.


lo        no frequency information.


wlp1s0    13 channels in total; available frequencies :
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


enp3s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      7   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:2.472 GHz (Channel 13)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'Your New Wi-Fi' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Your New Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017e4bb662e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'inet' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"inet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e44a6a1a1
                    Extra: Last beacon: 1252ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (4)
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e44a5f180
                    Extra: Last beacon: 1244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NTGR_VMB_1462060849' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NTGR_VMB_1462060849"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033fb36ad41
                    Extra: Last beacon: 1240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NET01' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"NET01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e44a78180
                    Extra: Last beacon: 1220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NETGEAR_EXT ' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_EXT "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ea689a179
                    Extra: Last beacon: 1076ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e44a91180
                    Extra: Last beacon: 1064ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

Cell 08 - Address: <MAC 'JSquared' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"JSquared"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000209d4f04bd7
                    Extra: Last beacon: 1020ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Darshan Home' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Darshan Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004144f805c
                    Extra: Last beacon: 848ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'DIRECT-HWDESKTOP-C8NO6VGms1T' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-HWDESKTOP-C8NO6VGms1T"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004144fd048
                    Extra: Last beacon: 860ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'SPARK-L53GLP' [AC11]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SPARK-L53GLP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d24f2d40
                    Extra: Last beacon: 664ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'inet' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"inet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008e3c45ff6e
                    Extra: Last beacon: 460ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (4)
          Cell 13 - Address: <MAC 'NTGR_VMB_1541402092' [AC13]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"NTGR_VMB_1541402092"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048c2d94941
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'SPARK-PSNE3J' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"SPARK-PSNE3J"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004d1327186
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Brick 2.4' [AC15]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Brick 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6673c7337
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################


[iwldvm]
filename:       /lib/modules/5.0.0-37-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C1AECE727ECF35F7B64093C
depends:        mac80211,iwlwifi,cfg80211
retpoline:      Y
intree:         Y
name:           iwldvm
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/5.0.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0CDD28A506BDDDE9444E85C
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/5.0.0-37-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-43.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-43.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-43.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-43.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-43.ucode
firmware:       iwlwifi-Qu-b0-jf-b0-43.ucode
firmware:       iwlwifi-su-z0-43.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-43.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-43.ucode
firmware:       iwlwifi-QuQnj-b0-hr-b0-43.ucode
firmware:       iwlwifi-Qu-b0-hr-b0-43.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-43.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-43.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-43.ucode
srcversion:     73136E4A47DE531CDC14864
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for 22560 devices, 4K for other devices 1:4K 2:8K 3:12K 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: 0 (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)


[cfg80211]
filename:       /lib/modules/5.0.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DCECEA5B6FF7EF332DBC1F5
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-37-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
disable_11ax: N
enable_ini: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[  579.383849] wlp1s0: deauthenticated from <MAC 'Your New Wi-Fi' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  579.492593] wlp1s0: authenticate with <MAC 'Your New Wi-Fi' [AC1]>
[  579.497193] wlp1s0: send auth to <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[  579.503139] wlp1s0: authenticated
[  579.505660] wlp1s0: associate with <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[  579.547755] wlp1s0: RX AssocResp from <MAC 'Your New Wi-Fi' [AC1]> (capab=0x431 status=0 aid=3)
[  579.556437] wlp1s0: associated
[  759.714581] wlp1s0: deauthenticated from <MAC 'Your New Wi-Fi' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  759.813034] wlp1s0: authenticate with <MAC 'Your New Wi-Fi' [AC1]>
[  759.816317] wlp1s0: send auth to <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[  759.831054] wlp1s0: authenticated
[  759.833534] wlp1s0: associate with <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[  759.841589] wlp1s0: RX AssocResp from <MAC 'Your New Wi-Fi' [AC1]> (capab=0x431 status=0 aid=3)
[  759.847970] wlp1s0: associated
[ 1359.893130] wlp1s0: deauthenticated from <MAC 'Your New Wi-Fi' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1360.000318] wlp1s0: authenticate with <MAC 'Your New Wi-Fi' [AC1]>
[ 1360.006797] wlp1s0: send auth to <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1360.013681] wlp1s0: authenticated
[ 1360.016067] wlp1s0: associate with <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1360.020027] wlp1s0: RX AssocResp from <MAC 'Your New Wi-Fi' [AC1]> (capab=0x431 status=0 aid=3)
[ 1360.022967] wlp1s0: associated
[ 1540.037733] wlp1s0: deauthenticated from <MAC 'Your New Wi-Fi' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1540.139258] wlp1s0: authenticate with <MAC 'Your New Wi-Fi' [AC1]>
[ 1540.142212] wlp1s0: send auth to <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1540.149668] wlp1s0: authenticated
[ 1540.153969] wlp1s0: associate with <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1540.161530] wlp1s0: RX AssocResp from <MAC 'Your New Wi-Fi' [AC1]> (capab=0x431 status=0 aid=3)
[ 1540.166560] wlp1s0: associated
[ 1591.474014] wlp1s0: deauthenticating from <MAC 'Your New Wi-Fi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1593.772438] iwlwifi 0000:01:00.0: RF_KILL bit toggled to enable radio.
[ 1597.322024] r8169 0000:03:00.0 enp3s0: Link is Down
[ 1597.335407] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1 (repeated 2 times)
[ 1598.127476] wlp1s0: authenticate with <MAC 'Your New Wi-Fi' [AC1]>
[ 1598.129607] wlp1s0: send auth to <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1598.132721] wlp1s0: authenticated
[ 1598.135237] wlp1s0: associate with <MAC 'Your New Wi-Fi' [AC1]> (try 1/3)
[ 1598.138719] wlp1s0: RX AssocResp from <MAC 'Your New Wi-Fi' [AC1]> (capab=0x431 status=0 aid=3)
[ 1598.141338] wlp1s0: associated
[ 1598.171830] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[ 1618.204754] r8169 0000:03:00.0 enp3s0: Link is Down


########## wireless info END ############
```

At least I hope that is the results!

---

### Post by coffeecat on 2020-01-06
@mugento, when posting output of a script, or terminal output, please use BBCode code tags. This preserves formatting, avoids spurious smileys (there are no images in your output), and avoids the huge walls of text you posted. I've added code tags to your various posts. There is a link in my sig if you need to know how to use code tags.

---

### Post by mugento on 2020-01-06
Thank you, I am obviously a novice at this!

---


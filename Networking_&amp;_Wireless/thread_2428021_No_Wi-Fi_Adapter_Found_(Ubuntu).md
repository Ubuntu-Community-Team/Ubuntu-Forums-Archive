---
title: "No Wi-Fi Adapter Found (Ubuntu)"
date: 2019-09-28
forum: Networking &amp; Wireless
---

### Post by infinite-way on 2019-09-28
I had Windows 7 on my Laptop Dell Inspiron 14 and now I'm using Ubuntu 18.04, first time using Ubuntu, it's not recognizing the internal wi-fi card, already did the thing so I'm posting results:

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

### Post by Yellow Pasque on 2019-09-29
You pasted the script itself. You need to run it and give the output from it. Read the directions and try again.

---

### Post by infinite-way on 2019-09-30
Oh my bad, here's the output

```
 
########## wireless info START ##########

Report from: 30 Sep 2019 09:24 -03 -0300

Booted last: 30 Sep 2019 00:00 -03 -0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.0.0-29-generic #31~18.04.1-Ubuntu SMP Thu Sep 12 18:29:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: bcma-pci-bridge

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:0651]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 1bcf:2b8b Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

cfg80211              675840  0
dell_laptop            20480  0
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_hda_codec_realtek,dell_laptop
dell_wmi               20480  0
sparse_keymap          16384  1 dell_wmi
dell_smbios            28672  2 dell_wmi,dell_laptop
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
wmi_bmof               16384  0
bcma                   61440  0
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
2: enp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp7s0' [IF1]> brd <MAC address>
    inet 192.168.1.135/24 brd 192.168.1.255 scope global dynamic noprefixroute enp7s0
       valid_lft 27897sec preferred_lft 27897sec
    inet6 fe80::6756:319f:e1b:d8c0/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp7s0    no wireless extensions.

##### route #############################

default via 192.168.1.1 dev enp7s0 proto dhcp metric 100 
169.254.0.0/16 dev enp7s0 scope link metric 1000 
192.168.1.0/24 dev enp7s0 proto kernel scope link src 192.168.1.135 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       997     1  0 09:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       enp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b7936ece-aac0-379e-b626-4477aca9356a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.135/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        unknown_120 = 1:0:0:0:0
DHCP4.OPTION[7]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        expiry = 1569874166
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       ip_address = 192.168.1.135
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_time_offset = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       dhcp_lease_time = 28800
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::6756:319f:e1b:d8c0/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b7936ece-aac0-379e-b626-4477aca9356a | Wired connection 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

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

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Santiago (based on set time zone)

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

lo        no frequency information.

enp7s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp7s0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.0.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8F0CAF5346FF71FCE9CB198
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.0.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/5.0.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     A58277A768AAB23C742A248
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       5.0.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

##### module parameters #################

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

[   32.450388] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0a5c-21d7.hcd failed with error -2
[   32.450392] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0a5c-21d7.hcd not found
[   50.958181] r8169 0000:07:00.0 enp7s0: Link is Down
[   52.621469] r8169 0000:07:00.0 enp7s0: Link is Up - 100Mbps/Full - flow control rx/tx
[   52.621492] IPv6: ADDRCONF(NETDEV_CHANGE): enp7s0: link becomes ready

########## wireless info END ############ 
```

---

### Post by Yellow Pasque on 2019-09-30
First thing to try (with internet connection):
```
sudo apt-get install broadcom-sta-dkms
```

---

### Post by slickymaster on 2019-09-30
Thread moved to **Networking & Wireless** for a better fit

---

### Post by infinite-way on 2019-09-30
It worked!, thank you user Yellow Pasque.

---

### Post by Yellow Pasque on 2019-09-30
You're welcome. You may also be interested in bluetooth support: [https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)
Specifically: [https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM43142A0-0a5c-21d7.hcd](https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM43142A0-0a5c-21d7.hcd)

---


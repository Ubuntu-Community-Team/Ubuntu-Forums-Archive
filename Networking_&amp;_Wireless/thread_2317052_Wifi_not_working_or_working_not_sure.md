---
title: "Wifi not working or working not sure??"
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by amol7 on 2016-03-13
Hi folks,

After going through the ordeal of trying to install Ubuntu on an HP 15ac170tu with UEFI mode ([http://ubuntuforums.org/showthread.php?t=2316116](http://ubuntuforums.org/showthread.php?t=2316116))
I'm now facing issue of having to get my Wifi up  n running.
The network adapter is Realtek's RTL8723BE.
Yeah I know many people have the same issue with the same adapter.
And so I have tried all these links below.
[http://ubuntuforums.org/showthread.php?t=222 0933]("http://ubuntuforums.org/showthread.php?t=2220933")
[URL="http://askubuntu.com/questions/632719/my-wifi-drops-the-connection-after-a-few-minutes-realtek8723be"]
[/URL][http://ubuntuforums.org/showthread.php?t=2205497](http://ubuntuforums.org/showthread.php?t=2205497)

[http://askubuntu.com/questions/632719/my-wifi-drops-the-connection-after-a-few-minutes-realtek8723be](http://askubuntu.com/questions/632719/my-wifi-drops-the-connection-after-a-few-minutes-realtek8723be)

[http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem](http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem)

[http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660](http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be/729660#729660)

But What I throughly tried was what was given here
[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04)

still nothing works. 

Now after doing what was given above, the wifi tries to connect but displays "Wifi disconnected" and gone again.

 This I wanted to try  but found it to be too confusing[URL="http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04"]
[/URL][https://rtl8723beubuntu1404.wordpress.com/](https://rtl8723beubuntu1404.wordpress.com/) 

but found it to be too confusing.


Please help

~a

---

### Post by Hadaka on 2016-03-13
Hi Please try this link 
this is about as clear and simple and well written as it gets.
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
thanks.

---

### Post by amol7 on 2016-03-13
> **Hadaka said:**
> Hi Please try this link 
this is about as clear and simple and well written as it gets.
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
thanks.

I tried what was written in the link you provided, still no improvements.

I tried ```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=1
```

but it works fine although being next to the router, literally, shows only two bars out of 4!

And If I go to a room, the connection gets disconneced.
The above code with "2" doesn't connect at all.

Thanks,

~a

---

### Post by Hadaka on 2016-03-14
did you load the new driver?
also please go here...
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
and run the script,it will build a file in your home directory
named wireless-info.txt, copy and paste that here.
thanks,

---

### Post by amol7 on 2016-03-15
> **Hadaka said:**
> did you load the new driver?
also please go here...
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
and run the script,it will build a file in your home directory
named wireless-info.txt, copy and paste that here.
thanks,

Here's the result
Hope you can help me.

Sorry for the late reply.

Thanks
~a

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

### Post by Hadaka on 2016-03-16
Hi, you posted the wireless script we need to see the the **wireless-info.txt** file
that the script writes into your home directory. Please try again. open a terminal
ctrl/alt/t then copy and paste this command.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
it will ask for your password and then run. When it is finished, in the same terminal list the files.
```
dir
```
you will see the **wireless-info.txt** file, copy and post it.
thanks.

---

### Post by amol7 on 2016-03-16
> **Hadaka said:**
> Hi, you posted the wireless script we need to see the the **wireless-info.txt** file
that the script writes into your home directory. Please try again. open a terminal
ctrl/alt/t then copy and paste this command.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
it will ask for your password and then run. When it is finished, in the same terminal list the files.
```
dir
```
you will see the **wireless-info.txt** file, copy and post it.
thanks.

Sorry about that.

Here's the code

```

########## wireless info START ##########

Report from: 17 Mar 2016 09:08 IST +0530

Booted last: 17 Mar 2016 08:57 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7340618 (7.3 MB)  TX bytes:409304 (409.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       901     1  0 08:57 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```


Thanks
~a

---

### Post by Hadaka on 2016-03-17
Hi, please open a terminal ctrl/alt/t then copy and paste..
```
sudo rfkill unblock all
```
then do..
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
boot
then pleased run and post the wireless-info.txt
again.
thanks.

---

### Post by amol7 on 2016-03-18
> **Hadaka said:**
> Hi, please open a terminal ctrl/alt/t then copy and paste..
```
sudo rfkill unblock all
```
then do..
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
boot
then pleased run and post the wireless-info.txt
again.
thanks.

here's the code,
```

########## wireless info START ##########

Report from: 18 Mar 2016 09:50 IST +0530

Booted last: 18 Mar 2016 09:31 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1730567 (1.7 MB)  TX bytes:365824 (365.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       850     1  0 09:31 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  661.686822] r8169 0000:07:00.0 eth0: link down (repeated 2 times)
[  702.461795] r8169 0000:07:00.0 eth0: link up
[  720.364479] r8169 0000:07:00.0 eth0: link down
[  721.997224] r8169 0000:07:00.0 eth0: link up
[  723.316320] r8169 0000:07:00.0 eth0: link down
[  724.849265] r8169 0000:07:00.0 eth0: link up

########## wireless info END ############


```

Thanks

~a

---

### Post by Hadaka on 2016-03-18
Hi, please go here..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
and do this again..all the lines,.,,not just the ant sel lines..the first command will probably fail...that is ok.
but do the rest.. also..click your wifi symbol and make sure you have  "Enable Wireless" checked.
it is important that you run every line in the above link.
thanks.

---

### Post by amol7 on 2016-03-19
> **Hadaka said:**
> Hi, please go here..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
and do this again..all the lines,.,,not just the ant sel lines..the first command will probably fail...that is ok.
but do the rest.. also..click your wifi symbol and make sure you have  "Enable Wireless" checked.
it is important that you run every line in the above link.
thanks.

ok Hadaka,

I tried every command and I mean every command and every instruction (when to reboot n all that) as indicated in the link.
The number "1" works for me. However, only when I'm sitting next to the router. But the signal strength is just 3 out of 4 bars (I otherwise I'm typing out this reply with a wired connection)
The moment I go to my room, it gets disconnected. And keep trying to connect.
Am gonna run the wifi_info script again for your reference.

```

########## wireless info START ##########

Report from: 19 Mar 2016 12:58 IST +0530

Booted last: 19 Mar 2016 12:47 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297088 (297.0 KB)  TX bytes:138096 (138.0 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104487 (104.4 KB)  TX bytes:71535 (71.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       843     1  0 12:47 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   49.160142] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.082007] wlan0: authenticate with <MAC address>
[   50.098250] wlan0: send auth to <MAC address> (try 1/3)
[   50.105606] wlan0: authenticated
[   50.105885] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   50.106503] wlan0: associate with <MAC address> (try 1/3)
[   50.110709] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=4)
[   50.111904] wlan0: associated
[   50.111916] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  191.485271] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  191.485363] wlan0: Connection to AP <MAC address> lost
[  209.233913] wlan0: authenticate with <MAC address>
[  209.245522] wlan0: direct probe to <MAC address> (try 1/3)
[  209.449109] wlan0: send auth to <MAC address> (try 2/3)
[  209.553279] wlan0: send auth to <MAC address> (try 3/3)
[  209.657231] wlan0: authentication with <MAC address> timed out
[  250.222406] wlan0: authenticate with <MAC address>
[  250.245088] wlan0: send auth to <MAC address> (try 1/3)
[  250.253301] wlan0: authenticated
[  250.253450] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  250.253536] wlan0: associate with <MAC address> (try 1/3)
[  250.257006] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=4)
[  250.258060] wlan0: associated
[  262.299400] r8169 0000:07:00.0 eth0: link up
[  262.299413] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  277.423810] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

Please help me. Do I have to do a clean install again? Like Install Ubuntu again ?

~a

---

### Post by Hadaka on 2016-03-19
ok, to begin i have no idea how you are even getting a connection wireless 
as it is blocked,.,,
```
##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: ***[COLOR=#ff0000]yes[/COLOR]*[COLOR=#ff0000][/COLOR]**[COLOR=#ff0000][/COLOR]
    Hard blocked: no
```
click your network mgr...connection symbol..the wireless or the up/down arrows..next to the envelope
and make sure **Enable Wireless **is checked.
and then do..
```
sudo rfkill unblock all
rfkill list all
```
is it unblocked now??

---

### Post by amol7 on 2016-03-20
> **Hadaka said:**
> ok, to begin i have no idea how you are even getting a connection wireless 
as it is blocked,.,,
```
##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: ***[COLOR=#ff0000]yes[/COLOR]***
    Hard blocked: no
```
click your network mgr...connection symbol..the wireless or the up/down arrows..next to the envelope
and make sure **Enable Wireless **is checked.
and then do..
```
sudo rfkill unblock all
rfkill list all
```
is it unblocked now??

No Hadaka, I was working with wireless mode ON as the wifi was continuously trying to connect.
Then I connected using the wired connection. To post my earlier reply. Hence the result "Soft blocked: ***[COLOR=#ff0000]yes [/COLOR]***"

I ran the script again and no problems at all. Please see the script again.

```

########## wireless info START ##########

Report from: 20 Mar 2016 10:00 IST +0530

Booted last: 20 Mar 2016 09:56 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:689835 (689.8 KB)  TX bytes:180125 (180.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2944 (2.9 KB)  TX bytes:19584 (19.5 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ASUS' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       841     1  0 09:56 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ASUS] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC 'ASUS' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WEP

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e8397ff6
                    Extra: Last beacon: 88ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   27.204319] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.724326] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[   30.743911] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[   30.752027] wlan0: authenticated
[   30.752219] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   30.752287] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[   30.755633] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[   30.756161] wlan0: associated
[   30.756193] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.491713] r8169 0000:07:00.0 eth0: link down
[   68.700766] wlan0: deauthenticating from <MAC 'ASUS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   74.496856] r8169 0000:07:00.0 eth0: link down
[   76.107695] r8169 0000:07:00.0 eth0: link up
[  161.166156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  162.044862] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  162.056463] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  162.067607] wlan0: authenticated
[  162.067786] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  162.070735] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[  162.074047] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[  162.074447] wlan0: associated
[  162.074456] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```



Thanks
~a

---

### Post by Hadaka on 2016-03-20
Hi,Let's try this.. Here is a copy of module information  from your wireless-info.
There is not a single entry for "ant_sel" in the parm.---parameters. Thats because
you did not load the new driver from here... 
                              [http://askubuntu.com/questions/71768.../722904#722904]("http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904")                                                                         
Also. yes you were able to enter and write to a file named "/etc/modprobe.d/rtlbtcoex.conf"
because you told it to..you created that file by editing "/etc/modprobe.d/rtlbtcoex.conf" and writing "options rtl8723be ant_sel=1"
to it. That command will never happen because you dont have the new dirver loaded.
This will never work.
```
[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1
```

Your current driver
```
##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
```
From a working wired connection COPY and paste one line at a time.
make sure wireless is enabled.
when done,please post the results of each command.

this may fail...that is ok..do it and continue on.
```
sudo apt-get remove rtlwifi-new-dkms
```
then do..
be sure to copy the link in line 2 ,the whole line is one line
```
sudo apt-get install git build-essential
git clone -b rock.new_btcoex [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) 
cd rtlwifi_new
make
sudo make install
sudo modprobe -v rtl8723be
```
disconnect wired connection boot and test
you already have "ant_sel=1" in "/etc/modprobe.c/rtlbtcoex.conf"
so using the "modprobe -v rtl8723be ant_sel=X" will not work.
to change do this.
if you need or want to try "ant_sel=2" you can change that value with..
Please COPY
```
sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.d/rtlbtcoex.conf
```
and back to a value of " 1 " if you need or want to.
 ```
sudo sed -i 's/ant_sel=2/ant_sel=1/' /etc/modprobe.d/rtlbtcoex.conf
```
please poat the results of all commands.

---

### Post by amol7 on 2016-03-20
> **Hadaka said:**
> Hi,Let's try this.. Here is a copy of module information  from your wireless-info.
There is not a single entry for "ant_sel" in the parm.---parameters. Thats because
you did not load the new driver from here... 
                              [http://askubuntu.com/questions/71768.../722904#722904]("http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904")                                                                         
Also. yes you were able to enter and write to a file named "/etc/modprobe.d/rtlbtcoex.conf"
because you told it to..you created that file by editing "/etc/modprobe.c/rtlbtcoex.conf" and writing "options rtl8723be ant_sel=1"
to it. That command will never happen because you dont have the new dirver loaded.
This will never work.
```
[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1
```

Your current driver
```
##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
```
From a working wired connection COPY and paste one line at a time.
make sure wireless is enabled.
when done,please post the results of each command.

this may fail...that is ok..do it and continue on.
```
sudo apt-get remove rtlwifi-new-dkms
```
then do..
be sure to copy the link in line 2 ,the whole line is one line
```
sudo apt-get install git build-essential
git clone -b rock.new_btcoex [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) 
cd rtlwifi_new
make
sudo make install
sudo modprobe -v rtl8723be
```
disconnect wired connection boot and test
you already have "ant_sel=1" in "/etc/modprobe.c/rtlbtcoex.conf"
so using the "modprobe -v rtl8723be ant_sel=X" will not work.
to change do this.
if you need or want to try "ant_sel=2" you can change that value with..
Please COPY
```
sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.c/rtlbtcoex.conf
```
and back to a value of " 1 " if you need or want to.
 ```
sudo sed -i 's/ant_sel=2/ant_sel=1/' /etc/modprobe.c/rtlbtcoex.conf
```
please poat the results of all commands.

OK so here's procedure I'm following (Step wise)

1.```
XXXX@XXXX-HP-Notebook:~$ sudo apt-get remove rtlwifi-new-dkms
[sudo] password for XXXX:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rtlwifi-new-dkms
```

2.```
XXXX@XXXX-HP-Notebook:~$ sudo apt-get install git build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
git is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 163 not upgraded.
```

3.```
XXXX@XXXX-HP-Notebook:~$ git clone -b rock.new_btcoex https://github.com/lwfinger/rtlwifi_new
fatal: destination path 'rtlwifi_new' already exists and is not an empty directory.
```

4.```
XXXX@XXXXl-HP-Notebook:~$ cd rtlwifi_new
amol@amol-HP-Notebook:~/rtlwifi_new$ make
make -C /lib/modules/3.19.0-51-generic/build M=/home/amol/rtlwifi_new modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
```

5.```
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$ sudo make install
make -C /lib/modules/3.19.0-51-generic/build M=/home/amol/rtlwifi_new modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
Install rtlwifi SUCCESS
```

6.```
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$ sudo modprobe -v rtl8723be
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$
```

Rebooted. Removed Wired connection. Connected to my Wifi and then went to the desired location.
And again wireless gets disconnected....

7. So I ran the code again to check if the setting to ant_sel=2 works......and then this happens

```
XXXX@XXXX-HP-Notebook:~$ sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.c/rtlbtcoex.conf
[sudo] password for XXXX: 
sed: can't read /etc/modprobe.c/rtlbtcoex.conf: No such file or directory
```


please advice.


Thanks
~a

---

### Post by Hadaka on 2016-03-20
Hi i made a typo, i am sorry.,.
I typed "modprobe.[COLOR=#ff0000]**c**[/COLOR]" instead of modprobe.[COLOR=#ff0000][B]d
[/B][/COLOR]the correct command is...[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]

```
sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.d/rtlbtcoex.conf
```

---

### Post by amol7 on 2016-03-20
OK I did that and tried connecting again.
And again, the connection again gets lost (disconnected). I used the value "ant_sel=1"
I'm posting the wireless-info results yet again for your reference,
```

########## wireless info START ##########

Report from: 20 Mar 2016 21:41 IST +0530

Booted last: 20 Mar 2016 21:33 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
snd_soc_rt286          32768  0 
snd_soc_core          196608  1 snd_soc_rt286
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218905 (218.9 KB)  TX bytes:85424 (85.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58511 (58.5 KB)  TX bytes:56308 (56.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ASUS' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:414   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       836     1  0 21:33 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ASUS] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC 'ASUS' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WEP

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bb4176beb
                    Extra: Last beacon: 80ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  317.892018] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  317.914801] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  317.917633] wlan0: authenticated
[  317.917836] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  317.919610] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[  317.923012] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=2)
[  317.924057] wlan0: associated
[  317.924067] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  364.109463] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  364.109478] wlan0: Connection to AP <MAC 'ASUS' [AC1]> lost
[  381.851249] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  381.862845] wlan0: direct probe to <MAC 'ASUS' [AC1]> (try 1/3)
[  382.065754] wlan0: direct probe to <MAC 'ASUS' [AC1]> (try 2/3)
[  382.269841] wlan0: direct probe to <MAC 'ASUS' [AC1]> (try 3/3)
[  382.473937] wlan0: authentication with <MAC 'ASUS' [AC1]> timed out
[  386.372246] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  386.395361] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  386.398085] wlan0: authenticated
[  386.398273] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  386.399916] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[  386.405775] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=2)
[  386.406808] wlan0: associated
[  394.484225] r8169 0000:07:00.0 eth0: link up
[  394.484242] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by Hadaka on 2016-03-20
ok, Let's clean this up first and then we will re address why the new driver
isnt loading.

this is a part of why it is failing.
```
Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC 'ASUS' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 [COLOR=#ff0000]**wep**[/COLOR]
```

```
##### dmesg #############################

[  317.892018] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  317.914801] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  317.917633] wlan0: authenticated
[  317.917836] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to [COLOR=#ff0000]**WEP/TKIP**[/COLOR] use
[  317.919610] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
```
Please access your router settings and make sure they are not set to  TKIP set to WPA2 AES
Then also check your network manager network setting for your connection named 'ASUS' and see that
its properly set to WAP2.
once that is made correct then with the wireless enabled do.
```
sudo modprobe -rf rtl8723be
sudo modprobe -vv rtl8723be
```
and post the output of,,
```
dmesg | grep rtl
```
thanks.

---

### Post by amol7 on 2016-03-20
OK changed the router to WPA2 AES and changed the Network settings to the same on my machine.
Ran the codes and then here are the results
```
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -rf rtl8723be
[sudo] password for amol: 
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -vv rtl8723be
modprobe: INFO: ../libkmod/libkmod.c:354 kmod_set_log_fn() custom logging function 0x55f406ffe090 registered
insmod /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=1 
modprobe: INFO: ../libkmod/libkmod.c:321 kmod_unref() context 0x55f407acc1f0 released
XXXX@XXXX-HP-Notebook:~$ dmesg | grep rtl
[   12.440571] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   13.101373] rtl8723be: unknown parameter 'ant_sel' ignored
[   13.139593] Using firmware rtlwifi/rtl8723befw.bin
[   13.140102] rtlwifi: channel plan 0x20
[   13.140104] rtlwifi: country code 11
[   13.144449] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.145058] rtlwifi: wireless switch is on
[  317.917836] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  364.109463] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  386.398273] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3443.493807] Modules linked in: rfcomm bnep uvcvideo nls_iso8859_1 videobuf2_vmalloc videobuf2_memops arc4 videobuf2_core v4l2_common videodev media rtl8723be(OE) btcoexist(OE) rtl_pci(OE) snd_hda_codec_hdmi hp_wmi sparse_keymap intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul rtlwifi(OE) crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_soc_rt286 i915_bpo snd_soc_core snd_hda_codec_realtek snd_compress mac80211 snd_hda_codec_generic snd_pcm_dmaengine intel_ips joydev drm_kms_helper snd_hda_intel serio_raw snd_hda_controller drm mei_me cfg80211 mei btusb lpc_ich shpchp snd_hda_codec bluetooth snd_hwdep i2c_algo_bit processor_thermal_device wmi snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq int3403_thermal snd_seq_device snd_timer snd i2c_hid soundcore video dw_dmac dw_dmac_core snd_soc_sst_acpi i2c_designware_platform 8250_dw i2c_designware_core spi_pxa2xx_platform int3402_thermal int3400_thermal mac_hid hp_wireless acpi_thermal_rel acpi_pad parport_pc ppdev lp parport hid_generic usbhid hid psmouse ahci r8169 libahci mii sdhci_acpi sdhci
[ 4019.864891] rtlwifi:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4405.914436] rtl8723be: unknown parameter 'ant_sel' ignored
[ 4405.930108] Using firmware rtlwifi/rtl8723befw.bin
[ 4405.930276] rtlwifi: channel plan 0x20
[ 4405.930278] rtlwifi: country code 11
[ 4405.931133] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 4405.932168] rtlwifi: wireless switch is on
```

---

### Post by Hadaka on 2016-03-20
ok, when you attempted to load the new driver you got this error..
```
XXXX@XXXX-HP-Notebook:~$ git clone -b rock.new_btcoex https://github.com/lwfinger/rtlwifi_new
fatal: destination path 'rtlwifi_new' already exists and is not an empty directory.
```
the new driver never loaded..and here are a couple items from your latest dmesg report.
```
[   12.440571] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   13.101373] rtl8723be: unknown parameter 'ant_sel' ignored
[   13.139593] Using firmware rtlwifi/rtl8723befw.bin
[  317.917836] rtl8723be 0000:0d:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
```
as you can see the 'ant_sel' command was ignored because your present driver doesnt have that ability.
and you still have the WEP/TKIP issue
untill the WEP/TKIP is cleaned up, it will continue to dump the connection even if we were able to
load the correct driver. so please go into your router setting and correct that and into network manager
and verify or correct the settings for your access point .
thanks.

---

### Post by amol7 on 2016-03-21
OK I made the changes, Please refer the attached images.
I ran the wifi-ifo script again. Please see the results.

```

########## wireless info START ##########

Report from: 21 Mar 2016 09:32 IST +0530

Booted last: 21 Mar 2016 09:22 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0 
snd_soc_rt286          32768  0 
sparse_keymap          16384  1 hp_wmi
snd_soc_core          196608  1 snd_soc_rt286
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 hp_wmi

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
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:819268 (819.2 KB)  TX bytes:231664 (231.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ASUS' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       792     1  0 09:22 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ASUS] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ASUS:           Infra, <MAC 'ASUS' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002c617121f
                    Extra: Last beacon: 132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   72.087785] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[   72.109736] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[   72.112391] wlan0: authenticated
[   72.114730] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[   72.121704] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[   72.122910] wlan0: associated
[   72.122932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  156.344225] wlan0: deauthenticating from <MAC 'ASUS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  157.280409] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  157.303520] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  157.307001] wlan0: authenticated
[  157.307383] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[  157.313145] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[  157.314186] wlan0: associated

########## wireless info END ############


```

Thanks

~a

PS: I'm writing this reply using the wifi connection sitting next to the router.

---

### Post by amol7 on 2016-03-21
and here's the wifi-info script when Wired connection in use and wifi is enabled (but not connected)

```

########## wireless info START ##########

Report from: 21 Mar 2016 09:47 IST +0530

Booted last: 21 Mar 2016 09:22 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c1]
    Kernel driver in use: r8169

0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57d6 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0 
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0 
snd_soc_rt286          32768  0 
sparse_keymap          16384  1 hp_wmi
snd_soc_core          196608  1 snd_soc_rt286
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_soc_rt286,snd_pcm_dmaengine
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:183536 (183.5 KB)  TX bytes:30268 (30.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1334213 (1.3 MB)  TX bytes:851830 (851.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ASUS

##### network managers ##################

Installed:

    NetworkManager

Running:

root       792     1  0 09:22 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ASUS:            Infra, <MAC 'ASUS' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ASUS' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f99bd537
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     BCA57D98F5F0A0D7655C7A6
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D9664C0F5BE20DE765F0727
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CAE0CD9428F7A2558314B97
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtlbtcoex.conf]
options rtl8723be ant_sel=1

##### rc.local ##########################

echo 55 > /sys/class/backlight/intel_backlight/brightness
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   72.087785] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[   72.109736] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[   72.112391] wlan0: authenticated
[   72.114730] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[   72.121704] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[   72.122910] wlan0: associated
[   72.122932] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  156.344225] wlan0: deauthenticating from <MAC 'ASUS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  157.280409] wlan0: authenticate with <MAC 'ASUS' [AC1]>
[  157.303520] wlan0: send auth to <MAC 'ASUS' [AC1]> (try 1/3)
[  157.307001] wlan0: authenticated
[  157.307383] wlan0: associate with <MAC 'ASUS' [AC1]> (try 1/3)
[  157.313145] wlan0: RX AssocResp from <MAC 'ASUS' [AC1]> (capab=0x411 status=0 aid=4)
[  157.314186] wlan0: associated
[ 1439.994242] r8169 0000:07:00.0 eth0: link up
[ 1439.994252] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1448.494052] wlan0: deauthenticating from <MAC 'ASUS' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```


Thanks

~a

---

### Post by jeremy31 on 2016-03-21
Post ```
cd rtlwifi_new
git status
```

---

### Post by amol7 on 2016-03-21
> **jeremy31 said:**
> Post ```
cd rtlwifi_new
git status
```

here's the result
```
XXXX@XXXX-HP-Notebook:~$ cd rtlwifi_new
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    backup_drivers.tar

nothing added to commit but untracked files present (use "git add" to track)


```


Thanks

~a

---

### Post by Hadaka on 2016-03-22
Thanks for making those changes, it made some improvement.
From a working wired connection with the wireless enabeled
open a terminal and do..
```
sudo rm -rf rtlwifi_new
sudo rm/etc/modprobe.d/rtlbtcoex.conf
```
then go here again and copy and paste every line
[URL="http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904"]http://askubuntu.com/questions/71768.../722904#722904

[/URL]if all goes well, the ant_sel method on that page should work.
thanks.

---

### Post by amol7 on 2016-03-22
> **Hadaka said:**
> Thanks for making those changes, it made some improvement.
From a working wired connection with the wireless enabeled
open a terminal and do..
```
sudo rm -rf rtlwifi_new
sudo rm/etc/modprobe.d/rtlbtcoex.conf
```
then go here again and copy and paste every line
[URL="http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904"]http://askubuntu.com/questions/71768.../722904#722904

[/URL]if all goes well, the ant_sel method on that page should work.
thanks.


YES! Finally started working!
THANKS Hadaka.

OK here are the reuslts just for the other users.

First:
```
XXXX@XXXX-HP-Notebook:~$ sudo rm -rf rtlwifi_new
[sudo] password for XXXX: 
XXXX@XXXX-HP-Notebook:~$ sudo rm/etc/modprobe.d/rtlbtcoex.conf
sudo: rm/etc/modprobe.d/rtlbtcoex.conf: command not found
XXXX@XXXX-HP-Notebook:~$
```

Second: 
Ran ALL the codes from the link [HTML]http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904[/HTML]
The first code obviously gave negative result. Yet I restarted.
Results
```
XXXX@XXXX-HP-Notebook:~$ sudo apt-get install git build-essential
[sudo] password for XXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
git is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 164 not upgraded.
XXXX@XXXX-HP-Notebook:~$ git clone -b rock.new_btcoex https://github.com/lwfinger/rtlwifi_new
Cloning into 'rtlwifi_new'...
remote: Counting objects: 4229, done.
remote: Total 4229 (delta 0), reused 0 (delta 0), pack-reused 4229
Receiving objects: 100% (4229/4229), 6.74 MiB | 421.00 KiB/s, done.
Resolving deltas: 100% (3565/3565), done.
Checking connectivity... done.
XXXX@XXXX-HP-Notebook:~$ cd rtlwifi_new
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$ make
make -C /lib/modules/3.19.0-51-generic/build M=/home/XXXX/rtlwifi_new modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'
  CC [M]  /home/XXXX/rtlwifi_new/base.o
  CC [M]  /home/XXXX/rtlwifi_new/cam.o
  CC [M]  /home/XXXX/rtlwifi_new/core.o
  CC [M]  /home/XXXX/rtlwifi_new/debug.o
  CC [M]  /home/XXXX/rtlwifi_new/efuse.o
  CC [M]  /home/XXXX/rtlwifi_new/ps.o
  CC [M]  /home/XXXX/rtlwifi_new/rc.o
  CC [M]  /home/XXXX/rtlwifi_new/regd.o
  CC [M]  /home/XXXX/rtlwifi_new/stats.o
  LD [M]  /home/XXXX/rtlwifi_new/rtlwifi.o
  CC [M]  /home/XXXX/rtlwifi_new/pci.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl_pci.o
  CC [M]  /home/XXXX/rtlwifi_new/usb.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl_usb.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8723b2ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtcoutsrc.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8192e2ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8723b1ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8821a1ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8821a2ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8812a1ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8812a2ant.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/halbtc8812a_ext.o
  CC [M]  /home/XXXX/rtlwifi_new/btcoexist/rtl_btc.o
  LD [M]  /home/XXXX/rtlwifi_new/btcoexist/btcoexist.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/pwrseq.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/pwrseqcmd.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8188ee/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8188ee/rtl8188ee.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192c/main.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192c/dm_common.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192c/fw_common.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192c/phy_common.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192c/rtl8192c-common.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ce/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192ce/rtl8192ce.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/mac.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192cu/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192cu/rtl8192cu.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192de/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192de/rtl8192de.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/pwrseq.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/pwrseqcmd.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192ee/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192ee/rtl8192ee.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8192se/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192se/rtl8192se.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/hal_btc.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/hal_bt_coexist.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/pwrseq.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/pwrseqcmd.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723ae/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8723ae/rtl8723ae.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/pwrseq.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/pwrseqcmd.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8723be/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8723be/rtl8723be.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/dm.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/fw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/hw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/led.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/phy.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/pwrseq.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/pwrseqcmd.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/rf.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/sw.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/table.o
  CC [M]  /home/XXXX/rtlwifi_new/rtl8821ae/trx.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8821ae/rtl8821ae.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/XXXX/rtlwifi_new/btcoexist/btcoexist.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/btcoexist/btcoexist.ko
  CC      /home/XXXX/rtlwifi_new/rtl8188ee/rtl8188ee.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8188ee/rtl8188ee.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192c/rtl8192c-common.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192ce/rtl8192ce.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192cu/rtl8192cu.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192de/rtl8192de.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192ee/rtl8192ee.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192ee/rtl8192ee.ko
  CC      /home/XXXX/rtlwifi_new/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8192se/rtl8192se.ko
  CC      /home/XXXX/rtlwifi_new/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8723ae/rtl8723ae.ko
  CC      /home/XXXX/rtlwifi_new/rtl8723be/rtl8723be.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8723be/rtl8723be.ko
  CC      /home/XXXX/rtlwifi_new/rtl8821ae/rtl8821ae.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl8821ae/rtl8821ae.ko
  CC      /home/XXXX/rtlwifi_new/rtl_pci.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl_pci.ko
  CC      /home/XXXX/rtlwifi_new/rtl_usb.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtl_usb.ko
  CC      /home/XXXX/rtlwifi_new/rtlwifi.mod.o
  LD [M]  /home/XXXX/rtlwifi_new/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
XXXX@XXXX-HP-Notebook:~/rtlwifi_new$ sudo make install
make -C /lib/modules/3.19.0-51-generic/build M=/home/XXXX/rtlwifi_new modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-51-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-51-generic'
Making backups
Install rtlwifi SUCCESS
```

Third
The value for ant_sel that worked for me was "2" and not "1" like it did earlier.
```
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -rv rtl8723be
[sudo] password for XXXX: 
rmmod rtl8723be
rmmod rtl_pci
rmmod btcoexist
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -v rtl8723be ant_sel=1
insmod /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=1 ant_sel=1
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -rv rtl8723be
rmmod rtl8723be
rmmod rtl_pci
rmmod btcoexist
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
XXXX@XXXX-HP-Notebook:~$ sudo modprobe -v rtl8723be ant_sel=2
insmod /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=1 ant_sel=2
XXXX@XXXX-HP-Notebook:~$ 

```

After setting the value of ant_sel to "2" I "forgot" the network I was trying to connect to. Keeping Wifi enabled of course! (Very Important). Then I restarted.
And then I chose the network I was trying to connect to....and _**voila!!!**_ Full strength next to the router unlike before and 3 bars in the desired location where earlier the connection was getting disconnected.

Thanks Hadaka for your continued support. And Patience.

~a

PS might need support again in case it goes rogue again. For now Marking this as SOLVED.

---

### Post by Hadaka on 2016-03-23
Great ! glad you got it working.

---

### Post by amol7 on 2016-03-23
> **jeremy31 said:**
> Post ```
cd rtlwifi_new
git status
```

> **Hadaka said:**
> Great ! glad you got it working.


Thanks Jeremy31 and Hadaka once again.


~a

---

### Post by Hadaka on 2016-03-23
Hi , I just noticed on post #26 this error..
```
XXXX@XXXX-HP-Notebook:~$ sudo rm/etc/modprobe.d/rtlbtcoex.conf
sudo: rm/etc/modprobe.d/rtlbtcoex.conf: command not found
```
That is my fault, there should have been a space after "rm"
```
sudo **rm** /etc/modprobe.d/rtlbtcoex.conf
```
please verify all is well by doing...
```
cat /etc/modprobe.d/rtlbtcoex.conf
```
*If the above command results in..."No such file or directory"
Then..do..
```
echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtlbtcoex.conf
```
*If and only if the value is " 1 " 
Then do..
```
sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.d/rtlbtcoex.conf
```
thanks.

---

### Post by amol7 on 2016-03-24
> **Hadaka said:**
> Hi , I just noticed on post #26 this error..
```
XXXX@XXXX-HP-Notebook:~$ sudo rm/etc/modprobe.d/rtlbtcoex.conf
sudo: rm/etc/modprobe.d/rtlbtcoex.conf: command not found
```
That is my fault, there should have been a space after "rm"
```
sudo **rm** /etc/modprobe.d/rtlbtcoex.conf
```
please verify all is well by doing...
```
cat /etc/modprobe.d/rtlbtcoex.conf
```
*If the above command results in..."No such file or directory"
Then..do..
```
echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtlbtcoex.conf
```
*If and only if the value is " 1 " 
Then do..
```
sudo sed -i 's/ant_sel=1/ant_sel=2/' /etc/modprobe.d/rtlbtcoex.conf
```
thanks.

Well here's the result of : 

```
cat /etc/modprobe.d/rtlbtcoex.conf
```

```
XXXX@XXXX-HP-Notebook:~$ cat /etc/modprobe.d/rtlbtcoex.conf
options rtl8723be ant_sel=2
```


I guess all well then..........


~a

---

### Post by Hadaka on 2016-03-24
Fantastic ! yes it is, you did great. 
thank you.

---

### Post by amol7 on 2016-03-24
Thanks :)

But I couldn't have done it with out your support and expertise. :)

---


---
title: "help please for newbie"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by yannis4 on 2016-04-12
I recently installed ubuntu  and I purchased a Le guang LG-N120 wireless adapter  since i dont have a cd on my laptop to install I downloaded Ralink_3070.rar qnd it gives me this file in the linux folder
2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DP , I searched the forum and tried some commands and it nothing.

---

### Post by andreid2 on 2016-04-12
That is a bit vague. You downloaded a RAR file, which (presumely) holds a driver for your wireless adapter. Unpacking the RAR file results in a extracted file you don't know what to do with it. First, I think it is odd that there comes no installation manual along with it (like a "install.txt" file). Perhaps installation instructions are to be found on the website of the distributor?
Secondly, is it the filename you describe or the folder name? If it is the folder name, look for some .sh files in it. If there are none, perhaps you can put a list of the content here.
If it is the name of the file, well... then I absolutely don't have a clue what kind of file it is :). You might try to execute it (something like ". filename"), but doubt that will have any true effect.

My advice would be to look up the installation manual of it. But on the other hand, perhaps someone else over here knows just exactly what the file is about and knows the proper solution :).

---

### Post by deadflowr on 2016-04-12
Moved to **Networking and Wireless** sub-forum

I would recommend taking a quick look at [this thread]("http://ubuntuforums.org/showthread.php?t=370108"), for starters.

---

### Post by leunam12 on 2016-04-12
It seems to me that the extracted file is also a compressed file, what happens in you double-click it?

---

### Post by Hadaka on 2016-04-12
Hi, please open a terminal ctrl/alt/t then Copy and paste the wireless script command
A file will be written to your home directory.The file name is ***wireless-info.txt***
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
From your home directory please copy and post the ***wireless-info.txt***
thanks.

---

### Post by yannis4 on 2016-04-13
lorena@lorena-Lenovo-B50-30:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
--2016-04-13 16:30:36--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.252.120
Connecting to github.com (github.com)|192.30.252.120|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2016-04-13 16:30:37--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.43.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.43.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2016-04-13 16:30:37--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Reusing existing connection to raw.githubusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: &#8216;wireless-info&#8217;


100%[======================================>] 15,868      --.-K/s   in 0.001s  


2016-04-13 16:30:38 (24.1 MB/s) - &#8216;wireless-info&#8217; saved [15868/15868]


[sudo] password for lorena: 


Results saved in "/home/lorena/wireless-info.txt".


Results also archived in "/home/lorena/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

---

### Post by slickymaster on 2016-04-13
> **yannis4 said:**
> lorena@lorena-Lenovo-B50-30:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
--2016-04-13 16:30:36--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.252.120
Connecting to github.com (github.com)|192.30.252.120|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2016-04-13 16:30:37--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 23.235.43.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|23.235.43.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2016-04-13 16:30:37--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Reusing existing connection to raw.githubusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 15868 (15K) [text/plain]
Saving to: ‘wireless-info’


100%[======================================>] 15,868      --.-K/s   in 0.001s  


2016-04-13 16:30:38 (24.1 MB/s) - ‘wireless-info’ saved [15868/15868]


[sudo] password for lorena: 


Results saved in "**[COLOR=#ff0000]/home/lorena/wireless-info.txt[/COLOR]**".


Results also archived in "/home/lorena/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
Please upload the wireless-info.txt file into the thread so we can see it. Alternatively you can post its contents, using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by yannis4 on 2016-04-13
i used the windows driver with winetricks and i get this message Ralink Wireless Card does not exist and testing mode showed no wlan card

---

### Post by X-RED_Tech on 2016-04-13
> **yannis4 said:**
> i used the windows driver with winetricks and i get this message Ralink Wireless Card does not exist and testing mode showed no wlan card

Obviously... Now please do as requested in the previous post - post the resulting file from the troubleshooting script - so the experts here can know what chipset it has, what driver is required and the best way to obtain it.

Also, a quick Google search suggests it has the old Ralink 3070 chipset which I think is has native support for a long time already. Have you really tested it or instead you immediately jumped to the conclusion you'd need to install a driver?

---

### Post by yannis4 on 2016-04-13
but how can i test it, sorry but im a little bit new lost here

---

### Post by slickymaster on 2016-04-13
> **yannis4 said:**
> but how can i test it, sorry but im a little bit new lost here

Please do what's requested [here]("http://ubuntuforums.org/showthread.php?t=2320273&p=13469731&viewfull=1#post13469731").

---

### Post by X-RED_Tech on 2016-04-13
Any wifi device with native support will just work.
If you click the network indicator (icon) and see wireless networks there then it's working. Select yours and enter the password when asked. Done.
If you don't see any then it isn't working out of the box, that simple.

PS - you again lost an opportunity to post the file slickymaster asked for. Without it it's hard if not impossible to help you. Please do it ASAP.

---

### Post by yannis4 on 2016-04-13
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

### Post by slickymaster on 2016-04-13
You posted the script itself, not the obtaining file from running it. Since you already had run the script, as proved in your post [here]("http://ubuntuforums.org/showthread.php?t=2320273&p=13469728&viewfull=1#post13469728"), all you have to do is to upload the _**wireless-info.txt **_(or copy/past its contents into the thread) you have in your **_/home/lorena/ _**directory.

---

### Post by Hadaka on 2016-04-13
Yannis4, 
```
 #
#Results saved in "/home/lorena/wireless-info.txt".
#Results also archived in "/home/lorena/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums
```
please open a terminal and do..
```
dir wireless-info.tar.gz
```
Then attach the file to your reply.
also please COPY and post the output of,,
```
lsusb
rfkill list all
```
the first command is 'LSUSB',lower case L ..lsusb
thanks
.

---

### Post by slickymaster on 2016-04-13
> **Hadaka said:**
> ...
```
 #
#Results saved in "/home/lorena/wireless-info.txt".
[COLOR="#FF0000"]#Results also archived in "/home/lorena/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums[/COLOR]
```...

Good catch, Hadaka. Didn't read all the way through.

---

### Post by yannis4 on 2016-04-13
> **Hadaka said:**
> Yannis4, 
```
 #
#Results saved in "/home/lorena/wireless-info.txt".
#Results also archived in "/home/lorena/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums
```
please open a terminal and do..
```
dir wireless-info.tar.gz
```
Then attach the file to your reply.
also please COPY and post the output of,,
```
lsusb
rfkill list all
```
the first command is 'LSUSB',lower case L ..lsusb
thanks
.
```
lorena@lorena-Lenovo-B50-30:~$ dir wireless-info.tar.gz
wireless-info.tar.gz
lorena@lorena-Lenovo-B50-30:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 036: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 001 Device 004: ID 13d3:5727 IMC Networks 
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lorena@lorena-Lenovo-B50-30:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
372: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
lorena@lorena-Lenovo-B50-30:~$
```

---

### Post by Hadaka on 2016-04-13
Hi, open a terminal ctrl/alt/t and do..
```
sudo modprobe -v rt2800usb
```
then please post what has been asked 5 times,.,.
insert your wireless usb
please open a terminal and do..
     Code:
     ```
dir wireless-info.tar.gz
```
this will be in your home directory the file...copy and paste it 
here OR paste the WIRELESS-INFO.TXT file...as much of it as you can,

Then attach the file to your reply.
thanks

---

### Post by yannis4 on 2016-04-13
```
########## wireless info START ##########


Report from: 13 Apr 2016 23:04 CEST +0200


Booted last: 13 Apr 2016 12:59 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################




03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380c]
    Kernel driver in use: r8169


04:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:4026]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 036: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 001 Device 004: ID 13d3:5727 IMC Networks 
Bus 001 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
372: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
471: phy674: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath3k                  17414  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
rt2800usb              27034  0 
ath9k                 164164  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638915  4 ath9k,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              496328  4 ath,ath9k,mac80211,rt2x00lib
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr f0:76:1c:1e:b1:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


virbr0    Link encap:Ethernet  HWaddr e2:b4:fa:59:12:34  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 5c:93:a2:e6:e7:e9  
          inet addr:192.168.182.11  Bcast:192.168.182.15  Mask:255.255.255.240
          inet6 addr: fe80::5e93:a2ff:fee6:e7e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1477500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1069751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2089164050 (2.0 GB)  TX bytes:112686952 (112.6 MB)


wlan1     Link encap:Ethernet  HWaddr 78:d3:8d:0c:0d:c2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


virbr0    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"PROXIMUS_FON"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 06:19:70:49:B9:F7   
          Bit Rate=36 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/70  Signal level=-90 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:449   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.182.1   0.0.0.0         UG    0      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.182.0   0.0.0.0         255.255.255.240 U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search coova.org


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root      1001     1  0 14:59 ?        00:00:55 NetworkManager


##### NetworkManager info ###############




NetworkManager Tool


State: connected (global)


- Device: wlan0  [PROXIMUS_FON] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        5C:93:A2:E6:E7:E9


  Capabilities:
    Speed:           36 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    WiFi-2.4-19ED:   Infra, 9C:97:26:99:19:ED, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA2
    WiFi-2.4-827D:   Infra, 30:91:8F:65:82:7D, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2
    MIK:             Infra, 30:91:8F:9E:88:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    MDF:             Infra, 28:C6:8E:6C:57:23, Freq 2422 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    PROXIMUS_AUTO_FON: Infra, 0A:19:70:49:B9:F7, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    Maison1:         Infra, 40:F2:01:83:39:7A, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    VOO-261054:      Infra, C0:3F:0E:F1:E8:1C, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    lillalina:       Infra, 00:19:70:49:B9:F7, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA
    WiFi-2.4-2211:   Infra, 30:91:8F:30:22:11, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    VOO-245211:      Infra, 6C:19:8F:A2:B1:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    VOO-130930:      Infra, 10:0D:7F:8F:DD:2D, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    VOO-245211:      Infra, A0:21:B7:D8:1C:11, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    WiFi-2.4-BC89:   Infra, 30:91:8F:DD:BC:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2

WiFi-2.4-B817: Infra, 30:91:8F:12:B8:17, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
BRUXELLES: Infra, 90:84:0D:D6:F8:93, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
PROXIMUS_AUTO_FON: Infra, 0A:19:70:A4:4C:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
Maison1_EXT: Infra, 00:0C:F6:FA:4D:16, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WEP
Maison2: Infra, 00:11:50:B5:31:A0, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WEP
SARAH: Infra, 00:18:39:DB:E0:37, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WEP
VOO_HOMESPOT: Infra, C2:3F:0E:F1:E8:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
VOO_HOMESPOT: Infra, 2A:C6:8E:6C:57:24, Freq 2422 MHz, Rate 54 Mb/s, Strength 54
VOO_HOMESPOT: Infra, 12:0D:7F:8F:DD:2E, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
VOO_HOMESPOT: Infra, A2:21:B7:E6:9A:34, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
*PROXIMUS_FON: Infra, 06:19:70:49:B9:F7, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
Le Wi-Fi du Cougar (The Return): Infra, 94:44:52:E9:8E:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
Maison3: Infra, BC:F2:AF:AE:0A:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
bbox2-529c: Infra, 00:19:70:92:10:89, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
WiFi-2.4-B560: Infra, 00:37:B7:60:B5:66, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
VOO-812937: Infra, 10:0D:7F:94:D7:BD, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
PROXIMUS_AUTO_FON: Infra, 42:F2:01:87:54:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
bbox2-6020: Infra, 00:19:70:91:BB:AC, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
bbox2-ce38: Infra, 00:19:70:34:10:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
bbox2-5fd8: Infra, 00:19:70:A4:4C:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
WiFi-2.4-5404: Infra, 40:F2:01:87:54:0A, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
VOO_HOMESPOT: Infra, A2:21:B7:D8:1C:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
PROXIMUS_FON: Infra, 42:F2:01:87:54:0B, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
PROXIMUS_FON: Infra, 06:19:70:A4:4C:27, Freq 2412 MHz, Rate 54 Mb/s, Strength 15
WiFi-2.4-EB2B: Infra, A4:B1:E9:AD:EB:2B, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
RA: Infra, 58:6D:8F:B4:48:70, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA2


IPv4 Settings:
Address: 192.168.182.11
Prefix: 28 (255.255.255.240)
Gateway: 192.168.182.1


DNS: 195.238.2.21
DNS: 195.238.2.22




- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: r8169
State: unavailable
Default: no
HW Address: F0:76:1C:1E:B1:2C


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off






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


no-auto-default=F0:76:1C:1E:B1:2C,


[ifupdown]
managed=false


##### NetworkManager profiles ###########
```

---

### Post by Hadaka on 2016-04-13
ok..you first posted..
"I recently installed ubuntu and I purchased a Le guang LG-N120 wireless adapter since i dont have a cd on my laptop to install I downloaded Ralink_3070.rar"
 
The Ralink_3070.rar file is usless on Ubuntu, it will not load, and the system will not even be able to read it.
so, if you can find the file, delete it.
That Ralink wireless usb, should run well on the native rt2800usb driver, that i had you activate. and it is currently
in your module list.
however..your internal card is currently running on wlan0 with driver ath9k.

04:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
Subsystem: Lenovo Device [17aa:4026]
Kernel driver in use: ath9k
---------------------------------------------------------------------------------------------------------------------
Network manager shows Wicd and Network manager both loaded...this will not work..you can only have one 
of them managing your network...so choose
##### network managers ##################

Installed:
NetworkManager
Wicd
----------------------------------------------------------------------------------------------------------------------
As you can see your internal wifi card is running and connected using driver ath9k on wlan0
wirth a very weak signal and confused about which network manager to use.

- Device: wlan0 [PROXIMUS_FON]
Type: 802.11 WiFi
Driver: ath9k
State: connected
Default: yes

wlan0 IEEE 802.11bgn ESSID:"PROXIMUS_FON"
Mode:Managed Frequency:2.412 GHz Access Point: 06:19:70:49:B9:F7
Bit Rate=36 Mb/s Tx-Power=16 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

Link Quality=20/70 Signal level=-90 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
---------------------------------------------------------------------------------------------------------------------
Im going to assume this is the usb wifi you plugged in and is not working...

wlan1 Link encap:Ethernet HWaddr 78:d3:8d:0c:0d:c2
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

##### iwconfig ##########################

virbr0 no wireless extensions. <<-----What is this????

so remove the usb wifi do not plug it in for now, decide which network manager you want to use, check your
antenna connections on your router and on your internal wifi card. Once you have some of this done then
again..do not ,... insert the usb for now...but run another wireless-info scan and then paste the results like you
finally did. And please explain to me what virbro0 is....i know nothing of virtual networking.
thanks.

---

### Post by leunam12 on 2016-04-14
> **yannis4 said:**
> but how can i test it, sorry but im a little bit new lost here
On your desktop on the upper right corner there should be a network manager icon, if you click on it you will be able to see if there are networks available, if you can see networks available it means that your wireless device is working. If it is then click on your network name and connect to it.

---


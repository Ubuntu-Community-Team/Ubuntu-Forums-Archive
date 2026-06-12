---
title: "wifi unbearably slow (I assure you i used the sticky post first)"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by subcook on 2015-07-13
I assure you that I used the sticky posting at the top of Networking first, to no avail.

I did the sudo apt-get update than ran [COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \

my result :

>


maybe I'm missing something as I am very far from a command line guru

My problem is that over the last day or so I noticed that my wifi was running horribly slow, as in 40-50 kb/s.  usually its 900kb - 1.5 mb /s

the specs to my computer (laptop)     [/FONT][/COLOR][http://www.cnet.com/products/toshiba...-series/specs/]("http://www.cnet.com/products/toshiba-satellite-l855-s5383-15-6-core-i7-3630qm-windows-8-8-gb-ram-640-gb-hdd-series/specs/")     however I don't seem to see a spec for the network card.

I know it's not the hardware as I am dual booting (win7/Kubuntu 14.04) and Windblow$ is running just fine when downloading files.  I should also point out that this is a relatively new clean install of kubuntu (1 week, tops)

I am stumped.  If I am entering the command to download the wireless-info program by all means please inform me how to correct me discrepancy as I'll probably learn even more.

Thanks in advance !

---

### Post by weatherman2 on 2015-07-13
After you download the wireless-info script, type this in a terminal:

(maybe "cd ~/Downloads" first)

```

/bin/bash ./wireless-info

```

(give your password as needed)

If you get "file not found" then you need to cd into the directory where you downloaded the wireless-info script.

---

### Post by subcook on 2015-07-13
thats the thing, I dont think I ever actually downloaded the wireless info script.

I did the command/script as stated above ......  but immediatly after hitting "the enter key" the next line :

>

....and stayed there forever..... I'm thinking I screwed up the command ....



that command being :           [COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 [/FONT][/COLOR][https://github.com/UbuntuForums/wire.../wireless-info]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info")[COLOR=#000000][FONT=Ubuntu Mono] && \[/FONT][/COLOR]

---

### Post by weatherman2 on 2015-07-13
Just run  it this way (one command per line:)

```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
/bin/bash ./wireless-info

```

---

### Post by subcook on 2015-07-13
weatherman,

thank you ... sometimes the linux community (as much as I love them and they have done nothing but help me)-(especially k/ubuntu) can be unforgiving .... I did what you said and it worked like a charm :

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
        Kernel driver in use: rtl8723ae


......assuming this is the info we need ... any advice ?

---

### Post by weatherman2 on 2015-07-13
The wireless script outputs a page or two of information, not just those two lines.  To help you, people are going to want to see it all...

And please post it within "CODE" tags - meaning, put 

[XXCODE]

first, then the output of the script, followed by

[XX/CODE]

but remove the "XX" (I forget how to type it so you'll actually see the braces - sorry.)

---

### Post by subcook on 2015-07-13
sorry, was trying to narrow it down

XXCODE

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


SCRIPTDATE="2015-05-21 11:10 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"


MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
DMESGMATCHES="(wlan[0-9]|eth[1-9]|firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"                                                                                                                                                                         
                                                                                                                                                                                                
DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"


NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")


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
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d;/^[^[:space:]]/ i\\'


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
ifconfig -a | sed '/^lo /,/^$/d'


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
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'


printf "\n########## wireless info END ############\n\n"


exec 2>&4 4>&-
exec 1>&3 3>&-


##### MAC address masking #####


RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'


ORIGIFS="$IFS"
IFS=$'\n'


IFACESRAW=$(sed -n '/^##### ifconfig #####/,/^##### /p' <<< "$RESULTS")
IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFACESRAW"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFACESRAW"))


WLAPSIWLRAW=$(sed -n '/^##### iwlist scan #####/,/^##### /p' <<< "$RESULTS")
WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h;/^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$WLAPSIWLRAW"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$WLAPSIWLRAW"))


WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))


IFS="$ORIGIFS"


for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]-address}>;I;"
done


for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]-address}>;I;"
done


for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]-address}>;I;"
done


sed "$MACMASKSED/\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"


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

XX/CODE

....I hope I did this correctly to help you read it easier, thank you again

---

### Post by weatherman2 on 2015-07-13
OK - that's not the output of the wireless script.  That IS the wireless script.  We don't need to see that.  

After you run it, it should create a file called "wireless-info.txt" in the current directory.  See if you can copy-and-paste that output here.

Try typing this:

```
more ./wireless-info.txt
```

And please use code tags.  Start the code with [XXCODE] and end with [/XXCODE] but remove the "XX" so the only letters between the braces are "CODE" and "/CODE" .  I can't actually write it out here or it will turn into a code section (someone will come along and show me how to quote it properly I suppose).

And please don't make a new reply for that if you can - try to go back and edit your previous post, remove all of those lines, and replace them with the contents of wireless-info.txt

---

### Post by subcook on 2015-07-13
I did, please see above

---

### Post by subcook on 2015-07-15
?

---

### Post by subcook on 2015-07-15
Okay, I think I have it correctly this time

Thanks for your patience




```


########## wireless info START ##########


Report from: 13 Jul 2015 21:29 EDT -0400


Booted last: 13 Jul 2015 17:23 EDT -0400


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty


##### kernel ############################


Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


KDE Plasma Workspace


##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
        Subsystem: Toshiba America Info Systems Device [1179:ff1e]
        Kernel driver in use: alx


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
        Kernel driver in use: rtl8723ae


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 10f1:1a43 Importek 
Bus 001 Device 004: ID 0930:021d Toshiba Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 003 Device 002: ID 047d:203e Kensington 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no


##### lsmod #############################


rtl8723ae              81799  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                64255  2 rtl_pci,rtl8723ae
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              494362  2 mac80211,rtlwifi
wmi                    19193  1 toshiba_acpi


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
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:18d:8000:c910:696b:c450:42f1:81a/64 Scope:Global
          inet6 addr: 2601:18d:8000:c910:2ed0:5aff:fe20:e5aa/64 Scope:Global
          inet6 addr: fe80::2ed0:5aff:fe20:e5aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41916802 (41.9 MB)  TX bytes:6307717 (6.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"HOME-BAB6"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HOME-BAB6' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################
Installed:


        NetworkManager


Running:


root      1154     1  0 17:23 ?        00:00:07 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [HOME-BAB6] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
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
    Ken's-pc:        Infra, <MAC 'Ken's-pc' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    notnetgear:      Infra, <MAC 'notnetgear' [AC10]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47
    linxlikeme:      Infra, <MAC 'linxlikeme' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    DIRECT-roku-E492BB: Infra, <MAC 'DIRECT-roku-E492BB' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 2 WPA2
    HOME-A422:       Infra, <MAC 'HOME-A422' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    HOME-5D22:       Infra, <MAC 'HOME-5D22' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Find me for Free WiFi: Infra, <MAC 'Find me for Free WiFi' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    *HOME-BAB6:      Infra, <MAC 'HOME-BAB6' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    NETGEAR29:       Infra, <MAC 'NETGEAR29' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    pete's network:  Infra, <MAC 'pete's network' [AN15]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    The Cellar:      Infra, <MAC 'The Cellar' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NETGEAR:         Infra, <MAC 'NETGEAR' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    NETGEAR_Guest1:  Infra, <MAC 'NETGEAR_Guest1' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    HOME-1472:       Infra, <MAC 'HOME-1472' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    NETGEAR11:       Infra, <MAC 'NETGEAR11' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    The Cellar_2GEXT:Infra, <MAC 'The Cellar_2GEXT:Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    HOME-436F:       Infra, <MAC 'HOME-436F' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76


  IPv6 Settings:
    Address:         2601:18d:8000:c910:2ed0:5aff:fe20:e5aa
    Prefix:          128
    Gateway:         ::


    Address:         2601:18d:8000:c910:696b:c450:42f1:81a
    Prefix:          64
    Gateway:         ::
Address:         2601:18d:8000:c910:2ed0:5aff:fe20:e5aa
    Prefix:          64
    Gateway:         ::


    Address:         fe80::2ed0:5aff:fe20:e5aa
    Prefix:          64
    Gateway:         ::


    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2


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


[[/etc/NetworkManager/system-connections/HOME-BAB6]] (600 root)
[connection] id=HOME-BAB6 | type=802-11-wireless
[802-11-wireless] ssid=HOME-BAB6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.452 GHz (Channel 9)
      10   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME-BAB6' [AC1]>
Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"HOME-BAB6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a95550ec
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e5a9180
                    Extra: Last beacon: 352ms ago
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a9555ebc
Extra: Last beacon: 4ms ago
          Cell 04 - Address: <MAC 'DIRECT-roku-E492BB' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-E492BB"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000785dee7039
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'linxlikeme' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"linxlikeme"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d1ab15c
                    Extra: Last beacon: 1964ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
   Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d12ebb4
                    Extra: Last beacon: 2472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'xfinitywifi' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d2d1b80
                    Extra: Last beacon: 4ms ago
          Cell 08 - Address: <MAC '
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a94aaa6d
                    Extra: Last beacon: 740ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm 
 Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e55e180
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'notnetgear' [AC10]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"notnetgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e577262
                    Extra: Last beacon: 508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HOME-7412-2.4' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"HOME-7412-2.4"
 Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000066ae6f26180
                    Extra: Last beacon: 3308ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Find me for Free WiFi' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Find me for Free WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000640c2a1648
                    Extra: Last beacon: 3268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'xfinitywifi' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7b21a530d
                    Extra: Last beacon: 464ms ago
          Cell 14 - Address: <MAC 'Ken's-pc' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Ken's-pc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f39221965e
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'HOME-5D22' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"HOME-5D22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7b210e177
                    Extra: Last beacon: 1084ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8723ae]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     5FDB4D618B8E6F42C4EA3C8
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723ae]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 3376.887042] rtlwifi: wireless switch is on
[ 3379.250902] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[ 3379.280474] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[ 3379.282038] wlan0: authenticated
[ 3379.284241] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[ 3379.287569] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[ 3379.287804] wlan0: associated
[11475.358108] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11476.789208] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11476.819614] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11476.821206] wlan0: authenticated
[11476.823200] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11476.826465] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11476.826705] wlan0: associated
[11530.008589] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11531.447399] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11531.478111] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11531.479650] wlan0: authenticated
[11531.481713] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11531.484975] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11531.485217] wlan0: associated
[11544.552951] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11545.988031] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11546.018427] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11546.122179] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 2/3)
[11546.226258] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 3/3)
[11546.330351] wlan0: authentication with <MAC 'HOME-BAB6' [AC1]> timed out
[11547.789719] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11547.819957] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11547.824897] wlan0: authenticated
[11547.827616] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11547.837945] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11547.838193] wlan0: associated


########## wireless info END ############














```

---

### Post by weatherman2 on 2015-07-16
You have a Realtek RTL8723AE wireless card.

A solution seems to be here - see if you can follow it:

[https://answers.launchpad.net/ubuntu/+question/245494](https://answers.launchpad.net/ubuntu/+question/245494)

---

### Post by subcook on 2015-07-16
```


########## wireless info START ##########


Report from: 13 Jul 2015 21:29 EDT -0400


Booted last: 13 Jul 2015 17:23 EDT -0400


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty


##### kernel ############################


Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


KDE Plasma Workspace


##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
        Subsystem: Toshiba America Info Systems Device [1179:ff1e]
        Kernel driver in use: alx


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
        Kernel driver in use: rtl8723ae


##### lsusb #############################
                                                                                                                                                                                                
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub                                                                                                                       
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                                                                                                                                  
Bus 001 Device 005: ID 10f1:1a43 Importek 
Bus 001 Device 004: ID 0930:021d Toshiba Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 003 Device 002: ID 047d:203e Kensington 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no


##### lsmod #############################


rtl8723ae              81799  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                64255  2 rtl_pci,rtl8723ae
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              494362  2 mac80211,rtlwifi
wmi                    19193  1 toshiba_acpi


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
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:18d:8000:c910:696b:c450:42f1:81a/64 Scope:Global
          inet6 addr: 2601:18d:8000:c910:2ed0:5aff:fe20:e5aa/64 Scope:Global
          inet6 addr: fe80::2ed0:5aff:fe20:e5aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41916802 (41.9 MB)  TX bytes:6307717 (6.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"HOME-BAB6"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HOME-BAB6' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


        NetworkManager


Running:


root      1154     1  0 17:23 ?        00:00:07 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [HOME-BAB6] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
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
    Ken's-pc:        Infra, <MAC 'Ken's-pc' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    notnetgear:      Infra, <MAC 'notnetgear' [AC10]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47
    linxlikeme:      Infra, <MAC 'linxlikeme' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    DIRECT-roku-E492BB: Infra, <MAC 'DIRECT-roku-E492BB' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 2 WPA2
    HOME-A422:       Infra, <MAC 'HOME-A422' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    HOME-5D22:       Infra, <MAC 'HOME-5D22' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Find me for Free WiFi: Infra, <MAC 'Find me for Free WiFi' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    *HOME-BAB6:      Infra, <MAC 'HOME-BAB6' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    NETGEAR29:       Infra, <MAC 'NETGEAR29' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    pete's network:  Infra, <MAC 'pete's network' [AN15]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA2
    The Cellar:      Infra, <MAC 'The Cellar' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NETGEAR:         Infra, <MAC 'NETGEAR' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    NETGEAR_Guest1:  Infra, <MAC 'NETGEAR_Guest1' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47
    HOME-1472:       Infra, <MAC 'HOME-1472' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    NETGEAR11:       Infra, <MAC 'NETGEAR11' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    The Cellar_2GEXT:Infra, <MAC 'The Cellar_2GEXT:Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    HOME-436F:       Infra, <MAC 'HOME-436F' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76


  IPv6 Settings:
    Address:         2601:18d:8000:c910:2ed0:5aff:fe20:e5aa
    Prefix:          128
    Gateway:         ::


    Address:         2601:18d:8000:c910:696b:c450:42f1:81a
    Prefix:          64
    Gateway:         ::


    Address:         2601:18d:8000:c910:2ed0:5aff:fe20:e5aa
    Prefix:          64
    Gateway:         ::


    Address:         fe80::2ed0:5aff:fe20:e5aa
    Prefix:          64
    Gateway:         ::


    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2


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


[[/etc/NetworkManager/system-connections/HOME-BAB6]] (600 root)
[connection] id=HOME-BAB6 | type=802-11-wireless
[802-11-wireless] ssid=HOME-BAB6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.452 GHz (Channel 9)
      10   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME-BAB6' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"HOME-BAB6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a95550ec
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e5a9180
                    Extra: Last beacon: 352ms ago
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a9555ebc
                    Extra: Last beacon: 4ms ago
          Cell 04 - Address: <MAC 'DIRECT-roku-E492BB' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-E492BB"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000785dee7039
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'linxlikeme' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"linxlikeme"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d1ab15c
                    Extra: Last beacon: 1964ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d12ebb4
                    Extra: Last beacon: 2472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'xfinitywifi' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000785d2d1b80
                    Extra: Last beacon: 4ms ago
          Cell 08 - Address: <MAC '
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a94aaa6d
                    Extra: Last beacon: 740ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e55e180
                    Extra: Last beacon: 684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'notnetgear' [AC10]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"notnetgear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000953e577262
                    Extra: Last beacon: 508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HOME-7412-2.4' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"HOME-7412-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000066ae6f26180
                    Extra: Last beacon: 3308ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Find me for Free WiFi' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Find me for Free WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000640c2a1648
                    Extra: Last beacon: 3268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'xfinitywifi' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7b21a530d
                    Extra: Last beacon: 464ms ago
          Cell 14 - Address: <MAC 'Ken's-pc' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Ken's-pc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f39221965e
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'HOME-5D22' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"HOME-5D22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7b210e177
                    Extra: Last beacon: 1084ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8723ae]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     5FDB4D618B8E6F42C4EA3C8
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723ae]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 3376.887042] rtlwifi: wireless switch is on
[ 3379.250902] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[ 3379.280474] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[ 3379.282038] wlan0: authenticated
[ 3379.284241] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[ 3379.287569] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[ 3379.287804] wlan0: associated
[11475.358108] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11476.789208] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11476.819614] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11476.821206] wlan0: authenticated
[11476.823200] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11476.826465] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11476.826705] wlan0: associated
[11530.008589] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11531.447399] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11531.478111] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11531.479650] wlan0: authenticated
[11531.481713] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11531.484975] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11531.485217] wlan0: associated
[11544.552951] wlan0: Connection to AP <MAC 'HOME-BAB6' [AC1]> lost
[11545.988031] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11546.018427] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11546.122179] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 2/3)
[11546.226258] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 3/3)
[11546.330351] wlan0: authentication with <MAC 'HOME-BAB6' [AC1]> timed out
[11547.789719] wlan0: authenticate with <MAC 'HOME-BAB6' [AC1]>
[11547.819957] wlan0: send auth to <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11547.824897] wlan0: authenticated
[11547.827616] wlan0: associate with <MAC 'HOME-BAB6' [AC1]> (try 1/3)
[11547.837945] wlan0: RX AssocResp from <MAC 'HOME-BAB6' [AC1]> (capab=0x411 status=0 aid=1)
[11547.838193] wlan0: associated


########## wireless info END ############


```

---

### Post by praseodym on 2015-07-16
If you are in the US the country settings do not fit.
```

sudo apt-get install iw
iw reg get
sudo iw reg set US
iw reg get
iwlist chan
```
Change the router settings to WPA2-AES (CCMP) and a fixed channel, not mixed mode WPA/WPA2! Check the router manual. Also deactivate IPv6 in the network manager profile

---


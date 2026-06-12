---
title: "Ubuntu 12.04 Ethernet not Detected"
date: 2014-10-19
forum: Networking &amp; Wireless
---

### Post by olyvkina on 2014-10-19
Hello All -this is my first post, so be please be kind if I come across as an idiot.

I have an old Dell Inspiron 600m, running Ubuntu 12.04 LTS. My wireless connection works, but my wired ethernet has recently decided not to cooperate. I have been lurking on these fora as a non-member for a few weeks now but I'm really at a loss and way beyond my league here. Here are some outputs that might be helpful towards a diagnosis:

Here's what my 'wireless script' file says (I know my question is about 'wired' networking, but just in case it's helpful):

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

SCRIPTDATE="2014-09-21 01:04 +0200"
FILEBASE="wireless-info"
OUTPUTDIR=$(pwd)
OUTPUTDIRFB="/tmp"

MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
DMESGMATCHES="(wlan[0-9]|eth[1-9]|firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"

DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"

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
    dialog_error "Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead."
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
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
    echo "Could not be determined."
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

printf "\n##### nm-tool ###########################\n\n"
nm-tool

printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### NetworkManager profiles ###########\n\n"
if [ -n "$SUDO" ]; then
    trap "" 2 3
    NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} + 2> /dev/null) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
    ORIGIFS="$IFS"
    IFS=$'\n'
    for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=802-11-wireless.*$/\1/p' <<< "$NMPROFILES"); do
        NMWLPRFFLPERMS=$(stat -c "%a %U" $NMWLPRFFILE)
        NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
        NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
    done
    IFS="$ORIGIFS"
    sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
    else
    echo "Acquisition of admin privileges failed."
    fi
else
    echo "No way to acquire admin privileges found."
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
iwlist chan

printf "\n##### iwlist scan #######################\n\n"
if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan 2>&1) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
    if [[ $IWLISTSCAN = *Frequency:* ]]; then
        printf "Channel occupancy:\n\n"
        grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
        echo
    fi
    egrep -v '^[ ]*IE: Unknown:|ibus-daemon' <<< "$IWLISTSCAN"
    else
    echo "Acquisition of admin privileges failed."
    fi
else
    echo "No way to acquire admin privileges found."
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

IFACESRAW=$(sed -n '/^[[:punct:]]\+ ifconfig [[:punct:]]\+/,/^[[:punct:]]\+ /p' <<< "$RESULTS")
IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFACESRAW"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFACESRAW"))

WLAPSIWLRAW=$(sed -n '/^[[:punct:]]\+ iwlist scan [[:punct:]]\+/,/^[[:punct:]]\+ /p' <<< "$RESULTS")
WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h;/^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$WLAPSIWLRAW"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$WLAPSIWLRAW"))

WLAPSNMRAW=$(sed -n '/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;p}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F ':' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
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
    PASTEBIN=$(dialog_question "Do you also want to pastebin them${DIALOGBREAK}to your default 'pastebinit' provider?")
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

rfkill list all produces:

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

 lspci -nn | grep 0280 produces:
```

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

```

Please let me know if I need to provide more information. Thanks for anyone's help!

---

### Post by ajgreeny on 2014-10-19
We need your ethernet hardware to try to figure this out.  Command **lspci -nn | grep Ethernet** should tell us what you have, though the fact that it did work and now doesn't points to something other than the ethernet card being the problem, unless it has just gone belly-up, of course.

---

### Post by olyvkina on 2014-10-19
Allrighty. Here's what I got:

```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```

---

### Post by Hadaka on 2014-10-19
Hi, you printed the script not the text file
please print the wireless script text file
and also open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b44
```
boot
connect the ethernet cable and test
thanks

---

### Post by olyvkina on 2014-10-19
Hi Hadaka- how embarassing. Here is the text file: 
```

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n########## wireless info START ##########\n\n"

########## wireless info START ##########

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z"  )
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\  +\(.\+\) - .*$/\1/p')
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 19 Oct 2014 11:38 PDT -0700

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 19 Oct 2014 09:10 PDT -0700

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 20 Sep 2014 23:04 UTC +0000
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### release ###########################\n\n"

##### release ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### kernel ############################\n\n"

##### kernel ############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ uname -srvmpio
Linux 3.2.0-69-generic-pae #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014 i686 i686 i386 GNU/Linux
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ echo

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Paramete  rs:/' /proc/cmdline
Parameters: ro, initrd=ubuntu-installer/lucid-i386/initrd.gz, splash, quiet, vt.handoff=7
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### desktop ###########################\n\n"

##### desktop ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.deskto  p")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     echo "Could not be determined."
> fi
Ubuntu 2D
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lspci #############################\n\n"

##### lspci #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d;/  ^[^[:space:]]/ i\\'

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lsusb #############################\n\n"

##### lsusb #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### PCMCIA card info ##################\n\n"

##### PCMCIA card info ##################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### rfkill ############################\n\n"

##### rfkill ############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lsmod #############################\n\n"

##### lsmod #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMAT  CHES)[^[:punct:] ]*([[:punct:] ]|$)")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ echo "$LSMOD"
ssb                    50691  1 b44
wl                   4003728  0 
ipw2200               146241  0 
libipw                 46732  1 ipw2200
cfg80211              178877  3 wl,ipw2200,libipw
lib80211               14040  4 lib80211_crypt_ccmp,wl,ipw2200,libipw
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### interfaces ########################\n\n"

##### interfaces ########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>  /' /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### ifconfig ##########################\n\n"

##### ifconfig ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ ifconfig -a | sed '/^lo /,/^$/d'
eth0      Link encap:Ethernet  HWaddr 00:13:ce:22:27:81  
          inet addr:192.168.43.240  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe22:2781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7463 errors:3 dropped:3 overruns:0 frame:0
          TX packets:9208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3214849 (3.2 MB)  TX bytes:1069976 (1.0 MB)
          Interrupt:5 Base address:0x8000 Memory:faffd000-faffdfff 

eth1      Link encap:Ethernet  HWaddr 00:12:3f:f4:00:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### iwconfig ##########################\n\n"

##### iwconfig ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:"ANDI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:0A:5B:AF:13:BB   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-19 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### route #############################\n\n"

##### route #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.43.1    0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.43.0    0.0.0.0         255.255.255.0   U     2      0        0 eth0
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### resolv.conf #######################\n\n"

##### resolv.conf #######################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/resolv.conf
nameserver 192.168.43.1
nameserver 127.0.0.1
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### nm-tool ###########################\n\n"

##### nm-tool ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [ANDI] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        00:13:CE:22:27:81

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    JC:              Infra, 00:1A:2B:A4:74:6B, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    JAM:             Infra, F8:8E:85:8A:97:93, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    *ANDI:           Infra, 5C:0A:5B:AF:13:BB, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA2
    TR:              Infra, F8:8E:85:93:95:23, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP
    HUAWEI-E5220-401b: Infra, 3C:DF:BD:7F:40:1B, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    OH:              Infra, 00:1A:2B:5D:3E:96, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WEP
    RS:              Infra, 38:72:C0:53:DE:A4, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    belkin.8d4:      Infra, 08:86:3B:FE:58:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    belkin.8d4.guests: Infra, 0A:86:3B:FE:58:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 40

  IPv4 Settings:
    Address:         192.168.43.240
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:F4:00:7A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager.state ##############\n\n"

##### NetworkManager.state ##############

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ cat -s /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager.conf ###############\n\n"

##### NetworkManager.conf ###############

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:12:3F:F4:00:7A,

[ifupdown]
managed=true
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager profiles ###########\n\n"

##### NetworkManager profiles ###########

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$SUDO" ]; then
>     trap "" 2 3
>     NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type   f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOC  MT" --} grep -vH '^$' {} + 2> /dev/null) && SUDOSUCCESS="yes" || SUDOSUCCESS="no  "
>     trap 2 3
>     if [ "$SUDOSUCCESS" = "yes" ]; then
> ORIGIFS="$IFS"
> IFS=$'\n'
> for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=802-11-wireless.*$/\1/p' <<< "$NM  PROFILES"); do
>     NMWLPRFFLPERMS=$(stat -c "%a %U" $NMWLPRFFILE)
>     NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "  $NMPROFILES"))
>     NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"  $'\n\n'
> done
> IFS="$ORIGIFS"
> sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\  ]$/d'
>     else
> echo "Acquisition of admin privileges failed."
>     fi
> else
>     echo "No way to acquire admin privileges found."
> fi
[[/etc/NetworkManager/system-connections/Auto myspot]] (600 root)
[connection] id=Auto myspot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=myspot

[[/etc/NetworkManager/system-connections/Auto Brown Home]] (600 root)
[connection] id=Auto Brown Home | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Brown Home

[[/etc/NetworkManager/system-connections/OUI PRESSE]] (600 root)
[connection] id=OUI PRESSE | type=802-11-wireless
[802-11-wireless] ssid=OUI PRESSE | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto PSU]] (600 root)
[connection] id=Auto PSU | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU

[[/etc/NetworkManager/system-connections/SC]] (600 root)
[connection] id=SC | type=802-11-wireless
[802-11-wireless] ssid=SC | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto NETGEAR64]] (600 root)
[connection] id=Auto NETGEAR64 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR64

[[/etc/NetworkManager/system-connections/Auto Bolt Bus]] (600 root)
[connection] id=Auto Bolt Bus | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Bolt Bus

[[/etc/NetworkManager/system-connections/Auto JC226]] (600 root)
[connection] id=Auto JC226 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=JC226

[[/etc/NetworkManager/system-connections/lookoutmountain404]] (600 root)
[connection] id=lookoutmountain404 | type=802-11-wireless
[802-11-wireless] ssid=lookoutmountain404 | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto McCoy South]] (600 root)
[connection] id=Auto McCoy South | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=McCoy South

[[/etc/NetworkManager/system-connections/belkin.8d4.guests]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LC Secure]] (600 root)
[ipv6] method=auto
[connection] id=LC Secure | type=802-11-wireless
[802-11-wireless] ssid=LC Secure | mac-address=00:13:CE:22:27:81
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-B40AE]] (600 root)
[connection] id=Auto MOTOROLA-B40AE | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=MOTOROLA-B40AE

[[/etc/NetworkManager/system-connections/Auto Grapes]] (600 root)
[connection] id=Auto Grapes | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grapes

[[/etc/NetworkManager/system-connections/Auto Denninwayne]] (600 root)
[connection] id=Auto Denninwayne | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Denninwayne

[[/etc/NetworkManager/system-connections/Frontier4579]] (600 root)
[connection] id=Frontier4579 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579 | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto [www.personaltelco.net]]](www.personaltelco.net]]) (600 root)
[connection] id=Auto [www.personaltelco.net](www.personaltelco.net) | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=www.personaltelco.net

[[/etc/NetworkManager/system-connections/MOTOROLA-2BAFB]] (600 root)
[connection] id=MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin.8d4.guests-b26ef860-2b58-46c3-8a57-658152b431cd]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto Doug Fir]] (600 root)
[connection] id=Auto Doug Fir | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Doug Fir

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-2BAFB]] (600 root)
[connection] id=Auto MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Boltbus_]] (600 root)
[connection] id=Auto Boltbus_ | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Boltbus_

[[/etc/NetworkManager/system-connections/Auto NETGEAR91]] (600 root)
[connection] id=Auto NETGEAR91 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR91

[[/etc/NetworkManager/system-connections/Auto CenturyLink5269]] (600 root)
[connection] id=Auto CenturyLink5269 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=CenturyLink5269
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Jupiterhotel]] (600 root)
[connection] id=Auto Jupiterhotel | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Jupiterhotel

[[/etc/NetworkManager/system-connections/Auto Library]] (600 root)
[connection] id=Auto Library | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Library

[[/etc/NetworkManager/system-connections/Auto Apple Network fa1dd8]] (600 root)
[connection] id=Auto Apple Network fa1dd8 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Apple Network fa1dd8

[[/etc/NetworkManager/system-connections/Auto new_azu_guest]] (600 root)
[connection] id=Auto new_azu_guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=new_azu_guest

[[/etc/NetworkManager/system-connections/Auto KIBO]] (600 root)
[connection] id=Auto KIBO | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KIBO

[[/etc/NetworkManager/system-connections/belkin.798.guests]] (600 root)
[connection] id=belkin.798.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.798.guests | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto qwest4352]] (600 root)
[connection] id=Auto qwest4352 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=qwest4352

[[/etc/NetworkManager/system-connections/Auto 102]] (600 root)
[connection] id=Auto 102 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=102

[[/etc/NetworkManager/system-connections/Auto LaughingPlanetBelmont]] (600 root)
[connection] id=Auto LaughingPlanetBelmont | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LaughingPlanetBelmont

[[/etc/NetworkManager/system-connections/Auto ACTIONTEC]] (600 root)
[connection] id=Auto ACTIONTEC | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ACTIONTEC

[[/etc/NetworkManager/system-connections/ANDI]] (600 root)
[connection] id=ANDI | type=802-11-wireless
[802-11-wireless] ssid=ANDI | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto hpsetup]] (600 root)
[connection] id=Auto hpsetup | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=hpsetup

[[/etc/NetworkManager/system-connections/Auto SCS]] (600 root)
[connection] id=Auto SCS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=SCS

[[/etc/NetworkManager/system-connections/Auto PEETS]] (600 root)
[connection] id=Auto PEETS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PEETS

[[/etc/NetworkManager/system-connections/Auto Grendelch]] (600 root)
[connection] id=Auto Grendelch | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grendelch

[[/etc/NetworkManager/system-connections/belkin.8d4]] (600 root)
[connection] id=belkin.8d4 | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4 | mac-address=00:13:CE:22:27:81
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX-guest]] (600 root)
[connection] id=Auto ScandalsPDX-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX-guest

[[/etc/NetworkManager/system-connections/ciita-guest]] (600 root)
[connection] id=ciita-guest | type=802-11-wireless
[802-11-wireless] ssid=ciita-guest | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX]] (600 root)
[connection] id=Auto ScandalsPDX | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX

[[/etc/NetworkManager/system-connections/Wireless connection 1]] (600 root)
[connection] id=Wireless connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto BV42_WiFi]] (600 root)
[connection] id=Auto BV42_WiFi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=BV42_WiFi

[[/etc/NetworkManager/system-connections/Auto LHS-PublicNet]] (600 root)
[connection] id=Auto LHS-PublicNet | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LHS-PublicNet

[[/etc/NetworkManager/system-connections/Auto Stephouse Wireless]] (600 root)
[connection] id=Auto Stephouse Wireless | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Stephouse Wireless

[[/etc/NetworkManager/system-connections/Auto attwifi]] (600 root)
[connection] id=Auto attwifi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=attwifi

[[/etc/NetworkManager/system-connections/Auto KindCedar-guest]] (600 root)
[connection] id=Auto KindCedar-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KindCedar-guest

[[/etc/NetworkManager/system-connections/Auto PSU Secure]] (600 root)
[connection] id=Auto PSU Secure | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU Secure

[[/etc/NetworkManager/system-connections/Auto PdaNet HotSpot]] (600 root)
[connection] id=Auto PdaNet HotSpot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PdaNet HotSpot

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=00:06:25:5B:03:CF | mac-address=00:13:CE:22:27:81
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto 2WIRE488]] (600 root)
[connection] id=Auto 2WIRE488 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=2WIRE488

[[/etc/NetworkManager/system-connections/Auto gogoinflight]] (600 root)
[connection] id=Auto gogoinflight | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=gogoinflight
```

---

### Post by olyvkina on 2014-10-19
And as for the commands to run in terminal that you provided, Hadaka, that didn't work : (

---

### Post by Hadaka on 2014-10-19
Hi, ok,let's try to clear some confusion. you need to be using 
a working internet connection for these commands. The commands
i gave you and the wireless script. the script is still a bit confusing.
to be more accurate on my part i should have saide please post the
 **wireless****-info.txt** file which should be in your home directory
please re-run and POST that and the output of
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b44
```
telling me 'that didnt work" doesnt give me any data to work with,
thanks.

---

### Post by olyvkina on 2014-10-19
Hi
I am using a working internet connection (wireless).
What I posted was the contents of my file wireless-info.txt which was in my home directory. Is that not what you needed me to do? If not, please explain.
I misunderstood what you needed me to do with regard to the terminal commands. Here are the outputs:

sudo apt-get remove --purge bcmwl-kernel-source produces:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1999 not upgraded.

```

sudo apt-get install b43-fwcutter firmware-b43-installer produces:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1999 not upgraded.

```

sudo modprobe b44 does not have an output. Is this supposed to produce some data?

---

### Post by jeremy31 on 2014-10-19
The modprobe will only have output if there is an error

Lets try option 2 for the wireless script, install pastebin ```
sudo apt-get install pastebinit
``` Then run the wireless script ```
./wireless_script
```  When the script asks if you want to upload to pastebin, choose Y and it should give you a URL in terminal that you can copy and paste into your next post.

Also feel free to try your wired connection to see if the modprobe command helped

---

### Post by Hadaka on 2014-10-19
Hi, it may be an issue with the info-text file, it looks like a combination
of the script and the text...odd. Please delete the wireless-info.txt file
in your home directory and run one more time please, sorry for all the
confusion. the output from the other commands are fine...thanks.

---

### Post by olyvkina on 2014-10-19
Okay.
sudo apt-get install pastebinit produces:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dh-python libc-dev-bin libc6 libc6-dev libdb5.3 libexpat1 liblzma5 libmpdec2
  libnih-dbus1 libnih1 libpython3-stdlib libpython3.4-minimal
  libpython3.4-stdlib python3 python3-minimal python3.4 python3.4-minimal
Suggested packages:
  glibc-doc python3-doc python3-tk python3.4-doc
The following NEW packages will be installed:
  dh-python libdb5.3 libmpdec2 libpython3-stdlib libpython3.4-minimal
  libpython3.4-stdlib pastebinit python3 python3-minimal python3.4
  python3.4-minimal
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dev libexpat1 liblzma5 libnih-dbus1 libnih1
7 upgraded, 11 newly installed, 0 to remove and 1992 not upgraded.
Need to get 4,693 kB/10.5 MB of archives.
After this operation, 8,627 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main libexpat1 i386 2.1.0-4ubuntu1 [71.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main libmpdec2 i386 2.4.0-6 [73.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpython3.4-minimal i386 3.4.0-2ubuntu1 [443 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty/main libdb5.3 i386 5.3.28-3ubuntu3 [651 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpython3.4-stdlib i386 3.4.0-2ubuntu1 [1,985 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3.4-minimal i386 3.4.0-2ubuntu1 [1,201 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3.4 i386 3.4.0-2ubuntu1 [163 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3-minimal i386 3.4.0-0ubuntu2 [23.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/main libpython3-stdlib i386 3.4.0-0ubuntu2 [6,928 B]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/main python3 i386 3.4.0-0ubuntu2 [8,676 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty/main dh-python all 1.20140128-1ubuntu8 [51.0 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 4,452 kB in 6min 24s (11.6 kB/s)                                       
Preconfiguring packages ...
(Reading database ... 313998 files and directories currently installed.)
Preparing to replace libnih-dbus1 1.0.3-4ubuntu9.1 (using .../libnih-dbus1_1.0.3-4ubuntu25_i386.deb) ...
Unpacking replacement libnih-dbus1 ...
Preparing to replace libnih1 1.0.3-4ubuntu9.1 (using .../libnih1_1.0.3-4ubuntu25_i386.deb) ...
Unpacking replacement libnih1 ...
Preparing to replace libc6-dev 2.15-0ubuntu10.7 (using .../libc6-dev_2.19-0ubuntu6.3_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-dev-bin 2.15-0ubuntu10.7 (using .../libc-dev-bin_2.19-0ubuntu6.3_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6 2.15-0ubuntu10.7 (using .../libc6_2.19-0ubuntu6.3_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.

Unpacking replacement libc6 ...
Processing triggers for man-db ...
Setting up libc6 (2.19-0ubuntu6.3) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Checking for services that may need to be restarted...
Checking init scripts...
Restarting services possibly affected by the upgrade:
  cron: restarting...done.
  atd: restarting...done.
  cups: restarting...done.

Services restarted successfully.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 313975 files and directories currently installed.)
Preparing to replace liblzma5 5.1.1alpha+20110809-3 (using .../liblzma5_5.1.1alpha+20120614-2ubuntu2_i386.deb) ...
Unpacking replacement liblzma5 ...
Setting up liblzma5 (5.1.1alpha+20120614-2ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 313975 files and directories currently installed.)
Preparing to replace libexpat1 2.0.1-7.2ubuntu1.1 (using .../libexpat1_2.1.0-4ubuntu1_i386.deb) ...
Unpacking replacement libexpat1 ...
Selecting previously unselected package libmpdec2.
Unpacking libmpdec2 (from .../libmpdec2_2.4.0-6_i386.deb) ...
Selecting previously unselected package libpython3.4-minimal.
Unpacking libpython3.4-minimal (from .../libpython3.4-minimal_3.4.0-2ubuntu1_i386.deb) ...
Selecting previously unselected package libdb5.3.
Unpacking libdb5.3 (from .../libdb5.3_5.3.28-3ubuntu3_i386.deb) ...
Selecting previously unselected package libpython3.4-stdlib.
Unpacking libpython3.4-stdlib (from .../libpython3.4-stdlib_3.4.0-2ubuntu1_i386.deb) ...
Selecting previously unselected package python3.4-minimal.
Unpacking python3.4-minimal (from .../python3.4-minimal_3.4.0-2ubuntu1_i386.deb) ...
Selecting previously unselected package python3.4.
Unpacking python3.4 (from .../python3.4_3.4.0-2ubuntu1_i386.deb) ...
Selecting previously unselected package python3-minimal.
Unpacking python3-minimal (from .../python3-minimal_3.4.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package libpython3-stdlib.
Unpacking libpython3-stdlib (from .../libpython3-stdlib_3.4.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package python3.
Unpacking python3 (from .../python3_3.4.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package dh-python.
Unpacking dh-python (from .../dh-python_1.20140128-1ubuntu8_all.deb) ...
Selecting previously unselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.4-3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libnih1 (1.0.3-4ubuntu25) ...
Setting up libnih-dbus1 (1.0.3-4ubuntu25) ...
Setting up libc-dev-bin (2.19-0ubuntu6.3) ...
Setting up libc6-dev (2.19-0ubuntu6.3) ...
Setting up libexpat1 (2.1.0-4ubuntu1) ...
Setting up libmpdec2 (2.4.0-6) ...
Setting up libpython3.4-minimal (3.4.0-2ubuntu1) ...
Setting up libdb5.3 (5.3.28-3ubuntu3) ...
Setting up libpython3.4-stdlib (3.4.0-2ubuntu1) ...
Setting up python3.4-minimal (3.4.0-2ubuntu1) ...
Setting up python3.4 (3.4.0-2ubuntu1) ...
Setting up python3-minimal (3.4.0-0ubuntu2) ...
Setting up libpython3-stdlib (3.4.0-0ubuntu2) ...
Setting up python3 (3.4.0-0ubuntu2) ...
running python rtupdate hooks for python3.4...
running python post-rtupdate hooks for python3.4...
Setting up dh-python (1.20140128-1ubuntu8) ...
Setting up pastebinit (1.4-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

when I try to run " ./wireless_script" the output is:
```

bash: ./wireless_script: Permission denied

```

I hope I've produced everything for you correctly.

---

### Post by jeremy31 on 2014-10-19
Hadaka must be correct, need to delete the current wireless_script and download new
```
rm wireless_script
```
```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```[/FONT][/COLOR]

---

### Post by olyvkina on 2014-10-19
Hi Hadaka-
I deleted the wireless-info.txt file and ran the script again. Here are the contents of the new wireless-info.txt file:

```

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n########## wireless info START ##########\n\n"

########## wireless info START ##########

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z"  )
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\  +\(.\+\) - .*$/\1/p')
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Report from: %s\n\n" "$REPORTDATE"
Report from: 19 Oct 2014 15:01 PDT -0700

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Booted last: %s\n\n" "$LASTBOOTDT"
Booted last: 19 Oct 2014 11:59 PDT -0700

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "Script from: %s\n" "$SCRIPTDATE"
Script from: 20 Sep 2014 23:04 UTC +0000
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### release ###########################\n\n"

##### release ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lsb_release -idrc
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### kernel ############################\n\n"

##### kernel ############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ uname -srvmpio
Linux 3.2.0-69-generic-pae #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014 i686 i686 i386 GNU/Linux
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ echo

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Paramete  rs:/' /proc/cmdline
Parameters: ro, initrd=ubuntu-installer/lucid-i386/initrd.gz, splash, quiet, vt.handoff=7
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### desktop ###########################\n\n"

##### desktop ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$DESKTOP_SESSION" ]; then
>     DESKTOP="$DESKTOP_SESSION"
> else
>     DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
>     DESKDMRC=" (from ~/.dmrc)"
> fi
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$DESKTOP" ]; then
>     if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
> DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.deskto  p")
>     fi
>     echo "${DESKTOP/ Session/}${DESKDMRC}"
> else
>     echo "Could not be determined."
> fi
Ubuntu 2D
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lspci #############################\n\n"

##### lspci #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d;/  ^[^[:space:]]/ i\\'

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lsusb #############################\n\n"

##### lsusb #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### PCMCIA card info ##################\n\n"

##### PCMCIA card info ##################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -x /sbin/pccardctl ]; then
>     pccardctl info
> else
>     echo "'pccardctl' is not installed (package \"pcmciautils\")."
> fi
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### rfkill ############################\n\n"

##### rfkill ############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### lsmod #############################\n\n"

##### lsmod #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMAT  CHES)[^[:punct:] ]*([[:punct:] ]|$)")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ echo "$LSMOD"
ipw2200               146241  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
lib80211               14040  3 lib80211_crypt_ccmp,ipw2200,libipw
ssb                    50691  1 b44
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### interfaces ########################\n\n"

##### interfaces ########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>  /' /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### ifconfig ##########################\n\n"

##### ifconfig ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ ifconfig -a | sed '/^lo /,/^$/d'
eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.43.240  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe22:2781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21204 errors:1 dropped:1 overruns:0 frame:0
          TX packets:24456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13172975 (13.1 MB)  TX bytes:3295224 (3.2 MB)
          Interrupt:5 Base address:0xe000 Memory:faffd000-faffdfff 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### iwconfig ##########################\n\n"

##### iwconfig ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:"ANDI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ANDI' [AN2]>   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-30 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### route #############################\n\n"

##### route #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.43.1    0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.43.0    0.0.0.0         255.255.255.0   U     2      0        0 eth0
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### resolv.conf #######################\n\n"

##### resolv.conf #######################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/resolv.conf
nameserver 192.168.43.1
nameserver 127.0.0.1
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### nm-tool ###########################\n\n"

##### nm-tool ###########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [ANDI] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TR:              Infra, <MAC 'TR' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WEP
    *ANDI:           Infra, <MAC 'ANDI' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 96 WPA2
    JC:              Infra, <MAC 'JC' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    belkin.8d4:      Infra, <MAC 'belkin.8d4' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    JAM:             Infra, <MAC 'JAM' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    HUAWEI-E5220-401b: Infra, <MAC 'HUAWEI-E5220-401b' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    OH:              Infra, <MAC 'OH' [AN7]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WEP
    belkin.8d4.guests: Infra, <MAC 'belkin.8d4.guests' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    DR:              Infra, <MAC 'DR' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP

  IPv4 Settings:
    Address:         192.168.43.240
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager.state ##############\n\n"

##### NetworkManager.state ##############

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ cat -s /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager.conf ###############\n\n"

##### NetworkManager.conf ###############

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth1' [IF]>,

[ifupdown]
managed=true
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
>     printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
>     grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
> fi
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### NetworkManager profiles ###########\n\n"

##### NetworkManager profiles ###########

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$SUDO" ]; then
>     trap "" 2 3
>     NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type   f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOC  MT" --} grep -vH '^$' {} + 2> /dev/null) && SUDOSUCCESS="yes" || SUDOSUCCESS="no  "
>     trap 2 3
>     if [ "$SUDOSUCCESS" = "yes" ]; then
> ORIGIFS="$IFS"
> IFS=$'\n'
> for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=802-11-wireless.*$/\1/p' <<< "$NM  PROFILES"); do
>     NMWLPRFFLPERMS=$(stat -c "%a %U" $NMWLPRFFILE)
>     NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "  $NMPROFILES"))
>     NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"  $'\n\n'
> done
> IFS="$ORIGIFS"
> sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\  ]$/d'
>     else
> echo "Acquisition of admin privileges failed."
>     fi
> else
>     echo "No way to acquire admin privileges found."
> fi
[[/etc/NetworkManager/system-connections/Auto myspot]] (600 root)
[connection] id=Auto myspot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=myspot

[[/etc/NetworkManager/system-connections/Auto Brown Home]] (600 root)
[connection] id=Auto Brown Home | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Brown Home

[[/etc/NetworkManager/system-connections/OUI PRESSE]] (600 root)
[connection] id=OUI PRESSE | type=802-11-wireless
[802-11-wireless] ssid=OUI PRESSE | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto PSU]] (600 root)
[connection] id=Auto PSU | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU

[[/etc/NetworkManager/system-connections/SC]] (600 root)
[connection] id=SC | type=802-11-wireless
[802-11-wireless] ssid=SC | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto NETGEAR64]] (600 root)
[connection] id=Auto NETGEAR64 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR64

[[/etc/NetworkManager/system-connections/Auto Bolt Bus]] (600 root)
[connection] id=Auto Bolt Bus | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Bolt Bus

[[/etc/NetworkManager/system-connections/Auto JC226]] (600 root)
[connection] id=Auto JC226 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=JC226

[[/etc/NetworkManager/system-connections/lookoutmountain404]] (600 root)
[connection] id=lookoutmountain404 | type=802-11-wireless
[802-11-wireless] ssid=lookoutmountain404 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto McCoy South]] (600 root)
[connection] id=Auto McCoy South | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=McCoy South

[[/etc/NetworkManager/system-connections/belkin.8d4.guests]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LC Secure]] (600 root)
[ipv6] method=auto
[connection] id=LC Secure | type=802-11-wireless
[802-11-wireless] ssid=LC Secure | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-B40AE]] (600 root)
[connection] id=Auto MOTOROLA-B40AE | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=MOTOROLA-B40AE

[[/etc/NetworkManager/system-connections/Auto Grapes]] (600 root)
[connection] id=Auto Grapes | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grapes

[[/etc/NetworkManager/system-connections/Auto Denninwayne]] (600 root)
[connection] id=Auto Denninwayne | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Denninwayne

[[/etc/NetworkManager/system-connections/Frontier4579]] (600 root)
[connection] id=Frontier4579 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto www.personaltelco.net]] (600 root)
[connection] id=Auto www.personaltelco.net | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=www.personaltelco.net

[[/etc/NetworkManager/system-connections/MOTOROLA-2BAFB]] (600 root)
[connection] id=MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin.8d4.guests-b26ef860-2b58-46c3-8a57-658152b431cd]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto Doug Fir]] (600 root)
[connection] id=Auto Doug Fir | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Doug Fir

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-2BAFB]] (600 root)
[connection] id=Auto MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Boltbus_]] (600 root)
[connection] id=Auto Boltbus_ | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Boltbus_

[[/etc/NetworkManager/system-connections/Auto NETGEAR91]] (600 root)
[connection] id=Auto NETGEAR91 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR91

[[/etc/NetworkManager/system-connections/Auto CenturyLink5269]] (600 root)
[connection] id=Auto CenturyLink5269 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=CenturyLink5269
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Jupiterhotel]] (600 root)
[connection] id=Auto Jupiterhotel | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Jupiterhotel

[[/etc/NetworkManager/system-connections/Auto Library]] (600 root)
[connection] id=Auto Library | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Library

[[/etc/NetworkManager/system-connections/Auto Apple Network fa1dd8]] (600 root)
[connection] id=Auto Apple Network fa1dd8 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Apple Network fa1dd8

[[/etc/NetworkManager/system-connections/Auto new_azu_guest]] (600 root)
[connection] id=Auto new_azu_guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=new_azu_guest

[[/etc/NetworkManager/system-connections/Auto KIBO]] (600 root)
[connection] id=Auto KIBO | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KIBO

[[/etc/NetworkManager/system-connections/belkin.798.guests]] (600 root)
[connection] id=belkin.798.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.798.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto qwest4352]] (600 root)
[connection] id=Auto qwest4352 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=qwest4352

[[/etc/NetworkManager/system-connections/Auto 102]] (600 root)
[connection] id=Auto 102 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=102

[[/etc/NetworkManager/system-connections/Auto LaughingPlanetBelmont]] (600 root)
[connection] id=Auto LaughingPlanetBelmont | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LaughingPlanetBelmont

[[/etc/NetworkManager/system-connections/Auto ACTIONTEC]] (600 root)
[connection] id=Auto ACTIONTEC | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ACTIONTEC

[[/etc/NetworkManager/system-connections/ANDI]] (600 root)
[connection] id=ANDI | type=802-11-wireless
[802-11-wireless] ssid=ANDI | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto hpsetup]] (600 root)
[connection] id=Auto hpsetup | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=hpsetup

[[/etc/NetworkManager/system-connections/Auto SCS]] (600 root)
[connection] id=Auto SCS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=SCS

[[/etc/NetworkManager/system-connections/Auto PEETS]] (600 root)
[connection] id=Auto PEETS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PEETS

[[/etc/NetworkManager/system-connections/Auto Grendelch]] (600 root)
[connection] id=Auto Grendelch | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grendelch

[[/etc/NetworkManager/system-connections/belkin.8d4]] (600 root)
[connection] id=belkin.8d4 | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX-guest]] (600 root)
[connection] id=Auto ScandalsPDX-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX-guest

[[/etc/NetworkManager/system-connections/ciita-guest]] (600 root)
[connection] id=ciita-guest | type=802-11-wireless
[802-11-wireless] ssid=ciita-guest | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX]] (600 root)
[connection] id=Auto ScandalsPDX | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX

[[/etc/NetworkManager/system-connections/Wireless connection 1]] (600 root)
[connection] id=Wireless connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto BV42_WiFi]] (600 root)
[connection] id=Auto BV42_WiFi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=BV42_WiFi

[[/etc/NetworkManager/system-connections/Auto LHS-PublicNet]] (600 root)
[connection] id=Auto LHS-PublicNet | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LHS-PublicNet

[[/etc/NetworkManager/system-connections/Auto Stephouse Wireless]] (600 root)
[connection] id=Auto Stephouse Wireless | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Stephouse Wireless

[[/etc/NetworkManager/system-connections/Auto attwifi]] (600 root)
[connection] id=Auto attwifi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=attwifi

[[/etc/NetworkManager/system-connections/Auto KindCedar-guest]] (600 root)
[connection] id=Auto KindCedar-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KindCedar-guest

[[/etc/NetworkManager/system-connections/Auto PSU Secure]] (600 root)
[connection] id=Auto PSU Secure | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU Secure

[[/etc/NetworkManager/system-connections/Auto PdaNet HotSpot]] (600 root)
[connection] id=Auto PdaNet HotSpot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PdaNet HotSpot

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto 2WIRE488]] (600 root)
[connection] id=Auto 2WIRE488 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=2WIRE488

[[/etc/NetworkManager/system-connections/Auto gogoinflight]] (600 root)
[connection] id=Auto gogoinflight | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=gogoinflight

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### iw reg get ########################\n\n"

##### iw reg get ########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -x /sbin/iw ]; then
>     if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
> REGION=$(cat /etc/timezone)
> printf "Region: %s (based on set time zone)\n\n" "$REGION"
>     fi
>     echo "$IWREGGET"
> else
>     echo "'iw' is not installed (package \"iw\")."
> fi
Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### iwlist channels ###################\n\n"

##### iwlist channels ###################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ iwlist chan
lo        no frequency information.

eth1      no frequency information.

eth0      11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### iwlist scan #######################\n\n"

##### iwlist scan #######################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ if [ -n "$SUDO" ]; then
>     trap "" 2 3
>     IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan 2>&1) && SUDOSUCCESS="yes" ||   SUDOSUCCESS="no"
>     trap 2 3
>     if [ "$SUDOSUCCESS" = "yes" ]; then
> if [[ $IWLISTSCAN = *Frequency:* ]]; then
>     printf "Channel occupancy:\n\n"
>     grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\  ([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
>     echo
> fi
> egrep -v '^[ ]*IE: Unknown:|ibus-daemon' <<< "$IWLISTSCAN"
>     else
> echo "Acquisition of admin privileges failed."
>     fi
> else
>     echo "No way to acquire admin privileges found."
> fi
Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: <MAC 'ANDI' [AN2]>
                    ESSID:"\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-31 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 36ms ago
          Cell 02 - Address: <MAC 'TR' [AN1]>
                    ESSID:"TR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    Extra: Last beacon: 84ms ago
          Cell 03 - Address: <MAC 'JC' [AN3]>
                    ESSID:"JC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 4ms ago
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### module infos ######################\n\n"

##### module infos ######################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ for MODULE in $MODULES; do
>     MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
>     printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
> done
[ipw2200]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     24E9BF82FCFA16D4C5D111B
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### module parameters #################\n\n"

##### module parameters #################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ for MODULE in $MODULES; do
>     if [ -d /sys/module/$MODULE/parameters ]; then
> MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^  .*/##;s/:/: /')
> printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
>     fi
> done
[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### /etc/modules ######################\n\n"

##### /etc/modules ######################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/modules

loop
lp
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### modprobe options ##################\n\n"

##### modprobe options ##################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.co  nf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort);   do
>     MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
>     if [ -n "$MODPROBEOPTS" ]; then
> printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
>     fi
> done
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### rc.local ##########################\n\n"

##### rc.local ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ grep -v '^#' /etc/rc.local

exit 0
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### pm-utils ##########################\n\n"

##### pm-utils ##########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \  ) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
>     PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
>     if [ -n "$PMUTFLCONT" ]; then
> PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
> printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
>     fi
> done
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### udev rules ########################\n\n"

##### udev rules ########################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
>     UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
>     if [ -n "$UDEVRULES" ]; then
> printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
>     fi
> done
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n##### dmesg #############################\n\n"

##### dmesg #############################

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$DMESGM  ATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's  /^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'
[   29.986540] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   29.986546] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.021386] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   30.021419] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.358222] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  342.395748] ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ printf "\n########## wireless info END ############\n\n"

########## wireless info END ############

]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ 
]0;laptop@dhcp-170: ~laptop@dhcp-170:~$ exec 2>&4 4>&-

```

Does this look right?

---

### Post by olyvkina on 2014-10-19
Haha, looks like our communications are overlapping-

Just to acknowledge you, jeremy31, I actually just moved the old file to trash (before I saw your removal terminal command) -I gather that action is sufficient?

---

### Post by jeremy31 on 2014-10-19
That wasn't pretty but I think this from /etc/network/interfaces is relevant to the problem
```
[COLOR=#000000][FONT=Ubuntu Mono]auto lo [/FONT][/COLOR]iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

It seems that your wifi is reported as eth0 instead of wlan0

If it was my pc I would edit the file to comment out the auto eth0 and iface eth0 inet dhcp lines or change eth0 to eth1

But I am not familiar with 12.04

---

### Post by olyvkina on 2014-10-19
hmm. Hadaka, your thoughts?

---

### Post by Hadaka on 2014-10-19
ok, lets try this one more time. all you need to do is..
open a terminal and do..
```
sudo rm wireless-info.txt
```
Then:
COPY AND PASTE into a terminal..
```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]
```
CTRL/ALT/T.....copy and paste the above
then.post the **wireless-info.txt **file.
I think you have been going about getting the script a different way...please do it this way.
thanks.

@jermy.lets see if we can get some clean data befoer tossing any more commands.

---

### Post by jeremy31 on 2014-10-19
Hadaka, in case the new report isn't any better, here is the old report minus the noise
```
########## wireless info START ##########



Report from: 19 Oct 2014 15:01 PDT -0700




Booted last: 19 Oct 2014 11:59 PDT -0700




Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################




Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################




Linux 3.2.0-69-generic-pae #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014 i686 i686 i386 GNU/Linux


Parameters: ro, initrd=ubuntu-installer/lucid-i386/initrd.gz, splash, quiet, vt.handoff=7


##### desktop ###########################




Ubuntu 2D


##### lspci #############################



02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44


02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200


##### lsusb #############################




Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################




PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################




0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################




ipw2200               146241  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
lib80211               14040  3 lib80211_crypt_ccmp,ipw2200,libipw
ssb                    50691  1 b44




##### interfaces ########################






auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


##### ifconfig ##########################




eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.43.240  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe22:2781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21204 errors:1 dropped:1 overruns:0 frame:0
          TX packets:24456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13172975 (13.1 MB)  TX bytes:3295224 (3.2 MB)
          Interrupt:5 Base address:0xe000 Memory:faffd000-faffdfff 


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 




##### iwconfig ##########################




lo        no wireless extensions.


eth1      no wireless extensions.


eth0      IEEE 802.11bg  ESSID:"ANDI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ANDI' [AN2]>   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-30 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




##### route #############################




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.43.1    0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.43.0    0.0.0.0         255.255.255.0   U     2      0        0 eth0


##### resolv.conf #######################




nameserver 192.168.43.1
nameserver 127.0.0.1




##### nm-tool ###########################






NetworkManager Tool


State: connected (global)


- Device: eth0  [ANDI] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TR:              Infra, <MAC 'TR' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WEP
    *ANDI:           Infra, <MAC 'ANDI' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 96 WPA2
    JC:              Infra, <MAC 'JC' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    belkin.8d4:      Infra, <MAC 'belkin.8d4' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    JAM:             Infra, <MAC 'JAM' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    HUAWEI-E5220-401b: Infra, <MAC 'HUAWEI-E5220-401b' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    OH:              Infra, <MAC 'OH' [AN7]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WEP
    belkin.8d4.guests: Infra, <MAC 'belkin.8d4.guests' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    DR:              Infra, <MAC 'DR' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP


  IPv4 Settings:
    Address:         192.168.43.240
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1


    DNS:             192.168.43.1


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




##### NetworkManager.state ##############






[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############




plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC 'eth1' [IF]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########




[[/etc/NetworkManager/system-connections/Auto myspot]] (600 root)
[connection] id=Auto myspot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=myspot


[[/etc/NetworkManager/system-connections/Auto Brown Home]] (600 root)
[connection] id=Auto Brown Home | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Brown Home


[[/etc/NetworkManager/system-connections/OUI PRESSE]] (600 root)
[connection] id=OUI PRESSE | type=802-11-wireless
[802-11-wireless] ssid=OUI PRESSE | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto PSU]] (600 root)
[connection] id=Auto PSU | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU


[[/etc/NetworkManager/system-connections/SC]] (600 root)
[connection] id=SC | type=802-11-wireless
[802-11-wireless] ssid=SC | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto NETGEAR64]] (600 root)
[connection] id=Auto NETGEAR64 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR64


[[/etc/NetworkManager/system-connections/Auto Bolt Bus]] (600 root)
[connection] id=Auto Bolt Bus | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Bolt Bus


[[/etc/NetworkManager/system-connections/Auto JC226]] (600 root)
[connection] id=Auto JC226 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=JC226


[[/etc/NetworkManager/system-connections/lookoutmountain404]] (600 root)
[connection] id=lookoutmountain404 | type=802-11-wireless
[802-11-wireless] ssid=lookoutmountain404 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto McCoy South]] (600 root)
[connection] id=Auto McCoy South | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=McCoy South


[[/etc/NetworkManager/system-connections/belkin.8d4.guests]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/LC Secure]] (600 root)
[ipv6] method=auto
[connection] id=LC Secure | type=802-11-wireless
[802-11-wireless] ssid=LC Secure | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto MOTOROLA-B40AE]] (600 root)
[connection] id=Auto MOTOROLA-B40AE | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=MOTOROLA-B40AE


[[/etc/NetworkManager/system-connections/Auto Grapes]] (600 root)
[connection] id=Auto Grapes | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grapes


[[/etc/NetworkManager/system-connections/Auto Denninwayne]] (600 root)
[connection] id=Auto Denninwayne | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Denninwayne


[[/etc/NetworkManager/system-connections/Frontier4579]] (600 root)
[connection] id=Frontier4579 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto www.personaltelco.net]] (600 root)
[connection] id=Auto www.personaltelco.net | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=www.personaltelco.net


[[/etc/NetworkManager/system-connections/MOTOROLA-2BAFB]] (600 root)
[connection] id=MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/belkin.8d4.guests-b26ef860-2b58-46c3-8a57-658152b431cd]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto Doug Fir]] (600 root)
[connection] id=Auto Doug Fir | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Doug Fir


[[/etc/NetworkManager/system-connections/Auto MOTOROLA-2BAFB]] (600 root)
[connection] id=Auto MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Auto Boltbus_]] (600 root)
[connection] id=Auto Boltbus_ | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Boltbus_


[[/etc/NetworkManager/system-connections/Auto NETGEAR91]] (600 root)
[connection] id=Auto NETGEAR91 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR91


[[/etc/NetworkManager/system-connections/Auto CenturyLink5269]] (600 root)
[connection] id=Auto CenturyLink5269 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=CenturyLink5269
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Auto Jupiterhotel]] (600 root)
[connection] id=Auto Jupiterhotel | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Jupiterhotel


[[/etc/NetworkManager/system-connections/Auto Library]] (600 root)
[connection] id=Auto Library | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Library


[[/etc/NetworkManager/system-connections/Auto Apple Network fa1dd8]] (600 root)
[connection] id=Auto Apple Network fa1dd8 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Apple Network fa1dd8


[[/etc/NetworkManager/system-connections/Auto new_azu_guest]] (600 root)
[connection] id=Auto new_azu_guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=new_azu_guest


[[/etc/NetworkManager/system-connections/Auto KIBO]] (600 root)
[connection] id=Auto KIBO | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KIBO


[[/etc/NetworkManager/system-connections/belkin.798.guests]] (600 root)
[connection] id=belkin.798.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.798.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto qwest4352]] (600 root)
[connection] id=Auto qwest4352 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=qwest4352


[[/etc/NetworkManager/system-connections/Auto 102]] (600 root)
[connection] id=Auto 102 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=102


[[/etc/NetworkManager/system-connections/Auto LaughingPlanetBelmont]] (600 root)
[connection] id=Auto LaughingPlanetBelmont | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LaughingPlanetBelmont


[[/etc/NetworkManager/system-connections/Auto ACTIONTEC]] (600 root)
[connection] id=Auto ACTIONTEC | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ACTIONTEC


[[/etc/NetworkManager/system-connections/ANDI]] (600 root)
[connection] id=ANDI | type=802-11-wireless
[802-11-wireless] ssid=ANDI | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto hpsetup]] (600 root)
[connection] id=Auto hpsetup | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=hpsetup


[[/etc/NetworkManager/system-connections/Auto SCS]] (600 root)
[connection] id=Auto SCS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=SCS


[[/etc/NetworkManager/system-connections/Auto PEETS]] (600 root)
[connection] id=Auto PEETS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PEETS


[[/etc/NetworkManager/system-connections/Auto Grendelch]] (600 root)
[connection] id=Auto Grendelch | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grendelch


[[/etc/NetworkManager/system-connections/belkin.8d4]] (600 root)
[connection] id=belkin.8d4 | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto ScandalsPDX-guest]] (600 root)
[connection] id=Auto ScandalsPDX-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX-guest


[[/etc/NetworkManager/system-connections/ciita-guest]] (600 root)
[connection] id=ciita-guest | type=802-11-wireless
[802-11-wireless] ssid=ciita-guest | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto ScandalsPDX]] (600 root)
[connection] id=Auto ScandalsPDX | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX


[[/etc/NetworkManager/system-connections/Wireless connection 1]] (600 root)
[connection] id=Wireless connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Auto BV42_WiFi]] (600 root)
[connection] id=Auto BV42_WiFi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=BV42_WiFi


[[/etc/NetworkManager/system-connections/Auto LHS-PublicNet]] (600 root)
[connection] id=Auto LHS-PublicNet | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LHS-PublicNet


[[/etc/NetworkManager/system-connections/Auto Stephouse Wireless]] (600 root)
[connection] id=Auto Stephouse Wireless | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Stephouse Wireless


[[/etc/NetworkManager/system-connections/Auto attwifi]] (600 root)
[connection] id=Auto attwifi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=attwifi


[[/etc/NetworkManager/system-connections/Auto KindCedar-guest]] (600 root)
[connection] id=Auto KindCedar-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KindCedar-guest


[[/etc/NetworkManager/system-connections/Auto PSU Secure]] (600 root)
[connection] id=Auto PSU Secure | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU Secure


[[/etc/NetworkManager/system-connections/Auto PdaNet HotSpot]] (600 root)
[connection] id=Auto PdaNet HotSpot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PdaNet HotSpot


[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto 2WIRE488]] (600 root)
[connection] id=Auto 2WIRE488 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=2WIRE488


[[/etc/NetworkManager/system-connections/Auto gogoinflight]] (600 root)
[connection] id=Auto gogoinflight | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=gogoinflight




##### iw reg get ########################




Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################




lo        no frequency information.


eth1      no frequency information.


eth0      11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)




##### iwlist scan #######################




Channel occupancy:


      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


lo        Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


eth0      Scan completed :
          Cell 01 - Address: <MAC 'ANDI' [AN2]>
                    ESSID:"\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-31 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 36ms ago
          Cell 02 - Address: <MAC 'TR' [AN1]>
                    ESSID:"TR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    Extra: Last beacon: 84ms ago
          Cell 03 - Address: <MAC 'JC' [AN3]>
                    ESSID:"JC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 4ms ago




##### module infos ######################




[ipw2200]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     24E9BF82FCFA16D4C5D111B
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)


[cfg80211]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 






##### module parameters #################




[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00




##### /etc/modules ######################






loop
lp




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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }




##### rc.local ##########################






exit 0




##### pm-utils ##########################




##### udev rules ########################




[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"






##### dmesg #############################




[   29.986540] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   29.986546] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.021386] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   30.021419] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.358222] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  342.395748] ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)




########## wireless info END ############

```

---

### Post by olyvkina on 2014-10-19
Okay.

I don't know if this effects things, but when I have previously input
```
[COLOR=#000000][FONT=Ubuntu Mono]
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]

```

this would happen:
```

--2014-10-19 15:54:55--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 23.23.254.171
Connecting to dl.dropbox.com (dl.dropbox.com)|23.23.254.171|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-10-19 15:54:58--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.21.216.250, 23.21.210.59, 184.73.224.5, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.216.250|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Location: https://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-10-19 15:55:06--  https://dl.dropboxusercontent.com/u/57264241/wireless_script
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.21.216.250|:443... connected.
ERROR: cannot verify dl.dropboxusercontent.com's certificate, issued by `/C=US/O=DigiCert Inc/OU=www.digicert.com/CN=DigiCert SHA2 High Assurance Server CA':
  Unable to locally verify the issuer's authority.
To connect to dl.dropboxusercontent.com insecurely, use `--no-check-certificate'.

```

so, I would then input this:
```

wget --no-check-certificate[COLOR=#000000][FONT=Ubuntu Mono] -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script[/FONT][/COLOR]

```

which now gives me this:
```

--2014-10-19 16:00:09--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 54.243.112.85
Connecting to dl.dropbox.com (dl.dropbox.com)|54.243.112.85|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-10-19 16:00:13--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.243.71.18, 107.22.170.202, 23.23.138.4, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.243.71.18|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dl.dropboxusercontent.com
Location: https://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-10-19 16:00:14--  https://dl.dropboxusercontent.com/u/57264241/wireless_script
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.243.71.18|:443... connected.
WARNING: cannot verify dl.dropboxusercontent.com's certificate, issued by `/C=US/O=DigiCert Inc/OU=www.digicert.com/CN=DigiCert SHA2 High Assurance Server CA':
  Unable to locally verify the issuer's authority.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-10-19 16:00:17--  https://dl.dropboxusercontent.com/u/57264241/wireless_script
Reusing existing connection to dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 13,362      --.-K/s   in 0s      

2014-10-19 16:00:20 (112 MB/s) - `wireless_script' saved [13362/13362]


Results saved in "/home/laptop/wireless-info.txt".

Results also archived in "/home/laptop/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to pastebin them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

http://paste.ubuntu.com/8594609/

```


Okay, so this is wierd: I've just opened the wireless-info.txt file and there is an orange-colored region with the text: "There was a problem opening the file /home/laptop/wireless-info.txt. The file you opened has some invalid characters. If you continue editing this file you could corrupt this document.
You can also choose another character encoding and try again." It then has the following options: 'Retry' 'Edit Anyway' and 'Cancel'

Then the contents of the file follow:
```

########## wireless info START ##########

Report from: 19 Oct 2014 16:00 PDT -0700

Booted last: 19 Oct 2014 11:59 PDT -0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-69-generic-pae #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014 i686 i686 i386 GNU/Linux

Parameters: ro, initrd=ubuntu-installer/lucid-i386/initrd.gz, splash, quiet, vt.handoff=7

##### desktop ###########################

Ubuntu 2D

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ipw2200               146241  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
lib80211               14040  3 lib80211_crypt_ccmp,ipw2200,libipw
ssb                    50691  1 b44

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.43.240  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe22:2781/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26906 errors:1 dropped:1 overruns:0 frame:0
          TX packets:31161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16068868 (16.0 MB)  TX bytes:4589458 (4.5 MB)
          Interrupt:5 Base address:0xe000 Memory:faffd000-faffdfff 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

##### iwconfig ##########################

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:"ANDI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC '\00\00\00\00' [AC1]>   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-21 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.43.1    0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.43.0    0.0.0.0         255.255.255.0   U     2      0        0 eth0

##### resolv.conf #######################

nameserver 192.168.43.1
nameserver 127.0.0.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [ANDI] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TR:              Infra, <MAC 'TR' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WEP
    *ANDI:           Infra, <MAC '\00\00\00\00' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA2
    JC:              Infra, <MAC 'JC' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    JAM:             Infra, <MAC 'JAM' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    belkin.8d4:      Infra, <MAC 'belkin.8d4' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    belkin.8d4.guests: Infra, <MAC 'belkin.8d4.guests' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42

  IPv4 Settings:
    Address:         192.168.43.240
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1

    DNS:             192.168.43.1

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth1' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto myspot]] (600 root)
[connection] id=Auto myspot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=myspot

[[/etc/NetworkManager/system-connections/Auto Brown Home]] (600 root)
[connection] id=Auto Brown Home | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Brown Home

[[/etc/NetworkManager/system-connections/OUI PRESSE]] (600 root)
[connection] id=OUI PRESSE | type=802-11-wireless
[802-11-wireless] ssid=OUI PRESSE | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto PSU]] (600 root)
[connection] id=Auto PSU | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU

[[/etc/NetworkManager/system-connections/SC]] (600 root)
[connection] id=SC | type=802-11-wireless
[802-11-wireless] ssid=SC | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto NETGEAR64]] (600 root)
[connection] id=Auto NETGEAR64 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR64

[[/etc/NetworkManager/system-connections/Auto Bolt Bus]] (600 root)
[connection] id=Auto Bolt Bus | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Bolt Bus

[[/etc/NetworkManager/system-connections/Auto JC226]] (600 root)
[connection] id=Auto JC226 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=JC226

[[/etc/NetworkManager/system-connections/lookoutmountain404]] (600 root)
[connection] id=lookoutmountain404 | type=802-11-wireless
[802-11-wireless] ssid=lookoutmountain404 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto McCoy South]] (600 root)
[connection] id=Auto McCoy South | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=McCoy South

[[/etc/NetworkManager/system-connections/belkin.8d4.guests]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LC Secure]] (600 root)
[ipv6] method=auto
[connection] id=LC Secure | type=802-11-wireless
[802-11-wireless] ssid=LC Secure | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-B40AE]] (600 root)
[connection] id=Auto MOTOROLA-B40AE | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=MOTOROLA-B40AE

[[/etc/NetworkManager/system-connections/Auto Grapes]] (600 root)
[connection] id=Auto Grapes | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grapes

[[/etc/NetworkManager/system-connections/Auto Denninwayne]] (600 root)
[connection] id=Auto Denninwayne | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Denninwayne

[[/etc/NetworkManager/system-connections/Frontier4579]] (600 root)
[connection] id=Frontier4579 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto www.personaltelco.net]] (600 root)
[connection] id=Auto www.personaltelco.net | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=www.personaltelco.net

[[/etc/NetworkManager/system-connections/MOTOROLA-2BAFB]] (600 root)
[connection] id=MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin.8d4.guests-b26ef860-2b58-46c3-8a57-658152b431cd]] (600 root)
[connection] id=belkin.8d4.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto Doug Fir]] (600 root)
[connection] id=Auto Doug Fir | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Doug Fir

[[/etc/NetworkManager/system-connections/Auto MOTOROLA-2BAFB]] (600 root)
[connection] id=Auto MOTOROLA-2BAFB | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-2BAFB
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Boltbus_]] (600 root)
[connection] id=Auto Boltbus_ | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Boltbus_

[[/etc/NetworkManager/system-connections/Auto NETGEAR91]] (600 root)
[connection] id=Auto NETGEAR91 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=NETGEAR91

[[/etc/NetworkManager/system-connections/Auto CenturyLink5269]] (600 root)
[connection] id=Auto CenturyLink5269 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=CenturyLink5269
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Auto Jupiterhotel]] (600 root)
[connection] id=Auto Jupiterhotel | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Jupiterhotel

[[/etc/NetworkManager/system-connections/Auto Library]] (600 root)
[connection] id=Auto Library | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Library

[[/etc/NetworkManager/system-connections/Auto Apple Network fa1dd8]] (600 root)
[connection] id=Auto Apple Network fa1dd8 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Apple Network fa1dd8

[[/etc/NetworkManager/system-connections/Auto new_azu_guest]] (600 root)
[connection] id=Auto new_azu_guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=new_azu_guest

[[/etc/NetworkManager/system-connections/Auto KIBO]] (600 root)
[connection] id=Auto KIBO | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KIBO

[[/etc/NetworkManager/system-connections/belkin.798.guests]] (600 root)
[connection] id=belkin.798.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.798.guests | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto qwest4352]] (600 root)
[connection] id=Auto qwest4352 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=qwest4352

[[/etc/NetworkManager/system-connections/Auto 102]] (600 root)
[connection] id=Auto 102 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=102

[[/etc/NetworkManager/system-connections/Auto LaughingPlanetBelmont]] (600 root)
[connection] id=Auto LaughingPlanetBelmont | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LaughingPlanetBelmont

[[/etc/NetworkManager/system-connections/Auto ACTIONTEC]] (600 root)
[connection] id=Auto ACTIONTEC | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ACTIONTEC

[[/etc/NetworkManager/system-connections/ANDI]] (600 root)
[connection] id=ANDI | type=802-11-wireless
[802-11-wireless] ssid=ANDI | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto hpsetup]] (600 root)
[connection] id=Auto hpsetup | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=hpsetup

[[/etc/NetworkManager/system-connections/Auto SCS]] (600 root)
[connection] id=Auto SCS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=SCS

[[/etc/NetworkManager/system-connections/Auto PEETS]] (600 root)
[connection] id=Auto PEETS | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PEETS

[[/etc/NetworkManager/system-connections/Auto Grendelch]] (600 root)
[connection] id=Auto Grendelch | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Grendelch

[[/etc/NetworkManager/system-connections/belkin.8d4]] (600 root)
[connection] id=belkin.8d4 | type=802-11-wireless
[802-11-wireless] ssid=belkin.8d4 | mac-address=<MAC 'eth0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX-guest]] (600 root)
[connection] id=Auto ScandalsPDX-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX-guest

[[/etc/NetworkManager/system-connections/ciita-guest]] (600 root)
[connection] id=ciita-guest | type=802-11-wireless
[802-11-wireless] ssid=ciita-guest | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto ScandalsPDX]] (600 root)
[connection] id=Auto ScandalsPDX | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=ScandalsPDX

[[/etc/NetworkManager/system-connections/Wireless connection 1]] (600 root)
[connection] id=Wireless connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Frontier4579
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto BV42_WiFi]] (600 root)
[connection] id=Auto BV42_WiFi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=BV42_WiFi

[[/etc/NetworkManager/system-connections/Auto LHS-PublicNet]] (600 root)
[connection] id=Auto LHS-PublicNet | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=LHS-PublicNet

[[/etc/NetworkManager/system-connections/Auto Stephouse Wireless]] (600 root)
[connection] id=Auto Stephouse Wireless | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=Stephouse Wireless

[[/etc/NetworkManager/system-connections/Auto attwifi]] (600 root)
[connection] id=Auto attwifi | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=attwifi

[[/etc/NetworkManager/system-connections/Auto KindCedar-guest]] (600 root)
[connection] id=Auto KindCedar-guest | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=KindCedar-guest

[[/etc/NetworkManager/system-connections/Auto PSU Secure]] (600 root)
[connection] id=Auto PSU Secure | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PSU Secure

[[/etc/NetworkManager/system-connections/Auto PdaNet HotSpot]] (600 root)
[connection] id=Auto PdaNet HotSpot | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=PdaNet HotSpot

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'eth0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto 2WIRE488]] (600 root)
[connection] id=Auto 2WIRE488 | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=2WIRE488

[[/etc/NetworkManager/system-connections/Auto gogoinflight]] (600 root)
[connection] id=Auto gogoinflight | type=802-11-wireless | permissions=user:laptop:;
[802-11-wireless] ssid=gogoinflight

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth1      no frequency information.

eth0      11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: <MAC '\00\00\00\00' [AC1]>
                    ESSID:"\x00\x00\x00\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-18 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 124ms ago
          Cell 02 - Address: <MAC 'TR' [AC2]>
                    ESSID:"TR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-56 dBm  
                    Extra: Last beacon: 88ms ago
          Cell 03 - Address: <MAC 'JC' [AC3]>
                    ESSID:"JC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=48/100  Signal level=-72 dBm  
                    Extra: Last beacon: 5100ms ago
          Cell 04 - Address: <MAC 'JAM' [AC4]>
                    ESSID:"JAM"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=39/100  Signal level=-77 dBm  
                    Extra: Last beacon: 10392ms ago
          Cell 05 - Address: <MAC '\00\00\00\00' [AC1]>
                    ESSID:"ANDI"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-26 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5108ms ago
          Cell 06 - Address: <MAC 'belkin.8d4' [AC6]>
                    ESSID:"belkin.8d4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5088ms ago
          Cell 07 - Address: <MAC 'belkin.8d4.guests' [AC7]>
                    ESSID:"belkin.8d4.guests"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-75 dBm  
                    Extra: Last beacon: 5084ms ago

##### module infos ######################

[ipw2200]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     24E9BF82FCFA16D4C5D111B
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[cfg80211]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A289A224DC04F871A44431D
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.2.0-69-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     9F5D4A88A58D2831D296FA3
depends:        
intree:         Y
vermagic:       3.2.0-69-generic-pae SMP mod_unload modversions 686 

##### module parameters #################

[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

loop
lp

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   29.986540] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   29.986546] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   30.021386] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   30.021419] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   30.358222] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  342.395748] ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)

########## wireless info END ############

```



Can either of you make any sense of this?

---

### Post by Hadaka on 2014-10-19
Hi, you have some kind of odd thing going on there, this last
wireless-info.txt file is the first that is finally readable,but you said
something about orange lines??any way, are you running this as a or
from a hot spot???
ide also like to see if we can get the eth0 and wlan0 correct in the udev file.
so please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT----RESTART
and see if it changed..please do and POST
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
lets do that to start 
thanks.

---

### Post by olyvkina on 2014-10-19
Yep, I'm using a wireless hotspot to access the internet.
I ran sudo rm /etc/udev/rules.d/70-persistent-net.rules. No output was given, and I believe that was to be expected.
After reboot, ethernet is still not detected.

cat /etc/udev/rules.d/70-persistent-net.rules produces:
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:3f:f4:00:7a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:ce:22:27:81", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

Next steps?

---

### Post by Hadaka on 2014-10-19
ok, so lets clean up your country code next.
please copy and paste..
```
sudo sed -i 's/^REG.*=$/&XX/' /etc/default/crda
sudo iw reg set US
```
post the output of..
```
cat /etc/default/crda
```

---

### Post by olyvkina on 2014-10-19
Allrighty. 
I did the first two commands and there was no output.

cat /etc/default/crda produces:
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=XX

```

Next steps?

---

### Post by Hadaka on 2014-10-19
oops..please re-run all the prior commands
from last post except replace this one for the last
one with invalid data...sorry
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
i forgort to insert US for XX in my template.

---

### Post by olyvkina on 2014-10-19
Oh okay.
Hrrm. well, it looks like after running the following, the output is the same:

sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda (no output)
sudo iw reg set US (no output)

cat /etc/default/crda produces:
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=XX

```

---

### Post by Hadaka on 2014-10-19
What exactly are you using for an internet source??
this "wireless hot spot" cant do both wired and wireless
so ,,,if you are currently getting a wireless signal from it
you wont have a wired connection as far as i know. My knowledge on hotspots
is limited so i invite any hotspot experts to chime in. I think we are trying to
fix someting that isnt broken ;)

---

### Post by olyvkina on 2014-10-19
I understand that a hotspot is not wired. 
I also have hughesnet wired internet. I would prefer to use that because 1) I'm paying for it 2) I dont want to have to rely on my work phone for internet and 3) it's a better connection.

---

### Post by olyvkina on 2014-10-19
. . . and I know it is a better connection because it connects to my million-year-old desktop just fine. but the million-year-old desktop is excrutiatingly slow, unlike my laptop.

---

### Post by jeremy31 on 2014-10-20
Will it connect to Hughes with the cable plugged in and ```
rfkill block all
``` If not ```
rfkill unblock all
```

Are you using the ethernet cable that came with the hughes device, have you tried a different one.  Does the Hughes box detect the laptop, should be a light on the Hughes panel labelled LAN.  It might take a couple minutes for Hughes to get the DHCP and other things coordinated with the PC.  Another thing to try is to attempt to ping the hughes modem and I think it was ```
ping -c3 192.168.0.1
```

What model Hughes do you have?  Do you have a wifi router?

What kind of install is this as your boot parameters are something I haven't seen before and it contains lucid and not precise
> [COLOR=#000000][FONT=Ubuntu Mono]##### kernel ############################[/FONT][/COLOR]
Linux 3.2.0-69-generic-pae #103-Ubuntu SMP Tue Sep 2 05:15:53 UTC 2014 i686 i686 i386 GNU/Linux

Parameters: ro, initrd=ubuntu-installer/lucid-i386/initrd.gz, splash, quiet, vt.handoff=7

---

### Post by olyvkina on 2014-10-20
While ethernet was plugged in, 'rfkill block all' disconnected my wireless.
'rfkill unblock all' allowed my wireless connection to re-connect. Ethernet was still not detected.
I am currently using the ethernet cable that came with my Hughesnet device. I have previously tried another ethernet cable, too, with no luck.
The Hughesnet box does not detect my laptop (the LED lights wheree the cable plugs into the box do not light, neither does the 'LAN' LED in the front of the box).

ping -c3 192.168.0.1 produces:
```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

```
Can you tell me what this means?

I have an HN9000 model Hughesnet router. I do not have a wifi router.

As far as "what kind of install" I have, that's a messy answer. I tried to update from 12.04 to 14.04 and ended up with a 'partial upgrade', as it did not complete. So that might have something to do with bizarre-looking "boot parameters". I hope I understood your question correctly and that this is responsive.

Please let me know if I misunderstood you at all. . .

and of course, thank you so much for taking time to help me. . .

---

### Post by jeremy31 on 2014-10-21
Do you still have the 14.04 install media or still have the iso to write to a DVD or USB?  I would like you to boot up with the DVD/USB and select Try Ubuntu and see if the hughesnet will work

Also check BIOS settings to see if the onboard ethernet is enabled

The partial upgrade might be causing the problems, one thing might reveal issues ```
dmesg | egrep 'eth1 | b44'
```

I had a HNS7000 for 7 years and finally ditched it in March after Hughes started redirecting my browsing to their ads to upgrade to Gen4

---

### Post by olyvkina on 2014-10-21
No, unfortunately I do not have 14.04 install media -I launched the upgrade from Update Manager.

dmesg | egrep 'eth1 | b44' produces:
```

[    3.507136] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.573553] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    3.593884] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:12:3f:f4:00:7a

```

I will check BIOS settings and confirm that onboard ethernet is enabled. . . .

And I'm only with HughesNet because I really have no choice (I live on an Indian reservation) .

---

### Post by olyvkina on 2014-10-21
. . .and onboard ethernet _is_ enabled.

---

### Post by olyvkina on 2014-10-24
Anyone able to help me with this issue?
My computer briefly detected my ethernet a bit ago for about 10 minutes and then it randomly disconnected. Haven't been able to get it to work for hours now : (

---

### Post by jeremy31 on 2014-10-24
```
sudo gedit /etc/network/interfaces
``` and you should have this ```
auto lo
iface lo inet loopback
``` 
But you have a couple extra lines edit the file to put a # in front of those lines, yours might be like this after editing to add # to a couple lines
```
[COLOR=#000000][FONT=Ubuntu Mono]auto lo[/FONT][/COLOR]
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp
```
Save file, exit program, restart

---

### Post by olyvkina on 2014-10-25
Hello, jeremy31. I edited the above file you mentioned and nothing changed upon restart. no ethernet connection.

I do want to mention: for the brief amount of time that my ethernet did connect the other day, i went ahead and took a look at "connection information". under **General **it listed 'interface', 'hardware address', 'driver', 'speed', and 'security'. under **IPv4** it listed 'ip address', 'broadcast address', 'subnet mask', default route', 'primary dns', and 'secondary dns' -each of these with values.

not sure how helpful this could be, but if so (and if this information is not sensitive to my computer) I can post a screenshot of this and/or provide those values.

---

### Post by jeremy31 on 2014-10-25
Have you rebooted with the Hughes hooked up to see if the LAN lights up on Hughes at any time while booting?

Of the connection info you listed, the hardware address is the only one that would be machine specific.

You could try some changes to the NetworkManager.conf file ```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```

Yours appears to be this now
```
[COLOR=#000000][FONT=Ubuntu Mono][main][/FONT][/COLOR]plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth1' [IF]>,

[ifupdown]
managed=true
```

I would make two changes put a # in front of no-auto-default and change the managed=true to managed=false, save and reboot

---

### Post by olyvkina on 2014-10-25
Hello

Unfortunately, at no point during my system re-boot did the LAN LED light up.
My NetworkManager.conf file is different from what you posted. it is:

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:12:3F:F4:00:7A,

[ifupdown]
managed=true

```

With that in mind, should I still make the change that you are proposing?

---

### Post by jeremy31 on 2014-10-25
> **olyvkina said:**
> Hello

Unfortunately, at no point during my system re-boot did the LAN LED light up.
My NetworkManager.conf file is different from what you posted. it is:

```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:12:3F:F4:00:7A,

[ifupdown]
managed=true

```

With that in mind, should I still make the change that you are proposing?

I would put the # in front of no-auto-default and change the managed line to false

---

### Post by olyvkina on 2014-10-25
Hello

Well, I tried that and re-booted my system. But ethernet is still not detected : (

---

### Post by jeremy31 on 2014-10-25
Time to search the logs ```
dmesg | grep -e b44 -e eth1
```

---

### Post by olyvkina on 2014-10-25
Okay.
dmesg | grep -e b44 -e eth1 produces:
```

[    1.748661] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.816970] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.836967] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:12:3f:f4:00:7a
[   58.400027] eth1: no IPv6 routers present

```

---

### Post by jeremy31 on 2014-10-25
Have you ever tried closing the lid on the laptop long enough for it to go into sleep mode, then open the lid to see if the wired connection works?  You could also enable airplane mode to disable wifi and change the wired settings to IPv6 ignore

Did you ever have Lucid installed on the laptop?

---

### Post by Hadaka on 2014-10-25
I "think" i found the confusion here, correct me if i am wrong.
you were posting from the old laptop,connected to the internet via your
hot spot created cell phone connection. You also have a huges modem/router
that can supply you a wired connection....THAT is what is not working...sooo
it looks like the b44 wired driver is loading just fine, your problem is just a 
a configuration. I have b44 as my hardwire/ethernet driver so i know this works.
click the wireless icon indicator..network/mgr..then click edit connections....wired
configure exactly like the attached.,,save,,close,,and boot.
[ATTACH=CONFIG]257489[/ATTACH][ATTACH=CONFIG]257490[/ATTACH][ATTACH=CONFIG]257491[/ATTACH]

*YES make it eth0
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:3f:f4:00:7a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

---

### Post by olyvkina on 2014-10-25
Hadaka, you are absolutely correct about what I have and what I'm trying to do.

I will follow your instructions from the images and report back. . .

---

### Post by olyvkina on 2014-10-25
Okay:

I'm about to try this out, but when I follow along from the first image, (input "00:15:C5:6D:CE:C5 (eth0)", it won't let me keep the "(eth0)" at the end. After saving and re-opening the tab, it reassigns "(eth0)" to the end of another previously set MAC address in the drop-down menu. I haven't re-booted to see if this does or doesn't have an effect, but is there a way that I can delete the other MAC address in the drop-down?

Also, I didn't understand the last 4 lines of your response : /

---

### Post by olyvkina on 2014-10-25
jeremy31-

I did try to close my laptop, let it get to sleep, and re-open to see if wired would connect. Well, I believe my computer is suffering from some bug where closing of the laptop lid and re-opening it does not make it 'awaken' from sleep mode. What it does is resume humming, but the screen remains black. So what I have to do is press and hold the power button for it to power off and then I just re-start again. very annoying.

HOWEVER, when I went into Network Connections to do what Hadaka suggested, I found that apparently just minutes ago 'Wired connection 2' was 'last used'. So it seems that your suggested method worked, its just that my computer was busy sleeping to deep for me to take advantage of the connection. I'm curious about what exactly is going on here!

---

### Post by olyvkina on 2014-10-26
Any further instructions, jeremy31 or Hadaka?

---

### Post by olyvkina on 2014-10-26
anyone. . . ? : (

---

### Post by jeremy31 on 2014-10-26
I would check the ethernet ports on the laptop and the hughes equipment for dirt and to see if the pins are nice and straight.

Other ideas, download a new ISO of Ubuntu 12.04 or 14.04 and put on USB or DVD and see if it works with the Try Ubuntu trial as you seem to have a frankenstein install with lucid in the boot parameter, precise kernel and a failed trusty upgrade, find a cheap wifi router as your wireless works

I dug out my Hughes 7000 and after finding the power cord, the LAN on the hughes lit up but no lights near my Ethernet port on my laptop and it took about 5 minutes to connect

---

### Post by olyvkina on 2014-10-27
Everything is working now!!! I'm not sure which suggestion worked, so I will attribute the solution a combination to all of the above. It also finally gave me the opportunity to set up my wireless router (needed the ethernet for that, too) so I am good to go : ) Thanks so much jeremy31 and Hadaka. I wish there was an emoticon for baking cookies because I would totally bake you both cookies as a token of gratitude. 

Everyone, have a great week : )

---


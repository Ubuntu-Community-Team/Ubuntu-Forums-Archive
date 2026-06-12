---
title: "Broadcom BCM4313"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by dank13 on 2014-10-30
Hi, it's my forst time on this forum.
After the installation of Ubuntu 14.10 I've a problem: my pc doesn't find any wireless conection.
Now i'm using my ethernet cable, but 'id like to return to use wireless.
This is what show the terminal with the code lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation 1st Generation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation 1st Generation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation 1st Generation Core Processor Reserved (rev 02)
```

---

### Post by jeremy31 on 2014-10-30
Hello dank
It does find your wireless, but the selected driver may not be ideal

Try the suggestions from [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) to see if your wifi works after- I would try the suggestions for 14.04 which would involve ```
sudo apt-get purge bcmwl-kernel-source
``````
sudo apt-get install firmware-b43-installer
``` if you have a wired connection available

If it still doesn't work, check [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) for instructions on using the wireless script to collect info on your current install and paste or attach the results


> **dank13 said:**
> Hi, it's my forst time on this forum.
After the installation of Ubuntu 14.10 I've a problem: my pc doesn't find any wireless conection.
Now i'm using my ethernet cable, but 'id like to return to use wireless.
This is what show the terminal with the code lspci

```

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

---

### Post by Hadaka on 2014-10-30
Hi ,please verify your PCI-ID is [14e4:4727] with the help of this guide
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
from there follow the instructions or,,,COPY and paste these commands
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf#ignore any cant find or error messages
```
then do..
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a  /etc/modprobe.d/blacklist.conf
sudo modprobe -rf b43
sudo modprobe brcmsmac
```
boot...test wireless
thanks.

---

### Post by dank13 on 2014-10-31
> **jeremy31 said:**
> Hello dank
It does find your wireless, but the selected driver may not be ideal

Try the suggestions from [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) to see if your wifi works after- I would try the suggestions for 14.04 which would involve ```
sudo apt-get purge bcmwl-kernel-source
``````
sudo apt-get install firmware-b43-installer
``` if you have a wired connection available

If it still doesn't work, check [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) for instructions on using the wireless script to collect info on your current install and paste or attach the results

Hi jeremy, I've tried to run the two codes you wrote but nothing change.
So I use the instruction in the link you posted and this is the wireless script

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

---

### Post by dank13 on 2014-10-31
> **Hadaka said:**
> Hi ,please verify your PCI-ID is [14e4:4727] with the help of this guide
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
from there follow the instructions or,,,COPY and paste these commands
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf#ignore any cant find or error messages
```
then do..
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a  /etc/modprobe.d/blacklist.conf
sudo modprobe -rf b43
sudo modprobe brcmsmac
```
boot...test wireless
thanks.

Hi hadaka, I've try this two different method but nothig change. Any others ideas?
My pci code i s 
```
14e4:4727 (ver 1)
```

---

### Post by Hadaka on 2014-10-31
hi, please post the output of..
```
lsmod
lspci -nn | egrep '0200|0280'
cat /etc/modprobe.d/blacklist.conf | egrep 'b43|ssb'
rfkill list all
```
Please use code tags
ALSO ..while connected to the internet with the wired connection
re-run the last commands i gave you.
thanks.

---

### Post by dank13 on 2014-11-01
> **Hadaka said:**
> hi, please post the output of..
```
lsmod
lspci -nn | egrep '0200|0280'
cat /etc/modprobe.d/blacklist.conf | egrep 'b43|ssb'
rfkill list all
```
Please use code tags
ALSO ..while connected to the internet with the wired connection
re-run the last commands i gave you.
thanks.

Sorry, I've just modify the previous post.
In these weeks I'm always in wired connection.
This is the output of your code (just a question: I put the code all at once, is it correct? Or is it better to put a line at a time?)

```
dank@DenPC:~$ lsmod
Module                  Size  Used by
bnep                   18829  2 
rfcomm                 58045  0 
bluetooth             390981  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
uvcvideo               71457  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         48344  1 uvcvideo
v4l2_common            15132  1 videobuf2_core
videodev              131257  3 uvcvideo,v4l2_common,videobuf2_core
media                  20951  2 uvcvideo,videodev
arc4                   12536  2 
brcmsmac              537999  0 
cordic                 12518  1 brcmsmac
brcmutil               15035  1 brcmsmac
mac80211              567098  1 brcmsmac
cfg80211              430618  2 brcmsmac,mac80211
hp_wmi                 13741  0 
sparse_keymap          13708  1 hp_wmi
intel_powerclamp       18385  0 
coretemp               13201  0 
joydev                 17072  0 
serio_raw              13210  0 
bcma                   46430  2 brcmsmac
lpc_ich                16877  0 
intel_ips              18069  0 
snd_hda_codec_realtek    69999  1 
snd_hda_codec_generic    62849  1 snd_hda_codec_realtek
snd_hda_intel          29211  3 
snd_hda_controller     29944  1 snd_hda_intel
snd_hda_codec         120356  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                91280  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
mei_me                 19102  0 
snd_seq_midi           13324  0 
mac_hid                13059  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  1 snd_seq_midi
snd_seq                56638  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28579  2 snd_pcm,snd_seq
mei                    72096  1 mei_me
snd                    66629  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              14604  2 snd,snd_hda_codec
shpchp                 32136  0 
parport_pc             32021  0 
ppdev                  17391  0 
lp                     17395  0 
parport                40795  3 lp,ppdev,parport_pc
xts                    12749  1 
gf128mul               14503  1 xts
dm_crypt               22584  1 
hid_generic            12503  0 
usbhid                 47001  0 
hid                    91893  2 hid_generic,usbhid
i915                  824137  3 
radeon               1328356  1 
i2c_algo_bit           13190  2 i915,radeon
ttm                    76915  1 radeon
ahci                   25622  2 
drm_kms_helper         55051  2 i915,radeon
psmouse                95318  0 
drm                   255383  8 ttm,i915,drm_kms_helper,radeon
libahci                31066  1 ahci
r8169                  61415  0 
mii                    13654  1 r8169
wmi                    18689  1 hp_wmi
video                  19528  1 i915
dank@DenPC:~$ lspci -nn | egrep '0200|0280'
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
dank@DenPC:~$ cat /etc/modprobe.d/blacklist.conf | egrep 'b43|ssb'
# replaced by b43 and ssb.
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb
dank@DenPC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Another thing that maybe can be usefull: in System Settings --> Network I can't able the wireless connection. I made a screenshot

---

### Post by wildmanne39 on 2014-11-01
Hi, according to the output you posted it is hard blocked which usually means it is turned off, do you have switch to turn wireless on? sometimes it takes a key combination like fn +f2. 
Thanks

---

### Post by Hadaka on 2014-11-01
Wild man is correct,please look for a keybord combo or regular on/off
switch, also please do.
```
sudo rfkill list unblock all
```
then to view...
```
rfkill list all
```
thanks.

---

### Post by dank13 on 2014-11-01
> **Wild Man said:**
> Hi, according to the output you posted it is hard blocked which usually means it is turned off, do you have switch to turn wireless on? sometimes it takes a key combination like fn +f2. 
Thanks
I've tried with fn +f2.but nothing happen. There some other way to turn wireless on?
As showed in the image in previous post, from setting -> network is impossible to active wireless

> **Hadaka said:**
> Wild man is correct,please look for a keybord combo or regular on/off
switch, also please do.
```
sudo rfkill list unblock all
```
then to view...
```
rfkill list all
```
thanks.

Here what happen with the two code

```
dank@DenPC:~$ sudo rfkill list unblock all
Bogus list argument 'unblock'.

dank@DenPC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

the hp wifi is always hard blocked

---

### Post by Hadaka on 2014-11-01
Hi, the last command i gave you was in error, sorry.
please do..
```
sudo rfkill unblock all
```
thanks

---

### Post by dank13 on 2014-11-02
> **Hadaka said:**
> Hi, the last command i gave you was in error, sorry.
please do..
```
sudo rfkill unblock all
```
thanks

I've tried the new command and check with the other command, but nothing change

```
dank@DenPC:~$ sudo rfkill unblock all

dank@DenPC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dank@DenPC:~$ 

```

---

### Post by Hadaka on 2014-11-02
hi please copy and paste one command at a time
```
sudo modprobe -rf hp_wmi
sudo rfkill unblock all
echo "blacklist hp_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
thanks

---

### Post by dank13 on 2014-11-03
> **Hadaka said:**
> hi please copy and paste one command at a time
```
sudo modprobe -rf hp_wmi
sudo rfkill unblock all
echo "blacklist hp_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
thanks

It works!!!! Great!!!
I'm vert happy. I love you man!!!!
Thanks

---

### Post by Hadaka on 2014-11-03
Glad you are happy and in love
have fun.

---


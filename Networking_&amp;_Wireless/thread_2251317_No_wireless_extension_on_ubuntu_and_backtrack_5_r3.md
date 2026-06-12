---
title: "No wireless extension on ubuntu and backtrack 5 r3"
date: 2014-11-03
forum: Networking &amp; Wireless
---

### Post by gamre2077 on 2014-11-03
Hi i'm new to this forum and to ubuntu as well however i have encounter a problem when trying to use backtrack 5 r3 it's said no wireless extension when i enter the command iwconfig on the terminal. Ubuntu does that too any help please?i have a toshiba qosmio-x875 thanks

---

### Post by slickymaster on 2014-11-03
*Moved to the* **Networking & Wireless** *sub-forum.*

Hi [COLOR=#000000]gamre2077[/COLOR], welcome to the forums.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please [use 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). It preserves the output's formatting and makes the post cleaner, compact and more readable.

---

### Post by gamre2077 on 2014-11-03
hi slickymaster
  thanks for responding i may forgot to mention that i have internet acces with both ubuntu and backtrack regarless the link you gave me. Everything work perfectly fine except the iwconfig problem that i've stated above

---

### Post by gamre2077 on 2014-11-03
```
#!/bin/bash
#
# Script adapted from 'wireless_script' originally written by:
# Ubuntu Forums members - Wild Man, Krytarik
# 
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
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
 
FILEBASE="wireless-info"
MODMATCHES="(air|ar5|ath[^3]|carl|at7|ipw|iwl|rt[23567l]|r(818|871)|8192[cd]|r92su|ssb|wl|b43|bcma|brcm|ndis|eth[1-9]|firm|etwork)[^[:punct:] ]*"

clear
printf "\n        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  \"Ctrl+Z\" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')\n\n"

exec 3>&1 4>&2
exec 1> $FILEBASE.tmp 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi

FILL=$(printf "%.1s" "~"{1..36})
FMT="\n%.36s\n"

## Wireless-Info START
printf "\n\t======== Wireless-Info START ========\n"

printf "$FMT\n" "System-Info $FILL"
printf "$(uname -nrm),  $(lsb_release -dcs | sed '/$/ {N; s:\n:, :}')\n"
CPU=$(grep -m1 'model name' /proc/cpuinfo); CPU=${CPU#*: }
MEM=$(free -m | awk 'NR==2 {print $2}')
printf "\nCPU    : $CPU\nMemory : $MEM MB\nUptime :"
uptime

## lspci
printf "\n$FMT\n" "lspci $FILL"
lspci -nnk | grep -iA2 net

## lsusb
printf "\n$FMT\n" "lsusb $FILL"
lsusb

## PCMCIA Card Info
printf "\n$FMT\n" "PCMCIA Card Info $FILL"
pccardctl info

## iwconfig
printf "\n$FMT\n" "iwconfig $FILL"
iwconfig

## rfkill
printf "\n$FMT\n" "rfkill $FILL"
RFKILL=$(rfkill list all)
if [ "$RFKILL" ]; then
    WIDTH=$(grep ^[0-9] <<< "$RFKILL" | wc -L)
    printf "%-*s  %s  %s" $WIDTH "      Interface" "Soft blocked" "Hard blocked"
    while read LINE; do
        if [ $(grep -o ^[0-9] <<< "$LINE") ]; then
            printf "\n%-$WIDTH.40s  " "$LINE"
        elif [ $(grep -o '^Soft' <<< "$LINE") ]; then
            printf "%-14s" "    ${LINE#*: }"
        else printf "%s" "    ${LINE#*: }"
        fi
    done <<< "$RFKILL"
fi

## lsmod
printf "\n\n$FMT\n" "lsmod $FILL"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])(${MODMATCHES}|wmi|ideapad)([[:punct:] ]|$)")
printf "$LSMOD\n"

## module parameters
printf "\n$FMT" "module parameters $FILL"
MODULES=$(awk '{print $1}' <<< "$LSMOD")
    while read LINE
    do
        if [ -d /sys/module/$LINE/parameters ]; then
            printf "\n%-12s %4s: " "$LINE" "($(ls -1 /sys/module/$LINE/parameters | wc -l))"
            PARMS=$(grep -H [[:graph:]] /sys/module/"$LINE"/parameters/*)
            PARMS=$(while read i; do printf "${i##*/} | "; done <<< "$PARMS")
            PARMS=${PARMS//:/=}; PARMS=${PARMS% | }
            printf "$PARMS"
        fi
    done <<< "$MODULES" | sort -d

## nm-tool
printf "\n$FMT\n" "nm-tool $FILL"
NMTOOL=$(nm-tool | egrep -v '^Net|^$|^  (Cap|IPv|Wir|  Car)' | \
        sed -r '/^- Device:/ s/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<BT Device>/')
F1=$(($(grep -o '^- Device: .* -' <<< "$NMTOOL" | wc -L)-10)); if [ $F1 -lt 16 ];then F1=16; fi
F2=$(($(grep '^  Type' <<< "$NMTOOL" | wc -L)-19)); if [ $F2 -lt 6 ];then F2=6; fi
F3=$(($(grep '^  Driver' <<< "$NMTOOL" | wc -L)-19)); if [ $F3 -lt 8 ];then F3=8; fi
F4=$(($(grep '^  State' <<< "$NMTOOL" | wc -L)-19)); if [ $F4 -lt 8 ];then F4=8; fi
#F4=14;
F5=9; F6=11; F7=11; F8=14 # State, Default, MAC ID, Speed, WEP/WPA/WPA2
WIDTH=$((F1+F2+F3+F4+F5+F6+F7+F8+7))
P1=$(printf '%0.1s' "="{1..60})
P2=$(printf '%0.1s' "-"{1..160})

FORMAT="%-${F1}s|%-${F2}s|%-${F3}s|%-${F4}s|%-${F5}s|%-${F7}s|%-${F8}s|%-${F6}s"
HEAD=$(printf $FORMAT " Interface & ID" " Type" " Driver" " State" " Default" " Speed" " Support" " HW Addr")
L1=$(printf '%.*so%.*so%.*so%.*so%.*so%.*so%.*so%.*s' $F1 $P1 $F2 $P1 $F3 $P1 $F4 $P1 $F5 $P1 $F7 $P1 $F8 $P1 $F6 $P1)
L2=$(printf '%.*s+%.*s+%.*s+%.*s+%.*s+%.*s+%.*s+%.*s' $F1 $P2 $F2 $P2 $F3 $P2 $F4 $P2 $F5 $P2 $F7 $P2 $F8 $P2 $F6 $P2)

printf "$(head -1 <<< "$NMTOOL")\n"
NMTOOL=$(tail -n +2 <<< "$NMTOOL")
printf -- "$L1\n$HEAD\n$L1"

DEVRANGES=$(printf "$(sed -n '/^- Device/ =' <<< "$NMTOOL")\n$(($(wc -l <<< "$NMTOOL")+1))");
PREV=0
while read CURR; do
    if [ $PREV -eq 0 ]; then PREV=$CURR
    else
        RANGE=$(sed -n "$PREV,$((CURR - 1)) p" <<< "$NMTOOL")
        SUBRANGE1=$(grep 'Freq .* Rate .* Strength ' <<< "$RANGE")
        SUBRANGE2=$(egrep '^    (Address|Prefix|Gateway|DNS)' <<< "$RANGE")
        
        ID=$(grep '^- Dev' <<< "$RANGE"); ID=${ID#*: }; ID=${ID% -*}
        TYPE=$(grep '^  Type' <<< "$RANGE"); TYPE=${TYPE##*    }
        DRVR=$(grep '^  Driver' <<< "$RANGE"); DRVR=${DRVR##*    }
        STATE=$(grep '^  State' <<< "$RANGE"); STATE=${STATE##*    }
        DEF=$(grep '^  Default' <<< "$RANGE"); DEF=${DEF##*    }
        HW=$(grep '^  HW' <<< "$RANGE"); HW=${HW##*    }
        SPEED=$(grep '^    Speed' <<< "$RANGE"); SPEED=${SPEED##*    }
        WEP=$(grep '^    WEP' <<< "$RANGE"); WEP=${WEP##* }; WEP=${WEP/yes/WEP/}; WEP=${WEP/no/}
        WPA=$(grep '^    WPA ' <<< "$RANGE"); WPA=${WPA##* }; WPA=${WPA/yes/WPA/}; WPA=${WPA/no/}
        WPA2=$(grep '^    WPA2 ' <<< "$RANGE"); WPA2=${WPA2##* }; WPA2=${WPA2/yes/WPA2}; WPA2=${WPA2/no/}
        
        printf "\n$FORMAT" " $ID" " $TYPE" " $DRVR" " $STATE" " $DEF" " $SPEED" " $WEP$WPA$WPA2" " $HW"
        if [ "$SUBRANGE1" ]; then
            printf "\n\n$SUBRANGE1"
        fi
        if [ "$SUBRANGE2" ]; then
            SUBRANGE2=${SUBRANGE2//    Address/\\n    Address}
            printf "\n$SUBRANGE2"
        fi
        printf "\n$L2"
        PREV=$CURR
    fi
done <<< "$DEVRANGES"

## NetworkManager.state
printf "\n\n$FMT" "NetworkManager.state $FILL"
cat /var/lib/NetworkManager/NetworkManager.state

## NetworkManager.conf
printf "\n$FMT\n" "NetworkManager.conf $FILL"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

## NM-Connection-Profiles
printf "\n$FMT" "NM WiFi Profiles $FILL"
CON_PROFILES=$(sudo grep -hA40 -B4 '^type=802-11-wireless' /etc/NetworkManager/system-connections/* |\
    egrep '^id=|^permissions|^autoconnect|^ssid|^mac-address|^bssid|^mtu|ipv4|ipv6|^method|ca-cert')
CON_PROFILES=$(while read LINE; do
        if [ "$(grep '^id=' <<< "$LINE")" ]; then
            ID=${LINE##id=}
            printf "\n%-20s : " "$ID"
        else
            echo -e "$LINE \c"
        fi
    done <<< "$CON_PROFILES")
CON_PROFILES=$(sed -r    's/( permissions=[[:graph:]]*)/ |&/; s/ autoconnect=[a-z]*/ |&/; s/ mac-address=[[:graph:]]*/ |&/
            s/ bssid=[[:graph:]]*/ |&/; s/ mtu=[0-9]*/ |&/; s/ \[(ipv[46])\] method(=[a-z]*)/ | \1\2/g
            s/ [[:graph:]]*a-cert[[:graph:]]*/ |&/' <<< "$CON_PROFILES")
CON_PROFILES=$(sed -r 's/(\| .*) (ssid=[[:graph:]]* )/\2\1 /' <<< "$CON_PROFILES")
printf "$CON_PROFILES\n"

## interfaces
printf "\n$FMT\n" "interfaces $FILL"
sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/' /etc/network/interfaces

## resolv.conf
printf "$FMT\n" "resolv.conf $FILL"
grep -v '^#' /etc/resolv.conf

## Routes & Ping
printf "\n$FMT\n" "Routes & Ping $FILL"
ROUTE=$(route -n)
printf "$ROUTE\n"
GW=$(awk 'NR==3 {print $2}' <<< "$ROUTE")
if [ "$GW" != "0.0.0.0" ]; then
    ping -nqw4 -c2 "$GW" | sed '/^PING/ d'
    if [ -e /run/nm-dns-dnsmasq.conf ]; then
        DNS=$(sed -n 's:^server=::p' /run/nm-dns-dnsmasq.conf)
    else
        DNS=$(sed -n 's:^nameserver ::p' /etc/resolv.conf)
    fi
    if [ "$DNS" ]; then
        while read LINE; do
            ping -nqw2 -c2 "$LINE" | sed '/^PING/ d'
        done <<< "$DNS"
    fi
fi

## iw reg get
printf "\n$FMT\n" "iw reg get $FILL"
printf "$(locale | sed -n '/IDENT/ s/LC.*=\(.*\)/(Region : \1)/p')\n"
iw reg get

## iwlist chan
printf "\n$FMT\n" "iwlist chan $FILL"
CHAN=$(iwlist chan)
START=""; BUFF1=""; BUFF2="";FLAG=0; BUFFLEN=0
while read LINE; do
    CH=${LINE#*Channel 0}; CH=${CH#*Channel }; CH=${CH% : *}
    if [ ${#LINE} -gt 25 ]; then
        if [ -z "$START" ]; then printf "$LINE\n"
        elif [ $FLAG -eq 0 ]; then printf "          $START%s\n\n          $LINE\n" " - $BUFF1"
        else printf "          $START\n\n          $LINE\n"
        fi
    elif [ -z "$START" ]; then START=${LINE/: /(}; START=${START/z/z)}; COUNT=$((CH + 1))
    elif [ $CH -eq $COUNT ]; then BUFF1=${LINE#*Channel }; BUFF1=${BUFF1/: /(}; BUFF1=${BUFF1/z/z)}; COUNT=$((COUNT + 1)); FLAG=0
    elif [ $FLAG -eq 0 ]; then printf "          $START%s\n" " - $BUFF1"; START=${LINE/: /(}; START=${START/z/z)}; COUNT=$((CH + 1)); FLAG=1
    else printf "          $START\n"; START=${LINE/: /(}; START=${START/z/z)}; COUNT=$((CH + 1))
    fi
    BUFFLEN=${#LINE}
done <<< "$CHAN"
if [ $BUFFLEN -lt 26 ];then printf "          $START%s\n" " - $BUFF1"; fi

## iwlist scan
printf "\n$FMT\n" "iwlist scan $FILL"
IWLIST=$(if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi | grep -v 'IE: Unknown: ') # Filtered out uninteresting lines from the output

if [ "$IWLIST" ]; then
    printf "$IWLIST\n"
fi

## blacklist
printf "\n$FMT" "blacklist $FILL"
for CONFFILE1 in /etc/modprobe.d/*.conf; do
    if [ "$(egrep -v 'alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee' <<< $CONFFILE1)" ]; then
        # filter out default blacklist entries
        BLACKLIST=$(grep '^blacklist' $CONFFILE1 |\
        egrep -v 'evbug|usb(kbd|mouse)|eepro|de4x5|eth1394| snd_|i2c_|prism54|bcm43xx|garmin|asus_acpi|pcspkr|amd76x')
        if [ "$BLACKLIST" ]; then
            printf "\n[%s]\n%s\n" $CONFFILE1 "$BLACKLIST"
        fi
    fi
done

## modinfo
printf "\n$FMT\n" "modinfo $FILL"
MODULNAMES=$(grep -v sparse <<< "$LSMOD" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    printf "[$MODULE]\n"
    modinfo $MODULE | egrep -i 'filename|version:|firmware|depends|parm:'
    echo
done

## udev rules
printf "$FMT" "udev rules $FILL"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules



## Custom files/entries
printf "\n$FMT\n" "Custom files/entries $FILL"
  # extra modules in /etc/modules
if [ $(egrep -v '^#|^$|^lp|^rtc|^vhba' /etc/modules | wc -l) -eq 0 ]; then
    MODFLAG=0
    STATUS="Default"
else
    MODFLAG=1
    STATUS="Not Default"
fi
printf "%-20s: $STATUS\n" "/etc/modules"

  # extra entries in /etc/rc.local
if [ $(egrep -v '^#|^exit 0|^$' /etc/rc.local | wc -l) -eq 0 ]; then
    RCFLAG=0
    STATUS="Default"
else
    RCFLAG=1
    STATUS="Not Default"
fi
printf "%-20s: $STATUS\n" "/etc/rc.local"

  # extra files in /etc/modprobe.d
CONFFILE2=$(egrep -vl '^#|^black|alias|^$' /etc/modprobe.d/* | cut -d '/' -f 4- | egrep -v '^vmw|^alsa|^oss-')
if [ -z "$CONFFILE2" ]; then
    MODCONFFLAG=0
    STATUS="Default"
else
    MODCONFFLAG=1
    STATUS="Not Default"
fi
printf "%-20s: $STATUS\n" "/etc/modprobe.d"

  # extra files in /etc/pm/(config.d|power.d|sleep.d)
PMFLAG=0
if [ "$(ls /etc/pm/config.d/)" ]; then PMFLAG=1; PCONFLAG=1
else PCONFLAG=0    
fi
if [ "$(ls /etc/pm/power.d/)" ]; then PMFLAG=1; PPOWFLAG=1
else PPOWFLAG=0
fi
SLEEP_D=$(find -L /etc/pm/sleep.d -type f | egrep -v '10_grub-common|10_unattended-upgrades|novatel_3g')
if [ "$SLEEP_D" ]; then PMFLAG=1; PSLFLAG=1
else PSLFLAG=0
fi

if [ $PMFLAG -eq 0 ]; then STATUS="Default"
else STATUS="Not Default"
fi
printf "%-20s: $STATUS\n" "/etc/pm/(cnf|pw|sl)"

  # Parsing Non-Default files/entries
if [ $MODFLAG -eq 1 ]; then
    printf "\n[/etc/modules]\n"
    egrep -v '^#|^$|^lp|^rtc|^vhba' /etc/modules
fi
if [ $RCFLAG -eq 1 ]; then
    printf "\n[/etc/rc.local]\n"
    egrep -v '^#|^$' /etc/rc.local
fi
if [ $MODCONFFLAG -eq 1 ]; then
    printf "\n[/etc/modprobe.d]\n"
    #sed 's/:/ : /' <<< "$CONFFILE2"
    for i in $CONFFILE2; do
        LINES=$(egrep -v '^#|^$' /etc/modprobe.d/"$i")
        if [ $(wc -l <<< "$LINES") -lt 2 ]; then
            printf "%-18s: %s\n" "$i" "$LINES"
        else
             printf "%-18s: " "$i"
             sed -n '1 p; 2,$ s/.*/                    &/p' <<< "$LINES"
        fi
    done
fi
if [ $PMFLAG -eq 1 ]; then
    # /etc/pm/config.d/*
    if [ $PCONFLAG -eq 1 ]; then
        for PMCONFIG in /etc/pm/config.d/*; do
            if [ -x "$PMCONFIG" ]; then
                printf "\n[$PMCONFIG] [executable]\n"
            else
                printf "\n[$PMCONFIG]\n"
            fi
            cat "$PMCONFIG"
        done
    fi
    # /etc/pm/power.d/*
    if [ $PPOWFLAG -eq 1 ]; then
        for PMPOWER in /etc/pm/power.d/*; do
            if [ -x "$PMPOWER" ]; then
                printf "\n[$PMPOWER] [executable]\n"
            else
                printf "\n[$PMPOWER]\n"
            fi
            cat "$PMPOWER"
        done    
    fi
    # /etc/pm/sleep.d/*
    if [ $PSLFLAG -eq 1 ]; then
        for PMSLEEP in $SLEEP_D; do
            if [ -x "$PMSLEEP" ]; then
                printf "\n[$PMSLEEP] [executable]\n"
            else
                printf "\n[$PMSLEEP]\n"
            fi
            cat "$PMSLEEP"
        done
    fi
fi

## Kernel boot line
printf "\n$FMT\n" "Kernel boot line $FILL"
cat /proc/cmdline

## dmesg
printf "\n$FMT\n" "dmesg $FILL"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]|net|ra[0-4]|wmi"

printf "\n\t======== Done ========\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-

# filter MAC IDs of interfaces
MAC_FILTER_IFACES=$(sed -r '/NAME="/ !d; s/.*(([[:alnum:]]{2}:){5}[[:alnum:]]{2}).*NAME="(.*)"/s\/\1\/\<MAC \3\>\/I/' /etc/udev/rules.d/70-persistent-net.rules)

# filter MAC IDs from iwlist scan
MAC_FILTER_IWLIST=$(sed -rn '/Cell / p; /ESSID:"/ p' <<< "$IWLIST" | sed -r '/Cell / N; {s/.* Cell ([[:digit:]]{2}).*(([[:alnum:]]{2}:){5}[[:alnum:]]{2}).*ESSID:"(.*)"/s\/\2\/\<MAC C-\1 \4\>\/I/}')

# filter MAC IDs from nm-tool cache
MAC_FILTER_NMTOOL=$(str_prev=""; loop=1
    sed -rn '/, (([[:alnum:]]{2}:){5}[[:alnum:]]{2}), / p' <<< "$NMTOOL" | sort |\
    sed -r 's/ *([[:graph:]].*): .* (([[:alnum:]]{2}:){5}[[:alnum:]]{2}), .*/s\/\2\/\<MAC \1\>\/I/' |\
    while read LINE; do
        if [ "$(echo $LINE | cut -d " " -f 2)" = "$str_prev" ]; then
            let loop=loop+1
        else loop=1
        fi
        sed "s/\(.*MAC \)\(.*\)\(>.\)/\1C-NA \2 $loop\3/" <<< "$LINE"
        str_prev=$(echo "$LINE" | cut -d " " -f 2)
    done)

# Original filter for leftover MAC IDs
MAC_FILTER_GENERAL='s/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC ID removed>/'

RESULTS=$(sed -r "$MAC_FILTER_IFACES" $FILEBASE.tmp)
RESULTS=$(sed -r "$MAC_FILTER_IWLIST" <<< "$RESULTS")
RESULTS=$(sed -r "$MAC_FILTER_NMTOOL" <<< "$RESULTS")
sed -r "$MAC_FILTER_GENERAL" <<< "$RESULTS" > $FILEBASE.txt
rm $FILEBASE.tmp

LINE=$(printf "%0.1s" "#"{1..72})
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    FILENAME="$FILEBASE.tar.gz"
else
    FILENAME="$FILEBASE.txt"
fi
MSG="    DONE! All results saved in -

         File Name: \t\"$FILENAME\" \n\t\t Directory: \t\"$(pwd)\"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------"
printf "\n\n    $LINE\n\n$MSG\n\n    $LINE\n\n\n\n"


```
i've run it and this is what i got

---

### Post by slickymaster on 2014-11-04
That's not what's intended. You have to run the '[wireless_script]("http://dl.dropbox.com/u/57264241/wireless_script")' in your system, not copy/past it into the thread.

please open a terminal (Ctrl-Alt-T) and run (copy-paste) the following code in it```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will automatically download and run the script, and generate a "**wireless-info.txt**" file in your home directory (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB). Post back this report file (or its contents) in the thread.

If posting the contents of the file, please use [code tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168").

---

### Post by gamre2077 on 2014-11-04
sorry for the confusion i've done it and the "wireless-info.txt" file is blank

---

### Post by slickymaster on 2014-11-04
[s]Sorry, I provided you a wrong/ancient command. My bad.[/s]
Try with this one.

Please, again open a terminal and then copy/paste this```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```Post back the wireless-info-text file (or its contents) in the thread. in your home directory,post that file here

---

### Post by gamre2077 on 2014-11-04
```

########## wireless info START ##########

Report from: 04 Nov 2014 22:45 EST -0500

Booted last: 04 Nov 2014 22:35 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx

08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a42 Importek 
Bus 001 Device 004: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

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
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6236:ddff:fef1:7e7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:1782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1362196 (1.3 MB)  TX bytes:232691 (232.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ClearSPOT_753b7"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'ClearSPOT_753b7' [AC1]>   
          Bit Rate=12 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:31   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ClearSPOT_753b7] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DIRECT-roku-951: Infra, <MAC 'DIRECT-roku-951' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2
    NETGEAR94:       Infra, <MAC 'NETGEAR94' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    NETGEAR81:       Infra, <MAC 'NETGEAR81' [AC13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Lydan02:         Infra, <MAC 'Lydan02' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    belkin.b7a:      Infra, <MAC 'belkin.b7a' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    DG1670A52:       Infra, <MAC 'DG1670A52' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    DG1670A52:       Infra, <MAC 'DG1670A52' [AN7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Johanny:         Infra, <MAC 'Johanny' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    DG860A62:        Infra, <MAC 'DG860A62' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    PS3-7711711:     Infra, <MAC 'PS3-7711711' [AN10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WPA
    TG1672G92:       Infra, <MAC 'TG1672G92' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    11FX07247871:    Infra, <MAC '11FX07247871' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WEP
    AndroidAP:       Infra, <MAC 'AndroidAP' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    linksys:         Infra, <MAC 'linksys' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    linksys:         Infra, <MAC 'linksys' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    DVW3201F0:       Infra, <MAC 'DVW3201F0' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    DG1670A02:       Infra, <MAC 'DG1670A02' [AN17]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA2
    HP-Print-C7-Officejet Pro 8620: Infra, <MAC 'HP-Print-C7-Officejet Pro 8620' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    belkin.077:      Infra, <MAC 'belkin.077' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    information:     Infra, <MAC 'information' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    djemy12:         Infra, <MAC 'djemy12' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WEP
    TWCWiFi-Passpoint: Infra, <MAC 'TWCWiFi-Passpoint' [AC10]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    DG1670A82:       Infra, <MAC 'DG1670A82' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    TG1672GB2:       Infra, <MAC 'TG1672GB2' [AN24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    JohannyNY:       Infra, <MAC 'JohannyNY' [AN25]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2
    TG1672G52:       Infra, <MAC 'TG1672G52' [AN26]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    prometheus:      Infra, <MAC 'prometheus' [AC14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 34 WEP
    CableWiFi:       Infra, <MAC 'CableWiFi' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 59
    TWCWiFi:         Infra, <MAC 'TWCWiFi' [AC9]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57
    MONEYTEAM1090:   Infra, <MAC 'MONEYTEAM1090' [AN30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    Global:          Infra, <MAC 'Global' [AN31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Skype Wifi:      Infra, <MAC 'Skype Wifi' [AC7]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 65
    dlink-0440:      Infra, <MAC 'dlink-0440' [AN33]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Kronos:          Infra, <MAC 'Kronos' [AN34]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    b0c5549f7cc6:    Infra, <MAC 'b0c5549f7cc6' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Flash:           Infra, <MAC 'Flash' [AN36]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TG1672GC2:       Infra, <MAC 'TG1672GC2' [AN37]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Alex:            Infra, <MAC 'Alex' [AN38]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    STEEPLECHASE:    Infra, <MAC 'STEEPLECHASE' [AN39]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    *ClearSPOT_753b7:Infra, <MAC 'ClearSPOT_753b7' [AC1]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    NETGEAR72:       Infra, <MAC 'NETGEAR72' [AN41]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2

  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/LaGuardia-WiFi]] (600 root)
[connection] id=LaGuardia-WiFi | type=802-11-wireless
[802-11-wireless] ssid=LaGuardia-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ASUS]] (600 root)
[connection] id=ASUS | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ClearSPOT_753b7]] (600 root)
[connection] id=ClearSPOT_753b7 | type=802-11-wireless
[802-11-wireless] ssid=ClearSPOT_753b7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country KR:
    (2402 - 2482 @ 20), (N/A, 20)
    (5170 - 5250 @ 20), (3, 20)
    (5250 - 5330 @ 20), (3, 20), DFS
    (5490 - 5630 @ 20), (3, 30), DFS
    (5735 - 5815 @ 20), (3, 30)

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ClearSPOT_753b7' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"ClearSPOT_753b7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000001bf4ba3
                    Extra: Last beacon: 220ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIRECT-roku-951' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-951"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041e50b668a
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR94' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR94"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'belkin.b7a' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"belkin.b7a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d9fda1bc8
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Nightwing' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Nightwing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3200002d85800020
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'djemy12' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"djemy12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000036e746d6e05
                    Extra: Last beacon: 12ms ago
          Cell 07 - Address: <MAC 'Skype Wifi' [AC7]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"Skype Wifi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c5e35180
                    Extra: Last beacon: 1288ms ago
          Cell 08 - Address: <MAC 'CableWiFi' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"CableWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c5e352ee
                    Extra: Last beacon: 1288ms ago
          Cell 09 - Address: <MAC 'TWCWiFi' [AC9]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"TWCWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c5e3545c
                    Extra: Last beacon: 1288ms ago
          Cell 10 - Address: <MAC 'TWCWiFi-Passpoint' [AC10]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"TWCWiFi-Passpoint"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c5e355c6
                    Extra: Last beacon: 1288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'AndroidAP' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"AndroidAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000f18ae18
                    Extra: Last beacon: 12ms ago
          Cell 12 - Address: <MAC 'belkin.077' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"belkin.077"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d9ffe9bbb
                    Extra: Last beacon: 1100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'NETGEAR81' [AC13]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR81"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000082eaf081e2
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'prometheus' [AC14]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"prometheus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001919d02df01
                    Extra: Last beacon: 12ms ago
          Cell 15 - Address: <MAC 'Lydan02' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Lydan02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017721e7fc94
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0887 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  482.540203] iwlwifi 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  482.540212] iwlwifi 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  482.540271] wlan0: associate with <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  482.551248] wlan0: RX AssocResp from <MAC 'ClearSPOT_753b7' [AC1]> (capab=0x431 status=0 aid=1)
[  482.554575] wlan0: associated
[  482.606805] wlan0: deauthenticating from <MAC 'ClearSPOT_753b7' [AC1]> by local choice (reason=2)
[  482.634435] wlan0: authenticate with <MAC 'ClearSPOT_753b7' [AC1]>
[  482.641489] wlan0: send auth to <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  482.645816] wlan0: authenticated
[  482.646062] iwlwifi 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  482.646070] iwlwifi 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  482.648364] wlan0: associate with <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  482.653709] wlan0: RX AssocResp from <MAC 'ClearSPOT_753b7' [AC1]> (capab=0x431 status=0 aid=1)
[  482.657758] wlan0: associated
[  555.538674] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  555.538683] iwlwifi 0000:08:00.0: Current SW read_ptr 37 write_ptr 39
[  555.538719] iwl data: 00000000: 00 00 00 00 00 00 00 00 60 00 00 00 00 00 00 00  ........`.......
[  555.538744] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  555.538762] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102026
[  555.538780] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  555.538797] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300010
[  555.538815] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  555.538832] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  555.538850] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  555.538868] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709009
[  555.538936] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [17,17]
[  555.539004] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  555.539075] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [37,39]
[  555.539150] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539218] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539285] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  555.539353] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  555.539421] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  555.539488] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  555.539556] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [10,10]
[  555.539624] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  555.539691] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539759] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539827] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539894] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.539962] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.540030] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.540097] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.540165] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  555.540236] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  556.306949] wlan0: authenticate with <MAC 'ClearSPOT_753b7' [AC1]>
[  556.309565] wlan0: send auth to <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  556.465391] wlan0: send auth to <MAC 'ClearSPOT_753b7' [AC1]> (try 2/3)
[  556.554910] wlan0: send auth to <MAC 'ClearSPOT_753b7' [AC1]> (try 3/3)
[  556.640919] wlan0: authentication with <MAC 'ClearSPOT_753b7' [AC1]> timed out
[  563.446371] wlan0: authenticate with <MAC 'ClearSPOT_753b7' [AC1]>
[  563.457521] wlan0: send auth to <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  563.461195] wlan0: authenticated
[  563.461446] iwlwifi 0000:08:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  563.461468] iwlwifi 0000:08:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  563.465466] wlan0: associate with <MAC 'ClearSPOT_753b7' [AC1]> (try 1/3)
[  563.471983] wlan0: RX AssocResp from <MAC 'ClearSPOT_753b7' [AC1]> (capab=0x431 status=0 aid=2)
[  563.481536] wlan0: associated

########## wireless info END ############


```
this what i've got

---

### Post by gamre2077 on 2014-11-11
hi i found and fix my problem i had to reinstall a new version of aircrack here's the link i followed in case it would help some people thks tho <snip>

---

### Post by Irihapeti on 2014-11-11
Thread closed.

From the Forums Code of Conduct:
Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---


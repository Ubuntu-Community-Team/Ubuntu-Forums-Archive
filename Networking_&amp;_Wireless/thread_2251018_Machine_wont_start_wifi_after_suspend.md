---
title: "Machine wont start wifi after suspend"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by marko17 on 2014-11-01
Good day,
I inherited a macbook pro and first thing I did is scrub Mac os and install ubuntu (clean install , no other os). Everything works, but when I close the lid (suspend) it wont wake up wifi after I reopen the lid (comes out of suspend). 

Ive tried a few things on here (looked for solution in forums) but got nowhere. 

Anyone has a similar problem? 

Marko

---

### Post by slickymaster on 2014-11-01
Hi marko17, welcome to the forums.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please [use 'Code' tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168"). It preserves the output's formatting and makes the post cleaner, compact and more readable.

---

### Post by marko17 on 2014-11-01
```
## Wireless-Info STARTprintf "\n\t======== Wireless-Info START ========\n"


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

---

### Post by marko17 on 2014-11-01
Hopefully I did that right....

---

### Post by marko17 on 2014-11-01
[http://ubuntuforums.org/showthread.php?t=2138927](http://ubuntuforums.org/showthread.php?t=2138927)

I tried following that article. didnt work. 

sudo /etc/init.d/networking restart does nothing

Interestingly sudo nmcli nm sleep false will get networking back and running (will show wifi networks) but will not connect

---

### Post by jeremy31 on 2014-11-01
> **marko17 said:**
> Hopefully I did that right....

That wasn't right, you need to find the wireless-info file to attach, you might need to run the script```
./wireless_script
```

---

### Post by marko17 on 2014-11-01
whoops...one sec

---

### Post by marko17 on 2014-11-01
```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


marko-laptop 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4750HQ CPU @ 2.00GHz
Memory : 7893 MB
Uptime : 10:56:49 up 3 min,  3 users,  load average: 0.16, 0.13, 0.05




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0134]
    Kernel driver in use: wl




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:0262 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abg  ESSID:"m&m"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 m<MAC C-NA *m<MAC ID removed>m 1>m>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface            Soft blocked  Hard blocked
0: phy0: Wireless LAN          no            no
1: brcmwl-0: Wireless LAN      no            no
2: hci0: Bluetooth             no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================o=============o========o===========o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
================o=============o========o===========o=========o===========o==============o===========
 wlan0  [m&m]   | 802.11 WiFi | wl     | connected | yes     | 130 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    DIRECT-roku-946-C2C48A: Infra, <MAC C-02 DIRECT-roku-946-C2C48A>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    internet1:       Infra, <MAC C-04 internet1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    HFlower Wedding: Infra, <MAC C-03 HFlower Wedding>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    pinkhouse:       Infra, <MAC C-NA pinkhouse 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
    Smith's:         Infra, <MAC C-NA Smith's 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WEP
    *m&m:            Infra, <MAC C-01 m<MAC C-NA *m<MAC ID removed>m 1>m>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2


    Address:         192.168.1.194
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------+-------------+--------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


AndroidAP            : ssid=AndroidAP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
cityhall-upstairs    : ssid=cityhall-upstairs | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DELTA                : ssid=DELTA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
m&m                  : ssid=m&m | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search citywest.ca




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.865/45.637/90.410/44.773 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.034/0.039/0.044/0.005 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_CA.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 m<MAC C-NA *m<MAC ID removed>m 1>m>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"m&m"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DIRECT-roku-946-C2C48A>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-946-C2C48A"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 HFlower Wedding>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HFlower Wedding"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 internet1>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"internet1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[lib80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        


[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x14e4:0x1682 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x43a0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/config.d/config]
SUSPEND_MODULES="wl"


[/etc/pm/config.d/config~]
SUSPEND_MODULES="wl"




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.13.0-34-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    2.605483] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.605719] audit: initializing netlink socket (disabled)
[    5.426736] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.428427] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    5.456314] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    5.543264] wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[    5.865981] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  220.938992] ERROR @wl_dev_intvar_get : error (-1)
[  220.938996] ERROR @wl_cfg80211_get_tx_power : error (-1)


    ======== Done ========
```

---

### Post by marko17 on 2014-11-01
Hopefully that is better. That was posted with wifi working. If you would like me to post it when wireless is not working (after suspend), please let me know

---

### Post by marko17 on 2014-11-02
anyone?

---

### Post by jeremy31 on 2014-11-09
I would delete the files you created in /etc/pm/config.d/config~
Does```
sudo /etc/init.d/networking restart
``` bring networking back after suspend?
Is your driver loaded after suspend```
lsmod | grep wl
```

---


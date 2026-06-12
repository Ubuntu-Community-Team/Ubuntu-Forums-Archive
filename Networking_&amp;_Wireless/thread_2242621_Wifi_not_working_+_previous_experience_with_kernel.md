---
title: "Wifi not working + previous experience with kernel panic - Realtek 8821AE"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by francis3 on 2014-09-02
I recently bought a Asus M51AC Desktop from Newegg. When I got the desktop, I installed Ubuntu 14.04 Trusty over the existing Windows 7. The wifi worked for a few days and all of a sudden it stopped working. In addition to that, I experienced a kernel panic when updating my kernel from 3.13.0-24.46 to 3.13.0-24.47, which caused me to reinstall Ubuntu again. 

After doing some research, I found out that my Realtek Wireless Card is a problem from some people as well. I have the RTL8821AE. 

What can I do to enable wifi to work again?

Please help. 

Thanks. 

Francis

---

### Post by praseodym on 2014-09-03
Try the mainline kernel 3.14, it should contain the driver:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)

---

### Post by francis3 on 2014-09-03
> **praseodym said:**
> Try the mainline kernel 3.14, it should contain the driver:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)

I tried updating the kernel to 3.14 and it screwed up my display. I ended up with a blank screen after login. So I loaded into tty3 and remove the kernel and now I am back to the previous kernel. 

Any other ideas?

---

### Post by francis3 on 2014-09-03
I managed to install 3.14.1 successfully without any issue but wifi is still not working. What else can I do?

---

### Post by varunendra on 2014-09-03
You can post a wireless_script report to show us a bigger picture of the problem : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by francis3 on 2014-09-04
SCRIPTDATE="2014-08-30 21:00 +0200"
FILEBASE="wireless-info"
OUTPUTDIR=$(pwd)
OUTPUTDIRFB="/tmp"
MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl)"
LSMODMATCHES="wmi"
DMESGMATCHES="(wlan[0-9]|eth[1-9]|firmware|[nN]etwork)"
DMESGEXCL="apparmor"
MODINFOEXCL="alias"
BLACKLISTEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"


export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"


if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
fi


exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt"
if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\", trying in \"%s\" instead.\n" "$OUTPUTDIR" "$OUTPUTDIRFB" >&2
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt"
    if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\" either, aborting.\n\n" "$OUTPUTDIR" >&2
    exit 1
    fi
fi
exec 2>&1


printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Script from: %s\n" "$SCRIPTDATE"


printf "\n##### release #####\n\n"
lsb_release -idrc


printf "\n##### kernel #####\n\n"
uname -srvmpio
echo
cat /proc/cmdline | sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/'


printf "\n##### desktop #####\n\n"
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


printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'


printf "\n##### lsusb #####\n\n"
lsusb


printf "\n##### PCMCIA card info #####\n\n"
pccardctl info


printf "\n##### rfkill #####\n\n"
rfkill list all


printf "\n##### lsmod #####\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"


printf "\n##### interfaces #####\n\n"
sed '/^#/d;s/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces


printf "\n##### ifconfig #####\n\n"
ifconfig | sed '/^lo[ ]/,/^$/d'


printf "\n##### iwconfig #####\n\n"
iwconfig


printf "\n##### route #####\n\n"
route -n


printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf


printf "\n##### nm-tool #####\n\n"
nm-tool


printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state


printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi


printf "\n##### iw reg get #####\n\n"
iw reg get


printf "\n##### iwlist channels #####\n\n"
iwlist chan


printf "\n##### iwlist scan #####\n\n"
if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO iwlist scan 2>&1 || echo "Acquisition of admin privileges failed.")
    trap 2 3
    if [[ $IWLISTSCAN = *Frequency:* ]]; then
    printf "Channel occupancy:\n\n"
    grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([0-9]\+\)[ ]\+/     \1   WLAPs on   /'
    echo
    fi
    grep -v '^[ ]*IE:[ ]*Unknown:' <<< "$IWLISTSCAN"
else
    echo "No way to acquire admin privileges found."
fi


printf "\n##### module infos #####\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done


printf "\n##### module parameters #####\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
    MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
    printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done


printf "\n##### /etc/modules #####\n\n"
grep -v '^#' /etc/modules


printf "\n##### blacklists #####\n\n"
for CONFFILE in $(ls /etc/modprobe.d/*.conf | egrep -v "$BLACKLISTEXCL"); do
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
    printf "[%s]\n%s\n\n" "$CONFFILE" "$BLACKLIST"
    fi
done


printf "\n##### rc.local #####\n\n"
grep -v '^#' /etc/rc.local


printf "\n##### udev rules #####\n\n"
for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
    printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done


printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.*\)\+$/\2 (repeated \1 times)/'


printf "\n########## wireless info END ############\n\n"


exec 2>&4 4>&-
exec 1>&3 3>&-


##### MAC address masking #####


RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")


ORIGIFS="$IFS"
IFS=$'\n'


LOCDEVSRAW=$(sed -n '/^[[:punct:]]\+[ ]ifconfig[ ][[:punct:]]\+/,/^[[:punct:]]\+[ ]/p' <<< "$RESULTS")
NETDEVNAMES=($(sed -n 's/^\([^ ]\+\)[ ]\+.*HWaddr.*/\1/p' <<< "$LOCDEVSRAW"))
NETDEVMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr[ ]\+\([^ ]\+\).*/\1/p' <<< "$LOCDEVSRAW"))


WLAPSRAW=$(sed -n '/^[ ]*Wireless Access Points/,/^$/p' <<< "$RESULTS")
NETDEVNAMES+=($(sed -n 's/^[ ]*\*\?\([^:]\+\):.*/\1/p' <<< "$WLAPSRAW"))
NETDEVMACS+=($(grep -o '\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]' <<< "$WLAPSRAW"))


IFS="$ORIGIFS"


for NETDEVNR in "${!NETDEVMACS[@]}"; do
    MACMASKSED+="s/${NETDEVMACS[$NETDEVNR]}/<MAC addr${NETDEVNAMES[$NETDEVNR]+ }${NETDEVNAMES[$NETDEVNR]-ess}>/I;"
done


sed "$MACMASKSED/\([[:alnum:]][[:alnum:]]:\)\{6,\}/! s/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"


##### The End #####

---

### Post by varunendra on 2014-09-04
You have posted the script itself, not the report it generates. Please read the linked post carefully and post back the report it generates... in **'Code'** tags please.

---

### Post by francis3 on 2014-09-04
My apologies. Here are the contents of the report. 

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


francisfreemanhkh-K30AD-M31AD-M51AD 3.15.0-031500rc2-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz
Memory : 15988 MB
Uptime : 22:49:14 up  4:18,  2 users,  load average: 0.21, 0.06, 0.06




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:859f]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0461:4e26 Primax Electronics, Ltd 
Bus 003 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 006: ID 13d3:3414 IMC Networks 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no
1: hci0: Bluetooth         no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8821ae             588203  0 
eeepc_wmi              13151  0 
mac80211              663883  1 rtl8821ae
asus_wmi               24697  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
cfg80211              515248  2 mac80211,rtl8821ae
wmi                    19379  1 asus_wmi
video                  19932  1 asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8821ae     (4): fwlps=N | ips=N | swenc=N | swlps=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o=======  ====o==============o=========o===========o========  ======o===========
 Interface & ID             | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=======  ====o==============o=========o===========o========  ======o===========
 wlan0                      | 802.11 WiFi | rtl8821ae | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | e1000e    | connected    | yes     | 1000 Mb/s |              | <MAC eth0>


    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
    DNS:             75.153.176.1
----------------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~


[main]
WirelessEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Alicia               : ssid=Alicia | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
TELUS0421            : ssid=TELUS0421 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search telus




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.534/0.553/0.573/0.030 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.008/0.011/0.015/0.004 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_CA.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8821ae]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
srcversion:     AC2D6BFB6A4368217108BFD
depends:        mac80211,cfg80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)


[eeepc_wmi]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     1124CB5EFC3269F50C3BDD9
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to acpi4asus-user@lists.sourceforge.net. (bool)


[mac80211]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/net/mac80211/mac80211.ko
srcversion:     AE7FF15CC48CEBF86450AA1
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[asus_wmi]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     F1B598E231F902960383641
depends:        sparse-keymap,wmi,video


[cfg80211]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/net/wireless/cfg80211.ko
srcversion:     EE81A925F8AD66571D5F75D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.15.0-031500rc2-generic/kernel/drivers/acpi/video.ko
srcversion:     D25687678246FBE9023F1F2
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modules]
rtl8821ae


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'


for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done


if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.15.0-031500rc2-generic root=UUID=1b5b2d4f-19ab-4298-9635-9d3385c799fe ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.016595] Initializing cgroup subsys net_cls
[    0.016598] Initializing cgroup subsys net_prio
[    0.479750] audit: initializing netlink subsys (disabled)
[   18.559796] wmi: Mapper loaded
[   18.748396] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.765050] asus_wmi: ASUS WMI generic driver loaded
[   18.878581] asus_wmi: Initialization: 0x0
[   18.878596] asus_wmi: BIOS WMI version: 0.9
[   18.878621] asus_wmi: SFUN value: 0x0
[   18.878833] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[   18.879726] asus_wmi: Disabling ACPI video driver
[   19.085859] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[   19.085865] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[   19.086571] rtl8821ae 0000:03:00.0: enabling device (0000 -> 0003)
[   19.086638] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7100000 len:00004000 flags:00140204, after map:0xffffc90005bb8000
[   19.086650] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[   19.086651] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 3:0:0:10ec:0
[   19.086652] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:lin  k_ctl_reg:amd 0:28:1:8086:40:40:0
[   19.086676] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[   19.099627] rtl8821ae: 
[   19.099735] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[   19.099738] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[   19.099739] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[   19.164670] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[   19.164672] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[   19.164673] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[   19.164830] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[   19.164831] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[   19.164843] WARNING: CPU: 0 PID: 394 at /home/apw/COD/linux/net/wireless/reg.c:1508 wiphy_apply_custom_regulatory+0xbc/0xe0 [cfg80211]()
[   19.164844] Modules linked in: ghash_clmulni_intel snd_hwdep snd_pcm aesni_intel rtl8821ae(C+) snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd snd_seq_device eeepc_wmi mac80211 asus_wmi snd_timer mei_me sparse_keymap lp cfg80211 snd drm parport mei lpc_ich soundcore wmi soc_button_array serio_raw video microcode mac_hid e1000e ahci psmouse libahci ptp pps_core
[   19.164879]  [<ffffffffa03305a0>] ? rtl_regd_init+0x310/0x310 [rtl8821ae]
[   19.164892]  [<ffffffffa03305a0>] ? rtl_regd_init+0x310/0x310 [rtl8821ae]
[   19.164896]  [<ffffffffa03303e2>] rtl_regd_init+0x152/0x310 [rtl8821ae]
[   19.164902]  [<ffffffffa032b771>] rtl_init_core+0x41/0x170 [rtl8821ae]
[   19.164908]  [<ffffffffa033f7bd>] rtl_pci_probe+0x28d/0x920 [rtl8821ae]
[   19.164938]  [<ffffffffa043602b>] rtl8821ae_module_init+0x2b/0x1000 [rtl8821ae]
[   19.223774] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.224277] rtlwifi: wireless switch is on
[   19.224288] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[   21.209118] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.065611] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[   22.071229] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 29198 
[   22.071231] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(18), Signature(0x2101),Size(32)
[   22.084600] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[   22.114171] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[   22.114173] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[   22.114174] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[   22.114175] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[   22.114176] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[   22.114177] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   22.114178] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   22.114178] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   22.114179] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[   22.114180] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[   22.114181] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[   22.114182] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[   22.114183] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   22.114184] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   22.114185] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   22.214769] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   22.214804] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[   22.214808] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[   22.215049] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[   22.215056] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[   22.215488] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.896354] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   24.300939] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   45.421752] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   46.826341] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   46.826584] wlan0: authenticate with <MAC ID removed>
[   46.826993] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   46.827041] wlan0: send auth to <MAC ID removed> (try 1/3)
[   46.827046] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   47.810720] wlan0: send auth to <MAC ID removed> (try 2/3)
[   47.810728] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   48.823159] wlan0: send auth to <MAC ID removed> (try 3/3)
[   48.823167] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   49.811596] wlan0: authentication with <MAC ID removed> timed out
[   49.819719] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   50.535891] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   51.940480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   57.562805] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   58.967411] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   64.593724] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   65.998348] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   69.679625] rtl8821ae-0:_rtl_pci_interrupt():<10000-1> rx descriptor unavailable!
[   69.679630] rtl8821ae-0:_rtl_pci_interrupt():<10000-1> rx overflow !
[   70.660265] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   72.064872] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   73.657540] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   75.062121] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   83.649711] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   85.054287] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   85.054512] wlan0: authenticate with <MAC ID removed>
[   85.054906] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   85.054957] wlan0: send auth to <MAC ID removed> (try 1/3)
[   85.054962] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   85.862649] wlan0: send auth to <MAC ID removed> (try 2/3)
[   85.862670] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   86.863029] wlan0: send auth to <MAC ID removed> (try 3/3)
[   86.863037] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   87.851434] wlan0: authentication with <MAC ID removed> timed out
[   87.859528] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   88.975935] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   90.380493] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   95.998863] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   97.403464] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  103.021795] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  104.426382] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  108.672166] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  110.076743] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  111.673404] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  113.085971] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  134.687001] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  136.091584] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  152.382394] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  153.786982] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  159.409316] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  160.813913] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  166.436271] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  167.840846] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  173.463165] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  174.867794] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  177.700962] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  179.105551] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  180.702213] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  182.106800] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  203.711817] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  205.116408] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  236.725596] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  238.130187] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  242.868144] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  244.272741] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  249.895092] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  251.299691] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  256.926001] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  258.330627] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  263.948970] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  265.353545] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  267.742543] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  269.147129] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  270.739774] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  272.144365] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  293.749394] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  295.153980] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  307.535147] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  308.939747] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  314.558075] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  315.962680] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  318.175588] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  319.580191] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  321.761083] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  323.165671] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  340.981107] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  342.385698] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  353.654408] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  355.058982] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  360.681324] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  362.085913] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  367.708258] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  369.112843] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  374.731199] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  376.135794] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  378.848909] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  380.253496] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  381.786147] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  383.190725] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  404.799739] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  406.204343] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  437.809516] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  439.214103] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  480.827469] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  482.232058] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  533.849597] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  535.254187] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  596.879902] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  598.284498] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  659.902205] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  661.306793] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  722.932510] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  724.337098] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  785.954812] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  787.359419] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  848.985115] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  850.389704] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  912.007419] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  913.412012] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  975.037724] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  976.442314] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1038.060026] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1039.464615] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1101.090332] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1102.494927] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1164.112634] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1165.517221] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1227.142937] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1228.547547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1290.165241] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1291.569830] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1353.195547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1354.600136] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1416.217848] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1417.622442] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1479.248153] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1480.652739] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1542.270454] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1543.675043] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1605.300760] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1606.705368] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1668.323063] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1669.727649] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1731.349365] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1732.753960] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1794.375669] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1795.780276] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1857.405975] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1858.810578] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1920.428276] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1921.832868] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1983.454579] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1984.859166] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2046.480884] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2047.885473] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2109.511189] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2110.915778] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2172.533492] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2173.938085] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2235.563796] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2236.968384] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2298.586097] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2299.990705] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2361.616403] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2363.020999] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2424.638705] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2426.043292] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2487.669009] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2489.073600] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2550.691313] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2552.095901] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2613.721618] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2615.126206] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2676.743920] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2678.148509] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2739.774225] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2741.178818] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2802.796527] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2804.201136] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2865.826831] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2867.231419] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2928.849134] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2930.253721] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 2991.879439] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 2993.284035] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3054.901741] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3056.306336] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3117.932046] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3119.336647] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3180.954348] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3182.358956] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3243.984652] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3245.389261] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3307.006956] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3308.411544] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3370.037261] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3371.441856] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3433.059563] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3434.464163] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3496.089869] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3497.494473] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3559.112169] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3560.516746] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3622.142477] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3623.547062] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3685.164777] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3686.569379] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3748.195082] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3749.599678] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3811.217384] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3812.621979] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3874.247690] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3875.652293] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3937.269992] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3938.674611] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4000.300297] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4001.704891] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4063.322599] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4064.727188] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4126.352904] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4127.757494] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4189.375210] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4190.779806] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4252.405511] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4253.810101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4315.427812] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4316.832411] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4378.454115] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4379.858705] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4441.480420] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4442.885029] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4504.510725] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4505.915327] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4567.533028] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4568.937622] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4630.563334] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4631.967920] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4693.585634] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4694.990234] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4756.615939] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4758.020546] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4819.638242] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4821.042830] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4882.668547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4884.073142] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 4945.690849] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 4947.095443] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5008.721154] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5010.125747] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5071.743459] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5073.148047] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5134.773759] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5136.178356] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5197.796062] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5199.200667] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5260.826368] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5262.230963] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5323.848669] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5325.253273] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5386.878976] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5388.283562] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5449.901277] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5451.305878] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5512.931610] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5514.336191] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5575.953885] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5577.358480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5638.984190] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5640.388784] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5702.006492] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5703.411086] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5765.036796] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5766.441405] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5828.059099] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5829.463700] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5891.089405] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5892.493999] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 5954.111706] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 5955.516294] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6017.142011] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6018.546620] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6080.164315] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6081.568921] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6143.194618] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6144.599206] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6206.216921] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6207.621514] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6269.247226] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6270.651821] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6332.269527] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6333.674127] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6395.299833] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6396.704423] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6458.322135] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6459.726729] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6521.352441] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6522.757035] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6584.374742] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6585.779349] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6647.405047] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6648.809648] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6710.427349] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6711.831944] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6773.457655] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6774.862247] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6836.479955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6837.884564] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6899.510263] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6900.914852] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 6962.532564] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 6963.937151] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7025.562869] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7026.967456] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7088.585172] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7089.989770] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7151.615476] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7153.020063] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7214.637777] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7216.042365] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7277.664081] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7279.068669] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7340.690385] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7342.094984] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7403.720690] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7405.125278] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7466.742992] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7468.147578] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7529.773299] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7531.177883] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7592.795600] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7594.200186] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7655.821903] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7657.226490] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7718.848206] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7720.252814] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7781.874510] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7783.279097] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7844.900813] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7846.305403] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7907.931119] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7909.335713] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 7970.953422] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 7972.358011] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8033.983727] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8035.388322] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8097.006028] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8098.410636] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8160.036334] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8161.440920] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8223.058635] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8224.463229] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8286.088941] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8287.493548] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8349.111236] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8350.515850] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8412.141548] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8413.546151] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8475.163849] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8476.568458] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8538.194155] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8539.598743] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8601.216457] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8602.621042] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8664.246760] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8665.651354] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8727.269065] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8728.673667] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8790.299371] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8791.703957] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8853.321672] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8854.726267] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8916.351977] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8917.756552] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 8979.374278] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 8980.778881] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9042.400567] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9043.805178] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9105.426885] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9106.831447] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9146.355968] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9147.760562] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9168.453189] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9169.857791] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9231.479494] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9232.884083] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9294.513771] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9295.918389] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9357.532101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9358.936670] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9420.562391] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9421.966984] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9483.584709] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9484.989287] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9487.654406] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9489.062998] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9494.681332] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9496.085923] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9501.708272] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9503.112872] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9508.739196] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9510.147790] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9512.600818] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9514.005405] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9515.598068] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9517.002655] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9538.607671] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9540.012249] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9571.625451] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9573.030007] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9614.639403] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9616.044010] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9667.665534] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9669.070127] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9730.687835] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9732.092437] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9793.718138] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9795.122725] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9856.740429] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9858.145032] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9919.766730] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9921.171340] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 9982.793043] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 9984.201651] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10045.823356] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10047.227948] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10108.845667] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10110.250244] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10171.871958] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10173.276561] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10234.898263] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10236.302854] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10297.928569] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10299.333157] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10360.950870] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10362.355475] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10423.981175] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10425.385769] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10487.003477] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10488.408064] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10550.029781] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10551.434370] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10613.056085] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10614.460687] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10676.086375] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10677.490987] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10739.108693] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10740.513279] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10802.134995] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10803.539579] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10865.161299] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10866.565885] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10928.191604] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10929.596198] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[10991.213906] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[10992.618480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11054.244212] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11055.648800] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11117.266513] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11118.671099] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11180.296818] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11181.701418] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11243.319120] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11244.723707] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11306.349425] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11307.754017] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11369.371727] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11370.776315] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11432.402034] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11433.806634] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11495.424336] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11496.828934] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11558.454639] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11559.859240] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11621.476942] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11622.881549] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11684.507247] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11685.911836] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11747.529549] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11748.934136] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11810.559854] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11811.964443] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11873.582155] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11874.986759] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11936.608460] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[11938.013047] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[11999.634763] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12001.039351] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12062.665072] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12064.069669] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12125.687370] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12127.091956] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12188.717676] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12190.122274] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12251.739978] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12253.144578] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12314.770283] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12316.174864] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12377.792584] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12379.197187] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12440.822891] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12442.227480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12503.845192] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12505.249793] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12566.875498] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12568.280099] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12629.897799] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12631.302385] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12692.928106] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12694.332676] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12755.950407] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12757.354995] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12818.980712] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12820.385293] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12882.003014] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12883.407601] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[12945.033318] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[12946.437905] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13008.055629] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13009.460229] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13071.085924] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13072.490531] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13134.108228] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13135.512816] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13197.138535] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13198.543120] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13260.160835] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13261.565435] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13323.191140] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13324.595740] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13386.213444] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13387.618029] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13449.243748] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13450.648333] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13512.266051] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13513.670636] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13575.296355] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13576.700955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13638.318656] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13639.723270] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13701.348961] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13702.753557] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13764.371264] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13765.775839] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13827.401569] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13828.806174] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13890.423872] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13891.828439] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[13953.454176] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[13954.858775] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14016.476477] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14017.881073] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14079.506783] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14080.911370] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14142.529086] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14143.933685] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14205.559390] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14206.963977] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14268.581693] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14269.986283] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14331.611998] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14333.016585] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14394.634300] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14396.038875] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14457.664605] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14459.069191] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14520.686908] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14522.091503] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14583.717211] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14585.121811] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14646.739504] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14648.144114] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14709.769819] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14711.174423] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14772.792120] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14774.196707] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14835.818426] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14837.223015] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14898.844728] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14900.249329] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[14961.875034] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[14963.279617] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15024.897336] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15026.301930] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15087.927641] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15089.332228] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15150.949943] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15152.354544] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15213.980249] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15215.384849] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15277.002550] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15278.407131] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15340.032855] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15341.437442] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15403.055157] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15404.459758] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[15466.085461] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[15467.490049] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G


    ======== Done ========

```

---

### Post by praseodym on 2014-09-04
On which channel does the router send? Which country do you live?

---

### Post by francis3 on 2014-09-04
> **praseodym said:**
> On which channel does the router send? Which country do you live?


```
       
3                     Frequency:2.412 GHz (Channel 1)3                     Frequency:2.437 GHz (Channel 6)

```

I live in Canada.

---

### Post by praseodym on 2014-09-04
Do you get an IP address?
```

ifconfig -a
arp -v
```

---

### Post by francis3 on 2014-09-04
I don't believe so. 

ifconfig -a gave me
```

wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:bc:14:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

arp -v gave me just one entry for the wired connection.

---

### Post by praseodym on 2014-09-04
Unplug the cable and check
```

sudo dhclient wlan0
ifconfig wlan0
iwconfig wlan0
```

---

### Post by francis3 on 2014-09-04
sudo dhclient wlan0 gave me nothing

ifconfig wlan0
```

wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:bc:14:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

---

### Post by varunendra on 2014-09-05
Just curious - is your router a dualband one? Are 2.4 GHz and 5 GHz both enabled? If yes, I thing you should try disabling 5 GHz mode and try 2.4 GHz only. The change may require a reboot on both the router and the laptop to take effect properly.

Additionally, try explicitly setting the country code for regdomain settings -
```
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
sudo iw reg set CA
```

---

### Post by francis3 on 2014-09-05
I don't think it's dualband. Here is the info on the modem router. 

[http://www.actiontec.com/191.html](http://www.actiontec.com/191.html)

---

### Post by varunendra on 2014-09-06
Hmm.. indeed it doesn't look like it can do dualband, not sure why the driver is going crazy about the 2.4/5GHz modes.

Anyway, looking at the router's manual gave me some more ideas -

**1)** Make sure 'WMM' is disabled. Evidently it is often a cause of troubles, although those troubles are 'slow speeds', not connection failure altogether.
**2)** Try 20 MHz channel width if it is set to 40 MHz.

And did you set the Regdomain code to 'CA' as suggested? Make sure the region in the router is also set to 'Canada'.

---

### Post by francis3 on 2014-09-07
Ok. WMM has been disabled. I was able to connect briefly but then the signal dropped again when the modem was restarting after I disable WMM. Channel is now at 20 MHz. 

And yes, I've set the Regdomain to CA.

---

### Post by varunendra on 2014-09-07
> **francis3 said:**
> I was able to connect briefly but then **the signal dropped again when the modem was restarting** after I disable WMM.

Obviously it would disconnect when the modem _is restarting_, but could you connect again when it got up and ready again? After a system (laptop) reboot?

Sorry for asking the obvious, but my experience has taught me that it is sometimes the obvious that needs to be cross-checked first, and then sometimes there is nothing else to check next. :)

---

### Post by francis3 on 2014-09-16
Hi Varun, 

The whole modem was changed and now the wifi works again. I haven't experienced any drop since. I am going to mark this as solved. 

Thank you all so much for your help. =)

---


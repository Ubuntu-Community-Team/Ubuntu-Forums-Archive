---
title: "WiFi not Working on 12.04 LTS"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by joginder2 on 2014-02-09
Hi wifi list is not showing on 12.04 LTS.

---

### Post by joginder2 on 2014-02-09
<code>
MODMATCHES="(air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|8192cu|8192du|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** PCMCIA Card Info *****\n\n"
pccardctl info
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
        printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
    fi
    fi
done
printf "\n***** modinfo *****\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done
printf "\n***** udev rules *****\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi




</code>

---

### Post by joginder2 on 2014-02-09
eth0      Link encap:Ethernet  HWaddr 74:86:7a:2e:d0:e6  
          inet addr:27.7.216.195  Bcast:27.7.223.255  Mask:255.255.248.0
          inet6 addr: fe80::7686:7aff:fe2e:d0e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32327004 (32.3 MB)  TX bytes:4821229 (4.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:210952 (210.9 KB)  TX bytes:210952 (210.9 KB)

---


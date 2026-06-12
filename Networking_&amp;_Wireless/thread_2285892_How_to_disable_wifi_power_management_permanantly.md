---
title: "How to disable wifi power management permanantly"
date: 2015-07-08
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2015-07-08
Since installing Ubuntu 15.04 on my hp netbook wifi has been disconnecting sporadically. After looking into the issue turns out that the culprit is power management. The problem disappears if I disable power management from the terminal.The netbook doesn't have a battery but it is of course plugged into AC, so I have no idea why power management would kick in (unstable AC outlet?)  I am looking for a way to do it permanently but all the sources I can get from google are quite old.

There is a file called /usr/lib/pm-utils/power.d/wireless I suppose I have to somehow edit it but I am not sure how

```
#!/bin/sh

. "${PM_FUNCTIONS}"

# See if we have the usual wireless tools.
# Do not just fail because not all cards require these.
which iwpriv >/dev/null 2>&1 && have_iwpriv="true"
which iwconfig >/dev/null 2>&1 && have_iwconfig="true"

# If only all the drivers did The Right Thing with iwconfig power.
# Too bad they do not.

get_wireless_params() {
    # $1 = interface 
    # $2 = on or off
    unset iwpriv iwconfig iwlevel
    
    # Don't do anything if we cannot find a driver for this iface.
    [ -L "/sys/class/net/$1/device/driver" ] || return 1
    # Skip if not a wireless card.
    [ -d "/sys/class/net/$1/wireless" ] || return 1
    # Also don't do anything if the device is disabled
    [ "$(cat /sys/class/net/$1/device/enabled)" = "1" ] || return 1
    driver="$(readlink "/sys/class/net/$1/device/driver")"
    driver=${driver##*/}
    case $driver in
        ipw2100) iwpriv_ac="set_power 0"
            iwpriv_batt="set_power 5"
            iwconfig_ac="power on"
            iwconfig_batt="power on";;
        ipw3945)
            iwpriv_ac="set_power 6"
            iwpriv_batt="set_power 7";;
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=3
              else
                 iwconfig_ac="power off"
                 iwconfig_batt="power on"
              fi;;
        *) iwconfig_ac="power off"
           iwconfig_batt="power on";;
    esac
    case $2 in
        off) [ "$iwpriv_ac" ] && iwpriv="$iwpriv_ac"
            [ "$iwconfig_ac" ] && iwconfig="$iwconfig_ac"
            [ "$iwlevel_ac" ] && iwlevel="$iwlevel_ac";;
        on) [ "$iwpriv_batt" ] && iwpriv="$iwpriv_batt"
            [ "$iwconfig_batt" ] && iwconfig="$iwconfig_batt"
            [ "$iwlevel_batt" ] && iwlevel="$iwlevel_batt";;
    esac
    return 0
}

wireless_powersave() {
    for dev in /sys/class/net/*; do
        get_wireless_params "${dev##*/}" "$1" || continue
    ret=0
    printf "Turning powersave for %s %s..." "${dev##*/}" "$1"
    if [ "$have_iwconfig" = true -a "$iwconfig" ]; then
        iwconfig "${dev##*/}" $iwconfig || ret=1
    fi
        if [ "$have_iwpriv" = true -a "$iwpriv" ]; then
        iwpriv "${dev##*/}" $iwpriv || ret=1
    fi
        if [ "$iwlevel" ]; then
        echo "$iwlevel" > "$dev/device/power_level" || ret=1
    fi
    [ "$ret" -eq 0 ] && echo Done. || echo Failed.
    done
}

case $1 in
    true) wireless_powersave on ;;
    false) wireless_powersave off ;;
    *) exit $NA ;;
esac

exit 0

```

Thanks for any help in advance.

---

### Post by vilson on 2015-07-09
Same problem here, also ubuntu 15.04 on an HP (Broadcom BCM43142). I've tried everything but wifi power management keeps turning on.
If the laptop is idling and i'm gonna use it again the wifi is connected but i can't open anything and all active downloads have stopped, i have to reconnect to access internet. After this when i do "iwconfig wlan0" power management is "on" again.

---

### Post by v3.xx on 2015-07-09
I wonder if rc.local is the answer.

[http://ubuntuforums.org/showthread.php?t=1844722](http://ubuntuforums.org/showthread.php?t=1844722)

---

### Post by vilson on 2015-07-09
tried that...at startup, power management is "off" indeed, but when the laptop is idling and shuts down the screen, stops all network activity and power management comes back "on".

---


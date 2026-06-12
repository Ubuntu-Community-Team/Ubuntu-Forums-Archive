---
title: "Asus k46C, Ubuntu 12.04 LTS WiFi doesn't work [SOFT BLOCKED]"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by Mercurio_Cadena on 2014-07-09
Hello.

Once again a newbie crashing the forum =(.

I have an Asus K46C and I use Ubuntu 12.04 LTS (64 bits). 

I cannot unblock my Wireless LAN, no matter how much I try all of Google solutions.

I have seen that there is a solution in this Community, but it refers to hard block. My problems has to do with soft block.

This is the result of typing rfkill list all in my terminal:

0: phy0: Wireless LAN
Soft blocked: yes.
Hard blocked: no. 

1: asus-wlan: Wireless LAN.
Soft blocked: yes.
Hard blocked: no.

2: asus-bluetooth: Bluetooth.
Soft blocked: no.
Hard blocked: no.

3: hcio: Bluetooth
Soft blocked: no.
Hard blocked: no. 

I have already tried many commands to solve this, such as sudo rfkill unblock all, rfkill unblock 0, and rfkill unblock 1. None of them worked.

I have also seen a community post refering to some sort of informational procedure ([http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)). The problem is I do not understand the procedure. I'm sure it must be a common, easy-to-follow procedure, but I am a hardcore newbie...

I can connect to the internet through an Ethernet conection, but I need to connect through Wireless in my job. 

Please help! I've been dealing with this for a while, and I'm starting to freak out.

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep "Eth\|Net" -A2

---

### Post by varunendra on 2014-07-13
Welcome to the forums Mercurio_Cadena!

I'll try to make the instructions to download and run the wireless script a bit clearer. It is almost the same process as you saw in the thread post you mentioned, just uses a newer script which is experimental yet, but provides extra information which is very helpful sometimes. So here are the instructions -

**1)** Please right-click **[this link]("https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script")** > click "Save Link As" (or whatever similar option your browser gives) to download the wireless_script (newer, experimental version).

**2)** By default this script would get downloaded into the "Downloads" directory within your 'Home' directory. If not, find it where it got downloaded (it's name would be "wireless_script" or "wireless_script.txt" depending on which browser you used to download it. Original file name is "wireless_script", but browsers like 'chromium' may automatically append ".txt" after its name). When found, copy it onto your Desktop.

**3)** Now open a terminal (by pressing Ctrl-Alt-T, or by finding it in applications menu) and enter (or copy-paste using mouse cursor) the following commands in it -
```
cd Desktop
bash ./wireless_script
```
(if the name of the downloaded script file is "wireless_script.txt", use that name instead in the second command. E.g., "bash ./wireless_script.txt")

**4)** Carefully watch the messages on the terminal window, and type your login password when asked (you won't see anything on the terminal while typing, just type it correctly and press 'Enter'). When the script finishes its task, it will create a file named "wireless-info.txt" or "wireless-info.tar.gz" on your Desktop. Either copy-paste its contents here or attach that file itself in your next post here.

This report is not necessary to troubleshoot wireless problems, but it definitely makes it a lot easier by providing most of the useful info at once.

---

### Post by Mercurio_Cadena on 2014-07-13
Hi Varun!

Thanks a lot man. That was very clear =)

Here's my info. Please let me know if it's enough:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Hachege-K46CM 3.5.0-52-generic x86_64,  Ubuntu 12.04.4 LTS, precise

CPU    : Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
Memory : 5856 MB
Uptime : 21:34:25 up  1:45,  1 user,  load average: 0.18, 0.22, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2c97]
    Kernel driver in use: ath9k
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:5165 IMC Networks 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: phy0: Wireless LAN             yes           no
1: asus-wlan: Wireless LAN        yes           no
2: asus-bluetooth: Bluetooth      yes           no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

asus_nb_wmi            12711  0 
asus_wmi               24457  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
ath9k                 133223  0 
mac80211              555318  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399752  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
mxm_wmi                13022  1 nouveau
cfg80211              208382  3 ath9k,mac80211,ath
wmi                    19257  3 asus_wmi,nouveau,mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
ath9k         (4): blink=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
ath9k_hw      (1): force_new_ani=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o==============o=========o===========o==============o===========
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
================o======o========o==============o=========o===========o==============o===========
                |      |        |              |         |           |              |           
----------------+------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

arris54              : ssid=arris54 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Cielito Michoacan    : ssid=Cielito Michoacan | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Comunidad_ITAM       : ssid=Comunidad_ITAM | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
CQ MICHOACAN         : ssid=CQ MICHOACAN | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CQ PLAZA JUAREZ      : ssid=CQ PLAZA JUAREZ | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CQ REFORMA           : ssid=CQ REFORMA | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Delicias             : ssid=Delicias | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
El-PENDULO           : ssid=El-PENDULO | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ETN                  : ssid=ETN | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ETN 6003             : ssid=ETN 6003 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FCE-WiFi             : ssid=FCE-WiFi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
GALAXYGRAND0044      : ssid=GALAXYGRAND0044 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
IhopWTC_Terraza      : ssid=IhopWTC_Terraza | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
INFINITUM03876F      : ssid=INFINITUM03876F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUM0768        : ssid=INFINITUM0768 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUM0fd2        : ssid=INFINITUM0fd2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUM1620        : ssid=INFINITUM1620 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUM59D15D      : ssid=INFINITUM59D15D | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUM78E2        : ssid=INFINITUM78E2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUMCB29        : ssid=INFINITUMCB29 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUMcpm4        : ssid=INFINITUMcpm4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUMD6A6        : ssid=INFINITUMD6A6 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUMdt28        : ssid=INFINITUMdt28 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INFINITUMf2b3        : ssid=INFINITUMf2b3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
infinitum movil      : ssid=infinitum movil | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
INFINITUMmvum        : ssid=INFINITUMmvum | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
INGRIDTAPIA          : ssid=INGRIDTAPIA | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
iPhone               : ssid=iPhone | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
itam_guest           : ssid=itam_guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ITAM-OFFICE          : ssid=ITAM-OFFICE | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LasAlitasInsurgentes : ssid=LasAlitasInsurgentes | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
La Vid Argentina Clientes : ssid=La Vid Argentina Clientes | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
NONSOLO              : ssid=NONSOLO | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
pepe                 : ssid=pepe | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Pinguino             : ssid=Pinguino | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
PINSP                : ssid=PINSP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
PPLUS 6280A          : ssid=PPLUS 6280A | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
RUTA CAFE            : ssid=RUTA CAFE | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
shark                : ssid=shark | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Starbucks            : ssid=Starbucks | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TEACONNECTION        : ssid=TEACONNECTION | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Teavana Anatara      : ssid=Teavana Anatara | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
wiffi plus 5955      : ssid=wiffi plus 5955 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WiFi PPLUS 5869B     : ssid=WiFi PPLUS 5869B | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WiFi PPLUS 6967      : ssid=WiFi PPLUS 6967 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WLAN_ITAM            : ssid=WLAN_ITAM | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.15.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

--- 192.168.15.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.560/0.569/0.579/0.025 ms

--- 192.168.15.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.485/0.531/0.578/0.051 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : es_MX.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist acer-wmi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.5.0-52-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     C8BAA1E567FF833D1510BA6
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.5.0-52-generic/kernel/net/mac80211/mac80211.ko
srcversion:     BEC330950D8489DA9D7A071
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath9k_common]
filename:       /lib/modules/3.5.0-52-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     1673D73171C827FC143E431
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.5.0-52-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     D2CC7E665A1FF9DC10231D9
depends:        ath
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

[ath]
filename:       /lib/modules/3.5.0-52-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     8C339DF4D303827C9304BB0
depends:        cfg80211

[cfg80211]
filename:       /lib/modules/3.5.0-52-generic/kernel/net/wireless/cfg80211.ko
srcversion:     74571C7FA6F4E9D34760CDF
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Not Default

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

BOOT_IMAGE=/boot/vmlinuz-3.5.0-52-generic root=UUID=ae6a5c37-d00b-49d7-8a90-e9141a9084a2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.649155] audit: initializing netlink socket (disabled)
[    1.909242] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   19.989661] wmi: Mapper loaded
[   20.054126] ath: EEPROM regdomain: 0x60
[   20.054130] ath: EEPROM indicates we should expect a direct regpair map
[   20.054133] ath: Country alpha2 being used: 00
[   20.054135] ath: Regpair used: 0x60
[   20.084987] Registered led device: ath9k-phy0
[   20.306179] asus_wmi: ASUS WMI generic driver loaded
[   20.306520] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   20.306626] asus_wmi: SFUN value: 0x4a0877<6>[   20.307763] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[   20.347235] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   20.400833] asus_wmi: Backlight controlled by ACPI video driver
[   20.686748] init: network-manager main process (1024) terminated with status 127
[   20.686779] init: network-manager main process ended, respawning
[   20.701709] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.798620] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)

    ======== Done ========
```

---

### Post by Elfy on 2014-07-14
@ Mercurio_Cadena 

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

thanks

---

### Post by varunendra on 2014-07-14
@Mercurio_Cadena,

Do you get any messages when you run the following command -
```
sudo rfkill unblock all
```..in a terminal? If yes, please post back the messages here. If none, please post back the following output -
```
ps -Af | grep -i network
```

And in the meanwhile, please try -

```
sudo chmod -x /etc/pm/power.d/wireless
```
followed by a reboot, and ..
```
sudo rfkill unblock all
```
command after the reboot. Does it remove the soft block?

While posting the outputs, please use 'Code' tags like elfy requested. To see a quick guide with screenshots, please follow the "Use Code Tags" link in my signature below. :)

---

### Post by Mercurio_Cadena on 2014-07-15
Thank you Elfy! Will do.

---

### Post by Mercurio_Cadena on 2014-07-15
@Varunendra:

```

sudo rkill unblock all

```
This command does not generate any kind of message =(.

_____

This is the output you asked me for:
```

ps -Af | grep -i network
3068 1859 0 15:27 pts/1    00:00:00 grep --color=auto -i network

``` 


And finally, the codes and reboots you suggested at the end of your post didn't work =/.

---

### Post by varunendra on 2014-07-15
> **Mercurio_Cadena said:**
> This is the output you asked me for:
```

ps -Af | grep -i network
3068 1859 0 15:27 pts/1    00:00:00 grep --color=auto -i network

```
..which means the NetworkManager has crashed and not running anymore. Please try running it manually and see what happens -
```
sudo service network-manager stop
sudo service network-manager start
```
You may ignore any error messages that the first command (..stop) returns. But if the second one returns any errors, please post them back here.

If no errors, please check again -
```
ps -Af | grep -i network
```
You should get, among some other lines, something like this -
```
root      1116     1  0 Jul15 ?        00:00:00 **NetworkManager**
```
If not, we have a deeper problem. If yes, is the network enabled or can be enabled now with "rfkill unblock all"?

---

### Post by Mercurio_Cadena on 2014-07-15
I think we have a deeper problem. I tried to run it manually; it didn't show any error. 

But, after

```

ps -Af | grep -i network

```

I got

```

2867 1895 0 17:56 pts/2 00:00:00 grep --color=auto -i network

```

So... no idea what to do...

---

### Post by varunendra on 2014-07-16
I am a bit short of time at the moment, so can you please do a test for me?

If you have or can create a live USB or DVD, try it in live session and let me know if the networking works in it. You can use the same commands to confirm whether the 'NetworkManager' is running or not in it.

---

### Post by Mercurio_Cadena on 2014-07-16
I am pleased to inform you that I am writing this post from a WiFI connection =).


Yet, mi solution was rather radical. I reinstalled Ubuntu (I had 12.04 and I got 14.04; so at least I got an upgrade). I really needed to recover my WiFi conection.

And it worked... although I'm afraid it might happen again. But the issue is solved, for now. 

Does this qualify as a solved thread?

Thank you so much for all your effort =).

---

### Post by varunendra on 2014-07-17
> **Mercurio_Cadena said:**
> I reinstalled Ubuntu (I had 12.04 and I got 14.04; so at least I got an upgrade). I really needed to recover my WiFi conection.

And it worked... although I'm afraid it might happen again. But the issue is solved, for now. 

**Does this qualify as a solved thread?**

I believe it does.

NetworkManager service crashing is not normal or usual - it indicates a strong possibility of a broken install/upgrade of a package or the whole OS. My next suggestion would have been to completely remove and reinstall the network-manager-gnome package, failing which my last suggestion would have been to do a fresh install of the whole OS anyway. :)

---

### Post by Mercurio_Cadena on 2014-07-18
Thanks a lot @varunendra =)

---

### Post by varunendra on 2014-07-18
Thanks for free credits! You didn't need any help for the solution that worked. :p

---


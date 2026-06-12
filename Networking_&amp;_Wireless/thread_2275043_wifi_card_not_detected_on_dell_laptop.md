---
title: "wifi card not detected on dell laptop"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by Hari_K on 2015-04-23
I have a Dell Inspiron 3537 with Qualcomm Atheros Card. I tried installing ath9k from backports as suggested in several forums. My card is STILL not detected. This is what I got after the wireless_script mentioned [http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222) 

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

hari-k-Inspiron-3537 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 7865 MB
Uptime : 06:51:23 up 30 min,  2 users,  load average: 0.13, 0.18, 0.20


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 004: ID 064e:812e Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                  91958  0 
ath9k_common           15983  1 ath9k
ath9k_hw              424573  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              540466  1 ath9k
cfg80211              498848  4 ath,ath9k_common,ath9k,mac80211
compat                 14261  4 cfg80211,ath9k_common,ath9k,mac80211
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
wmi                    19177  1 dell_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): 
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.726/1.263/1.801/0.538 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.016/0.028/0.041/0.013 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.15.9-0-g0617859) using backports v3.15.9-1-0-g3c01584
srcversion:     84DCC5AD18A6CD60DD897CB
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.15.9-0-g0617859) using backports v3.15.9-1-0-g3c01584
srcversion:     66AA9C1A5DA6517CE5DA146
depends:        compat,cfg80211,ath9k_hw,ath

[ath9k_hw]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     F18F6522E60CD2311A3675C
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-24-generic/updates/drivers/net/wireless/ath/ath.ko
srcversion:     62CCE3A0B4A1CC9207A10E0
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/mac80211/mac80211.ko
version:        backported from Linux (v3.15.9-0-g0617859) using backports v3.15.9-1-0-g3c01584
srcversion:     CD54D090E9DCB6CB0B870CF
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.15.9-0-g0617859) using backports v3.15.9-1-0-g3c01584
srcversion:     34D5EE52DD97EB3AF084436
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.13.0-24-generic/updates/compat/compat.ko
version:        backported from Linux (v3.15.9-0-g0617859) using backports v3.15.9-1-0-g3c01584
srcversion:     3585E30CED1C59C4BE78CE7
depends:        
parm:           backported_kernel_name:The kernel tree name that was used for this backport (Linux) (charp)
parm:           backported_kernel_version:The kernel version that was used for this backport (v3.15.9-0-g0617859) (charp)
parm:           backports_version:The git version of the backports tree used to generate this backport (v3.15.9-1-0-g3c01584) (charp)

[dell_wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=046bf0a9-516b-4b82-bcb1-ec991754e2d1 ro quiet splash video.use_native_backlight=1 vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.274031] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.274430] audit: initializing netlink socket (disabled)
[    1.932732] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   15.655385] wmi: Mapper loaded
[   19.107930] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  254.571682] dell_wmi: Unknown key e00e pressed
[  257.753887] dell_wmi: Unknown key e00e pressed

    ======== Done ========

```

---

### Post by kc1di on 2015-04-24
The wireless script shows no Wireless card installed.  Are you sure it's turned on in Bios or is there a switch to manually turn it on?

Otherwise there is no wiresles card present. 

you could try this from a teminal:```
rfkill list all
``` and post the results here , though the script did that it did not show any cards.
also try this ```
rfkill unblock all
```
good luck

P.S. on my Dell the wireless card switch is found on the F2 key :)

---

### Post by Hari_K on 2015-04-24
I have been using wifi on my laptop for an entire year(on trusty). It worked fine in the morning and is not even being detected in the evening. This happened yesterday on utopic. Since then I reinstalled trusty and the backports but to no avail. rfkill doesnt return anything. I cant get bluetooth either. The indicator for my hardware switch doesnt go on no matter how many times I press it. My card IS on in BIOS.

---

### Post by kc1di on 2015-04-24
Sounds like a bad card to me - maybe time for a new one or a call to Dell.

---

### Post by Hari_K on 2015-04-24
Ohh.... Ironically my parts only warranty ended on 22nd April 2015.

---

### Post by Hari_K on 2015-04-24
At a friend's suggestion I reinstalled ubuntu and almost magically the card came alive but after I installed xserver-xorg-core i started getting
 ```

ath:phy failed to restart in 500us....

```
error in tty and then wifi card went back to the dead state. Also while the card worked, I could see any wireless networks even though there was one quite near it.

---

### Post by Hari_K on 2015-04-24
Solved it. After upgrading to 3.19 kernel and installing the non-free linux firmware. Thanks for your time Dave. Really appreciate it. :)

---

### Post by kc1di on 2015-04-24
Glad it wasn't the card and it's working for you. Strange though :p

---

### Post by Hari_K on 2015-04-25
Looks i spoke too soon ;( ;( the problem has resurfaced again!!!!!!!!!!!

---

### Post by wildmanne39 on 2015-04-25
It looks like the card is going out. If you have legacy bios you can check the settings or reset the bios but it probably will not help.

---

### Post by Hari_K on 2015-04-25
My laptop is just 13 months old. Is 1 year the life time of a wireless card ??? That too of one from Qualcomm.

---

### Post by wildmanne39 on 2015-04-25
Not usually but it can happen post a new wireless file and lets see if the device is missing again.

---

### Post by Hari_K on 2015-04-25
Here is the output of wireless script. Have to mention that between your post and this my wireless came back to life and died. Connected to a network successfully as well.
```


########## wireless info START ##########

Report from: 25 Apr 2015 19:48 IST +0530

Booted last: 25 Apr 2015 19:42 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-031900-generic #201504091832 SMP Thu Apr 9 17:35:46 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, nomodeset, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 003 Device 004: ID 064e:812e Suyin Corp. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_wmi               13132  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            14147  0 
dcdbas                 15017  1 dell_laptop
wmi                    19379  2 dell_led,dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe7c:6460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8269210 (8.2 MB)  TX bytes:645828 (645.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/home-network]] (600 root)
[connection] id=home-network | type=802-11-wireless
[802-11-wireless] ssid=home-network | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/D-Link_DIR-600M]] (600 root)
[connection] id=D-Link_DIR-600M | type=802-11-wireless
[802-11-wireless] ssid=D-Link_DIR-600M | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############



```

I see that there is an entry for 'home-network' in network manager profiles. What does that mean ?

---

### Post by wildmanne39 on 2015-04-25
This > home-networkmeans at some point your wifi connected to that network.
Very strange, your device does not show and your drivers are not loaded. Did you unload or uninstall your drivers? Did you install a new kernel that is what it looks like but possibly you did not install all modules like wifi driver and more.

Even if the driver is not installed or loaded your device should be seen in 
```
lspci
```
or
```
lsusb
```
so what all have you tried?
Thanks

---

### Post by Hari_K on 2015-04-26
>  Very strange, your device does not show and your drivers are not loaded. 

I have.  
```

modinfo ath9k

```
returns this
```

filename:       /lib/modules/3.19.0-031900-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6D1C555B730584789ECF3D1
......

```
Havent done anything other than installing kernel 3.19.0-031900-generic and installing the linux-firmware-nonfree.

---

### Post by wildmanne39 on 2015-04-26
Please provide link to kernel and the directions you used to install it.
Thanks

---

### Post by Hari_K on 2015-04-26
[Link]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/") to the kernel. 

I followed the instructions given [here ]("http://ubuntuhandbook.org/index.php/2015/02/upgrade-linux-kernel-3-19-ubuntu-14-04/")for a generic 64bit kernel.

The commands I ran were
```

wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/linux-headers-3.19.0-031900_3.19.0-031900.201504091832_all.deb
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/linux-headers-3.19.0-031900-generic_3.19.0-031900.201504091832_amd64.deb
wget kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/linux-image-3.19.0-031900-generic_3.19.0-031900.201504091832_amd64.deb
sudo dpkg -i linux-headers-3.19.0-*.deb linux-image-3.19.0-*.deb
 
```

---

### Post by wildmanne39 on 2015-04-26
Did you install them in the order you posted them or the order in the link?

They have to be installed in a certain order so if the guy at the link knows what he is doing he should have had them in the correct order and should have stated that they have to be installed in that order.

I do not know if that would make the device disappear but it could cause issues with the driver.
thanks

---

### Post by Hari_K on 2015-04-26
I installed it in the order I posted them. I was copying and pasting from bash history.

Should I install it in another way ?? If so could you please post that order ???

---

### Post by wildmanne39 on 2015-04-26
I checked several sources and it looks like the kernel install is good.
Please try:
```
sudo modprobe ath9k
``` 
does it come on?
if so do:
```
sudo su 
echo ath9k >> /etc/modules 
exit
```
Reboot

---

### Post by Hari_K on 2015-04-27
```

sudo modprobe ath9k

```

did not return or do anything

---

### Post by wildmanne39 on 2015-04-27
Do you have windows installed also? if so does the card work all the time in windows? I still suspect hardware failure, but it is worth reformatting the ubuntu partition and reinstalling ubuntu, but do not update kernel.

---

### Post by Hari_K on 2015-04-28
I don't have windows installed. I will reformat the ubuntu partition.

---

### Post by Hari_K on 2015-04-29
Reformatted the partition but no luck. I did notice that on the first boot, there was some error related to ath9k driver and some error logs saying the kernel has gone into panic mode and all.

---

### Post by wildmanne39 on 2015-04-29
What version of ubuntu did you install? Post a new file from the wireless script so we can see if the issues are the same or different.
Thanks

---

### Post by Hari_K on 2015-04-29
Installed 14.04
```


########## wireless info START ##########

Report from: 30 Apr 2015 05:40 IST +0530

Booted last: 30 Apr 2015 05:31 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, video.use_native_backlight=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 064e:812e Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

dell_laptop            18168  0 
dell_wmi               12761  0 
dcdbas                 14928  1 dell_laptop
sparse_keymap          13948  1 dell_wmi
wmi                    19177  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe7c:6460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24786977 (24.7 MB)  TX bytes:1262450 (1.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/pm/power.d/disable_wol] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############



```

---

### Post by chili555 on 2015-04-29
>  I did notice that on the first boot, there was some error related to ath9k driver and some error logs saying the kernel has gone into panic mode and all. May we see them?```
cat /var/log/syslog | grep ath
cat /var/log/syslog.1 | grep ath 
```It might be dozens of lines long. You might have to post just the 20 or so lines that look most alarming.

Unless the syslog says something to the contrary, I am also of the opinion that the hardware is failing.

---

### Post by Hari_K on 2015-04-29
I feel really embarrassed. Since I din't record the error when it occured, I formatted the system so the error would occur again. It didn't. But wireless still doesn't work. :-(

---

### Post by Hari_K on 2015-04-30
Ok did a fresh install of windows. Surprisingly my bluetooth adapter is recognized there but I couldnt install wireless drivers(not ethernet drivers for that matter). In ubuntu however my aeroplane mode switch seems to work fine and so does bluetooth. Output of wireless script

```


########## wireless info START ##########

Report from: 30 Apr 2015 22:50 IST +0530

Booted last: 30 Apr 2015 21:40 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 005: ID 064e:812e Suyin Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
ath3k                  13331  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wmi                    19193  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe7c:6460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204353671 (204.3 MB)  TX bytes:10241208 (10.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     F6EB9B4BD50E1F5EB2462B2
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512

##### module parameters #################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-04-30
With windows you should not have to manually install those drivers, it appears that your hardware is either failed or it is loose, has this laptop been dropped? I just do not have any other suggestions.
I am sorry.

---

### Post by chili555 on 2015-04-30
> **Wild Man said:**
> With windows you should not have to manually install those drivers, it appears that your hardware is either failed or it is loose, has this laptop been dropped? I just do not have any other suggestions.
I am sorry.I have seen nothing in your readings, Hari_K, that suggest anything else to me but hardware that is failing or failed. I think Wild Man is entirely correct.

---

### Post by Hari_K on 2015-05-04
Installed windows and the drivers. Wireless is working fine there after an initial glitch.

In ubuntu wireless script returns this

```


########## wireless info START ##########

Report from: 04 May 2015 19:33 IST +0530

Booted last: 04 May 2015 06:57 IST +0530

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-36-generic #48~14.04.1-Ubuntu SMP Wed Apr 15 13:11:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:05ea]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev ff)

03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M] [1002:6660] (rev ff)
    Kernel driver in use: radeon

##### lsusb #############################

Bus 001 Device 005: ID 064e:812e Suyin Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
ath3k                  13331  0 
bluetooth             446409  23 bnep,ath3k,btusb,rfcomm
wmi                    19193  2 dell_led,dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe7c:6460/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2989962 (2.9 MB)  TX bytes:336945 (336.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     05170C37AC7B7A82211E896
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.16.0-36-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     8449188E53D477A663A0DBF
depends:        bluetooth
intree:         Y
vermagic:       3.16.0-36-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AC:F6:91:81:39:AD:3F:CA:CC:01:C2:6A:B2:49:09:D5:90:79:A5:78
sig_hashalgo:   sha512

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

[/etc/pm/power.d/disable_wol] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############



```
and 
```

cat /var/log/syslog |grep ath9k

```
returns
```

May  4 06:57:37 hari-k-Inspiron-3537 kernel: [   10.579928] ath9k 0000:02:00.0: Failed to initialize device
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [   10.587860] ath9k: probe of 0000:02:00.0 failed with error -95

```

---

### Post by Hari_K on 2015-05-04
Wireless still doesnt work in ubuntu.

---

### Post by chili555 on 2015-05-04
> probe of 0000:02:00.0 failed with error -95Let's see what's going wrong on the PCI bus:```
dmesg | grep 02:00
dmesg | grep -i error
```

---

### Post by Hari_K on 2015-05-05
I couldn't get 
```

dmesg | grep 02:00

```
So I got 
```

cat /var/log/syslog.1 | grep 02:00

```

It returned this

```

May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.522585] pci 0000:02:00.0: [168c:0036] type 00 class 0x028000
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.522622] pci 0000:02:00.0: reg 0x10: [mem 0xc0600000-0xc067ffff 64bit]
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.522701] pci 0000:02:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.522810] pci 0000:02:00.0: supports D1 D2
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.522812] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.704751] pci 0000:02:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    0.704804] pci 0000:02:00.0: BAR 6: assigned [mem 0xc0680000-0xc068ffff pref]
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [    1.168776] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [   10.579928] ath9k 0000:02:00.0: Failed to initialize device
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [   10.587860] ath9k: probe of 0000:02:00.0 failed with error -95

```

```

cat /var/log/syslog.1 | grep -i error

```
returned this among some other stuff about usb
```

May  4 07:46:18 hari-k-Inspiron-3537 NetworkManager[892]: <error> [1430705778.780474] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May  4 06:57:37 hari-k-Inspiron-3537 kernel: [   10.587860] ath9k: probe of 0000:02:00.0 failed with error -95

```

---

### Post by chili555 on 2015-05-05
I don't see much that's helpful there except this:> ath9k: probe of 0000:02:00.0 failed with error -95A Google search finds this: [https://bugzilla.redhat.com/show_bug.cgi?id=1199630](https://bugzilla.redhat.com/show_bug.cgi?id=1199630) A comment says:> 3.19 works.I suggest you try the live DVD or USB for Ubuntu 15.04 which uses kernel version 3.19 and see if the wireless now works as expected. If so, I'd certainly install it.

If you had a tricky or troublesome install, we can backport the ath9k driver from 3.19 instead of a possibly risky reinstall. I will be happy to help in either case.

---

### Post by Hari_K on 2015-05-09
Wireless did not work in vivid.

---

### Post by chili555 on 2015-05-09
> ath9k: probe of 0000:02:00.0 failed with error -95Is the error the same in 15.04? If so,then I wonder if it's actually a hardware fault, either with the PCI bus or the wireless card itself.

---


---
title: "WiFi disconnects with Ubuntu 14.10 on Lenovo Y50-90"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by shree-cse on 2014-10-25
Hi all, 

I am new to Ubuntu, Installed this on my New Lenovo Y50-90, Everything feels good except WIFI and battery life. I don't talk about battery life, but my WiFi keeps on disconnecting.
It works for a while, then stops working and then to make it work again, I had to reboot the PC. I am posting the Wireless Script in this post.


```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Shreelu-Lenovo-Y50-70 3.18.0-031800rc1-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4710HQ CPU @ 2.50GHz
Memory : 7896 MB
Uptime : 17:37:04 up 18 min,  2 users,  load average: 0.39, 0.35, 0.40




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 5986:055e Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"<MAC ID removed>"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 <MAC ID removed>>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN                no            no
3: hci0: Bluetooth                   no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8723be              96097  0 
btcoexist              51822  1 rtl8723be
rtl8723_common         23662  1 rtl8723be
rtl_pci                27417  1 rtl8723be
rtlwifi                74534  2 rtl_pci,rtl8723be
mac80211              697143  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              520257  2 mac80211,rtlwifi
ideapad_laptop         18524  0 
sparse_keymap          13890  1 ideapad_laptop
wmi                    19379  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
ideapad_laptop  (1): no_bt_rfkill=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | disable_watchdog=N | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
======================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
======================o=============o===========o=============o=========o===========o==============o===========
 eth0                 | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [<BT Device>] | 802.11 WiFi | rtl8723be | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    *<MAC ID removed>: Infra, <MAC C-01 4C:60:DE:FC:49:0D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2


    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             10.0.0.1
----------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


<MAC ID removed>    : ssid=4C:60:DE:FC:49:0D | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
D-Link_DIR-524       : ssid=D-Link_DIR-524 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
HTC Portable Hotspot 9BE1 : ssid=HTC Portable Hotspot 9BE1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.925/2.005/2.086/0.092 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.013/0.017/0.022/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 <MAC ID removed>>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"<MAC ID removed>"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000022e5dcd19
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8723be]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     5D113E08097276ABF2EF3C6
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)


[btcoexist]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     0C170EE6883C780D98D7EC3
depends:        


[rtl8723_common]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     251C540A2D3AD38CCA85ED9
depends:        


[rtl_pci]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     DCE642AF51FCBF67FE7DEB6
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     35225554E432897005F9BA7
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/net/mac80211/mac80211.ko
srcversion:     94D2BCBEF47023226C94CB7
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/net/wireless/cfg80211.ko
srcversion:     38480743B72586E8ACD5AEC
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ideapad_laptop]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/platform/x86/ideapad-laptop.ko
srcversion:     671575052EDF181E26050E7
depends:        sparse-keymap
parm:           no_bt_rfkill:No rfkill for bluetooth. (bool)


[wmi]
filename:       /lib/modules/3.18.0-031800rc1-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     2E987FE96F7EBB6BFC7E2B2
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0xb723 (rtl8723be)
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
                    options iwlwifi 11n_disable=8
                    options iwlwifi 11n_disable=8
mlx4.conf         : softdep mlx4_core post: mlx4_en
modprobe.conf     : options rtl8192ce ips=1
                    options rtl8192ce fwlps=0
                    options rtl8192ce swenc=1
rtl8188ee.conf    : options rtl8188ee ips=0 fwlps=0


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


BOOT_IMAGE=/boot/vmlinuz-3.18.0-031800rc1-generic root=UUID=81b4850c-ce00-493c-902e-9200929b5d15 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.033371] Initializing cgroup subsys net_cls
[    0.033376] Initializing cgroup subsys net_prio
[    4.066172] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.066553] audit: initializing netlink subsys (disabled)
[    4.261260] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.756614] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x495f01)
[   11.995420] wmi: Mapper loaded
[   12.653340] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   12.670766] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.670936] rtlwifi: rtlwifi: wireless switch is on
[   18.954393] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.882304] thinkpad_acpi: http://ibm-acpi.sf.net/
[   22.650830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.280001] wlan0: authenticate with <MAC C-01 <MAC ID removed>>
[   24.295195] wlan0: send auth to <MAC C-01 <MAC ID removed>> (try 1/3)
[   24.300810] wlan0: authenticated
[   24.301152] wlan0: associate with <MAC C-01 <MAC ID removed>> (try 1/3)
[   24.305826] wlan0: RX AssocResp from <MAC C-01 <MAC ID removed>> (capab=0x411 status=0 aid=1)
[   24.306350] wlan0: associated
[   24.306357] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


    ======== Done ========

```

---

### Post by jeremy31 on 2014-10-25
I would start by ```
sudo gedit /etc/modprobe.d/modprobe.conf
``` and replace rtl8192ce with rtl8723be in the three lines, save and reboot

---

### Post by shree-cse on 2014-10-26
Tried it, will check for an hour and post the update here. Thank u

---

### Post by shree-cse on 2014-10-28
> **jeremy31 said:**
> I would start by ```
sudo gedit /etc/modprobe.d/modprobe.conf
``` and replace rtl8192ce with rtl8723be in the three lines, save and reboot

Hi, Tried this and tested for 2 days, its far better. But still the connection is unstable. Not that frequent anyway. Thank you!

---


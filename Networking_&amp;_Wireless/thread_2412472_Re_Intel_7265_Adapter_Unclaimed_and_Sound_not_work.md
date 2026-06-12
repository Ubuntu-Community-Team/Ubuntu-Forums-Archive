---
title: "Re: Intel 7265 Adapter Unclaimed and Sound not working"
date: 2019-02-13
forum: Networking &amp; Wireless
---

### Post by sfksfk on 2019-02-13
Hi everyone,

first of all, English is definitely not my first language, so sorry for the mistakes. Although I have been using Ubuntu for a few years now, I am still a newbie. As such, noticing a problem similar to this thread <https://ubuntuforums.org/showthread.php?t=2390709>, I was not sure if I should have replied it or started a new one.

Anyway, my Intel AC 7265 Wifi adapter as well as my sound (in and output) are not working after the latest kernel update. This happened two days ago, and so far I already have gone through a number of threads and posts with similar issues, tried many commands, rebooted many times, and everything stayed the same. I am connected through my ethernet, that is working just fine. The command sudo lshw -class network returned that my wifi adapter is unclaimed.

I verified the updates more than once and everything seems ok, and therefore I executed the following script (following the instructions on this thread: <https://ubuntuforums.org/showthread.php?t=370108>:

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

I will paste the results in the next thread.
Thanks.
Sfk.

```
########## wireless info START ##########

Report from: 13 Feb 2019 08:10 -02 -0200

Booted last: 13 Feb 2019 07:55 -02 -0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-166-generic #216-Ubuntu SMP Thu Feb 7 14:07:53 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, locale=de_DE, quiet, splash, pcie_aspm=default, radeon.modeset=0, nouveau.modeset=0, video.use_native_backlight=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:0641]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5410]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 8087:0a2a Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18133  0 
dcdbas                 14928  1 dell_laptop
wmi                    19177  1 dell_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eth0' [IF1]> brd <MAC address>
    inet 10.4.108.48/24 brd 10.4.108.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'eth0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 10.4.108.254 dev eth0  proto static 
10.4.108.0/24 dev eth0  proto kernel  scope link  src 10.4.108.48  metric 1 

##### resolv.conf #######################

[777 root ‘/etc/resolv.conf’ -> ‘../run/resolvconf/resolv.conf’]
nameserver 127.0.1.1
search soziologie.privat privat

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1178     1  0 07:55 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.4.108.48
    Prefix:          24 (255.255.255.0)
    Gateway:         10.4.108.254

    DNS:             132.230.200.200
    DNS:             132.230.201.111

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/devolo-a93]] (600 root)
[connection] id=devolo-a93 | type=802-11-wireless
[802-11-wireless] ssid=devolo-a93 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Meri4001]] (600 root)
[connection] id=Meri4001 | type=802-11-wireless
[802-11-wireless] ssid=Meri4001 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ABG BRASIL]] (600 root)
[connection] id=ABG BRASIL | type=802-11-wireless
[802-11-wireless] ssid=ABG BRASIL | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ligiatoledo2]] (600 root)
[connection] id=Ligiatoledo2 | type=802-11-wireless
[802-11-wireless] ssid=Ligiatoledo2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/mtfsfk]] (600 root)
[connection] id=mtfsfk | type=802-11-wireless
[802-11-wireless] ssid=mtfsfk | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC3401973]] (600 root)
[connection] id=UPC3401973 | type=802-11-wireless
[802-11-wireless] ssid=UPC3401973 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Telekom_FON]] (600 root)
[connection] id=Telekom_FON | type=802-11-wireless
[802-11-wireless] ssid=Telekom_FON | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Audi_MMI_4478]] (600 root)
[connection] id=Audi_MMI_4478 | type=802-11-wireless
[802-11-wireless] ssid=Audi_MMI_4478 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VIA_WIFI_VIDEO]] (600 root)
[connection] id=VIA_WIFI_VIDEO | type=802-11-wireless
[802-11-wireless] ssid=VIA_WIFI_VIDEO | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Free Airport WIFI]] (600 root)
[connection] id=Free Airport WIFI | type=802-11-wireless
[802-11-wireless] ssid=Free Airport WIFI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MTFSFK]] (600 root)
[connection] id=MTFSFK | type=802-11-wireless
[802-11-wireless] ssid=MTFSFK | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-4CA2]] (600 root)
[connection] id=HOME-4CA2 | type=802-11-wireless
[802-11-wireless] ssid=HOME-4CA2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box 7490]] (600 root)
[connection] id=FRITZ!Box 7490 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7490 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel Le Dauphin Montreal]] (600 root)
[connection] id=Hotel Le Dauphin Montreal | type=802-11-wireless
[802-11-wireless] ssid=Hotel Le Dauphin Montreal | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KLWIFINET]] (600 root)
[connection] id=KLWIFINET | type=802-11-wireless
[802-11-wireless] ssid=KLWIFINET | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/#NET-CLARO-WIFI]] (600 root)
[connection] id=#NET-CLARO-WIFI | type=802-11-wireless
[802-11-wireless] ssid=#NET-CLARO-WIFI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DornellesKlein]] (600 root)
[connection] id=DornellesKlein | type=802-11-wireless
[802-11-wireless] ssid=DornellesKlein | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hotel_Champlain]] (600 root)
[connection] id=hotel_Champlain | type=802-11-wireless
[802-11-wireless] ssid=hotel_Champlain | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/.Aeroporto WiFi Gratis]] (600 root)
[connection] id=.Aeroporto WiFi Gratis | type=802-11-wireless
[802-11-wireless] ssid=.Aeroporto WiFi Gratis | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/USPnet]] (600 root)
[connection] id=USPnet | type=802-11-wireless
[802-11-wireless] ssid=USPnet | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Villa Kunterbund Gastzugang]] (600 root)
[connection] id=Villa Kunterbund Gastzugang | type=802-11-wireless
[802-11-wireless] ssid=Villa Kunterbund Gastzugang | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Villa Kunterbunt]] (600 root)
[connection] id=Villa Kunterbunt | type=802-11-wireless
[802-11-wireless] ssid=Villa Kunterbunt | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Novotel Toronto Centre]] (600 root)
[connection] id=Novotel Toronto Centre | type=802-11-wireless
[802-11-wireless] ssid=Novotel Toronto Centre | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

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
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/video.conf]
options video use_native_backlight=1

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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x095a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   16.649692] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[   16.736492] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   21.319155] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   21.319196] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.913465] r8169 0000:02:00.0 eth0: link up
[   22.913473] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2019-02-13
Please run the terminal command:```
sudo modprobe iwlwifi && dmesg | grep iwl
```Next, post the exact result.

---

### Post by sfksfk on 2019-02-13
Hi chili555,
thanks for the fast reply.
I don't know how bad this is, but the output was very simple:

modprobe: ERROR: could not insert 'iwlwifi': Package not installed

Regards.
Sfk.

---

### Post by chili555 on 2019-02-13
Let's have a look at:```
sudo updatedb && locate iwlwifi.ko
```updatedb take a few moments, please be patient.

Thanks.

---

### Post by sfksfk on 2019-02-13
Thanks again: below the return for 

sudo updatedb && locate iwlwifi.ko

```
/lib/modules/3.13.0-101-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-101-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-102-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-102-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-107-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-107-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-109-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-109-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-117-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-117-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-119-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-119-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-124-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-124-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-125-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-125-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-126-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-126-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-128-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-128-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-129-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-129-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-130-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-130-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-131-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-131-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-132-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-132-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-133-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-133-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-134-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-134-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-135-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-135-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-136-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-136-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-137-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-137-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-138-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-138-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-139-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-139-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-140-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-140-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-141-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-141-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-142-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-142-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-143-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-143-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-144-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-144-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-145-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-145-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-146-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-146-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-147-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-147-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-148-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-148-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-149-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-149-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-150-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-150-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-151-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-151-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-153-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-153-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-154-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-154-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-155-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-155-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-156-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-156-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-158-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-158-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-159-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-159-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-160-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-160-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-161-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-161-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-162-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-162-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-163-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-163-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-164-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-164-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-165-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-165-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-36-generic/updates/dkms/iwlwifi.ko
/lib/modules/3.13.0-99-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.13.0-99-generic/updates/dkms/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-101-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-102-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-107-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-109-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-117-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-119-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-124-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-125-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-126-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-128-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-129-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-130-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-131-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-132-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-133-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-134-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-135-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-136-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-137-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-138-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-139-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-140-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-141-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-142-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-143-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-144-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-145-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-146-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-147-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-148-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-149-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-150-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-151-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-153-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-154-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-155-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-156-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-158-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-159-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-160-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-161-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-162-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-163-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-164-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-165-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-166-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-36-generic/x86_64/module/iwlwifi.ko
/var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-99-generic/x86_64/module/iwlwifi.ko


```

---

### Post by chili555 on 2019-02-13
> /var/lib/dkms/iwlwifi-3.16.2/1.0/3.13.0-166-generic/x86_64/module/iwlwifi.ko
What explains this? Why did you find it necessary to install a dkms module for iwlwifi? Is your exact device ID not covered in the built-in iwlwifi module? Or....what??

You have too many kernels installed on your system, perhaps 30 or so!!! You will very soon run out of room in your /boot partition and be unable to install or update anything like this: [https://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to](https://askubuntu.com/questions/171209/my-boot-partition-hit-100-and-now-i-cant-upgrade-cant-remove-old-kernels-to)

I suggest that you trim down to the last two with:

```
sudo apt-get autoremove

```
iwlwifi seems to be well and truly present, so we still wonder why it doesn't load or even modprobe.

---

### Post by sfksfk on 2019-02-13
Thanks again!

In fact, I only performed the updates suggested by Ubuntu itself, never installing any module myself (meaning, I do not know how to explain it and it was not an individual choice to install a dkms module..). So if I run the autoremove, it will trim it down automatically, or do I have to tell him to which to trim it down?

---

### Post by chili555 on 2019-02-13
autoremove means just that: auto. It will do everything for you. Please proceed.

---

### Post by sfksfk on 2019-02-13
Thank you for your patience!

Well, I proceeded with it, the process was very (I think maybe too) quick - only a few seconds -, and the output was:

0 aktualisiert, 0 neu installiert, 0 zu entfernen und 9 nicht aktualisiert

I translate:

0 updated, 0 newly installed, 0 to be removed and 9 not updated.

---

### Post by chili555 on 2019-02-13
Wierd. 

Please let us see:

```
modinfo /lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko | grep 095A
```

And also:

```
modinfo /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko | grep 095A
```The kernel cleanup will be a longer process a bit later. I'm sorry that autoremove didn't help.

---

### Post by sfksfk on 2019-02-13
Thanks again - not your fault it did not work. ;)

Below code for both outputs (do not know what it means, but noticed that they are fairly similar, while not equal...although some of them appear in a different order...)

Output for:
modinfo /lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko | grep 095
```
alias:          pci:v00008086d0000095Asv*sd00009400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005F10bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005102bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005412bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005C10bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*

```

And output for:

modinfo /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko | grep 095A```
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005102bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005412bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*

```

---

### Post by chili555 on 2019-02-13
It appears that both the normal built-in module as well as the added later dkms module cover your device. Let's try again:

```
sudo modprobe  /lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
```

Please carefully copy the exact result and post it.

---

### Post by sfksfk on 2019-02-13
Ok, once again, a very clear response (now, wondering if this will show us a way out or if it is the sign of doom...).

Output for 

sudo modprobe  /lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko

is

modprobe: FATAL: Module /lib/modules/3.13.0-166-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko not found.

---

### Post by chili555 on 2019-02-13
Still weird!

Let's try:```
sudo modprobe /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko
```Also, please show me:```
ls -al /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko
```

---

### Post by sfksfk on 2019-02-13
So, for the first one, the same problem as we just had:

Output for

sudo modprobe /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko

is


```
modprobe: FATAL: Module /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko not found.


```

As for

ls -al /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko

he returned a "could not find directory or file" (pasted it below).


```
ls: Zugriff auf /lib/modules/3.13.0-166-generic/updates/dkms/ilwifi.ko nicht möglich: Datei oder Verzeichnis nicht gefunden
```

---

### Post by chili555 on 2019-02-13
That is beyond weird. Obviously, as you posted above, the command locate sees it but modprobe does not.

Please run and post these commands. Let's see what goes wrong:

```
ls /lib/modules/3.13.0-166-generic/

```
And then:

```
/lib/modules/3.13.0-166-generic/updates/
```

And then:

```
ls /lib/modules/3.13.0-166-generic/updates/dkms/
```

Finally:

```
sudo dkms status
```

---

### Post by sfksfk on 2019-02-13
Here they come!

For

ls /lib/modules/3.13.0-166-generic/

Output:


```
build          modules.alias.bin    modules.dep.bin  modules.symbols
initrd         modules.builtin      modules.devname  modules.symbols.bin
kernel         modules.builtin.bin  modules.order    updates
modules.alias  modules.dep          modules.softdep  vdso


```

For (I added the ls that I suppose was needed up front)

ls /lib/modules/3.13.0-166-generic/updates/


Output:

```
dkms
```

For

ls /lib/modules/3.13.0-166-generic/updates/dkms/


Output:

```
cfg80211.ko              snd-hda-codec-ca0110.ko    snd-hda-codec-idt.ko
compat.ko                snd-hda-codec-ca0132.ko    snd-hda-codec.ko
iwldvm.ko                snd-hda-codec-cirrus.ko    snd-hda-codec-realtek.ko
iwlmvm.ko                snd-hda-codec-cmedia.ko    snd-hda-codec-si3054.ko
iwlwifi.ko               snd-hda-codec-conexant.ko  snd-hda-codec-via.ko
mac80211.ko              snd-hda-codec-generic.ko   snd-hda-controller.ko
snd-hda-codec-analog.ko  snd-hda-codec-hdmi.ko      snd-hda-intel.ko
```

And, last but not least (this is a long one...), for

sudo dkms status

Output:

```
iwlwifi-3.16.2, 1.0, 3.13.0-101-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-102-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-107-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-109-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-117-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-119-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-124-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-125-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-126-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-128-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-129-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-130-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-131-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-132-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-133-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-134-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-135-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-136-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-137-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-138-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-139-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-140-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-141-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-142-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-143-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-144-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-145-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-146-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-147-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-148-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-149-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-150-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-151-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-153-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-154-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-155-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-156-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-158-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-159-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-160-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-161-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-162-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-163-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-164-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-165-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-166-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-36-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-99-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-101-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-102-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-107-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-109-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-117-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-119-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-124-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-125-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-126-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-128-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-129-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-130-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-131-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-132-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-133-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-134-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-135-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-136-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-137-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-138-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-139-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-140-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-141-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-142-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-143-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-144-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-145-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-146-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-147-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-148-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-149-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-150-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-151-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-153-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-154-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-155-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-156-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-158-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-159-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-160-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-161-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-162-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-163-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-164-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-165-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-166-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-36-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-99-generic, x86_64: installed

```

Thanks!

---

### Post by chili555 on 2019-02-13
Please run:```
sudo depmod -a
```Post any output. Then try again:```
sudo modprobe  /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko
```We know it's there; we've seen it...twice!

---

### Post by sfksfk on 2019-02-14
Hi chili,

different time zones, and after I leave my office, no more internet access.

Bizarrely, for 

sudo depmod -a

my laptop "thought" and processed for maybe about a minute, did something, but there was no (visual) code output at all.

For its turn,

sudo modprobe  /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko

produced the same output as before:

```
modprobe: FATAL: Module /lib/modules/3.13.0-166-generic/updates/dkms/iwlwifi.ko not found
```.

Absolutely awkward to me.

---

### Post by chili555 on 2019-02-14
And is the result any different for:```
sudo modprobe iwlwifi
```Second, if you interrupt the boot process at the GRUB menu and, under Advanced Options, select a kernel version earlier than -166, does the wireless work? Please try several.

Here is a post that describes the GRUB menu process: [https://askubuntu.com/questions/1114230/no-internet-connection-how-to-reinstall-network-drivers-on-bionic/1114266#1114266](https://askubuntu.com/questions/1114230/no-internet-connection-how-to-reinstall-network-drivers-on-bionic/1114266#1114266)

---

### Post by sfksfk on 2019-02-14
Hi Chili,

for

sudo modprobe iwlwifi
the output was similar:

```
modprobe: ERROR: could not insert 'iwlwifi': Package not installed
```

Will not try to reboot through GRUB.

---

### Post by chili555 on 2019-02-14
> 
modprobe: ERROR: could not insert 'iwlwifi': [COLOR="#FF0000"]Package not installed[/COLOR]
That's a very unusual response. I've never seen it before. May I see the original German? I am hoping something is lost in translation.

---

### Post by sfksfk on 2019-02-14
Hi chili,

in fact, in this case the output was in English: I pasted it exactly like it appeared in my terminal.

Furthermore, so far I have gone until Kernel 130, and nothing...btw, Kernels 157 and 152 are missing on the GRUB list. Should I continue trying?

---

### Post by chili555 on 2019-02-14
> 
Should I continue trying?
No. I am studying and Googling. I'll be back later.

---

### Post by sfksfk on 2019-02-14
Ok! Thanks a lot.

---

### Post by praseodym on 2019-02-14
Lets see
```

dkms status
sudo dkms autoinstall
sudo modprobe -v iwiwifi
```

---

### Post by chili555 on 2019-02-14
Is this a Dell that came with Ubuntu?

---

### Post by chili555 on 2019-02-15
I have consulted with several of my colleagues here, the people who trained me and who taught me most of what I know. We are essentially agreed on one strategy.

Ubuntu 14.04 will be end-of-life on April 30, 2019. End-of-life means that it will no longer receive any updates, including, of course, crucial security updates. It is frustrating for all of us to try to resuscitate an installation that is going away soon, no matter what we do.

We suggest that you do a complete backup and next, on some other computer, download the iso image for Ubuntu 18.04 LTS. LTS means long term support. It will not reach end-of-life until April 30, 2023. [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Once you have burned the iso image to DVD or USB, try it in your computer running a live session; that is, Try Ubuntu. If everything works as expected, which we believe it wil, install it. 

Please post back if you have more questions. Don't forget to back up your present data!

---

### Post by sfksfk on 2019-02-15
Hi praseodym,

the output for dkms status is:

```
iwlwifi-3.16.2, 1.0, 3.13.0-101-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-102-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-107-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-109-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-117-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-119-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-124-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-125-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-126-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-128-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-129-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-130-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-131-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-132-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-133-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-134-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-135-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-136-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-137-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-138-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-139-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-140-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-141-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-142-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-143-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-144-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-145-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-146-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-147-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-148-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-149-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-150-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-151-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-153-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-154-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-155-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-156-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-158-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-159-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-160-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-161-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-162-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-163-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-164-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-165-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-166-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-36-generic, x86_64: installed
iwlwifi-3.16.2, 1.0, 3.13.0-99-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-101-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-102-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-107-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-109-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-117-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-119-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-124-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-125-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-126-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-128-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-129-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-130-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-131-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-132-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-133-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-134-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-135-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-136-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-137-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-138-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-139-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-140-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-141-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-142-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-143-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-144-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-145-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-146-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-147-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-148-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-149-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-150-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-151-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-153-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-154-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-155-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-156-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-158-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-159-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-160-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-161-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-162-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-163-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-164-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-165-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-166-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-36-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-99-generic, x86_64: installed


```

After the autoinstall command, the output for 
sudo modprobe -v iwiwifi
was

```
modprobe: FATAL: Module iwiwifi not found.

```

and for 
sudo modprobe -v iwlwifi

was

```
modprobe: ERROR: could not insert 'iwlwifi': Package not installed

```

---

### Post by sfksfk on 2019-02-15
Hi chili,

regarding your first question: yes, indeed, it is a Dell laptop that came with Ubuntu (exactly this 14.04) installed.

I was getting concerned that the most "reasonable" alternative would be to install a newer distro of Ubuntu. The only reason I was refraining from proposing it rightaway is the fact that I will not be able to do a full backup for almost two weeks and, as such, was hoping that somehow it would be possible to - at least - regain sound output during this time, since as it is what I am able to do with my laptop at my local home, were I have no ethernet support, is very much limited without internet and no sound.

But, life as it is: thanks a lot for the support and time you put into it.

The other question is: shouldn&#8217;t it be possible to upgrade from this distro to 18.04 directly through my laptop, without burning it onto another hardware?

---

### Post by jeremy31 on 2019-02-15
I would search Synaptic Package Manager or the Ubuntu software manager for package iwlwifi as I know it doesn't exist in Ubuntu repos but Dell has their own repos
I would definitely make a backup of everything before attempting an update to 18.04 or even 16.04, even 16.04 should support that wifi and it is still supported for 3 more years

---

### Post by sfksfk on 2019-02-16
Hi jeremy,

at the software manager I found the iwlwifi installed (3.16.2 dkms), and since it was not working, decided do reinstall it - unfortunately, after deinstalling it, now it does not offer me the alternative of reinstalling (bizarre?).

I looked into "additional drivers" at the update menu, and it displayed me the following info for an Intel device (I suppose it is the wireless adapter and/or soundcard):

oem-audio-hda-daily driver in DKMS format

How can I install it?

---

### Post by jeremy31 on 2019-02-16
I thought the oem-audio driver was already installed with dkms.  You should be able to search Synaptic to find the iwlwifi package again so it can be installed

---

### Post by sfksfk on 2019-02-16
Hi chili, praseodym and jeremy,

ironically I just noted, after rebooting, that apparently the wifi adapter has been claimed and is working (?!?). I cannot tell if it is effectively working, since I do not have a wifi network to connect here, but the option of turning wifi on and off appears in the menu, and it is showing two available networks.

Edit: unfortunately, the sound continues inexistent.

---

### Post by sfksfk on 2019-02-16
And, well, in the software manager he shows that the "oem-audio-hda-daily driver in DKMS format" is installed: should I uninstall it as well?

---

### Post by sfksfk on 2019-02-16
Now I can officially say that the wireless adapter is working again - this is really bizarre: may it be the last update installed something that made it malfunction?

At the same time, strange that I was able to reclaim the adapter in such manner, and it did nothing for the sound.

---

### Post by jeremy31 on 2019-02-16
I would at least try uninstalling the sound driver.  It isn't working now

---

### Post by sfksfk on 2019-02-23
Hi jeremy and chili

had a busy week, and decided not to mess with the sound drivers, since next week I should finally be able to backup everything and try to move forward (furthermore: I am frightened that the wifi stops again if the sound drivers are uninstalled...).

However, I would like to know if you could point out advantages/disadvantages between simply installing Ubuntu 18.04 from scratch, as initially suggested by chili, or attempting to upgrade from my current distro to 16.04 and then seeing if I upgrade again rightaway to 18.04 before reinstalling my stuff.

Thanks a lot!

---

### Post by chili555 on 2019-02-23
If your goal is, as we recommended, 18.04, why not take the shortest, most direct route possible?

I suggest that you download the iso for 18.04. Burn it to a DVD or a USB and reboot into 18.04. Use the option, Try Ubuntu. It makes no change whatever to your current install or your harddrive. 

Test your sound and wireless. If they work, as we suspect they do, install it.

Done.

---

### Post by sfksfk on 2019-02-25
Hi chili,

indeed, a very compelling argument. :)

Just so I understand correctly (I will backup everything anyway): if I install the 18.04 the way you suggested it, if the installation goes through without problems, will it use the programs and data that are already installed, or would I have to install them again (as well as personal files)? This is the (minor) setback I expected would be present by installing the way you suggest instead of upgrading - but still, I understand even under these circumstances it might be the best alternative to start out fresh; just trying to understand the differences and not get surprised.

Thanks again!

---

### Post by chili555 on 2019-02-25
The installation aims to recognize your /home/user directory and preserve it. In my experience, going back 10-12 years in Ubuntu, most often, it succeeds. However, sometimes it fails. That's life. Nothing technological is 100% perfect. That's why we recommend a full backup of everything in your /home/user (/home/sfksfk ?) directory. The chances are that it's going to go perfectly, but, in case not, you have a Plan B.

Upgrading to 18.04 will install all new everything. If you have custom configuration files, blacklists, etc., it is supposed to ask if you want the new version, old version or if you'd like to see the differences to decide.

There are quite a few configurations that are specific to you in hidden files in /home/user; typically called .config, .cups, .gconf and more. Please back up all hidden files.

If you have installed non-default programs in 14.04, Dropbox for example, they will not survive. You will need to re-install those.

More questions? Concerns?

---

### Post by sfksfk on 2019-02-28
Thanks chili: I think I am all set. Bought the USB and am now preparing it to be a bootable flash drive, afterwards will backup everything, doing my best to remember checking if hidden configuration files you mentioned are also there, and tomorrow try to install it and see how it works out (my afternoon is already packed, so I probably won't be able to do everything today).

---

### Post by sfksfk on 2019-02-28
> **chili555 said:**
> I have consulted with several of my colleagues here, the people who trained me and who taught me most of what I know. We are essentially agreed on one strategy.

Ubuntu 14.04 will be end-of-life on April 30, 2019. End-of-life means that it will no longer receive any updates, including, of course, crucial security updates. It is frustrating for all of us to try to resuscitate an installation that is going away soon, no matter what we do.

We suggest that you do a complete backup and next, on some other computer, download the iso image for Ubuntu 18.04 LTS. LTS means long term support. It will not reach end-of-life until April 30, 2023. [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Once you have burned the iso image to DVD or USB, try it in your computer running a live session; that is, Try Ubuntu. If everything works as expected, which we believe it wil, install it. 

Please post back if you have more questions. Don't forget to back up your present data!

Hi chili,

the USB flash drive now seems ready and bootable with Ubuntu 18.04.2. Nevertheless, rereading the first post where you suggested to install a newer flavour and get over the end-of-life issue, I noted and got curious about a specific aspect: you said to "on some other computer, download the iso image for Ubuntu 18.04 LTS". Was there a specific reason to do it on another computer? Because I simply used the same notebook I am having trouble with, under Ubuntu 14.04, and did it over here.

Thanks and sorry if the question comes off as unnecessary.

---

### Post by chili555 on 2019-02-28
> Was there a specific reason to do it on another computer? I suggested another computer as I wondered if the non-operational wireless meant that you had no internet access at all.

Any computer will do.

---

### Post by sfksfk on 2019-03-01
Hi chili,

backed up and am all set to install Ubuntu LTS 18.04.2, in fact, right now using it from the usb drive. When I started the installation process, he identified the existing 14.04.5 version, and prompted me with alternatives, and I am not sure which one to choose, if the first one (translating from German) "Erase Ubuntu 14.04.5 and install the new one" - or the second - "Install Ubuntu 18.04.2 besides 14.04.5".

The problem is: in the first case he tells me "personal data will be erased from 14.04.5": does this mean he will not copy them at all, or he will only copy them to the newer flavour without keeping the old one? I do not have any need for the dual boot that comes with the second option, partitioning the hard drive etc., and would be favorable to getting away entirely with the older version, but the first option did not seem clear to me in terms of trying to keep the old data.

Thanks a lot!

---

### Post by chili555 on 2019-03-01
> "Erase Ubuntu 14.04.5 and install the new one" And also: > personal data will be erased from 14.04.5...means that all the personal data and folders in your /home/sfksfk directory will be erased. That's why you are advised to back up everything you want and need. That way, when 18.04 LTS is installed, you can simply drag and drop from the backup media, a USB drive, I assume, to your new, almost empty /home/sfksfk directory. That's what I recommend that you do.

May I assume that in 18.04, even running from the USB, the wireless works perfectly?

---

### Post by sfksfk on 2019-03-01
Yes, wifi as well as sound are working flawlessly! Now, let's proceed with the installation.

Thanks!

---

### Post by sfksfk on 2019-03-01
Hi chili,

thank you (all): everything seems to be working!

Have already gotten back my firefox settings and am in the process of finishing copying back my old files.

---

### Post by chili555 on 2019-03-01
> **sfksfk said:**
> Hi chili,

thank you (all): everything seems to be working!

Have already gotten back my firefox settings and am in the process of finishing copying back my old files.Awesome! Glad it's working as expected.

---


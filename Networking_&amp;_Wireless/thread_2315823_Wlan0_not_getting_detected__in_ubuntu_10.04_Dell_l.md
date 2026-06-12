---
title: "Wlan0 not getting detected  in ubuntu 10.04 Dell latitude 6430u"
date: 2016-03-02
forum: Networking &amp; Wireless
---

### Post by psrujith on 2016-03-02
result of lspci command is 

00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Device 1e1a (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e55 (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
02:00.0 PCI bridge: Device 1ae9:0101 (rev 04)
03:00.0 PCI bridge: Device 1ae9:0201 (rev 04)
03:02.0 PCI bridge: Device 1ae9:0201 (rev 04)
03:03.0 PCI bridge: Device 1ae9:0201 (rev 04)
04:00.0 Network controller: Atheros Communications Inc. Device 0034 (rev 01)
07:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)

---

### Post by psrujith on 2016-03-02
I am attaching wireless info here please check this 


########## wireless info START ##########

Report from: 02 Mar 2016 17:29 EST -0500

Booted last: 02 Mar 2016 17:28 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

##### kernel ############################

Linux 2.6.32-74-generic #142-Ubuntu SMP Tue Apr 28 10:03:02 UTC 2015 x86_64 unknown unknown GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

GNOME

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
    Kernel driver in use: e1000e
    Kernel modules: e1000e

04:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0034] (rev 01)

07:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8221] (rev 05)
    Kernel driver in use: sdhci-pci

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 002 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 003: ID 0cf3:817b Atheros Communications, Inc. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 08ff:2810 AuthenTec, Inc. 
Bus 001 Device 003: ID 1bcf:289b Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi                2177  0 
dell_laptop             7973  0 
dcdbas                  6886  1 dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.226  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd6a:ff64:3ff5:0:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:796772 (796.7 KB)  TX bytes:97626 (97.6 KB)
          Interrupt:20 Memory:f7c00000-f7c20000 

pan0      Link encap:Ethernet  HWaddr <MAC 'pan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

##### resolv.conf #######################

domain lan
search lan
nameserver 192.168.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       893     1  0 17:28 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.226
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

nm-system-settings.conf (used up to Ubuntu 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

pan0      no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/action_wpa] (777 root)
PATH=/sbin:/usr/sbin:/bin:/usr/bin
if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi
SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=
case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac
if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.
    IFPLUGD_IFACE="${1}"
    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi
if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi
for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue
    IFACE="${CTRL#/var/run/wpa_supplicant/}"
    wpa_action "${IFACE}" check || continue
    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi
    wpa_cli -i "${IFACE}" "${COMMAND}"
done

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    2.591112] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) <MAC 'eth0' [IF]>
[    2.591115] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.591146] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: E011FF-0FF
[    2.921394] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.468123] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    4.468125] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[    4.468948] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

---

### Post by chili555 on 2016-03-02
Your operating system is almost six years old. Security updates haven't been issued for many years. No-one but old Chili even knows what a 2.6.xx kernel is!!

I urge you to install, at least, Ubuntu 14.04 LTS. [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Your device will spring to life using the driver ath9k.

---


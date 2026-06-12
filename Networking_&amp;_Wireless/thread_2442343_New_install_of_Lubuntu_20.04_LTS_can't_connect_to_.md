---
title: "New install of Lubuntu 20.04 LTS can't connect to Internet"
date: 2020-05-02
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2020-05-02
I installed Lubuntu 20.04 LTS over 18.04 LTS. No internet connection is working. It seems neither my ethernet nor my wi-fi is recognised. "Wired connection 1" in network manager icon is disconnected. If I click on it nothing happens. "Wi-fi networks" is greyed out. Right click shows "Enable Wi-fi" is checked. Click on "Wi-fi request scan" does nothing at all. Please let me know what information to post so you can help me. Many thanks.

---

### Post by rdh61 on 2020-05-02
Administrators please move this to "Networking and Wireless". Thank you.

---

### Post by oldfred on 2020-05-02
Moved.
Correct way to request change is to use the report post at bottom. That is not just for spam but anything you need an Admin for.

If you can run the wireless script shown in stick threads at top of Wireless sub-forum can copy to a system that can connect, post the results of that script.

What wired & wireless chips do you have? Some wireless chips need you to download a driver. But usually wired connections work.

---

### Post by rdh61 on 2020-05-02
> **oldfred said:**
> 

If you can run the wireless script shown in stick threads at top of Wireless sub-forum can copy to a system that can connect, post the results of that script.

What wired & wireless chips do you have? Some wireless chips need you to download a driver. But usually wired connections work.

Thank you for your reply. Do you mean this script?

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Surely that requires a connection, which I don't have.

How can I find out which wired and wireless chips I have?

Thank you again.

---

### Post by CelticWarrior on 2020-05-02
Please run the script as per the instructions. It doesn't require any internet connection to run and it's intended to troubleshoot any connection. Most users running it have no connection. You may need to download it from somewhere else though.
It'll create a report file and that file - its contents actually - is what you should post here. Of course, you may need to copy it from that computer to the one you're using to post in the forum.

---

### Post by rdh61 on 2020-05-04
Here is the output of the wireless-info script:


```
########## wireless info START ##########

Report from: 04 May 2020 08:39 CEST +0200

Booted last: 04 May 2020 00:00 CEST +0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]

03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 07)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:5002]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 006: ID 13fe:3623 Kingston Technology Company Inc. 
Bus 001 Device 003: ID 04f2:b2fa Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wmi_bmof               16384  0
wmi                    32768  1 wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

##### resolv.conf #######################

[644 root '/etc/resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root         756       1  0 08:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     10 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.368111] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[   13.368115] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[   28.765787] r8169 0000:03:00.0 enp3s0: Link is Down
[   88.443970] r8169 0000:03:00.0 enp3s0: Link is Up - 10Mbps/Half - flow control off
[   88.443983] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   89.963429] r8169 0000:03:00.0 enp3s0: Link is Down
[  101.362310] r8169 0000:03:00.0 enp3s0: Link is Up - 10Mbps/Half - flow control off
[  101.748830] r8169 0000:03:00.0 enp3s0: Link is Down
[  111.174321] r8169 0000:03:00.0 enp3s0: Link is Up - 10Mbps/Half - flow control off
[  111.378703] r8169 0000:03:00.0 enp3s0: Link is Down
[  156.557614] r8169 0000:03:00.0 enp3s0: Link is Up - 10Mbps/Half - flow control off
[  157.011324] r8169 0000:03:00.0 enp3s0: Link is Down
[  165.700444] r8169 0000:03:00.0 enp3s0: Link is Up - 10Mbps/Half - flow control off
[  165.867797] r8169 0000:03:00.0 enp3s0: Link is Down

########## wireless info END ############
```

---

### Post by rdh61 on 2020-05-05
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---


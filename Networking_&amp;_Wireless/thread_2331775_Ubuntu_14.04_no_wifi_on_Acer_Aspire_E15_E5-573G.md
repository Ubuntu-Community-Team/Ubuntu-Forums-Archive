---
title: "Ubuntu 14.04 no wifi on Acer Aspire E15 E5-573G"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by cg.c on 2016-07-25
The wireless is not working, Ubuntu 14.04 and I have Acer Aspire E15-E5-573G.
I used some "guides" from the forum or askubuntu, but didn't worked :-(
Someone can help me?

PS: before worked, but I updated my laptop ( the daily updates from linux), and everytime I made the update my wifi stoped working, but every time I could fix them with "guides" I found here, but now no one worked :-(

---

### Post by jeremy31 on 2016-07-25
Please see the wireless script link in  my signature and post your results

---

### Post by cg.c on 2016-07-26
Nothing worked, I get error at some places after I download  wireless-info,my wireless-info.txt content is different from the one is  posted in thaat thread.

```

########## wireless info START ##########

Report from: 26 Jul 2016 11:24 EEST +0300

Booted last: 26 Jul 2016 11:19 EEST +0300

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-65-generic #73~14.04.1-Ubuntu SMP Wed Jun 29 21:05:22 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]

04:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce 920M] [10de:1299] (rev a1)

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 1bcf:2c81 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 002: ID 10c4:8105 Cygnal Integrated Products, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6451200  0 
cfg80211              532480  1 wl
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
mxm_wmi                16384  1 nouveau
video                  20480  3 i915_bpo,acer_wmi,nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.174  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:295325 (295.3 KB)  TX bytes:278110 (278.1 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF2]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

virbr0    no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       912     1  0 11:19 ?        00:00:00 NetworkManager

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
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.174
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

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/HAZARD]] (600 root)
[connection] id=HAZARD | type=802-11-wireless
[802-11-wireless] ssid=HAZARD | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Home]] (600 root)
[connection] id=Home | type=802-11-wireless
[802-11-wireless] ssid=Home | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IT School]] (600 root)
[connection] id=IT School | type=802-11-wireless
[802-11-wireless] ssid=IT School | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Betel]] (600 root)
[connection] id=Betel | type=802-11-wireless
[802-11-wireless] ssid=Betel | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ioana&Valy]] (600 root)
[connection] id=Ioana&Valy | type=802-11-wireless
[802-11-wireless] ssid=Ioana&Valy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIGI WIFI 2.4 Web Login]] (600 root)
[connection] id=DIGI WIFI 2.4 Web Login | type=802-11-wireless
[802-11-wireless] ssid=DIGI WIFI 2.4 Web Login | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Leo Home]] (600 root)
[connection] id=Leo Home | type=802-11-wireless
[802-11-wireless] ssid=Leo Home | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DigiWifi 2.4Ghz]] (600 root)
[connection] id=DigiWifi 2.4Ghz | type=802-11-wireless
[802-11-wireless] ssid=DigiWifi 2.4Ghz | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HUAWEI-QVNe]] (600 root)
[connection] id=HUAWEI-QVNe | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-QVNe | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ASUS 1]] (600 root)
[connection] id=ASUS 1 | type=802-11-wireless
[802-11-wireless] ssid=ASUS | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DigiWifi 5Ghz]] (600 root)
[connection] id=DigiWifi 5Ghz | type=802-11-wireless
[802-11-wireless] ssid=DigiWifi 5Ghz | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Bucharest (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

virbr0    no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-65-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     D46E6565F844EFBD46CE0FC
depends:        cfg80211
vermagic:       3.19.0-65-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-65-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     381EA511B7BC282E4E24C0E
depends:        
intree:         Y
vermagic:       3.19.0-65-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9B:61:23:81:C2:74:1F:1D:FD:FE:7D:9E:98:8A:BE:98:59:16:70:2A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0042 (ath10k_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.845096] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.848517] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.949427] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   17.949476] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.892412] r8169 0000:02:00.0 eth0: link up
[   20.892420] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-07-26
Does ```
sudo modprobe -v ath10k_pci
``` give an error about required key not available?  If so disable Secure Boot in BIOS

---

### Post by cg.c on 2016-07-26
No error

---

### Post by jeremy31 on 2016-07-26
What is the result of ```
ls | grep backports; modinfo ath10k_pci
```

---

### Post by cg.c on 2016-07-26
```
backports-20150903
backports-20150903b.tar.gz
backports-20151120
filename:       /lib/modules/3.19.0-65-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     06FDAE7EFB4CDD527508269
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core
intree:         Y
vermagic:       3.19.0-65-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9B:61:23:81:C2:74:1F:1D:FD:FE:7D:9E:98:8A:BE:98:59:16:70:2A
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


```

---

### Post by jeremy31 on 2016-07-26
You must have used backports in the past to make it work
```
sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make
sudo make install
```

Reboot

If you loose wifi after a reboot it is likely that a new kernel was installed and you will need to

```

cd backports-4.4.2-1
make clean
make defconfig-wifi
make
sudo make install
```

Reboot

---

### Post by cg.c on 2016-07-26
Thanks, my wifi started working :-D

Just 2 questions....

1) You said if I lose my wifi after a reboot.... can happen often or rare?

2) I will lose my wifi after every update I will make? because everytime when in my launcher appear an update and I make it, my wifi is gone :-(

---

### Post by jeremy31 on 2016-07-26
You will lose wifi only after a reboot following a kernel update and I don't know how often they will happen. With 16.04 this is not an issue because backports are not needed and wifi should work after linux-firmware is updated with the newer version

---


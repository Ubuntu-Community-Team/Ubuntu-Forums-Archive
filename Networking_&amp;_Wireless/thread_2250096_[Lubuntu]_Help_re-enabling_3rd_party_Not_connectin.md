---
title: "[Lubuntu] Help re-enabling 3rd party? Not connecting to Wi-Fi after upgrade to 14.10"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by raen on 2014-10-26
[Currently have the Ethernet physically plugged into my netbook.]

This seems to be a perennial problem for me (although miraculously enough it wasn't an issue when I upgraded to 14.04). I did try to [back-reference the solution that worked for me previously]("http://ubuntuforums.org/showthread.php?t=2134147"), but it doesn't apply anymore. Under the "Additional Drivers" tab in the "Software & Updates" panel, it says:

```
O Broadcom Corporation: BCM4312 802.11b/g LP-PHY (T77H106.00 Wireless Half-size Mini PCIe Card)
     This device is using an alternative driver.
     o Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary) //selected
     o Do not use the device

```Underneath, it says:
1 proprietary driver in use.

Before the upgrade commenced, it did pop up a notice that I should re-enable 3rd party capabilities afterward with either the `software-properties` tool or the package manager, but I'm not sure how to do that.

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)

```




```



########## wireless info START ##########


Report from: 26 Oct 2014 15:28 EDT -0400


Booted last: 26 Oct 2014 11:04 EDT -0400


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]


03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c


##### lsusb #############################


Bus 001 Device 002: ID 04f2:b175 Chicony Electronics Co., Ltd 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18777  2 i915,acer_wmi
wmi                    18590  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe7a:5cf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11580 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:7425664 (7.4 MB)  TX bytes:2339463 (2.3 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search wowway.com


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.140
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             64.233.217.2
    DNS:             64.233.217.3


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


[[/etc/NetworkManager/system-connections/Redacted-1]] (600 root)
[connection] id=Redacted-1 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Redacted-2]] (600 root)
[connection] id=Redacted-2 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Redacted-3]] (600 root)
[connection] id=Redacted-3 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Redacted-4]] (600 root)
[connection] id=Redacted-4 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Redacted-5]] (600 root)
[connection] id=Redacted-5 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-5 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Redacted-6]] (600 root)
[connection] id=Redacted-6 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-6 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Redacted-7]] (600 root)
[connection] id=Redacted-7 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-7 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Redacted-8]] (600 root)
[connection] id=Redacted-8 | type=802-11-wireless
[802-11-wireless] ssid=Redacted-8 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


loop
lp


##### modprobe options ##################


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


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
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############

```

If I forgot to include anything, let me know. Thanks.

---

### Post by raen on 2014-10-27
It's been a day and this has dropped off the front page, so *bump*.

I don't know if I'm Googling the wrong thing or if I'm the only one with this problem, but my top search result is this thread. :cry: I'm between doing a fresh install of lubuntu 14.10, a fresh install of lubuntu 14.04.1, or a fresh install of xubuntu 14.10 (on the off chance that distro doesn't have these bugs I've been wrestling with). I'm also experiencing the "[notification dialogue has horizontal bars]("https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd/+bug/1362555")" bug, but the fix in comment #6 didn't help.

---

### Post by chili555 on 2014-10-27
What does the Broadcom sticky suggest is the correct driver for your device?

---

### Post by raen on 2014-10-27
> **chili555 said:**
> What does the Broadcom sticky suggest is the correct driver for your device?

```

$ lspci -nn -d 14e4:
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

```

pci.id                     12.04 LTS                                     14.04 LTS
14e4:4315             firmware-b43-lpphy-installer          firmware-b43-installer

```

Not really sure where to go from there. I'm not as savvy as other *nix users. Also, I'm not sure how much to apply from the "going from 12.04 to 14.04" sticky to my going from 14.04 to 14.10.

Thanks.

---

### Post by chili555 on 2014-10-27
With the internet temporarily enabled, open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get purge bcmwl-kernel-source 
```Reboot and let us have your report.

---

### Post by raen on 2014-10-27
> **chili555 said:**
> Reboot and let us have your report.

It worked. :grin:

Thank you! ):P

---


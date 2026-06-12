---
title: "No Available Wifi - Lenovo Y50, Ubuntu 14.04 Trusty"
date: 2017-02-03
forum: Networking &amp; Wireless
---

### Post by pvtwojtek on 2017-02-03
Hello, I have been using Ubuntu for about 6 months with no problems.  Recently, I have been trying to get a bluetooth issue sorted out and my last round of attempts seemed to have lost all Wifi capabilities for this laptop.  The last bit of commands I ran is the following:

```

[COLOR=#000000][FONT=&amp]sudo apt-get install --reinstall linux-headers-generic build-essential
[/FONT][/COLOR]
```

then I downloaded the latest backport drivers from [http://drvbp1.linux-foundation.org/~...tml/backports/]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/") and executed the following code:

```

cd Desktop/backports-4.2.6-1
make defconfig-ath9k
make
sudo make install
```

These suggestions came from the following thread: [https://ubuntuforums.org/showthread.php?t=2251009](https://ubuntuforums.org/showthread.php?t=2251009)

I am not worried about fixing my bluetooth issues right now, just getting my wireless back up and running.  Here is the output from my wireless_info.txt file:

```



########## wireless info START ##########


Report from: 03 Feb 2017 09:34 CST -0600


Booted last: 03 Feb 2017 09:30 CST -0600


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 4.4.0-62-generic #83~14.04.1-Ubuntu SMP Wed Jan 18 18:10:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 005: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 003 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 5986:055e Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:165.134.18.86  Bcast:165.134.18.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:817225 (817.2 KB)  TX bytes:172628 (172.6 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         165.134.18.254  0.0.0.0         UG    0      0        0 eth0
165.134.18.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search ds.slu.edu


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root       992     1  0 09:30 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         165.134.18.86
    Prefix:          24 (255.255.255.0)
    Gateway:         165.134.18.254


    DNS:             165.134.246.4
    DNS:             165.134.246.2
    DNS:             165.134.234.6
    DNS:             165.134.38.4


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


[[/etc/NetworkManager/system-connections/NETGEAR54]] (600 root)
[connection] id=NETGEAR54 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR54 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto
[802-1x] ca-cert=/home/kyle/.joinnow/campusca.pem


[[/etc/NetworkManager/system-connections/SOE-Robots]] (600 root)
[connection] id=SOE-Robots | type=802-11-wireless
[802-11-wireless] ssid=SOE-Robots | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR54-5G]] (600 root)
[connection] id=NETGEAR54-5G | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR54-5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SLU-users]] (600 root)
[ipv6] method=auto
[connection] id=SLU-users | type=802-11-wireless
[802-11-wireless] ssid=SLU-users | mac-address=<MAC address>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Welcome to SIUE]] (600 root)
[connection] id=Welcome to SIUE | type=802-11-wireless
[802-11-wireless] ssid=Welcome to SIUE | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Maeva's Coffee Guests]] (600 root)
[connection] id=Maeva's Coffee Guests | type=802-11-wireless
[802-11-wireless] ssid=Maeva's Coffee Guests | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


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


[/etc/modprobe.d/ideapad.conf]
blacklist ideapad_laptop


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   30.888164] r8169 0000:09:00.0 eth0: link down
[   30.888221] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   53.349909] r8169 0000:09:00.0 eth0: link up
[   53.349917] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   94.758021] r8169 0000:09:00.0 eth0: link down (repeated 2 times)
[   95.317338] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   95.465317] r8169 0000:09:00.0 eth0: link down
[   95.465378] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.928659] r8169 0000:09:00.0 eth0: link up
[  120.928666] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############



```


I am definitely stumped with this one, so any help will be greatly appreciated!  Please feel free to reply with any additional information you might need.

Thanks!

---

### Post by wildmanne39 on 2017-02-03
No big mystery you have an intel card and you installed the ath9k atheos driver.

Did you uninstall your original driver before installing the wrong one?

Please do:
```
cd Desktop/backports-4.2.6-1
sudo make uninstall
```
Reboot, if your wifi does not come on do:
```
sudo modprobe -v iwlwifi
```
post any errors.
Thanks

---

### Post by praseodym on 2017-02-03
Typo, its

```
sudo modprobe -v iwlwifi
```

Check also
```

dmesg | grep iwl
```afterwards

---


---
title: "wifi not working in my ubuntu 14.04 LTS"
date: 2015-10-11
forum: Networking &amp; Wireless
---

### Post by shivank1969 on 2015-10-11
I need help in getting the WiFi to show in the ubuntu and help getting the WiFi to connect. 

Here is the script below.

```



########## wireless info START ##########

Report from: 11 Oct 2015 23:47 IST +0530

Booted last: 11 Oct 2015 23:05 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3826]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

04:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Venus XTX [Radeon HD 8890M] [1002:6820] (rev ff)

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 003: ID 174f:14ee Syntek 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wmi                    19177  0 
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.100.21  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27216317 (27.2 MB)  TX bytes:2177122 (2.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

    NetworkManager

Running:

root       762     1  0 23:05 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ethernet connection 2] ----------------------------------------
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
    Address:         192.168.100.21
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1

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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 6]] (600 root)
[connection] id=Wi-Fi connection 6 | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 4]] (600 root)
[connection] id=Wi-Fi connection 4 | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 3]] (600 root)
[connection] id=Wi-Fi connection 3 | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=shi
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 2]] (600 root)
[connection] id=Wi-Fi connection 2 | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 5]] (600 root)
[connection] id=Wi-Fi connection 5 | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/bc-227_1]] (600 root)
[connection] id=bc-227_1 | type=802-11-wireless
[802-11-wireless] ssid=bc-227_1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/middle]] (600 root)
[connection] id=middle | type=802-11-wireless
[802-11-wireless] ssid=middle
[ipv4] method=auto
[ipv6] method=auto

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

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[  244.523021] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[  244.523114] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[  247.214925] r8169 0000:02:00.0 eth0: link up
[  247.214940] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

Please help me to resove the problem.
Thanks in Advance.

---

### Post by cariboo on 2015-10-11
You marked the thread Solved, can you tell us what you did to solve your problem?

---

### Post by jeremy31 on 2015-10-12
This should get it going


```

echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
sudo apt-get install build-essential linux-headers-$(uname -r) git
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz
tar -zxvf backports-20150903.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
git clone https://github.com/atondwal/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
```

Reboot and wifi should work


If you get a new kernel, your wireless will quit working until the new kernel contains the fix, if you notice wifi isn't working after a reboot 
```
cd backports-20150903
make clean
make defconfig-ath10k
make
sudo make install
```


Reboot

---

### Post by slickymaster on 2015-10-12
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by shivank1969 on 2015-10-12
I have not marked the thread solved.

---

### Post by shivank1969 on 2015-10-12
[COLOR=#000000]Hey , jeremy31 what should i do with the code given by you ?
Should I run this code in Terminal?[/COLOR]

---

### Post by slickymaster on 2015-10-12
> **shivank1969 said:**
> [COLOR=#000000]I have not marked the thread solved.[/COLOR]
The thread was marked as solved since you open it. You've probably done it inadvertently.

Anyway you can remove it by scrolling to the top of your thread and look for the Thread Tools menu item on the right of the toolbar.

---

### Post by jeremy31 on 2015-10-12
Run in terminal, one line at a time

---

### Post by shivank1969 on 2015-10-12
Thanks jeremy31 for the help. Now my laptop wifi is running perfectly.

---


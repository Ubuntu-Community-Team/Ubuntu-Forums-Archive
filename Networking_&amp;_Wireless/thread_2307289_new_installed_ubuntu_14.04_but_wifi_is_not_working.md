---
title: "new installed ubuntu 14.04 but wifi is not working"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by Junpu_Fan on 2015-12-23
```
########## wireless info START ##########

Report from: 23 Dec 2015 14:27 EST -0500

Booted last: 23 Dec 2015 14:25 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1010]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3831]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b512 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  1 nouveau
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2750726 (2.7 MB)  TX bytes:268142 (268.1 KB)

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

##### network managers ##################

Installed:

    NetworkManager

Running:

root       791     1  0 14:25 ?        00:00:00 NetworkManager

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
    Address:         192.168.1.31
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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Indiana/Indianapolis (based on set time zone)

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
alias net-pf-9 off[PHP][/PHP]
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

[   28.112477] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[   28.112482] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2

########## wireless info END ######
```

Thanks for any help!

---

### Post by Hadaka on 2015-12-23
hi please open a terminal and do..
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
boot and test
*If that helps then from a working wirered connection
copy and paste..
```
sudo apt-get update
suo apt-get dist-upgrade
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
thanks.

---

### Post by Junpu_Fan on 2015-12-23
Hi, thanks for trying to help. the wifi is still not working. I have regenerated the wireless report.

```
########## wireless info START ##########

Report from: 23 Dec 2015 15:02 EST -0500

Booted last: 23 Dec 2015 15:01 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1010]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3831]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b512 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  1 nouveau
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1168996 (1.1 MB)  TX bytes:116327 (116.3 KB)

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

##### network managers ##################

Installed:

    NetworkManager

Running:

root       781     1  0 15:01 ?        00:00:00 NetworkManager

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
    Address:         192.168.1.31
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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Indiana/Indianapolis (based on set time zone)

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
blacklist ideapad-laptop

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

[    2.241512] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    2.241517] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    2.299313] r8169 0000:09:00.0 eth0: link down (repeated 2 times)
[    2.299406] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.692642] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    3.692646] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    3.929380] r8169 0000:09:00.0 eth0: link up
[    3.929386] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by Hadaka on 2015-12-23
you are still showing hard blocks...
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
Please do those commands again and also look for a physical or keyboard wifi switch.
thanks.

---

### Post by Junpu_Fan on 2015-12-23
```
########## wireless info START ##########

Report from: 23 Dec 2015 16:03 EST -0500

Booted last: 23 Dec 2015 16:02 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Device [8086:1010]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo Device [17aa:3831]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b512 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

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

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98117 (98.1 KB)  TX bytes:61110 (61.1 KB)

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

##### network managers ##################

Installed:

    NetworkManager

Running:

root       776     1  0 16:02 ?        00:00:00 NetworkManager

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
    Address:         192.168.1.31
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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: America/Indiana/Indianapolis (based on set time zone)

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
blacklist ideapad-laptop
blacklist ideapad-laptop

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

[    2.259364] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    2.259368] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    2.333958] r8169 0000:09:00.0 eth0: link down (repeated 2 times)
[    2.334264] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.745239] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv117_fuc409c failed with error -2
[    3.745244] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    4.041415] r8169 0000:09:00.0 eth0: link up
[    4.041422] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

now the blacks are gone thanks for your help.

I wonder what does this means?

eth0      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by praseodym on 2015-12-23
Load the driver by hand:
```

sudo modprobe -v iwlwifi
sudo rfkill unblock all
```
Any button, switch, key or key combination to turn wifi on?

---

### Post by Junpu_Fan on 2015-12-23
hi praseodym, thanks for sharing, I ran these code in the terminal. And the switch is no, I also have a windows10 installed in this computer, the wifi works just fine.

I wonder what does this means?

eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by jeremy31 on 2015-12-23
Show ```
modinfo iwlwifi | grep 1010
```
I don't think the wifi is supported by your current kernel but we can use backports

---

### Post by Junpu_Fan on 2015-12-23
hi jeremy31, this is what the terminal shows
```
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*


```

---

### Post by praseodym on 2015-12-23
```
modprobe -c | grep -i "8086.*24f3"
alias pci:v00008086d000024F3sv*sd00000010bc*sc*i* iwlwifi
```
and
```
modprobe -c | grep -i "8086.*1010"
alias pci:v00008086d0000095Asv*sd00001010bc*sc*i* iwlwifi
```
Driver is correct. Check if Windows deactivates the card when shutting down. Also check if wireless can be activated by default in your BIOS/UEFI and/or if the network can be booted there before the OS.

---

### Post by lisati on 2015-12-23
@junpu_fan: I've edit some of your posts to use CODE tags. Doing so helps preserve formatting and can make a massive output easier to read.

---

### Post by Junpu_Fan on 2015-12-23
The Wireless in the BIOS is currently enabled.

```
junpu@junpu-Lenovo-ideapad-Y700-15ISK:~$ modprobe -c | grep -i "8086.*24f3"
alias pci:v00008086d000024F3sv*sd00000004bc*sc*i* iwlwifi
alias pci:v00008086d000024F3sv*sd00000010bc*sc*i* iwlwifi

junpu@junpu-Lenovo-ideapad-Y700-15ISK:~$ alias pci:v00008086d000024F3sv*sd00000010bc*sc*i* iwlwifi
bash: alias: pci:v00008086d000024F3sv*sd00000010bc*sc*i*: not found
bash: alias: iwlwifi: not found

junpu@junpu-Lenovo-ideapad-Y700-15ISK:~$ modprobe -c | grep -i "8086.*1010"
alias pci:v00008086d0000095Asv*sd00001010bc*sc*i* iwlwifi
alias pci:v00008086d00001010sv*sd*bc*sc*i* e1000

junpu@junpu-Lenovo-ideapad-Y700-15ISK:~$ alias pci:v00008086d0000095Asv*sd00001010bc*sc*i* iwlwifi
bash: alias: pci:v00008086d0000095Asv*sd00001010bc*sc*i*: not found
bash: alias: iwlwifi: not found


```

---

### Post by Junpu_Fan on 2015-12-23
Thanks, I know how to use Code tag now.

---

### Post by jeremy31 on 2015-12-23
```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-8000-ucode-25.30.13.0.tgz
tar -zxvf iwlwifi-8000-ucode-25.30.13.0.tgz
cd iwlwifi-8000-ucode-25.30.13.0
sudo cp iwlwifi*.ucode /lib/firmware/iwlwifi-8000-13.ucode
cd ~
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz
tar -zxvf backports-4.3-1.tar.gz
cd backports-4.3-1
make defconfig-iwlwifi
make
sudo make install
```

Reboot and wifi should work

---

### Post by Junpu_Fan on 2015-12-23
Yes! it worked! Thank you so much jeremy31!

Could you briefly explain what was happening please?

I kind understand that I was downloading a driver and installed it, then it worked.

---

### Post by jeremy31 on 2015-12-23
Your 3.19 kernel didn't support your wifi card and I suspected that you didn't have the firmware either

Your results of my command was ```
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
```
And to support the wifi card it should have been ```
alias:          pci:v00008086d000024F3sv*sd00001010bc*sc*i*
```

The backports was the simplest route to fix but if updates happen to install a new kernel that still doesn't support your wifi, you will need to
```
cd backports-4.3-1
make clean
make defconfig-iwlwifi
make
sudo make install
```

---

### Post by Junpu_Fan on 2015-12-23
Thanks jeremy31 and everyone who helped. I started to like the Ubuntu community now.

---

### Post by jeremy31 on 2015-12-23
Use the Thread Tools dropdown at the top of the page to "Mark as Solved"

---

### Post by praseodym on 2015-12-23
Great Job@Jeremy :)

"linux-firmware" of Wily and Xenial contain that firmware, but also named with "C":

[http://packages.ubuntu.com/xenial/all/linux-firmware/filelist](http://packages.ubuntu.com/xenial/all/linux-firmware/filelist)

How did you have the idea to rename it without "C"?

```
/lib/firmware/iwlwifi-8000C-13.ucode
/lib/firmware/iwlwifi-8000C-16.ucode
```
If its the same one we can simply install the xenial package in the future.

---

### Post by jeremy31 on 2015-12-23
A guess based on the source code in the backports

---


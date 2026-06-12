---
title: "WiFi and Ethernet not working."
date: 2018-05-10
forum: Networking &amp; Wireless
---

### Post by addngkr on 2018-05-10
I mistakenly un-installed the network-manager, wpasupplicant and following packages (**attached in** package-history.jpg)

I have now successfully reinstalled them except network-manager-gnome. All my attempts to reinstall it end up with a broken network-manager-gnome.

However, when i tried to connect to internet through commands i failed. 

WiFi and ethernet are no longer showing in the ifconfig. please find the following info : 

```


########## wireless info START ##########

Report from: 10 May 2018 15:18 IST +0530

Booted last: 10 May 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-36-generic #40~16.04.1-Ubuntu SMP Fri Feb 16 23:25:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]

05:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lenovo Device [17aa:0901]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 04f2:b5c0 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0781:5590 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:551808 (551.8 KB)  TX bytes:551808 (551.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       846     1  0 14:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Superior-Eero]] (600 root)
[connection] id=Superior-Eero | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Superior-Eero
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sltest]] (600 root)
[connection] id=sltest | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sltest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Medipoint]] (600 root)
[connection] id=Medipoint | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Medipoint
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Superior]] (600 root)
[connection] id=Superior | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Superior
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DLINK_WIRELESS]] (600 root)
[connection] id=DLINK_WIRELESS | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DLINK_WIRELESS
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JioFi2_A3FDE1]] (600 root)
[connection] id=JioFi2_A3FDE1 | type=wifi | autoconnect=false | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=JioFi2_A3FDE1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ab1#!$%]] (600 root)
[connection] id=Ab1#!$% | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ab1#!$%
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Moto E³ POWER 1117]] (600 root)
[connection] id=Moto E³ POWER 1117 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=77;111;116;111;32;69;194;179;32;80;79;87;69;82;32;49;49;49;55;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi 3S]] (600 root)
[connection] id=Redmi 3S | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi 3S
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Moto C 5836]] (600 root)
[connection] id=Moto C 5836 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Moto C 5836
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AAAAALN9MjQAAwGaRedmi 3S]] (600 root)
[connection] id=AAAAALN9MjQAAwGaRedmi 3S | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AAAAALN9MjQAAwGaRedmi 3S
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=wifi | permissions=user:adarsh:;
[wifi] bssid=<MAC address> | mac-address=B0:52:16:28:20:B7 | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PAPPILON PALACE 3]] (600 root)
[connection] id=PAPPILON PALACE 3 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PAPPILON PALACE 3
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[    7.536209] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############


```

**attached **wireless-info.txt

I no longer understand what has gone wrong! What do I do?

---

### Post by jeremy31 on 2018-05-10
Try command ```
locate ath10k_pci
```
If this has any results reboot and use a kernel that was listed in results from the grub menu advanced options

---

### Post by addngkr on 2018-05-10
Nothing turned up from locate command.

---

### Post by praseodym on 2018-05-10
Please show
```

dpkg -l linux-image-* | grep ii
```

---

### Post by addngkr on 2018-05-10
> **praseodym said:**
> Please show
```

dpkg -l linux-image-* | grep ii
```

Hi, please find the output from the mentioned command

```

dpkg -l linux-image-* | grep ii
ii  linux-image-4.13.0-32-generic       4.13.0-32.35~16.04.1 amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-36-generic       4.13.0-36.40~16.04.1 amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic        4.4.0-21.37          amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic  4.4.0-21.37          amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                 4.4.0.21.22          amd64        Generic Linux kernel image

```

---

### Post by praseodym on 2018-05-10
[https://packages.ubuntu.com/xenial/linux-image-extra-4.13.0-32-generic](https://packages.ubuntu.com/xenial/linux-image-extra-4.13.0-32-generic)

Download and install the respective 32 or 64bit package, install it and reboot. Drivers are missing

---

### Post by addngkr on 2018-05-10
> **praseodym said:**
> [https://packages.ubuntu.com/xenial/linux-image-extra-4.13.0-32-generic](https://packages.ubuntu.com/xenial/linux-image-extra-4.13.0-32-generic)

Download and install the respective 32 or 64bit package, install it and reboot. Drivers are missing

Um, still facing the same issue. ifconfig shows I've only got loopback running. No Ethernet and wireless. Could you please check if it could be due to one or more packages in "package-history.jpg" image attached? I have re-installed all the missing packages except network-manager-gnome, which is broken.

---

### Post by jeremy31 on 2018-05-10
See if you can boot into the 4.4.0-21 kernel and have the interfaces show up

---

### Post by praseodym on 2018-05-10
Please run

```
sudo modprobe -v r8169
sudo modprobe -v ath10k_pci
dmesg | egrep 'r8|ath'
```

---

### Post by axiomanarcho on 2018-05-10
> **addngkr said:**
> I mistakenly un-installed the network-manager, wpasupplicant and following packages (**attached in** package-history.jpg)

I have now successfully reinstalled them except network-manager-gnome. All my attempts to reinstall it end up with a broken network-manager-gnome.

However, when i tried to connect to internet through commands i failed. 

WiFi and ethernet are no longer showing in the ifconfig. please find the following info : 

```


########## wireless info START ##########

Report from: 10 May 2018 15:18 IST +0530

Booted last: 10 May 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-36-generic #40~16.04.1-Ubuntu SMP Fri Feb 16 23:25:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]

05:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lenovo Device [17aa:0901]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 003: ID 04f2:b5c0 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0781:5590 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:551808 (551.8 KB)  TX bytes:551808 (551.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       846     1  0 14:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Superior-Eero]] (600 root)
[connection] id=Superior-Eero | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Superior-Eero
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sltest]] (600 root)
[connection] id=sltest | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=sltest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Medipoint]] (600 root)
[connection] id=Medipoint | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Medipoint
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Superior]] (600 root)
[connection] id=Superior | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Superior
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DLINK_WIRELESS]] (600 root)
[connection] id=DLINK_WIRELESS | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DLINK_WIRELESS
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JioFi2_A3FDE1]] (600 root)
[connection] id=JioFi2_A3FDE1 | type=wifi | autoconnect=false | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=JioFi2_A3FDE1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Ab1#!$%]] (600 root)
[connection] id=Ab1#!$% | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ab1#!$%
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Moto E³ POWER 1117]] (600 root)
[connection] id=Moto E³ POWER 1117 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=77;111;116;111;32;69;194;179;32;80;79;87;69;82;32;49;49;49;55;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi 3S]] (600 root)
[connection] id=Redmi 3S | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi 3S
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Moto C 5836]] (600 root)
[connection] id=Moto C 5836 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Moto C 5836
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AAAAALN9MjQAAwGaRedmi 3S]] (600 root)
[connection] id=AAAAALN9MjQAAwGaRedmi 3S | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AAAAALN9MjQAAwGaRedmi 3S
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=wifi | permissions=user:adarsh:;
[wifi] bssid=<MAC address> | mac-address=B0:52:16:28:20:B7 | mac-address-blacklist= | ssid=linksys
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PAPPILON PALACE 3]] (600 root)
[connection] id=PAPPILON PALACE 3 | type=wifi | permissions=user:adarsh:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PAPPILON PALACE 3
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[    7.536209] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

########## wireless info END ############


```

**attached **wireless-info.txt

I no longer understand what has gone wrong! What do I do?

Have you tried installing the r8168-dkms it needs to built into the kernel drivers.
sudo apt-get install r8168-dkms

[https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://unixblogger.com/2016/08/11/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

Thats a solution for your ethernet driver...

---

### Post by axiomanarcho on 2018-05-10
If you can't get a hold of the driver... by internet means download the package manually from repos and put on usb.... 

[https://packages.ubuntu.com/xenial/all/r8168-dkms/download](https://packages.ubuntu.com/xenial/all/r8168-dkms/download)

---

### Post by axiomanarcho on 2018-05-10
After you install the DKMS file can you please do 

ifconfig command in terminal see if we get any "UP,BROADCAST,RUNNING,MULTICAST"

---

### Post by addngkr on 2018-05-11
Hi, the issue got resolved. I reinstalled all the hwe packages that had gone missing. Ethernet and WiFi are up now! 

Thanks!

---


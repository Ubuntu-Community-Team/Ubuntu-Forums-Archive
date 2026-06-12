---
title: "Ubuntu 16.04 - Connection not working after updates"
date: 2017-05-03
forum: Networking &amp; Wireless
---

### Post by carlo8 on 2017-05-03
Hi guys, as mentioned in the title, yesterday I installed a few suggested updates, and since I restarted I can't connect to Internet.
The Wi-Fi icon is still present in the menu, but when I click on it, it doesn't show any available network.
I tried to connect using an ethernet cable, but nothing changes.

If it's any use, I ran the wireless-info script, this is the output

```



########## wireless info START ##########


Report from: 03 May 2017 12:09 CEST +0200


Booted last: 03 May 2017 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:81ef]


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Sanji2 
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:81c1]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b56c Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:b008 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


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


root      2508     1  0 11:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


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


[[/etc/NetworkManager/system-connections/BadMoos_Guest]] (600 root)
[connection] id=BadMoos_Guest | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BadMoos_Guest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Osservatorio]] (600 root)
[connection] id=Osservatorio | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Osservatorio
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NOKIA Lumia 625_6986 1]] (600 root)
[connection] id=NOKIA Lumia 625_6986 1 | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NOKIA Lumia 625_6986
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/units]] (600 root)
[connection] id=units | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=units
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telecom-56411965]] (600 root)
[connection] id=Telecom-56411965 | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Telecom-56411965
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NOKIA Lumia 625_6986]] (600 root)
[connection] id=NOKIA Lumia 625_6986 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NOKIA Lumia 625_6986
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam-80e4b56c-8a43-4ced-b47a-d26d0092e342]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:carlo:;
[wifi] mac-address-blacklist= | ssid=eduroam
[802-1x] ca-cert=/home/carlo/.cat_installer/ca.pem
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/rtmcopisteria]] (600 root)
[connection] id=rtmcopisteria | type=wifi | permissions=user:carlo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=rtmcopisteria
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


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


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be ips=0 fwlps=0 ant_sel=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    4.320189] systemd[1]: Set hostname to <carlo-HP-Notebook>.
[    6.221840] systemd[1]: Started Trigger resolvconf update for networkd DNS.


########## wireless info END ############



```

I'm still a newbie on Ubuntu....anyone can help?
Thanks!

---

### Post by slickymaster on 2017-05-03
See this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

You'll have to revert to an older kernel until the bug is fixed.

---

### Post by carlo8 on 2017-05-03
Thanks a lot, it works by reverting to 4.4.0-75 from Grub.
At this point, should I wait until they fix the bug and then update the system from 4.4.0-75?

---

### Post by slickymaster on 2017-05-03
You can try to run ```
sudo apt update && sudo apt upgrade
```to see if you get some missing kernel additions, like modules for ethernet and wireless. Then reboot kernel 4.4.0-77 to check. If not you'll have to wait.

---

### Post by carlo8 on 2017-05-03
It works fine again after booting to a previous kernel version and using

```

sudo apt-get update && sudo apt-get dist-upgrade

```


thanks again for the help!

---


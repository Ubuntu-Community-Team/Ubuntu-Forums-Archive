---
title: "No wired connection &amp; no wifi adapter found after software update"
date: 2021-12-21
forum: Networking &amp; Wireless
---

### Post by ea24 on 2021-12-21
[COLOR=#000000]

Using Ubuntu 20.04.3 LTS on Lenovo Ideapad 510-15isk. (I'm new to Linux)[/COLOR]

[COLOR=#000000]After the software update both wired and wireless connections were lost. I followed the Method 2 in this [/COLOR][link]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385")[COLOR=#000000]. The content of the wireless-info.txt is copied below. I would appreciate any help.


[/COLOR]

```
########## wireless info START ##########


Report from: 21 Dec 2021 16:02 +03 +0300


Booted last: 21 Dec 2021 00:00 +03 +0300


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal


##### kernel ############################


Linux 5.11.0-41-generic #45~20.04.1-Ubuntu SMP Wed Nov 10 10:20:10 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3854]


02:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:3166] (rev 99)
	Subsystem: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:4210]


03:00.0 3D controller [0302]: NVIDIA Corporation GM108M [GeForce 940MX] [10de:134d] (rev a2)


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 5986:0711 Acer, Inc EasyCamera
Bus 001 Device 006: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot enabled


##### lsmod #############################


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad


##### network managers ##################


Installed:


	NetworkManager


Running:


root         758       1  0 15:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


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


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/umram-wifi.nmconnection]] (600 root)
[connection] id=umram-wifi | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=umram-wifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NIKOLA_TESLA_5GHz.nmconnection]] (600 root)
[connection] id=NIKOLA_TESLA_5GHz | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=NIKOLA_TESLA_5GHz
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


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


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/amddeepcolor-psychtoolbox.conf]
options radeon deep_color=1
options amdgpu deep_color=1


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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


[/etc/modprobe.d/blacklist-psychtoolbox.conf]
blacklist lp
install lp /bin/false


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


########## wireless info END ############

```

---

### Post by praseodym on 2021-12-21
Try
```

sudo modprobe -v r8169
sudo modprobe -v iwlwifi
dmesg | egrep 'r8|iwl'
```

---

### Post by ea24 on 2021-12-21
```
ecem@ecem-Lenovo-ideapad-510-15ISK:~$ sudo modprobe -v r8169
modprobe: FATAL: Module r8169 not found in directory /lib/modules/5.11.0-41-generic


ecem@ecem-Lenovo-ideapad-510-15ISK:~$ sudo modprobe -v iwlwifi
modprobe: ERROR: ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)


ecem@ecem-Lenovo-ideapad-510-15ISK:~$ dmesg | egrep 'r8|iwl'
[    0.032722] percpu: Embedded 56 pages/cpu s192512 r8192 d28672 u524288
[    0.032732] pcpu-alloc: s192512 r8192 d28672 u524288 alloc=1*2097152

```

---

### Post by praseodym on 2021-12-22
Driver files are  missing. Download these files and save them in "Downloads":

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-5.11.0-41-generic_5.11.0-41.45~20.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-5.11.0-41-generic_5.11.0-41.45~20.04.1_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-41-generic_5.11.0-41.45~20.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-41-generic_5.11.0-41.45~20.04.1_amd64.deb)

Installation
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot (network works?) and run

```
sudo apt-get install linux-generic
```

---

### Post by ea24 on 2021-12-22
This solved the problem. Many thanks!

---


---
title: "z490 ethernet issue"
date: 2021-02-01
forum: Networking &amp; Wireless
---

### Post by sediizz on 2021-02-01
Dear all.

I have bought 2 new pc. they both are z490 m/b (with wifi adaptor).
I ran into networking issues both pc cannot connect to the internet (not found either ethernet cable or wifi adaptor).
However, I need to use Kernel version 4.15 and ubuntu 18.04.

_1st pc Spec_
CPU: Intel I9-10900K
M/B: ASUS ROG STRIXX Z490-F Gaming
VGA: RTX3080
RAM: DDR4 16GB/3600x2
SSD: 2TB Samsung 970 Evo+
Wifi script output :
```


########## wireless info START ##########


Report from: 02 Feb 2021 05:58 +07 +0700


Booted last: 02 Feb 2021 00:00 +07 +0700


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


00:14.3 Network controller [0280]: Intel Corporation Device [8086:06f0]
    Subsystem: Intel Corporation Device [8086:0074]


00:16.0 Communication controller [0780]: Intel Corporation Device [8086:06e0]


05:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:15f3] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 2516:0015  
Bus 001 Device 003: ID 046d:c08f Logitech, Inc. 
Bus 001 Device 004: ID 1e71:2007 NZXT 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 007: ID 8087:0026 Intel Corp. 
Bus 001 Device 006: ID 048d:5702 Integrated Technology Express, Inc. 
Bus 001 Device 008: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,intel_wmi_thunderbolt,mxm_wmi,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


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


##### network managers ##################


Installed:


    NetworkManager


Running:


root       820     1  0 05:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


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
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


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


Region: Asia/Bangkok (based on set time zone)


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 1331.956889] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[ 1918.956024] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2


########## wireless info END ############



```

_2nd pc Spec_
CPU: Intel I7-10700K
M/B: ASROCK Z490 STEEL LEGEND
VGA: RTX3070
RAM: DDR4 16GB/3200x2
SSD: 1TB WD Blue M.2 NVMe
Wifi script output :
```


########## wireless info START ##########


Report from: 02 Feb 2021 05:02 +07 +0700


Booted last: 02 Feb 2021 00:00 +07 +0700


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:8125] (rev 05)
    Subsystem: ASRock Incorporation Device [1849:8168]


04:00.0 Non-Volatile memory controller [0108]: Sandisk Corp Device [15b7:5009] (rev 01)


##### lsusb #############################


Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 004: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 003: ID 046d:c08f Logitech, Inc. 
Bus 001 Device 002: ID 2516:0015  
Bus 001 Device 006: ID 26ce:01a2  
Bus 001 Device 005: ID 1e71:2007 NZXT 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


wmi_bmof               16384  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  1 nouveau
wmi                    24576  4 wmi_bmof,intel_wmi_thunderbolt,mxm_wmi,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


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


##### network managers ##################


Installed:


    NetworkManager


Running:


root       693     1  0 05:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


Sorry, try again.
cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


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
unmanaged-devices=*,except:type:wifi,except:type:wwan


[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/


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


Region: Asia/Bangkok (based on set time zone)


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   78.907929] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2


########## wireless info END ############



```[COLOR=#000000]

I think there is a driver compatibility problem.
Thank you in advance.[/COLOR]

---

### Post by praseodym on 2021-02-07
1st spec: Wifi card could be too new for kernel 4.15. Try installing this package:

[https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi/+files/backport-iwlwifi-dkms_8324-0ubuntu1~latest~ubuntu18.04.1_all.deb](https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi/+files/backport-iwlwifi-dkms_8324-0ubuntu1~latest~ubuntu18.04.1_all.deb)

and reboot. Wifi works? For LAN here, check

```
sudo modprobe -rfv e1000e
sudo modprobe -v e1000e
dmesg | egrep 'e1|iwl'
```

2nd spec: No wifi card (?!) but Realtek LAN which is too new as well. You need an external driver here. Download this file and save it to "Downloads":

[https://media-cdn.ubuntu-de.org/forum/attachments/27/49/9210307-r8125-dkms_9.004.01.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/27/49/9210307-r8125-dkms_9.004.01.tar.gz)

Installation:```

cd ~/Downloads/
sudo tar xvf 9210307-r8125-dkms_9.004.01.tar.gz -C /usr/src
sudo dkms add -m r8125 -v 9.004.01
sudo dkms build -m r8125 -v 9.004.01
sudo dkms install -m r8125 -v 9.004.01 
sudo depmod -a
sudo update-initramfs -u
sudo modprobe -v r8125 
```

Please report any errors

---


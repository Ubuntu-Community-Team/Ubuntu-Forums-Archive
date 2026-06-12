---
title: "Fresh 18.04 Install on Gigabyte H270-HD3 - No Ethernet Connection"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by nfgallimore on 2019-01-31
Hello,

I have never posted here before and I have looked at almost every post regarding Gigabyte motherboards and the ethernet not working. 

First off, I had to add nomodeset to the grub command line, and now I can actually get past seeing just a black screen.

 However, now that I am this far, the ethernet is not working.

 I have seen some other posts regarding gigabyte motherboards but they all talk about disabling IOMMU in bios and setting it to "soft" in the grub command line arguments. See [https://ubuntuforums.org/showthread.php?t=2347115](https://ubuntuforums.org/showthread.php?t=2347115) 

However, this is a different motherboard (H270-HD3) and I am not seeing any option to disable IOMMU under the peripherals section. 

I added the grub argument for IOMMU, but the ethernet still does not work. 

Attached I have ran the wireless info script, however this is a desktop and I have no concerns about wireless, just ethernet. 

What else can I do?

---

### Post by nfgallimore on 2019-01-31
```
########## wireless info START ##########


Report from: 31 Jan 2019 10:01 EST -0500


Booted last: 31 Jan 2019 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, iommu=soft, nomodeset, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I219-V [1458:e000]
    Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 003: ID 1532:0053 Razer USA, Ltd 
Bus 001 Device 002: ID 2516:0020  
Bus 001 Device 006: ID 1532:0504 Razer USA, Ltd 
Bus 001 Device 008: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 005: ID 1e71:170e NZXT 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto eth0
iface eth0 inet dhcp


auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>


##### iwconfig ##########################


enp0s31f6  no wireless extensions.


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       713     1  0 09:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   afd965fe-0171-3792-a808-6b65fb74aceb | Wired connection 1


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


Region: America/New_York (based on set time zone)


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


enp0s31f6  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp0s31f6  Interface doesn't support scanning.


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   22.551164] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[   25.926394] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   25.926463] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready


########## wireless info END ############
```

---

### Post by praseodym on 2019-01-31
> ```
[/etc/network/interfaces]
auto eth0
iface eth0 inet dhcp


auto lo
iface lo inet loopback
```
Revert that file with those (false!) entries:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot

---

### Post by nfgallimore on 2019-01-31
I reverted it but I only made those changes trying to fix it. Note, on the live USB the ethernet works fine. Also no black screen.

---

### Post by nfgallimore on 2019-01-31
Router wasn't giving out an IP-address for the desktop. Restarted router. Problem solved.

---


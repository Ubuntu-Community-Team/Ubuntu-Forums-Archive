---
title: "Network Adapter not found, no idea what to do"
date: 2022-01-18
forum: Networking &amp; Wireless
---

### Post by RJLiberator on 2022-01-18
[COLOR=#000000]I have:[/COLOR]

[COLOR=#000000]- Ubuntu 20.04.2 LTS installed[/COLOR]
[COLOR=#000000]- 802.11AC 1200Mbps USB Wireless Network Adapter is the hardware ( [/COLOR][Link]("https://www.amazon.com/dp/B07V4R3QHW?psc=1&ref=ppx_yo2_dt_b_product_details")[COLOR=#000000] )[/COLOR]

[COLOR=#000000]I have a dual-boot system running Windows OS on the other boot and it works flawlessly there.[/COLOR]
[COLOR=#000000]I have no way to get a wired connection to my Ubuntu OS.[/COLOR]

[COLOR=#000000]I've tried a few things:[/COLOR]

[COLOR=#000000]1) Tried manually installing the driver through google search ( [/COLOR][THIS]("https://github.com/aircrack-ng/rtl8812au")[COLOR=#000000] )[/COLOR]
[COLOR=#000000]2) Tried updating my ubuntu, but no luck.[/COLOR]
[COLOR=#000000]3) I've read the thread on here and here are my results:

```
[/COLOR]########## wireless info START ##########

Report from: 18 Jan 2022 05:43 CST -0600


Booted last: 18 Jan 2022 00:00 CST -0600


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal


##### kernel ############################


Linux 5.11.0-43-generic #47~20.04.2-Ubuntu SMP Mon Dec 13 11:06:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1] (rev 05)
	DeviceName:  Onboard LAN
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]


##### lsusb #############################


Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 1532:0037 Razer USA, Ltd Razer DeathAdder 2013
Bus 003 Device 006: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 005: ID 0d8c:0005 C-Media Electronics, Inc. Blue Snowball
Bus 003 Device 004: ID 1532:011b Razer USA, Ltd BlackWidow Classic
Bus 003 Device 003: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot enabled


##### lsmod #############################


eeepc_wmi              16384  0
wmi_bmof               16384  0
intel_wmi_thunderbolt    20480  0
mxm_wmi                16384  1 nouveau
asus_wmi               36864  2 eeepc_wmi,mfd_aaeon
sparse_keymap          16384  1 asus_wmi
video                  53248  2 asus_wmi,nouveau
wmi                    32768  6 intel_wmi_thunderbolt,asus_wmi,wmi_bmof,mfd_aaeon,mxm_wmi,nouveau


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp0s25


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad


##### network managers ##################


Installed:


	NetworkManager


Running:


root         880       1  0 05:16 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.11.0-43-generic
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


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


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


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


eno1      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


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


########## wireless info END ############


[COLOR=#000000]
```

I've tried various other things, but honestly I am completely lost now. 

If anyone has any experience on this end, it would really help -- I have a USB stick to transfer files from my mac to the ubuntu if needed. 

I'll be around all day to reply to any questions/help. 

Thank you kindly.[/COLOR]

---

### Post by RJLiberator on 2022-01-18
As an update, I'm currently trying to tether my phone to my computer to give the ubuntu OS an internet connection -- my hope is that i can run updates/install drivers for the adapter that way.

---

### Post by TheFu on 2022-01-18
I see you have secureboot on. Try disabling that first.

The amazon reviews say it isn't good for Linux.
>  However, the unit I received uses the Realtek rtl8822bu chipset, which is slightly notorious for not having good linux support. Don't be fooled by the seller's claim of linux compatibility.
It is technically possible to get this device working in linux, and I did manage to get it running using the included driver disc (which has a set of linux drivers). Unfortunately, not only did I have to build them myself, the included drivers do not work on all versions of the linux kernel. Regardless of distribution, if you're on a kernel that's too old OR **one that's too new (5.6+)** you'll be hit with a series of compiler errors when you try to set up the driver.
Sorry.

If it were me, I'd return this device and get one that has been Linux support.  The hassles for the next 3 yrs with this realtek just aren't worth it to me.  But it does appear that some people have been successful getting the driver code, compiling and using modprobe to get the driver in and available. It is possible that every kernel update going forward will need these same steps again.

[https://askubuntu.com/questions/1178802/proper-way-of-installing-wifi-drivers-rtl8822bu](https://askubuntu.com/questions/1178802/proper-way-of-installing-wifi-drivers-rtl8822bu) is a reputable how-to.

---

### Post by RJLiberator on 2022-01-18
> **TheFu said:**
> I see you have secureboot on. Try disabling that first.

The amazon reviews say it isn't good for Linux.

Sorry.

If it were me, I'd return this device and get one that has been Linux support.  The hassles for the next 3 yrs with this realtek just aren't worth it to me.  But it does appear that some people have been successful getting the driver code, compiling and using modprobe to get the driver in and available. It is possible that every kernel update going forward will need these same steps again.

[https://askubuntu.com/questions/1178802/proper-way-of-installing-wifi-drivers-rtl8822bu](https://askubuntu.com/questions/1178802/proper-way-of-installing-wifi-drivers-rtl8822bu) is a reputable how-to.

Damn, that's a real bummer.

I agree - hassle not worth it. Is there any network adapaters that you would suggest? :x

---

### Post by RJLiberator on 2022-01-18
I just saw the topic in the forum. I bought a linux based network adapater to arrive tomorrow. Hopefully it will work! 

Thank you for taking the time to look over this -- I feel a lot better now. Cheers

---

### Post by morrownr on 2022-01-18
> **RJLiberator said:**
> Damn, that's a real bummer.

I agree - hassle not worth it. Is there any network adapters that you would suggest? :x

It appears you have already found the sticky with this link but here it is just in case:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

### Post by TheFu on 2022-01-18
> **RJLiberator said:**
> Damn, that's a real bummer.

I agree - hassle not worth it. Is there any network adapaters that you would suggest? :x

There's a difference between "may" and "will".  Lots of these drivers work with dkms scripts which could make this automatic until the next install or major kernel update.

But until the kernel includes the driver exactly as you need it, it will probably be a hassle.

---


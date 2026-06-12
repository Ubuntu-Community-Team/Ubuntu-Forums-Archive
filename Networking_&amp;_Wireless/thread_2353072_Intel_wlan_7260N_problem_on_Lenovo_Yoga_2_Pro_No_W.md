---
title: "Intel wlan 7260N problem on Lenovo Yoga 2 Pro: No Wifi, Disapeared Wifi Card"
date: 2017-02-18
forum: Networking &amp; Wireless
---

### Post by downlink on 2017-02-18
Hi,

I'm running 64-bit Ubuntu 16.04 with kernel 4.4.0 on a Lenovo Yoga 2 Pro and am having a very confusing issue. Up until now my wifi has been working perfectly but yesterday out of nowhere my internet dropped. When I went to reconnect I noticed that no wireless networks were even showing. What's really strange about it is that the wifi interface doesn't even seem to be recognized, yet bluetooth is working just fine. In fact, I'm hotspotting my laptop through bluetooth right now. This leads me to believe this isn't a hardware issue as the Intel 7260 wireless card integrates both wifi and bluetooth. I don't want to buy a new wireless card without fist exhausting all my software options only to find out a new chip won't work either. I've read other threads but can't find anything similar. Any help would be seriously appreciated!

[B]iwconfig

[/B]```

lo        no wireless extensions.


bnep0     no wireless extensions.

```

[B]lshw -C network

[/B]```
  *-network               
       description: Ethernet interface
       physical id: 3
       logical name: bnep0
       serial: 5c:51:4f:70:84:e1
       capabilities: ethernet physical
       configuration: broadcast=yes ip=172.20.10.5 multicast=yes

```

[B]dmesg | grep iwl

[/B]does't output anything

[B]rfkill list all
[/B]
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

**sudo iwlist wlan0 scan**

```

wlan0     Interface doesn't support scanning.

```


Let me know if there's anything else I can check to maybe figure this out.

Thanks!

---

### Post by jeremy31 on 2017-02-18
Check settings in BIOS.  If WLAN is set to disabled in BIOS my lspci shows no results for wifi on my Lenovo G710

But I just checked and disabling wireless in BIOS also disables bluetooth on my laptop, you may have to reset to defaults in BIOS and see if that works or remove the wifi card from the motherboard and reinstall it in case it has a bad connection

---

### Post by stavrosian on 2017-02-18
I also have a Lenovo and the wireless has always given me trouble. Two months ago my wifi went out (again) after four (4) months of working perfectly. Bluetooth was working even after the wifi gave out, then last week Blutooth stopped as well. I opened up the back and played with the wires and now bluetooth works and wifi is now recognized but network manager still says "device not ready" so it's not working yet. I've just purchased my third replacement card I need to install.
[I]
Downlink, you should download the Wireless Script from jeremy31's signature and run that and upload the file that it creates which has lots of useful info, like the stuff you posted originally.[/I]

---

### Post by downlink on 2017-02-18
Hi and thanks for your answer. Wireless was enabled already though. I disabled and re-enabled but that didn't change anything. Reseting the BIOS settings had no effect and neither did physically pulling out the chip. 

I should also mention that I've tried reinstalling the iwlwifi driver but that didn't do anything either.

---

### Post by downlink on 2017-02-18
Does changing the cards solve the issues for you? I'm just confused how it can be the card itself when bluetooth still works fine.

---

### Post by jeremy31 on 2017-02-18
Lenovo's usually have a whitelist in the BIOS.  That means you cannot just put any wifi card in one and be able to boot as I tried putting a few different Intel cards in mine and I get a warning message and it won't boot.  You can use about any USB wifi card that is supported by Linux in one way or another, I have a TP-Link TL-WN722N 150Mbps on hand in case my internal wifi goes bad

---

### Post by downlink on 2017-02-18
If I do replace the wireless card I was thinking of just getting the same one I already have. It worked well on my laptop for so long. Do you guys think it could be the card when the Intel 7260 has both wifi and bluetooth in one but only one stopped working? Like does it have separate chipsets for each within the same card?

Also, here are the results of your wireless script Jeremy31:



```
########## wireless info START ##########


Report from: 18 Feb 2017 18:32 EST -0500


Booted last: 18 Feb 2017 00:00 EST -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 002 Device 007: ID 04f3:016f Elan Microelectronics Corp. 
Bus 002 Device 004: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 0bda:0176 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback
source-directory interfaces.d


##### ifconfig ##########################


bnep0 Link encap:Ethernet HWaddr <MAC 'bnep0' [IF1]> 
inet addr:172.20.10.5 Bcast:172.20.10.15 Mask:255.255.255.240
inet6 addr: fe80::f62:c45e:926:5ae9/64 Scope:Link
inet6 addr: 2607:fb90:76f:2bbe:<IP6 'bnep0' [IF1]>/64 Scope:Global
inet6 addr: 2607:fb90:76f:2bbe:d282:ce4c:f647:8f03/64 Scope:Global
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4742 errors:0 dropped:0 overruns:0 frame:0
TX packets:3390 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:5365066 (5.3 MB) TX bytes:488847 (488.8 KB)


##### iwconfig ##########################


lo no wireless extensions.


bnep0 no wireless extensions.


##### route #############################


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 172.20.10.1 0.0.0.0 UG 750 0 0 bnep0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 bnep0
172.20.10.0 0.0.0.0 255.255.255.240 U 750 0 0 bnep0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root 873 1 0 18:26 ? 00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE: <MAC address>
GENERAL.TYPE: bt
GENERAL.NM-TYPE: NMDeviceBt
GENERAL.VENDOR: 
GENERAL.PRODUCT: 
GENERAL.DRIVER: bluez
GENERAL.DRIVER-VERSION: 
GENERAL.FIRMWARE-VERSION: 
GENERAL.HWADDR: <MAC address>
GENERAL.MTU: 0
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /org/bluez/hci0/dev_70_EC_E4_80_C5_03
GENERAL.IP-IFACE: bnep0
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: iPhone Network
GENERAL.CON-UUID: ec348a8d-598f-4e79-8f2a-8b09c12f747b
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED: no (guessed)
CAPABILITIES.CARRIER-DETECT: no
CAPABILITIES.SPEED: unknown
CAPABILITIES.IS-SOFTWARE: no
BLUETOOTH.CAPABILITIES: NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: ec348a8d-598f-4e79-8f2a-8b09c12f747b | iPhone Network
IP4.ADDRESS[1]: 172.20.10.5/28
IP4.GATEWAY: 172.20.10.1
IP4.ROUTE[1]: dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]: 172.20.10.1
DHCP4.OPTION[1]: requested_routers = 1
DHCP4.OPTION[2]: requested_domain_search = 1
DHCP4.OPTION[3]: server_name = iPhone
DHCP4.OPTION[4]: requested_time_offset = 1
DHCP4.OPTION[5]: requested_domain_name = 1
DHCP4.OPTION[6]: requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]: requested_broadcast_address = 1
DHCP4.OPTION[8]: requested_wpad = 1
DHCP4.OPTION[9]: requested_netbios_scope = 1
DHCP4.OPTION[10]: next_server = 172.20.10.1
DHCP4.OPTION[11]: expiry = 1487545966
DHCP4.OPTION[12]: requested_interface_mtu = 1
DHCP4.OPTION[13]: requested_subnet_mask = 1
DHCP4.OPTION[14]: dhcp_lease_time = 85536
DHCP4.OPTION[15]: dhcp_message_type = 5
DHCP4.OPTION[16]: ip_address = 172.20.10.5
DHCP4.OPTION[17]: requested_static_routes = 1
DHCP4.OPTION[18]: requested_domain_name_servers = 1
DHCP4.OPTION[19]: routers = 172.20.10.1
DHCP4.OPTION[20]: broadcast_address = 172.20.10.15
DHCP4.OPTION[21]: requested_ntp_servers = 1
DHCP4.OPTION[22]: requested_netbios_name_servers = 1
DHCP4.OPTION[23]: domain_name_servers = 172.20.10.1
DHCP4.OPTION[24]: requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]: subnet_mask = 255.255.255.240
DHCP4.OPTION[26]: network_number = 172.20.10.0
DHCP4.OPTION[27]: requested_host_name = 1
DHCP4.OPTION[28]: dhcp_server_identifier = 172.20.10.1
IP6.ADDRESS[1]: 2607:fb90:76f:2bbe:d282:ce4c:f647:8f03/64
IP6.ADDRESS[2]: 2607:fb90:76f:2bbe:<IP6 'bnep0' [IF1]>/64
IP6.ADDRESS[3]: fe80::f62:c45e:926:5ae9/64
IP6.GATEWAY: fe80::1477:dc2d:4972:3e7d
IP6.ROUTE[1]: dst = fe80::1477:dc2d:4972:3e7d/128, nh = ::, mt = 750
IP6.DNS[1]: fe80::1477:dc2d:4972:3e7d


GENERAL.DEVICE: <MAC address>
GENERAL.TYPE: bt
GENERAL.NM-TYPE: NMDeviceBt
GENERAL.VENDOR: 
GENERAL.PRODUCT: 
GENERAL.DRIVER: bluez
GENERAL.DRIVER-VERSION: 
GENERAL.FIRMWARE-VERSION: 
GENERAL.HWADDR: <MAC address>
GENERAL.MTU: 0
GENERAL.STATE: 30 (disconnected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /org/bluez/hci0/dev_44_6D_6C_F0_95_EF
GENERAL.IP-IFACE: 
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: --
GENERAL.CON-UUID: --
GENERAL.CON-PATH: --
GENERAL.METERED: unknown
CAPABILITIES.CARRIER-DETECT: no
CAPABILITIES.SPEED: unknown
CAPABILITIES.IS-SOFTWARE: no
BLUETOOTH.CAPABILITIES: NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: a73ff9c7-46c9-4c56-89b7-4616d81a5c8c | SAMSUNG-SM-G900V Network


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


[[/etc/NetworkManager/system-connections/OrderInKhaos]] (600 root)
[connection] id=OrderInKhaos | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=OrderInKhaos
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo no frequency information.


bnep0 no frequency information.


##### iwlist scan #######################


lo Interface doesn't support scanning.


bnep0 Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi000.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/myownblacklist.conf]
blacklist ideapad_laptop


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 7.474742] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 7.612537] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated


########## wireless info END ############
```

---

### Post by jeremy31 on 2017-02-18
I would contact Lenovo about replacement of the wireless card.  Does this laptop not have an ethernet connection?  Just asking because I know some laptops don't but I am not sure about this one

---

### Post by downlink on 2017-02-18
No, the yoga 2 pro doesn't have an ethernet slot. I could get an adaptor but that's not really an issue since I can tether it through my phone's bluetooth. I'd just rather get wifi working again. Also, Lenovo won't be of any help. This laptop is beyond its warranty period so I'm on my own. :/

I guess I'll just try to replace the wireless card and hope for the best.

Thanks guys.

---

### Post by stavrosian on 2017-02-18
I called Lonovo originally about my Yoga 2 Pro and they sent me a new WiFi card out free of charge and never asked about my warranty.  I don't remember the timing exactly but it was pretty easy, I think they've had lots of complaints about the wifi.

---

### Post by downlink on 2017-02-19
Cool. I will definitely try that then. Thanks!

---

### Post by downlink on 2017-03-02
So I got a new wireless card and it still didn't work. Everything was the same as before, with ubuntu not even recognizing wireless ability.

---


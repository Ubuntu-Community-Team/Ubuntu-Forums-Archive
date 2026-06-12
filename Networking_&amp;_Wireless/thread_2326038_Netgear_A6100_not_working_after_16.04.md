---
title: "Netgear A6100 not working after 16.04"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by colmeweb on 2016-05-27
So I just updated to 16.04 yesterday, and I got a few errors during the update, but my main one is that my USB wifi stick isn't working anymore.
Before I had to reinstall the driver after each kernel update, but now even that isn't working.

As for the basics:
```
~$ ls usbls: cannot access 'usb': No such file or directory
colin@Lenovo-Edge:~$ lsusb
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 03eb:8a1d Atmel Corp. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 5986:055e Acer, Inc 
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And to get it working I usually did 
```
cd [~/rtl8812AU_8821AU_linux]("http://ubuntuforums.org/~/rtl8812AU_8821AU_linux")
make
sudo make install
sudo modprobe 8812au
```

I know there is probably an easy way around this, but drivers and coding were never my strong suit.
Thanks in advance.

---

### Post by jeremy31 on 2016-05-27
There is a dkms package in the repos
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/r/rtl8812au/rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
sudo dpkg -i rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb
```

Reboot

---

### Post by colmeweb on 2016-05-27
No effect.

---

### Post by jeremy31 on 2016-05-28
See the wireless script link in my signature and post the results

---

### Post by colmeweb on 2016-05-28
Here you go,

```
########## wireless info START ##########

Report from: 28 May 2016 20:14 PDT -0700


Booted last: 28 May 2016 00:00 PDT -0700


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3818]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 03eb:8a1d Atmel Corp. 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 5986:055e Acer, Inc 
Bus 002 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
ath                    32768  1 ath10k_core
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
wmi                    20480  3 ideapad_laptop,mxm_wmi,nouveau
video                  40960  3 i915,ideapad_laptop,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9630:8469:ed1:d17e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1327732 (1.3 MB)  TX bytes:157115 (157.1 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       731     1  0 20:07 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       688a7e9a-b17c-4aea-b284-4b9de1254bd1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{10}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   688a7e9a-b17c-4aea-b284-4b9de1254bd1 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.19/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464577748
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.19
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::9630:8469:ed1:d17e/64
IP6.GATEWAY:                            


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


[[/etc/NetworkManager/system-connections/MercuryMongoose-5G-1]] (600 root)
[connection] id=MercuryMongoose-5G-1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MercuryMongoose-5G-1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR37-5G-1]] (600 root)
[connection] id=NETGEAR37-5G-1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR37-5G-1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-1EC2]] (600 root)
[connection] id=HOME-1EC2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-1EC2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MercuryMongoose]] (600 root)
[connection] id=MercuryMongoose | type=wifi
[wifi] ssid=MercuryMongoose | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR37]] (600 root)
[connection] id=NETGEAR37 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR37
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MercuryMongoose-5G]] (600 root)
[connection] id=MercuryMongoose-5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MercuryMongoose-5G
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME WiFi 2]] (600 root)
[connection] id=HOME WiFi 2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME WiFi 2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Home WiFi 1]] (600 root)
[connection] id=Home WiFi 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Home WiFi 1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Home WiFi 2]] (600 root)
[connection] id=Home WiFi 2 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Home WiFi 2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ClearSPOT_2eb78]] (600 root)
[connection] id=ClearSPOT_2eb78 | type=wifi
[wifi] ssid=ClearSPOT_2eb78 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Vancouver (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


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


[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8812au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   16.403317] Bluetooth: hci0: QCA: patch rome 0x200 build 0x299, firmware rome 0x200 build 0x111
[   16.436352] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   16.689501] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   16.865308] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-5.bin failed with error -2
[   16.865313] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-5.bin': -2
[   16.865323] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[   16.865325] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[   16.865330] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[   16.865331] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[   16.865336] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-2.bin failed with error -2
[   16.865337] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -2
[   16.865343] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware.bin failed with error -2
[   16.865344] ath10k_pci 0000:02:00.0: could not fetch firmware (-2)
[   16.865345] ath10k_pci 0000:02:00.0: could not fetch firmware files (-2)
[   16.865347] ath10k_pci 0000:02:00.0: could not probe fw (-2)
[   35.021468] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.182291] r8169 0000:03:00.0 eth0: link down
[   35.182346] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   98.268169] r8169 0000:03:00.0 eth0: link up
[   98.268177] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


########## wireless info END ############



```


Thanks

---

### Post by colmeweb on 2016-05-29
I probably should have listed this before. 
The first step of the setup process works as before, but the sudo make install and modprobe steps give different results than before.

```

@Lenovo-Edge:~/rtl8812AU_8821AU_linux$ sudo make installinstall -p -m 644 8812au.ko  /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.4.0-22-generic
@Lenovo-Edge:~/rtl8812AU_8821AU_linux$ sudo modprobe 8812au
modprobe: ERROR: could not insert '8812au': Required key not available
@Lenovo-Edge:~/rtl8812AU_8821AU_linux$ 

```

UPDATE: I was able to take care of the "Required key not available" issue by deactivating secure boot. Somehow it got reset when I installed 16.04. It still didn't get the wifi working though. Darn.

---

### Post by jeremy31 on 2016-05-29
You have a nice internal card, it should work properly after ```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

---

### Post by colmeweb on 2016-05-29
Holy god, thank you. I have been trying to get the internal card working since I got the computer. I went through 353 comments on the bug report and you did more in 2 lines of terminal code :)
So do I mark this one as solved? I am definitely happy with the results.

P.S. Is there a place I can check to update the wget address as needed?

HUGE Thank You.

---

### Post by jeremy31 on 2016-05-29
Use the Thread Tools at the top of the page to mark as solved.  You shouldn't need to update as this should soon be part of normal updates

---


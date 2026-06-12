---
title: "Wifi network not showing up"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by gustavosmonteiro on 2017-02-21
Hello,

I can't use wifi on my Dell notebook. There's no wifi avaiable.
I ran the following code:

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

And I got:


```

########## wireless info START ##########


Report from: 21 Feb 2017 09:22 BRT -0300


Booted last: 21 Feb 2017 00:00 BRT -0300


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.5.0-040500-generic #201603140130 SMP Mon Mar 14 05:32:22 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter [1028:0310]


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:070a]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e007 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 1bcf:28b0 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 1c4f:0032 SiGma Micro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


cfg80211              557056  0
compat                 16384  1 cfg80211
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::cc02:bc2:5fe0:9d94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111172769 (111.1 MB)  TX bytes:3320645 (3.3 MB)


##### iwconfig ##########################


enp3s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search dlinkrouter


##### network managers ##################


Installed:


	NetworkManager


Running:


root     31988     1  0 09:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet automática
GENERAL.CON-UUID:                       61208e61-637e-431c-8560-de2717b0d05c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8d70f522-0621-467c-8edc-9853b7ac93d1 | Ethernet automática
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   61208e61-637e-431c-8560-de2717b0d05c | Ethernet automática
IP4.ADDRESS[1]:                         192.168.0.112/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          dlinkrouter
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.112
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1487766105
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = dlinkrouter
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[25]:                       dhcp_option_overload = 3
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       routers = 192.168.0.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::cc02:bc2:5fe0:9d94/64
IP6.GATEWAY:                            


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


[[/etc/NetworkManager/system-connections/CHAPOLIN]] (600 root)
[connection] id=CHAPOLIN | type=wifi | permissions=user:apisys:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CHAPOLIN
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CHAPOLIN 2]] (600 root)
[connection] id=CHAPOLIN 2 | type=wifi | permissions=user:gustavo:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CHAPOLIN
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CHAPOLIN-2.4GHz]] (600 root)
[connection] id=CHAPOLIN-2.4GHz | type=wifi | permissions=user:apisys:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CHAPOLIN-2.4GHz
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Fortaleza (based on set time zone)


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


enp3s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp3s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.5.0-040500-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20150731-0-g37bd1ea) using backports backports-20150731-0-g2af997b
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6BE4ED42578C9DFBE16CE50
depends:        compat
vermagic:       4.5.0-040500-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


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


[    5.892987] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    6.084319] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[    6.084375] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    7.665866] r8169 0000:03:00.0 enp3s0: link up
[    7.665873] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready


########## wireless info END ############

```

How can I fix it?

PS: I'm new on Ubuntu

---

### Post by chili555 on 2017-02-21
Let's gather some information from the log first. Please open a terminal and do:```
sudo modprobe ath10k_pci && dmesg | grep ath
```Post the result and we'll see what's going wrong.

---

### Post by gustavosmonteiro on 2017-02-21
Thank you for your reply.

But nothing happened.

---

### Post by gustavosmonteiro on 2017-02-21
Then I ran just: sudo modprobe ath10k_pci && dmesg

That's what I got:

```

gustavo@apisys-Inspiron-5457:~$ sudo modprobe ath10k_pci && dmesg | grep ath
[sudo] senha para gustavo: 
gustavo@apisys-Inspiron-5457:~$ sudo modprobe ath10k_pci && dmesg
[    0.000000] Linux version 4.5.0-040500-generic (kernel@tangerine) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201603140130 SMP Mon Mar 14 05:32:22 UTC 2016
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.5.0-040500-generic root=UUID=dfc64e85-1966-4e37-a1ed-38236c968cdf ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: xstate_offset[3]:  960, xstate_sizes[3]:   64
[    0.000000] x86/fpu: xstate_offset[4]: 1024, xstate_sizes[4]:   64
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 1088 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000006a3c1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000006a3c2000-0x000000006a3c2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006a3c3000-0x000000006a3ecfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000006a3ed000-0x000000006a448fff] usable
[    0.000000] BIOS-e820: [mem 0x000000006a449000-0x000000006abf8fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000006abf9000-0x0000000076c0ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000076c10000-0x0000000076c7bfff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000076c7c000-0x0000000077627fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000077628000-0x0000000077f98fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077f99000-0x0000000077ffdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000077ffe000-0x0000000077ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000078000000-0x00000000780fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000282ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ACPI=0x77fd4000  ACPI 2.0=0x77fd4000  SMBIOS=0xf0000  ESRT=0x76fe7598 
[    0.000000] esrt: Reserving ESRT space from 0x0000000076fe7598 to 0x0000000076fe75d0.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Dell Inc. Inspiron 5457/0WT51R, BIOS 1.1.9 04/25/2016
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x283000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   1 base 007C000000 mask 7FFC000000 uncachable
[    0.000000]   2 base 007A000000 mask 7FFE000000 uncachable
[    0.000000]   3 base 0079800000 mask 7FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x77fff max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x03207000, 0x03207fff] PGTABLE
[    0.000000] BRK [0x03208000, 0x03208fff] PGTABLE
[    0.000000] BRK [0x03209000, 0x03209fff] PGTABLE
[    0.000000] BRK [0x0320a000, 0x0320afff] PGTABLE
[    0.000000] BRK [0x0320b000, 0x0320bfff] PGTABLE
[    0.000000] BRK [0x0320c000, 0x0320cfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x32ff0000-0x357effff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x0000000077FD4000 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x0000000077FD40B8 0000F4 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000077FF1BD0 00010C (v05 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x0000000077FD4240 01D98C (v02 DELL   CBX3     01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000077F97F80 000040
[    0.000000] ACPI: APIC 0x0000000077FF1CE0 000084 (v03 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000077FF1D68 000044 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000077FF1DB0 00009C (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000077FF1E50 00003C (v01 DELL   CBX3     01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000077FF1E90 000038 (v01 DELL   CBX3     01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000077FF1EC8 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x0000000077FF21E0 000094 (v01 INTEL  SKL-ULT  00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000077FF2278 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000077FF24C0 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000077FF5070 000C45 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000077FF5CB8 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000077FF5CF0 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000077FF5D48 000740 (v02 INTEL  xh_rvp07 00000000 INTL 20120913)
[    0.000000] ACPI: BOOT 0x0000000077FF6488 000028 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x0000000077FF64B0 003617 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000077FF9AC8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000077FF9B10 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: MSDM 0x0000000077FFA968 000055 (v03 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SLIC 0x0000000077FFA9C0 000176 (v03 DELL   CBX3     01072009 MSFT 00010013)
[    0.000000] ACPI: BGRT 0x0000000077FFAB38 000038 (v00 ??ry            01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x0000000077FFAB70 0006AA (v02 SgRef  SgPch    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x0000000077FFB220 0000F0 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: TPM2 0x0000000077FFB310 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x0000000077FFB348 0018B8 (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x0000000077FFCC00 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000282ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x282ff8000-0x282ffbfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x0000000282ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000006a3c1fff]
[    0.000000]   node   0: [mem 0x000000006a3ed000-0x000000006a448fff]
[    0.000000]   node   0: [mem 0x000000006abf9000-0x0000000076c0ffff]
[    0.000000]   node   0: [mem 0x0000000077ffe000-0x0000000077ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000282ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000282ffffff]
[    0.000000] On node 0 totalpages: 2069457
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7505 pages used for memmap
[    0.000000]   DMA32 zone: 480310 pages, LIFO batch:31
[    0.000000]   Normal zone: 24768 pages used for memmap
[    0.000000]   Normal zone: 1585152 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x7a000000-0x7bffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x6a3c2000-0x6a3c2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x6a3c3000-0x6a3ecfff]
[    0.000000] PM: Registered nosave memory: [mem 0x6a449000-0x6abf8fff]
[    0.000000] PM: Registered nosave memory: [mem 0x76c10000-0x76c7bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x76c7c000-0x77627fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77628000-0x77f98fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77f99000-0x77ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x77fff000-0x77ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x78000000-0x780fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x78100000-0x79ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a000000-0x7bffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7c000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x7c000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880282c00000 s97624 r8192 d29352 u524288
[    0.000000] pcpu-alloc: s97624 r8192 d29352 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2037098
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.5.0-040500-generic root=UUID=dfc64e85-1966-4e37-a1ed-38236c968cdf ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7793804K/8277828K available (8352K kernel code, 1299K rwdata, 4048K rodata, 1488K init, 1292K bss, 484024K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 2591.948 MHz processor
[    0.000024] Calibrating delay loop (skipped), value calculated using timer frequency.. 5183.89 BogoMIPS (lpj=10367792)
[    0.000026] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20160108
[    0.028883] ACPI: 10 ACPI AML tables successfully acquired and loaded


[    0.030865] Security Framework initialized
[    0.030867] Yama: becoming mindful.
[    0.030872] AppArmor: AppArmor initialized
[    0.031266] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.032734] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.033469] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.033476] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.033674] CPU: Physical Processor ID: 0
[    0.033675] CPU: Processor Core ID: 0
[    0.033679] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.033679] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.033683] mce: CPU supports 8 MCE banks
[    0.033695] CPU0: Thermal monitoring enabled (TM1)
[    0.033702] process: using mwait in idle threads
[    0.033704] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.033705] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.033991] Freeing SMP alternatives memory: 32K (ffffffff820ba000 - ffffffff820c2000)
[    0.048406] ftrace: allocating 31937 entries in 125 pages
[    0.059235] DMAR: Host address width 39
[    0.059237] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.059244] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0505e
[    0.059245] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.059248] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.059249] DMAR: RMRR base: 0x0000007758a000 end: 0x000000775a9fff
[    0.059250] DMAR: RMRR base: 0x00000079800000 end: 0x0000007bffffff
[    0.059251] DMAR: ANDD device: 1 name: \_SB.PCI0.I2C0
[    0.059252] DMAR: ANDD device: 2 name: \_SB.PCI0.I2C1
[    0.059254] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.059254] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.059255] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.059256] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.060681] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.060682] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.064569] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.104260] TSC deadline timer enabled
[    0.104265] smpboot: CPU0: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz (family: 0x6, model: 0x4e, stepping: 0x3)
[    0.104288] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.104311] ... version:                4
[    0.104312] ... bit width:              48
[    0.104312] ... generic registers:      4
[    0.104313] ... value mask:             0000ffffffffffff
[    0.104314] ... max period:             0000ffffffffffff
[    0.104314] ... fixed-purpose events:   3
[    0.104315] ... event mask:             000000070000000f
[    0.104927] x86: Booting SMP configuration:
[    0.104928] .... node  #0, CPUs:      #1
[    0.107403] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.107455]  #2 #3
[    0.112498] x86: Booted up 1 node, 4 CPUs
[    0.112501] smpboot: Total of 4 processors activated (20735.58 BogoMIPS)
[    0.116445] devtmpfs: initialized
[    0.118128] evm: security.selinux
[    0.118129] evm: security.SMACK64
[    0.118129] evm: security.SMACK64EXEC
[    0.118130] evm: security.SMACK64TRANSMUTE
[    0.118131] evm: security.SMACK64MMAP
[    0.118131] evm: security.ima
[    0.118132] evm: security.capability
[    0.118174] PM: Registering ACPI NVS region [mem 0x6a3c2000-0x6a3c2fff] (4096 bytes)
[    0.118175] PM: Registering ACPI NVS region [mem 0x77628000-0x77f98fff] (9900032 bytes)
[    0.118317] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.118363] pinctrl core: initialized pinctrl subsystem
[    0.118514] RTC time: 12:07:10, date: 02/21/17
[    0.119396] NET: Registered protocol family 16
[    0.128271] cpuidle: using governor ladder
[    0.144291] cpuidle: using governor menu
[    0.144296] PCCT header not found.
[    0.144330] Simple Boot Flag at 0x47 set to 0x80
[    0.144380] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.144382] ACPI: bus type PCI registered
[    0.144383] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.144448] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.144449] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.144460] PCI: Using configuration type 1 for base access
[    0.144465] dmi type 0xB1 record - unknown flag
[    0.156383] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.156384] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.156618] ACPI: Added _OSI(Module Device)
[    0.156620] ACPI: Added _OSI(Processor Device)
[    0.156621] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156622] ACPI: Added _OSI(Processor Aggregator Device)
[    0.160206] ACPI: Executed 21 blocks of module-level executable AML code
[    0.166011] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.175148] ACPI: Dynamic OEM Table Load:
[    0.175154] ACPI: SSDT 0xFFFF880278938C00 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.175978] ACPI: Dynamic OEM Table Load:
[    0.175982] ACPI: SSDT 0xFFFF880278E82800 000660 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.177535] ACPI: Dynamic OEM Table Load:
[    0.177540] ACPI: SSDT 0xFFFF880278E83000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.178394] ACPI: Dynamic OEM Table Load:
[    0.178398] ACPI: SSDT 0xFFFF880278998400 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.180446] ACPI : EC: EC started
[    0.182263] ACPI: Interpreter enabled
[    0.182304] ACPI: (supports S0 S3 S4 S5)
[    0.182305] ACPI: Using IOAPIC for interrupt routing
[    0.182330] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.183292] ACPI: Power Resource [PG00] (on)
[    0.183533] ACPI: Power Resource [PG01] (on)
[    0.183761] ACPI: Power Resource [PG02] (on)
[    0.184738] ACPI: Power Resource [WRST] (off)
[    0.184978] ACPI: Power Resource [WRST] (off)
[    0.185217] ACPI: Power Resource [WRST] (off)
[    0.185455] ACPI: Power Resource [WRST] (off)
[    0.185690] ACPI: Power Resource [WRST] (off)
[    0.185726] ACPI: Power Resource [PC09] (on)
[    0.186483] ACPI: Power Resource [WRST] (off)
[    0.186717] ACPI: Power Resource [WRST] (off)
[    0.186948] ACPI: Power Resource [WRST] (off)
[    0.187317] ACPI: Power Resource [WRST] (off)
[    0.187559] ACPI: Power Resource [WRST] (off)
[    0.187791] ACPI: Power Resource [WRST] (off)
[    0.188021] ACPI: Power Resource [WRST] (off)
[    0.188258] ACPI: Power Resource [WRST] (off)
[    0.188493] ACPI: Power Resource [WRST] (off)
[    0.188728] ACPI: Power Resource [WRST] (off)
[    0.188959] ACPI: Power Resource [WRST] (off)
[    0.189192] ACPI: Power Resource [WRST] (off)
[    0.189422] ACPI: Power Resource [WRST] (off)
[    0.189654] ACPI: Power Resource [WRST] (off)
[    0.198445] ACPI: Power Resource [FN00] (off)
[    0.198498] ACPI: Power Resource [FN01] (off)
[    0.198550] ACPI: Power Resource [FN02] (off)
[    0.198600] ACPI: Power Resource [FN03] (off)
[    0.198650] ACPI: Power Resource [FN04] (off)
[    0.199423] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.199427] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.199450] \_SB_.PCI0 (33DB4D5B-1FF7-401C-9657-7441C03DD766): _OSC invalid UUID
[    0.199451] _OSC request data: 1 1f 0
[    0.199454] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.199875] PCI host bridge to bus 0000:00
[    0.199877] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.199878] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.199879] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.199880] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.199881] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.199882] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.199883] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.199884] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.199885] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.199886] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.199887] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.199888] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.199889] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.199890] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.199890] pci_bus 0000:00: root bus resource [mem 0x7c000000-0xdfffffff window]
[    0.199891] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.199893] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.199898] pci 0000:00:00.0: [8086:1904] type 00 class 0x060000
[    0.199984] pci 0000:00:02.0: [8086:1916] type 00 class 0x030000
[    0.199991] pci 0000:00:02.0: reg 0x10: [mem 0xd4000000-0xd4ffffff 64bit]
[    0.199996] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.199999] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.200146] pci 0000:00:14.0: [8086:9d2f] type 00 class 0x0c0330
[    0.200164] pci 0000:00:14.0: reg 0x10: [mem 0xd5310000-0xd531ffff 64bit]
[    0.200232] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.200303] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.200334] pci 0000:00:14.2: [8086:9d31] type 00 class 0x118000
[    0.200351] pci 0000:00:14.2: reg 0x10: [mem 0xd5330000-0xd5330fff 64bit]
[    0.200571] pci 0000:00:15.0: [8086:9d60] type 00 class 0x118000
[    0.200779] pci 0000:00:15.0: reg 0x10: [mem 0xd532f000-0xd532ffff 64bit]
[    0.201705] pci 0000:00:15.1: [8086:9d61] type 00 class 0x118000
[    0.201913] pci 0000:00:15.1: reg 0x10: [mem 0xd532e000-0xd532efff 64bit]
[    0.202774] pci 0000:00:16.0: [8086:9d3a] type 00 class 0x078000
[    0.202795] pci 0000:00:16.0: reg 0x10: [mem 0xd532d000-0xd532dfff 64bit]
[    0.202867] pci 0000:00:16.0: PME# supported from D3hot
[    0.202971] pci 0000:00:17.0: [8086:9d03] type 00 class 0x010601
[    0.202985] pci 0000:00:17.0: reg 0x10: [mem 0xd5328000-0xd5329fff]
[    0.202993] pci 0000:00:17.0: reg 0x14: [mem 0xd532c000-0xd532c0ff]
[    0.203000] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.203008] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.203015] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.203022] pci 0000:00:17.0: reg 0x24: [mem 0xd532b000-0xd532b7ff]
[    0.203062] pci 0000:00:17.0: PME# supported from D3hot
[    0.203162] pci 0000:00:1c.0: [8086:9d10] type 01 class 0x060400
[    0.203221] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.203306] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.203343] pci 0000:00:1c.4: [8086:9d14] type 01 class 0x060400
[    0.203400] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.203481] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.203506] pci 0000:00:1c.5: [8086:9d15] type 01 class 0x060400
[    0.203563] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.203644] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.203683] pci 0000:00:1f.0: [8086:9d48] type 00 class 0x060100
[    0.203866] pci 0000:00:1f.2: [8086:9d21] type 00 class 0x058000
[    0.203875] pci 0000:00:1f.2: reg 0x10: [mem 0xd5324000-0xd5327fff]
[    0.203998] pci 0000:00:1f.3: [8086:9d70] type 00 class 0x040300
[    0.204018] pci 0000:00:1f.3: reg 0x10: [mem 0xd5320000-0xd5323fff 64bit]
[    0.204044] pci 0000:00:1f.3: reg 0x20: [mem 0xd5300000-0xd530ffff 64bit]
[    0.204090] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.204198] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.204229] pci 0000:00:1f.4: [8086:9d23] type 00 class 0x0c0500
[    0.204276] pci 0000:00:1f.4: reg 0x10: [mem 0xd532a000-0xd532a0ff 64bit]
[    0.204345] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.204550] pci 0000:01:00.0: [10de:1346] type 00 class 0x030200
[    0.204563] pci 0000:01:00.0: reg 0x10: [mem 0xd2000000-0xd2ffffff]
[    0.204575] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.204587] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.204595] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.204602] pci 0000:01:00.0: reg 0x30: [mem 0xd3000000-0xd307ffff pref]
[    0.204718] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.212551] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.212554] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.212557] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xd30fffff]
[    0.212777] pci 0000:02:00.0: [168c:003e] type 00 class 0x028000
[    0.212815] pci 0000:02:00.0: reg 0x10: [mem 0xd5000000-0xd51fffff 64bit]
[    0.213018] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.213126] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.220700] pci 0000:00:1c.4: PCI bridge to [bus 02]
[    0.220704] pci 0000:00:1c.4:   bridge window [mem 0xd5000000-0xd51fffff]
[    0.220793] pci 0000:03:00.0: [10ec:8136] type 00 class 0x020000
[    0.220814] pci 0000:03:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.220840] pci 0000:03:00.0: reg 0x18: [mem 0xd5204000-0xd5204fff 64bit]
[    0.220858] pci 0000:03:00.0: reg 0x20: [mem 0xd5200000-0xd5203fff 64bit pref]
[    0.220957] pci 0000:03:00.0: supports D1 D2
[    0.220958] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.221045] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.228577] pci 0000:00:1c.5: PCI bridge to [bus 03]
[    0.228579] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.228582] pci 0000:00:1c.5:   bridge window [mem 0xd5200000-0xd52fffff]
[    0.230201] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230245] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.230286] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230328] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230369] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230411] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230452] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.230493] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.231845] ACPI: Enabled 6 GPEs in block 00 to 7F
[    0.231934] ACPI : EC: GPE = 0x45, I/O: command/status = 0x934, data = 0x930
[    0.232024] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.232025] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.232028] vgaarb: loaded
[    0.232029] vgaarb: bridge control possible 0000:00:02.0
[    0.232227] SCSI subsystem initialized
[    0.232259] libata version 3.00 loaded.
[    0.232276] ACPI: bus type USB registered
[    0.232289] usbcore: registered new interface driver usbfs
[    0.232296] usbcore: registered new interface driver hub
[    0.232306] usbcore: registered new device driver usb
[    0.232454] PCI: Using ACPI for IRQ routing
[    0.260487] PCI: pci_cache_line_size set to 64 bytes
[    0.260854] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.260855] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.260856] e820: reserve RAM buffer [mem 0x6a3c2000-0x6bffffff]
[    0.260857] e820: reserve RAM buffer [mem 0x6a449000-0x6bffffff]
[    0.260858] e820: reserve RAM buffer [mem 0x76c10000-0x77ffffff]
[    0.260859] e820: reserve RAM buffer [mem 0x77fff000-0x77ffffff]
[    0.260860] e820: reserve RAM buffer [mem 0x283000000-0x283ffffff]
[    0.260942] NetLabel: Initializing
[    0.260943] NetLabel:  domain hash size = 128
[    0.260944] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.260952] NetLabel:  unlabeled traffic allowed by default
[    0.261036] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.261040] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.263083] clocksource: Switched to clocksource hpet
[    0.267484] VFS: Disk quotas dquot_6.6.0
[    0.267500] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.267584] AppArmor: AppArmor Filesystem Enabled
[    0.267632] pnp: PnP ACPI init
[    0.267790] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.267792] system 00:00: [io  0xffff] has been reserved
[    0.267793] system 00:00: [io  0xffff] has been reserved
[    0.267794] system 00:00: [io  0xffff] has been reserved
[    0.267795] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.267796] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.267798] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267864] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.267892] system 00:02: [io  0x1854-0x1857] has been reserved
[    0.267893] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.267914] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.267929] pnp 00:04: Plug and Play ACPI device, IDs DLLb70a PNP0f13 (active)
[    0.268080] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.268082] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.268083] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.268084] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    0.268085] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.268086] system 00:05: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.268087] system 00:05: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.268089] system 00:05: [mem 0xff000000-0xffffffff] has been reserved
[    0.268090] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.268091] system 00:05: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.268093] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.268121] system 00:06: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.268123] system 00:06: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.268124] system 00:06: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.268125] system 00:06: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.268126] system 00:06: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.268127] system 00:06: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.268128] system 00:06: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.268130] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.268872] system 00:07: [mem 0xfe029000-0xfe029fff] has been reserved
[    0.268873] system 00:07: [mem 0xfe028000-0xfe028fff] has been reserved
[    0.268875] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.273704] pnp: PnP ACPI: found 8 devices
[    0.282611] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.282632] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.282634] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.282638] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xd30fffff]
[    0.282643] pci 0000:00:1c.4: PCI bridge to [bus 02]
[    0.282647] pci 0000:00:1c.4:   bridge window [mem 0xd5000000-0xd51fffff]
[    0.282652] pci 0000:00:1c.5: PCI bridge to [bus 03]
[    0.282653] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.282657] pci 0000:00:1c.5:   bridge window [mem 0xd5200000-0xd52fffff]
[    0.282663] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.282664] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.282665] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.282666] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.282667] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.282667] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.282668] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.282669] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.282670] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.282671] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.282672] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.282673] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff window]
[    0.282674] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff window]
[    0.282675] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff window]
[    0.282676] pci_bus 0000:00: resource 18 [mem 0x7c000000-0xdfffffff window]
[    0.282677] pci_bus 0000:00: resource 19 [mem 0xfd000000-0xfe7fffff window]
[    0.282678] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.282679] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xd30fffff]
[    0.282680] pci_bus 0000:02: resource 1 [mem 0xd5000000-0xd51fffff]
[    0.282681] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.282682] pci_bus 0000:03: resource 1 [mem 0xd5200000-0xd52fffff]
[    0.282703] NET: Registered protocol family 2
[    0.282851] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.282983] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.283185] TCP: Hash tables configured (established 65536 bind 65536)
[    0.283207] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.283235] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.283282] NET: Registered protocol family 1
[    0.283291] pci 0000:00:02.0: Video device with shadowed ROM
[    0.284353] PCI: CLS 0 bytes, default 64
[    0.284383] Trying to unpack rootfs image as initramfs...
[    0.765727] Freeing initrd memory: 40960K (ffff880032ff0000 - ffff8800357f0000)
[    0.765796] DMAR: ACPI device "device:65" under DMAR at fed91000 as 00:15.0
[    0.765799] DMAR: ACPI device "device:66" under DMAR at fed91000 as 00:15.1
[    0.765821] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.765822] software IO TLB [mem 0x64737000-0x68737000] (64MB) mapped at [ffff880064737000-ffff880068736fff]
[    0.765969] Scanning for low memory corruption every 60 seconds
[    0.766312] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.766336] audit: initializing netlink subsys (disabled)
[    0.766348] audit: type=2000 audit(1487678830.764:1): initialized
[    0.766571] Initialise system trusted keyring
[    0.768001] zbud: loaded
[    0.768470] fuse init (API version 7.24)
[    0.768596] Key type big_key registered
[    0.769604] Key type asymmetric registered
[    0.769607] Asymmetric key parser 'x509' registered
[    0.769631] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.769696] io scheduler noop registered
[    0.769699] io scheduler deadline registered (default)
[    0.769719] io scheduler cfq registered
[    0.770124] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.770127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.770148] efifb: probing for efifb
[    0.770158] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90001000000, using 4160k, total 4160k
[    0.770159] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    0.770159] efifb: scrolling: redraw
[    0.770160] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.771910] Console: switching to colour frame buffer device 170x48
[    0.773458] fb0: EFI VGA frame buffer device
[    0.773463] intel_idle: MWAIT substates: 0x11142120
[    0.773464] intel_idle: v0.4 model 0x4E
[    0.773465] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.774312] ACPI: AC Adapter [AC] (off-line)
[    0.774366] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.774654] ACPI: Lid Switch [LID0]
[    0.774681] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.774683] ACPI: Power Button [PBTN]
[    0.774707] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.774708] ACPI: Sleep Button [SBTN]
[    0.774743] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.774744] ACPI: Power Button [PWRF]
[    0.776580] thermal LNXTHERM:00: registered as thermal_zone0
[    0.776582] ACPI: Thermal Zone [THM] (25 C)
[    0.776848] thermal LNXTHERM:01: registered as thermal_zone1
[    0.776849] ACPI: Thermal Zone [TZ00] (28 C)
[    0.776944] thermal LNXTHERM:02: registered as thermal_zone2
[    0.776945] ACPI: Thermal Zone [TZ01] (30 C)
[    0.776980] GHES: HEST is not enabled!
[    0.777089] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.780280] Linux agpgart interface v0.103
[    0.791336] ACPI: Battery Slot [BAT0] (battery present)
[    0.794876] brd: module loaded
[    0.796597] loop: module loaded
[    0.796763] libphy: Fixed MDIO Bus: probed
[    0.796766] tun: Universal TUN/TAP device driver, 1.6
[    0.796767] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.796821] PPP generic driver version 2.4.2
[    0.796892] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.796895] ehci-pci: EHCI PCI platform driver
[    0.796903] ehci-platform: EHCI generic platform driver
[    0.796911] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.796914] ohci-pci: OHCI PCI platform driver
[    0.796921] ohci-platform: OHCI generic platform driver
[    0.796927] uhci_hcd: USB Universal Host Controller Interface driver
[    0.797040] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.797044] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.798128] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.798132] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.798196] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.798198] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.798199] usb usb1: Product: xHCI Host Controller
[    0.798200] usb usb1: Manufacturer: Linux 4.5.0-040500-generic xhci-hcd
[    0.798200] usb usb1: SerialNumber: 0000:00:14.0
[    0.798290] hub 1-0:1.0: USB hub found
[    0.798303] hub 1-0:1.0: 12 ports detected
[    0.803656] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.803659] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.803678] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.803679] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.803680] usb usb2: Product: xHCI Host Controller
[    0.803681] usb usb2: Manufacturer: Linux 4.5.0-040500-generic xhci-hcd
[    0.803682] usb usb2: SerialNumber: 0000:00:14.0
[    0.803808] hub 2-0:1.0: USB hub found
[    0.803816] hub 2-0:1.0: 6 ports detected
[    0.806444] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.806762] i8042: Warning: Keylock active
[    0.808035] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.808043] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.808250] mousedev: PS/2 mouse device common for all mice
[    0.808868] rtc_cmos 00:01: RTC can wake from S4
[    0.809665] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.809773] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.809792] rtc_cmos 00:01: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.809799] i2c /dev entries driver
[    0.809863] device-mapper: uevent: version 1.0.3
[    0.809975] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    0.809986] Intel P-state driver initializing.
[    0.809988] intel_pstate: HWP enabled
[    0.810518] ledtrig-cpu: registered to indicate activity on CPUs
[    0.810521] EFI Variables Facility v0.08 2004-May-17
[    0.819196] NET: Registered protocol family 10
[    0.819509] NET: Registered protocol family 17
[    0.819518] Key type dns_resolver registered
[    0.819689] microcode: CPU0 sig=0x406e3, pf=0x80, revision=0x8a
[    0.819731] microcode: CPU1 sig=0x406e3, pf=0x80, revision=0x8a
[    0.819751] microcode: CPU2 sig=0x406e3, pf=0x80, revision=0x8a
[    0.819807] microcode: CPU3 sig=0x406e3, pf=0x80, revision=0x8a
[    0.819934] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.820318] registered taskstats version 1
[    0.820333] Loading compiled-in X.509 certificates
[    0.820882] Loaded X.509 cert 'Build time autogenerated kernel key: e87c17e018f1352bf3cbc45e4c354f6fb3f9e5e9'
[    0.820895] zswap: loaded using pool lzo/zbud
[    0.822531] Key type trusted registered
[    0.826518] Key type encrypted registered
[    0.826523] AppArmor: AppArmor sha1 policy hashing enabled
[    0.826526] ima: No TPM chip found, activating TPM-bypass!
[    0.826538] evm: HMAC attrs: 0x1
[    0.827755]   Magic number: 5:888:127
[    0.827821] acpi device:02: hash matches
[    0.828029] rtc_cmos 00:01: setting system clock to 2017-02-21 12:07:10 UTC (1487678830)
[    0.828131] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.828131] EDD information not available.
[    0.828215] PM: Hibernation image not present or could not be loaded.
[    0.829109] Freeing unused kernel memory: 1488K (ffffffff81f46000 - ffffffff820ba000)
[    0.829110] Write protecting the kernel read-only data: 14336k
[    0.829786] Freeing unused kernel memory: 1876K (ffff88000282b000 - ffff880002a00000)
[    0.829945] Freeing unused kernel memory: 48K (ffff880002df4000 - ffff880002e00000)
[    0.838391] random: systemd-udevd urandom read with 9 bits of entropy available
[    0.856770] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    0.877654] hidraw: raw HID events driver (C) Jiri Kosina
[    0.885597] [drm] Initialized drm 1.1.0 20060810
[    0.886292] ahci 0000:00:17.0: version 3.0
[    0.886636] ahci 0000:00:17.0: SSS flag set, parallel bus scan disabled
[    0.886657] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    0.886660] ahci 0000:00:17.0: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
[    0.887035] scsi host0: ahci
[    0.887181] ata1: SATA max UDMA/133 abar m2048@0xd532b000 port 0xd532b100 irq 275
[    0.887511] nvidia: module license 'NVIDIA' taints kernel.
[    0.887512] Disabling lock debugging due to kernel taint
[    0.891778] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    0.892911] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.892931] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.892953] r8169 0000:03:00.0: enabling device (0000 -> 0003)
[    0.893573] r8169 0000:03:00.0 eth0: RTL8106e at 0xffffc90000c9e000, 84:7b:eb:e7:01:ad, XID 04900000 IRQ 276
[    0.896418] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[    0.896615] nvidia-nvlink: Nvlink Core is being initialized, major device number 247
[    0.896628] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  367.57  Mon Oct  3 20:37:01 PDT 2016
[    0.907399] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  367.57  Mon Oct  3 20:32:57 PDT 2016
[    0.908326] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    0.909092] [drm] Memory usable by graphics device = 4096M
[    0.909095] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[    0.909096] fb: switching to inteldrmfb from EFI VGA
[    0.909112] Console: switching to colour dummy device 80x25
[    0.909305] [drm] Replacing VGA console driver
[    0.915501] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.915503] [drm] Driver supports precise vblank timestamp query.
[    0.917387] [drm] Finished loading i915/skl_dmc_ver1.bin (v1.26)
[    0.942596] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    1.055665] fbcon: inteldrmfb (fb0) is primary device
[    1.175250] usb 1-1: new low-speed USB device number 2 using xhci_hcd
[    1.199722] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.286209] ata1.00: ATA-8: TOSHIBA MQ02ABD100H, HEF01D, max UDMA/100
[    1.286210] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.288422] ata1.00: configured for UDMA/100
[    1.289009] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ02ABD1 1D   PQ: 0 ANSI: 5
[    1.311401] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    1.311402] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.311403] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.311609] sd 0:0:0:0: [sda] Write Protect is off
[    1.311610] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.311730] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.315271]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.316197] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.364395] usb 1-1: New USB device found, idVendor=1c4f, idProduct=0032
[    1.364396] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.364397] usb 1-1: Product: Usb Mouse
[    1.364397] usb 1-1: Manufacturer: SIGMACHIP
[    1.369488] usbcore: registered new interface driver usbhid
[    1.369488] usbhid: USB HID core driver
[    1.370992] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:1C4F:0032.0001/input/input7
[    1.371319] hid-generic 0003:1C4F:0032.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-1/input0
[    1.531288] usb 1-5: new high-speed USB device number 3 using xhci_hcd
[    1.602008] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.602798] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    1.602978] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20160108/video-1248)
[    1.602979] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    1.603003] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1b/LNXVIDEO:01/input/input9
[    1.603190] [drm] Initialized i915 1.6.0 20151218 for 0000:00:02.0 on minor 1
[    1.763239] tsc: Refined TSC clocksource calibration: 2592.000 MHz
[    1.763240] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x255cb6cc5db, max_idle_ns: 440795203504 ns
[    1.769959] usb 1-5: New USB device found, idVendor=1bcf, idProduct=28b0
[    1.769960] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.769960] usb 1-5: Product: Integrated_Webcam_HD
[    1.769961] usb 1-5: Manufacturer: CN06307G724876BOC139A02
[    1.842426] psmouse serio1: synaptics: queried max coordinates: x [..5664], y [..4648]
[    1.869992] psmouse serio1: synaptics: queried min coordinates: x [1278..], y [1206..]
[    1.924027] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd40123/0x840300/0x126800/0x0, board id: 3024, fw id: 1693264
[    1.957915] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.007243] usb 1-6: new high-speed USB device number 4 using xhci_hcd
[    2.191647] usb 1-6: New USB device found, idVendor=0bda, idProduct=0129
[    2.191648] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.191648] usb 1-6: Product: USB2.0-CRW
[    2.191649] usb 1-6: Manufacturer: Generic
[    2.191649] usb 1-6: SerialNumber: 20100201396000000
[    2.195546] usbcore: registered new interface driver rtsx_usb
[    2.359232] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[    2.363521] Console: switching to colour frame buffer device 170x48
[    2.365239] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.500651] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.544570] usb 1-8: New USB device found, idVendor=0cf3, idProduct=e007
[    2.544572] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.763529] clocksource: Switched to clocksource tsc
[    2.783379] [drm] RC6 on
[    2.817060] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    2.817152] systemd[1]: Detected architecture x86-64.
[    2.817347] systemd[1]: Set hostname to <apisys-Inspiron-5457>.
[    2.910758] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    2.910793] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    2.910808] systemd[1]: Listening on udev Kernel Socket.
[    2.910884] systemd[1]: Created slice System Slice.
[    2.910910] systemd[1]: Listening on Syslog Socket.
[    2.910918] systemd[1]: Reached target Remote File Systems (Pre).
[    2.910964] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    2.910979] systemd[1]: Listening on Journal Socket (/dev/log).
[    2.911014] systemd[1]: Created slice User and Session Slice.
[    2.911020] systemd[1]: Reached target Slices.
[    2.911025] systemd[1]: Reached target Remote File Systems.
[    2.911045] systemd[1]: Listening on Journal Socket.
[    2.923189] systemd[1]: Mounting Debug File System...
[    2.927395] systemd[1]: Mounting POSIX Message Queue File System...
[    2.927677] systemd[1]: Mounting Huge Pages File System...
[    2.928915] systemd[1]: Starting Load Kernel Modules...
[    2.929209] systemd[1]: Started Read required files in advance.
[    2.929617] systemd[1]: Starting Uncomplicated firewall...
[    2.929997] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    2.930316] systemd[1]: Starting Set console keymap...
[    2.930398] systemd[1]: Listening on fsck to fsckd communication Socket.
[    2.930416] systemd[1]: Reached target User and Group Name Lookups.
[    2.930485] systemd[1]: Listening on Journal Audit Socket.
[    2.930882] systemd[1]: Starting Journal Service...
[    2.931183] systemd[1]: Started Braille Device Support.
[    2.931310] systemd[1]: Listening on udev Control Socket.
[    2.931331] systemd[1]: Reached target Encrypted Volumes.
[    2.931382] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    2.945240] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    2.945684] systemd[1]: Starting Create Static Device Nodes in /dev...
[    2.958270] systemd[1]: Started Uncomplicated firewall.
[    2.962710] systemd[1]: Mounted Debug File System.
[    2.962733] systemd[1]: Mounted Huge Pages File System.
[    2.962746] systemd[1]: Mounted POSIX Message Queue File System.
[    2.990342] lp: driver loaded but no devices found
[    2.996295] ppdev: user-space parallel port driver
[    3.003637] systemd[1]: Started Load Kernel Modules.
[    3.023274] systemd[1]: Starting Apply Kernel Variables...
[    3.023655] systemd[1]: Mounting FUSE Control File System...
[    3.023973] systemd[1]: Started Journal Service.
[    3.098669] random: nonblocking pool is initialized
[    3.284030] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    3.302012] systemd-journald[228]: Received request to flush runtime journal from PID 1
[    3.363190] resource sanity check: requesting [mem 0xfed40040-0xfed4103f], which spans more than MSFT0101:00 [mem 0xfed40000-0xfed4087f]
[    3.363194] caller devm_ioremap_nocache+0x42/0x80 mapping multiple BARs
[    3.387632] input: DELL Wireless hotkeys as /devices/virtual/input/input10
[    3.387658] wmi: Mapper loaded
[    3.397566] Bluetooth: Core ver 2.21
[    3.397577] NET: Registered protocol family 31
[    3.397578] Bluetooth: HCI device and connection manager initialized
[    3.397580] Bluetooth: HCI socket layer initialized
[    3.397582] Bluetooth: L2CAP socket layer initialized
[    3.397586] Bluetooth: SCO socket layer initialized
[    3.423272] Bluetooth: HCI UART driver ver 2.3
[    3.423274] Bluetooth: HCI UART protocol H4 registered
[    3.423275] Bluetooth: HCI UART protocol BCSP registered
[    3.423276] Bluetooth: HCI UART protocol LL registered
[    3.423277] Bluetooth: HCI UART protocol ATH3K registered
[    3.423278] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.423299] Bluetooth: HCI UART protocol Intel registered
[    3.423308] Bluetooth: HCI UART protocol BCM registered
[    3.423309] Bluetooth: HCI UART protocol QCA registered
[    3.451399] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[    3.471132] idma64 idma64.0: Found Intel integrated DMA 64-bit
[    3.476926] usbcore: registered new interface driver btusb
[    3.503165] intel-lpss 0000:00:15.1: enabling device (0000 -> 0002)
[    3.503419] idma64 idma64.1: Found Intel integrated DMA 64-bit
[    3.519190] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    3.522776] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.533274] media: Linux media interface: v0.10
[    3.553631] Linux video capture interface: v2.00
[    3.604829] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    3.604962] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.612824] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:28b0)
[    3.615542] AVX2 version of gcm_enc/dec engaged.
[    3.615544] AES CTR mode by8 optimization enabled
[    3.623230] uvcvideo 1-5:1.0: Entity type for entity Extension 4 was not initialized!
[    3.623234] uvcvideo 1-5:1.0: Entity type for entity Extension 3 was not initialized!
[    3.623236] uvcvideo 1-5:1.0: Entity type for entity Processing 2 was not initialized!
[    3.623238] uvcvideo 1-5:1.0: Entity type for entity Camera 1 was not initialized!
[    3.624381] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input11
[    3.624439] usbcore: registered new interface driver uvcvideo
[    3.624441] USB Video Class driver (1.1.1)
[    3.723550] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC3234: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.723553] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.723554] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.723555] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.723556] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.723558] snd_hda_codec_realtek hdaudioC0D0:      Headset Mic=0x19
[    3.723559] snd_hda_codec_realtek hdaudioC0D0:      Headphone Mic=0x1a
[    3.723560] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    3.774328] intel_rapl: Found RAPL domain package
[    3.774333] intel_rapl: Found RAPL domain core
[    3.774334] intel_rapl: Found RAPL domain uncore
[    3.774336] intel_rapl: Found RAPL domain dram
[    3.779779] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    3.779904] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    3.779979] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    3.780066] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    3.836170] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 243
[    3.854697] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854748] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854773] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854796] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854817] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854851] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.854873] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.871853] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.970276] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.005416] Adding 8278012k swap on /dev/sda8.  Priority:-1 extents:1 across:8278012k FS
[    4.028961] dell_wmi: Detected Dell WMI interface version 1
[    4.029021] input: Dell WMI hotkeys as /devices/virtual/input/input16
[    4.043302] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    4.109324] input: DLLA70A:00 06CB:7621 Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-4/i2c-DLLA70A:00/0018:06CB:7621.0002/input/input17
[    4.109397] hid-multitouch 0018:06CB:7621.0002: input,hidraw1: I2C HID v1.00 Mouse [DLLA70A:00 06CB:7621] on i2c-DLLA70A:00
[    4.229263] audit: type=1400 audit(1487678833.895:2): apparmor="STATUS" operation="profile_load" name="/usr/bin/ubuntu-core-launcher" pid=786 comm="apparmor_parser"
[    4.237794] audit: type=1400 audit(1487678833.903:3): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
[    4.237799] audit: type=1400 audit(1487678833.903:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
[    4.237802] audit: type=1400 audit(1487678833.903:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=783 comm="apparmor_parser"
[    4.237804] audit: type=1400 audit(1487678833.903:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=783 comm="apparmor_parser"
[    4.242175] audit: type=1400 audit(1487678833.907:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=782 comm="apparmor_parser"
[    4.242180] audit: type=1400 audit(1487678833.907:8): apparmor="STATUS" operation="profile_load" name="chromium" pid=782 comm="apparmor_parser"
[    4.246233] audit: type=1400 audit(1487678833.911:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/snapd/snap-confine" pid=788 comm="apparmor_parser"
[    4.246238] audit: type=1400 audit(1487678833.911:10): apparmor="STATUS" operation="profile_load" name="mount-namespace-capture-helper" pid=788 comm="apparmor_parser"
[    5.609240] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.609242] Bluetooth: BNEP filters: protocol multicast
[    5.609245] Bluetooth: BNEP socket layer initialized
[    5.651936] bbswitch: version 0.8
[    5.651942] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    5.651946] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.RP01.PEGP
[    5.651954] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    5.652014] bbswitch: detected an Optimus _DSM function
[    5.652334] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    5.892987] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    6.084319] r8169 0000:03:00.0 enp3s0: link down
[    6.084322] r8169 0000:03:00.0 enp3s0: link down
[    6.084375] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    6.166371] vgaarb: this pci device is not a vga device
[    6.170455] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170505] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170542] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170572] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170595] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170630] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.170653] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.173585] ACPI Warning: \_SB.PCI0.RP01.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    6.307063] nvidia-modeset: Allocated GPU:0 (GPU-01f44ba1-65d8-9b0f-f8de-1173730e2caf) @ PCI:0000:01:00.0
[    6.307152] nvidia-modeset: Freed GPU:0 (GPU-01f44ba1-65d8-9b0f-f8de-1173730e2caf) @ PCI:0000:01:00.0
[    6.847769] vgaarb: this pci device is not a vga device
[    7.665866] r8169 0000:03:00.0 enp3s0: link up
[    7.665873] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[    9.931924] Bluetooth: RFCOMM TTY layer initialized
[    9.931929] Bluetooth: RFCOMM socket layer initialized
[    9.931933] Bluetooth: RFCOMM ver 1.11
[  192.634959] audit_printk_skb: 42 callbacks suppressed
[  192.634962] audit: type=1400 audit(1487679022.702:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/snapd/snap-confine" pid=3951 comm="apparmor_parser"
[  192.644726] audit: type=1400 audit(1487679022.714:26): apparmor="STATUS" operation="profile_replace" name="mount-namespace-capture-helper" pid=3951 comm="apparmor_parser"
[  320.650843] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  320.664724] JFS: nTxBlock = 8192, nTxLock = 65536
[  320.733451] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[  320.784530] QNX4 filesystem 0.2.3 registered.
[  320.908758] raid6: sse2x1   gen()  7528 MB/s
[  320.976762] raid6: sse2x1   xor()  5419 MB/s
[  321.044766] raid6: sse2x2   gen()  9875 MB/s
[  321.112766] raid6: sse2x2   xor()  6598 MB/s
[  321.180779] raid6: sse2x4   gen() 11694 MB/s
[  321.248776] raid6: sse2x4   xor()  6858 MB/s
[  321.316771] raid6: avx2x1   gen() 18596 MB/s
[  321.384774] raid6: avx2x2   gen() 21903 MB/s
[  321.452773] raid6: avx2x4   gen() 22832 MB/s
[  321.452776] raid6: using algorithm avx2x4 gen() 22832 MB/s
[  321.452777] raid6: using avx2x2 recovery algorithm
[  321.471686] xor: automatically using best checksumming function:
[  321.508772]    avx       : 25353.000 MB/sec
[  321.564472] Btrfs loaded
[  881.610762] Loading modules backported from Linux version next-20150731-0-g37bd1ea
[  881.610765] Backport generated by backports.git backports-20150731-0-g2af997b
[  881.654871] cfg80211: World regulatory domain updated:
[  881.654874] cfg80211:  DFS Master region: unset
[  881.654876] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  881.654879] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  881.654880] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  881.654882] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  881.654884] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  881.654886] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  881.654887] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[  881.654889] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  881.654890] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[ 3732.640052] vgaarb: this pci device is not a vga device
[ 3852.848101] vgaarb: this pci device is not a vga device
[ 5834.669491] vgaarb: this pci device is not a vga device
[ 7401.325867] vgaarb: this pci device is not a vga device
[ 7438.708430] vgaarb: this pci device is not a vga device
[ 7542.992939] vgaarb: this pci device is not a vga device
[11253.639164] perf interrupt took too long (2527 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[11590.955616] vgaarb: this pci device is not a vga device
[14111.280850] vgaarb: this pci device is not a vga device



```

---

### Post by jeremy31 on 2017-02-21
```
cd backports-20150731
sudo make uninstall
```
 Reboot

---

### Post by gustavosmonteiro on 2017-02-21
[COLOR=#000000][FONT=&quot]cd backports-20150731 : [/FONT][/COLOR]The directory or file was not found.

---

### Post by gustavosmonteiro on 2017-02-21
I found the directory and ran the code you said.
Now it works!!!! =DD

Thank you so much dudes!!

---


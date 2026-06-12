---
title: "Intel AX201 and AX101 driver patch"
date: 2023-06-20
forum: Networking &amp; Wireless
---

### Post by snewby on 2023-06-20
System is Beelink SEi11, wifi is not working

```
dmesg | grep iwl
[   12.085160] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   12.089997] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-74.ucode failed with error -2
[   12.091453] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[   12.091468] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[   12.091872] iwlwifi 0000:00:14.3: loaded firmware version 73.35c0a2c6.0 QuZ-a0-hr-b0-73.ucode op_mode iwlmvm
[   12.185290] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX101, REV=0x351
[   12.309621] iwlwifi 0000:00:14.3: Detected RF HR1 B3, rfid=0x10c000
[   13.339484] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[   13.340603] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[   13.340608] iwlwifi 0000:00:14.3: Transport status: 0x0000004A, valid: 6
[   13.340612] iwlwifi 0000:00:14.3: Loaded firmware version: 73.35c0a2c6.0 QuZ-a0-hr-b0-73.ucode
[   13.340616] iwlwifi 0000:00:14.3: 0x00000084 | NMI_INTERRUPT_UNKNOWN       
[   13.340620] iwlwifi 0000:00:14.3: 0x000022F0 | trm_hw_status0
[   13.340623] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status1
[   13.340626] iwlwifi 0000:00:14.3: 0x004CC0FE | branchlink2
[   13.340629] iwlwifi 0000:00:14.3: 0x004C2512 | interruptlink1
[   13.340632] iwlwifi 0000:00:14.3: 0x004C2512 | interruptlink2
[   13.340635] iwlwifi 0000:00:14.3: 0x004CADB8 | data1
[   13.340638] iwlwifi 0000:00:14.3: 0x01000000 | data2
[   13.340640] iwlwifi 0000:00:14.3: 0x00000000 | data3
[   13.340643] iwlwifi 0000:00:14.3: 0x00000000 | beacon time
[   13.340646] iwlwifi 0000:00:14.3: 0x00110C39 | tsf low
[   13.340649] iwlwifi 0000:00:14.3: 0x00000000 | tsf hi
[   13.340651] iwlwifi 0000:00:14.3: 0x00000000 | time gp1
[   13.340654] iwlwifi 0000:00:14.3: 0x001167E7 | time gp2
[   13.340657] iwlwifi 0000:00:14.3: 0x00000001 | uCode revision type
[   13.340660] iwlwifi 0000:00:14.3: 0x00000049 | uCode version major
[   13.340663] iwlwifi 0000:00:14.3: 0x35C0A2C6 | uCode version minor
[   13.340666] iwlwifi 0000:00:14.3: 0x00000351 | hw version
[   13.340669] iwlwifi 0000:00:14.3: 0x18C89001 | board version
[   13.340672] iwlwifi 0000:00:14.3: 0x8002FC12 | hcmd
[   13.340674] iwlwifi 0000:00:14.3: 0x00020000 | isr0
[   13.340677] iwlwifi 0000:00:14.3: 0x00000000 | isr1
[   13.340680] iwlwifi 0000:00:14.3: 0x08F00002 | isr2
[   13.340682] iwlwifi 0000:00:14.3: 0x00C0000C | isr3
[   13.340685] iwlwifi 0000:00:14.3: 0x00000000 | isr4
[   13.340688] iwlwifi 0000:00:14.3: 0x00000000 | last cmd Id
[   13.340690] iwlwifi 0000:00:14.3: 0x004CADB8 | wait_event
[   13.340693] iwlwifi 0000:00:14.3: 0x00000000 | l2p_control
[   13.340696] iwlwifi 0000:00:14.3: 0x00000000 | l2p_duration
[   13.340699] iwlwifi 0000:00:14.3: 0x00000000 | l2p_mhvalid
[   13.340701] iwlwifi 0000:00:14.3: 0x00000000 | l2p_addr_match
[   13.340704] iwlwifi 0000:00:14.3: 0x0000000B | lmpm_pmg_sel
[   13.340707] iwlwifi 0000:00:14.3: 0x00000000 | timestamp
[   13.340709] iwlwifi 0000:00:14.3: 0x00000020 | flow_handler
[   13.340754] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[   13.340757] iwlwifi 0000:00:14.3: Transport status: 0x0000004A, valid: 7
[   13.340760] iwlwifi 0000:00:14.3: 0x20000066 | NMI_INTERRUPT_HOST
[   13.340764] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[   13.340767] iwlwifi 0000:00:14.3: 0x80455E18 | umac branchlink2
[   13.340770] iwlwifi 0000:00:14.3: 0x804723AE | umac interruptlink1
[   13.340773] iwlwifi 0000:00:14.3: 0xC0081DE0 | umac interruptlink2
[   13.340775] iwlwifi 0000:00:14.3: 0x01000000 | umac data1
[   13.340778] iwlwifi 0000:00:14.3: 0xC0081DE0 | umac data2
[   13.340781] iwlwifi 0000:00:14.3: 0x00000000 | umac data3
[   13.340783] iwlwifi 0000:00:14.3: 0x00000049 | umac major
[   13.340786] iwlwifi 0000:00:14.3: 0x35C0A2C6 | umac minor
[   13.340789] iwlwifi 0000:00:14.3: 0x001167E5 | frame pointer
[   13.340792] iwlwifi 0000:00:14.3: 0xC0887EFC | stack pointer
[   13.340794] iwlwifi 0000:00:14.3: 0x00010C00 | last host cmd
[   13.340797] iwlwifi 0000:00:14.3: 0x00000004 | isr status reg
[   13.340821] iwlwifi 0000:00:14.3: IML/ROM dump:
[   13.340823] iwlwifi 0000:00:14.3: 0x00000003 | IML/ROM error/state
[   13.340850] iwlwifi 0000:00:14.3: 0x00005654 | IML/ROM data1
[   13.340879] iwlwifi 0000:00:14.3: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[   13.340904] iwlwifi 0000:00:14.3: Fseq Registers:
[   13.340925] iwlwifi 0000:00:14.3: 0x20000000 | FSEQ_ERROR_CODE
[   13.340930] iwlwifi 0000:00:14.3: 0x80290033 | FSEQ_TOP_INIT_VERSION
[   13.340951] iwlwifi 0000:00:14.3: 0x00090006 | FSEQ_CNVIO_INIT_VERSION
[   13.340974] iwlwifi 0000:00:14.3: 0x0000A482 | FSEQ_OTP_VERSION
[   13.340979] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_TOP_CONTENT_VERSION
[   13.341001] iwlwifi 0000:00:14.3: 0x4552414E | FSEQ_ALIVE_TOKEN
[   13.341006] iwlwifi 0000:00:14.3: 0x20000302 | FSEQ_CNVI_ID
[   13.341027] iwlwifi 0000:00:14.3: 0x00000501 | FSEQ_CNVR_ID
[   13.341032] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP
[   13.341055] iwlwifi 0000:00:14.3: 0x00000501 | CNVR_AUX_MISC_CHIP
[   13.341077] iwlwifi 0000:00:14.3: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   13.341100] iwlwifi 0000:00:14.3: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   13.677865] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
```

```
lspci -kvnn | sed -n '/Network/,/^$/ p'
00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 30)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 [8086:0244]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 6001124000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```


I believe this may be an answer but I have no idea how to apply this patch:

[https://askubuntu.com/questions/1459856/intel-alder-lake-n100-wifi-and-bluetooth-issues/1462190#1462190](https://askubuntu.com/questions/1459856/intel-alder-lake-n100-wifi-and-bluetooth-issues/1462190#1462190)

Any help would be greatly appreciated.[URL="https://askubuntu.com/questions/1459856/intel-alder-lake-n100-wifi-and-bluetooth-issues/1462190#1462190"]
[/URL]

---

### Post by jeremy31 on 2023-06-20
See the wireless script link in my signature and post results

---

### Post by snewby on 2023-06-30
I actually prefer Mint but I tried the latest ubuntu.

```

########## wireless info START ##########

Report from: 30 Jun 2023 07:55 EDT -0400

Booted last: 30 Jun 2023 00:00 EDT -0400

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.19.0-46-generic #47~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 21 15:35:31 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 30)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 [8086:0244]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13fe:6700 Kingston Technology Company Inc. USB DISK 3.2
Bus 003 Device 003: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

iwlmvm                610304  0
mac80211             1323008  1 iwlmvm
libarc4                16384  1 mac80211
iwlwifi               503808  1 iwlmvm
wmi_bmof               16384  0
cfg80211             1052672  3 iwlmvm,iwlwifi,mac80211
wmi                    32768  1 wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.69.214/24 brd 192.168.69.255 scope global dynamic noprefixroute enp3s0
       valid_lft 42482sec preferred_lft 42482sec
    inet6 fe80::1824:289e:ee68:2dd9/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

default via 192.168.69.1 dev enp3s0 proto dhcp metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 
192.168.69.0/24 dev enp3s0 proto kernel scope link src 192.168.69.214 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root         672       1  0 07:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 5.19.0-46-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/net/enp3s0
GENERAL.PATH:                           pci-0000:03:00.0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       49198ab1-c768-370e-92d6-b4dfb4c432d8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.69.214/24
IP4.GATEWAY:                            192.168.69.1
IP4.ROUTE[1]:                           dst = 192.168.69.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 0.0.0.0/0, nh = 192.168.69.1, mt = 100
IP4.DNS[1]:                             192.168.69.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        broadcast_address = 192.168.69.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 43200
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.69.1
DHCP4.OPTION[4]:                        domain_name = lan
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.69.1
DHCP4.OPTION[6]:                        expiry = 1688168618
DHCP4.OPTION[7]:                        host_name = van-media
DHCP4.OPTION[8]:                        ip_address = 192.168.69.214
DHCP4.OPTION[9]:                        next_server = 192.168.69.1
DHCP4.OPTION[10]:                       requested_broadcast_address = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_domain_search = 1
DHCP4.OPTION[14]:                       requested_host_name = 1
DHCP4.OPTION[15]:                       requested_interface_mtu = 1
DHCP4.OPTION[16]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_nis_domain = 1
DHCP4.OPTION[18]:                       requested_nis_servers = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_root_path = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_static_routes = 1
DHCP4.OPTION[24]:                       requested_subnet_mask = 1
DHCP4.OPTION[25]:                       requested_time_offset = 1
DHCP4.OPTION[26]:                       requested_wpad = 1
DHCP4.OPTION[27]:                       routers = 192.168.69.1
DHCP4.OPTION[28]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::1824:289e:ee68:2dd9/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   49198ab1-c768-370e-92d6-b4dfb4c432d8 | Wired connection 1

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
description:    The new Intel(R) wireless AGN driver for Linux
depends:        mac80211,cfg80211,iwlwifi
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/5.19.0-46-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
description:    Intel(R) Wireless WiFi driver for Linux
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K (16K buffers) 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:0:disable, 1-15:FW_DBG_PRESET Values, 16:enabled without preset value defined,Debug INI TLV FW debug infrastructure (default: 16)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.19.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

grep: /sys/module/iwlwifi/parameters/enable_ini: Operation not permitted
[iwlwifi]
11n_disable: 0
amsdu_size: 0
bt_coex_active: Y
disable_11ac: N
disable_11ax: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

[    7.222416] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
[    7.234772] iwlwifi 0000:00:14.3: retry init count 2
[    8.084519] r8169 0000:03:00.0 enp3s0: Link is Down
[  287.683108] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[  287.683133] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############


```

And same from Mint if you care to see.
```

########## wireless info START ##########

Report from: 21 Jun 2023 08:00 EDT -0400

Booted last: 21 Jun 2023 00:00 EDT -0400

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Linuxmint
Description:    Linux Mint 21.1
Release:    21.1
Codename:    vera

##### kernel ############################

Linux 5.15.0-75-generic #82-Ubuntu SMP Tue Jun 6 23:10:23 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Cinnamon

##### lspci #############################

00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 30)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 [8086:0244]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0a12:4007 Cambridge Silicon Radio, Ltd eppfun AK3040Plus
Bus 003 Device 004: ID 0a12:4010 Cambridge Silicon Radio, Ltd 
Bus 003 Device 003: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

iwlmvm                569344  0
mac80211             1249280  1 iwlmvm
libarc4                16384  1 mac80211
iwlwifi               450560  1 iwlmvm
wmi_bmof               16384  0
cfg80211              974848  3 iwlmvm,iwlwifi,mac80211
wmi                    32768  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
source /etc/network/interfaces.d/*

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.69.214/24 brd 192.168.69.255 scope global dynamic noprefixroute enp3s0
       valid_lft 25657sec preferred_lft 25657sec
    inet6 fe80::2dbc:6451:a5d0:11ed/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

##### route #############################

default via 192.168.69.1 dev enp3s0 proto dhcp metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 
192.168.69.0/24 dev enp3s0 proto kernel scope link src 192.168.69.214 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root         707       1  0 Jun20 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 5.15.0-75-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/net/enp3s0
GENERAL.PATH:                           pci-0000:03:00.0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       52de6bc9-603e-3978-a49e-526ffc94da08
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.69.214/24
IP4.GATEWAY:                            192.168.69.1
IP4.ROUTE[1]:                           dst = 192.168.69.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 0.0.0.0/0, nh = 192.168.69.1, mt = 100
IP4.DNS[1]:                             192.168.69.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        broadcast_address = 192.168.69.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 43200
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.69.1
DHCP4.OPTION[4]:                        domain_name = lan
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.69.1
DHCP4.OPTION[6]:                        expiry = 1687374473
DHCP4.OPTION[7]:                        host_name = vanbox
DHCP4.OPTION[8]:                        ip_address = 192.168.69.214
DHCP4.OPTION[9]:                        next_server = 192.168.69.1
DHCP4.OPTION[10]:                       requested_broadcast_address = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_domain_search = 1
DHCP4.OPTION[14]:                       requested_host_name = 1
DHCP4.OPTION[15]:                       requested_interface_mtu = 1
DHCP4.OPTION[16]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_nis_domain = 1
DHCP4.OPTION[18]:                       requested_nis_servers = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_root_path = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_static_routes = 1
DHCP4.OPTION[24]:                       requested_subnet_mask = 1
DHCP4.OPTION[25]:                       requested_time_offset = 1
DHCP4.OPTION[26]:                       requested_wpad = 1
DHCP4.OPTION[27]:                       routers = 192.168.69.1
DHCP4.OPTION[28]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::2dbc:6451:a5d0:11ed/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   52de6bc9-603e-3978-a49e-526ffc94da08 | Wired connection 1

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
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/1-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (755 - 928 @ 2), (N/A, 20), (N/A), PASSIVE-SCAN
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/5.15.0-75-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
description:    The new Intel(R) wireless AGN driver for Linux
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       5.15.0-75-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/5.15.0-75-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.15.0-75-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/5.15.0-75-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
description:    Intel(R) Wireless WiFi driver for Linux
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.15.0-75-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K (16K buffers) 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: true (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.15.0-75-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-75-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
bt_coex_active: Y
disable_11ac: N
disable_11ax: N
enable_ini: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

[   12.015013] iwlwifi 0000:00:14.3: Transport status: 0x0000004A, valid: 6
[   12.015016] iwlwifi 0000:00:14.3: Loaded firmware version: 66.f1c864e0.0 QuZ-a0-hr-b0-66.ucode
[   12.015017] iwlwifi 0000:00:14.3: 0x00000084 | NMI_INTERRUPT_UNKNOWN       
[   12.015019] iwlwifi 0000:00:14.3: 0x000022F0 | trm_hw_status0
[   12.015020] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status1
[   12.015021] iwlwifi 0000:00:14.3: 0x004CB01A | branchlink2
[   12.015023] iwlwifi 0000:00:14.3: 0x004C183E | interruptlink1
[   12.015024] iwlwifi 0000:00:14.3: 0x004C183E | interruptlink2
[   12.015025] iwlwifi 0000:00:14.3: 0x004C9CEE | data1
[   12.015026] iwlwifi 0000:00:14.3: 0x01000000 | data2
[   12.015027] iwlwifi 0000:00:14.3: 0x00000000 | data3
[   12.015028] iwlwifi 0000:00:14.3: 0x00000000 | beacon time
[   12.015029] iwlwifi 0000:00:14.3: 0x0010A52D | tsf low
[   12.015031] iwlwifi 0000:00:14.3: 0x00000000 | tsf hi
[   12.015032] iwlwifi 0000:00:14.3: 0x00000000 | time gp1
[   12.015033] iwlwifi 0000:00:14.3: 0x00110326 | time gp2
[   12.015034] iwlwifi 0000:00:14.3: 0x00000001 | uCode revision type
[   12.015035] iwlwifi 0000:00:14.3: 0x00000042 | uCode version major
[   12.015037] iwlwifi 0000:00:14.3: 0xF1C864E0 | uCode version minor
[   12.015038] iwlwifi 0000:00:14.3: 0x00000351 | hw version
[   12.015039] iwlwifi 0000:00:14.3: 0x18C89004 | board version
[   12.015040] iwlwifi 0000:00:14.3: 0x8003F502 | hcmd
[   12.015041] iwlwifi 0000:00:14.3: 0x00020000 | isr0
[   12.015042] iwlwifi 0000:00:14.3: 0x00000000 | isr1
[   12.015044] iwlwifi 0000:00:14.3: 0x08F00002 | isr2
[   12.015045] iwlwifi 0000:00:14.3: 0x00C0000C | isr3
[   12.015046] iwlwifi 0000:00:14.3: 0x00000000 | isr4
[   12.015047] iwlwifi 0000:00:14.3: 0x00000000 | last cmd Id
[   12.015048] iwlwifi 0000:00:14.3: 0x004C9CEE | wait_event
[   12.015049] iwlwifi 0000:00:14.3: 0x00000000 | l2p_control
[   12.015050] iwlwifi 0000:00:14.3: 0x00000000 | l2p_duration
[   12.015052] iwlwifi 0000:00:14.3: 0x00000000 | l2p_mhvalid
[   12.015053] iwlwifi 0000:00:14.3: 0x00000000 | l2p_addr_match
[   12.015054] iwlwifi 0000:00:14.3: 0x0000000B | lmpm_pmg_sel
[   12.015055] iwlwifi 0000:00:14.3: 0x00000000 | timestamp
[   12.015056] iwlwifi 0000:00:14.3: 0x00000020 | flow_handler
[   12.015095] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[   12.015096] iwlwifi 0000:00:14.3: Transport status: 0x0000004A, valid: 7
[   12.015098] iwlwifi 0000:00:14.3: 0x20000066 | NMI_INTERRUPT_HOST
[   12.015099] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[   12.015101] iwlwifi 0000:00:14.3: 0x80455AE6 | umac branchlink2
[   12.015102] iwlwifi 0000:00:14.3: 0x8047430E | umac interruptlink1
[   12.015103] iwlwifi 0000:00:14.3: 0xC0084176 | umac interruptlink2
[   12.015104] iwlwifi 0000:00:14.3: 0x01000000 | umac data1
[   12.015105] iwlwifi 0000:00:14.3: 0xC0084176 | umac data2
[   12.015106] iwlwifi 0000:00:14.3: 0x00000000 | umac data3
[   12.015107] iwlwifi 0000:00:14.3: 0x00000042 | umac major
[   12.015109] iwlwifi 0000:00:14.3: 0xF1C864E0 | umac minor
[   12.015110] iwlwifi 0000:00:14.3: 0x00110324 | frame pointer
[   12.015111] iwlwifi 0000:00:14.3: 0xC0887F00 | stack pointer
[   12.015112] iwlwifi 0000:00:14.3: 0x00010C00 | last host cmd
[   12.015113] iwlwifi 0000:00:14.3: 0x00000004 | isr status reg
[   12.015134] iwlwifi 0000:00:14.3: IML/ROM dump:
[   12.015135] iwlwifi 0000:00:14.3: 0x00000003 | IML/ROM error/state
[   12.015144] iwlwifi 0000:00:14.3: 0x00005944 | IML/ROM data1
[   12.015153] iwlwifi 0000:00:14.3: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[   12.015159] iwlwifi 0000:00:14.3: Fseq Registers:
[   12.015162] iwlwifi 0000:00:14.3: 0x60000000 | FSEQ_ERROR_CODE
[   12.015165] iwlwifi 0000:00:14.3: 0x80290033 | FSEQ_TOP_INIT_VERSION
[   12.015168] iwlwifi 0000:00:14.3: 0x00090006 | FSEQ_CNVIO_INIT_VERSION
[   12.015171] iwlwifi 0000:00:14.3: 0x0000A482 | FSEQ_OTP_VERSION
[   12.015193] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_TOP_CONTENT_VERSION
[   12.015196] iwlwifi 0000:00:14.3: 0x4552414E | FSEQ_ALIVE_TOKEN
[   12.015199] iwlwifi 0000:00:14.3: 0x20000302 | FSEQ_CNVI_ID
[   12.015202] iwlwifi 0000:00:14.3: 0x00000501 | FSEQ_CNVR_ID
[   12.015205] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP
[   12.015211] iwlwifi 0000:00:14.3: 0x00000501 | CNVR_AUX_MISC_CHIP
[   12.015216] iwlwifi 0000:00:14.3: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   12.015240] iwlwifi 0000:00:14.3: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   12.352170] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
[   12.364605] iwlwifi 0000:00:14.3: retry init count 2
[   13.906783] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   13.906797] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2023-07-06
Power off and remove power cord and battery(if possible) the hold power button for 30 seconds, put back together and boot

---


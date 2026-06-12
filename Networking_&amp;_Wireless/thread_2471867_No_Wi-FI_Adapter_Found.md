---
title: "No Wi-FI Adapter Found"
date: 2022-02-11
forum: Networking &amp; Wireless
---

### Post by spiruel on 2022-02-11
Hello,

I have a Intel Corporation Wi-Fi 6 AX201 wifi adapter that is suddenly not working after a reboot. I have followed many proposed solutions online and have not been able to use them to resolve the issue.

Results from `dmesg | grep iwl`

```
[    2.149266] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    2.162835] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[    2.162852] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[    2.163139] iwlwifi 0000:00:14.3: loaded firmware version 63.c04f3485.0 QuZ-a0-hr-b0-63.ucode op_mode iwlmvm
[    2.402444] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354
[    3.435257] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x5881, CPU2 Status: 0x3
[    3.435305] iwlwifi 0000:00:14.3: UMAC PC: 0xc008097e
[    3.435314] iwlwifi 0000:00:14.3: LMAC PC: 0x149e6
[    3.435316] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    3.436400] iwlwifi 0000:00:14.3: Loaded firmware version: 63.c04f3485.0 QuZ-a0-hr-b0-63.ucode
[    3.436402] iwlwifi 0000:00:14.3: 0x00000000 | ADVANCED_SYSASSERT          
[    3.436403] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status0
[    3.436404] iwlwifi 0000:00:14.3: 0x00000000 | trm_hw_status1
[    3.436405] iwlwifi 0000:00:14.3: 0x00000000 | branchlink2
[    3.436406] iwlwifi 0000:00:14.3: 0x00000000 | interruptlink1
[    3.436407] iwlwifi 0000:00:14.3: 0x00000000 | interruptlink2
[    3.436408] iwlwifi 0000:00:14.3: 0x00000000 | data1
[    3.436409] iwlwifi 0000:00:14.3: 0x00000000 | data2
[    3.436410] iwlwifi 0000:00:14.3: 0x00000000 | data3
[    3.436411] iwlwifi 0000:00:14.3: 0x00000000 | beacon time
[    3.436412] iwlwifi 0000:00:14.3: 0x00000000 | tsf low
[    3.436413] iwlwifi 0000:00:14.3: 0x00000000 | tsf hi
[    3.436414] iwlwifi 0000:00:14.3: 0x00000000 | time gp1
[    3.436415] iwlwifi 0000:00:14.3: 0x00000000 | time gp2
[    3.436416] iwlwifi 0000:00:14.3: 0x00000000 | uCode revision type
[    3.436417] iwlwifi 0000:00:14.3: 0x00000000 | uCode version major
[    3.436417] iwlwifi 0000:00:14.3: 0x00000000 | uCode version minor
[    3.436418] iwlwifi 0000:00:14.3: 0x00000000 | hw version
[    3.436419] iwlwifi 0000:00:14.3: 0x00000000 | board version
[    3.436420] iwlwifi 0000:00:14.3: 0x00000000 | hcmd
[    3.436421] iwlwifi 0000:00:14.3: 0x00000000 | isr0
[    3.436422] iwlwifi 0000:00:14.3: 0x00000000 | isr1
[    3.436423] iwlwifi 0000:00:14.3: 0x00000000 | isr2
[    3.436424] iwlwifi 0000:00:14.3: 0x00000000 | isr3
[    3.436425] iwlwifi 0000:00:14.3: 0x00000000 | isr4
[    3.436426] iwlwifi 0000:00:14.3: 0x00000000 | last cmd Id
[    3.436427] iwlwifi 0000:00:14.3: 0x00000000 | wait_event
[    3.436427] iwlwifi 0000:00:14.3: 0x00000000 | l2p_control
[    3.436428] iwlwifi 0000:00:14.3: 0x00000000 | l2p_duration
[    3.436429] iwlwifi 0000:00:14.3: 0x00000000 | l2p_mhvalid
[    3.436430] iwlwifi 0000:00:14.3: 0x00000000 | l2p_addr_match
[    3.436431] iwlwifi 0000:00:14.3: 0x00000000 | lmpm_pmg_sel
[    3.436432] iwlwifi 0000:00:14.3: 0x00000000 | timestamp
[    3.436433] iwlwifi 0000:00:14.3: 0x00000000 | flow_handler
[    3.436469] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[    3.436470] iwlwifi 0000:00:14.3: Status: 0x00000000, count: 7
[    3.436471] iwlwifi 0000:00:14.3: 0x20000066 | NMI_INTERRUPT_HOST
[    3.436473] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[    3.436474] iwlwifi 0000:00:14.3: 0x8045544E | umac branchlink2
[    3.436475] iwlwifi 0000:00:14.3: 0x8047395A | umac interruptlink1
[    3.436476] iwlwifi 0000:00:14.3: 0xC00834C2 | umac interruptlink2
[    3.436476] iwlwifi 0000:00:14.3: 0x01000000 | umac data1
[    3.436478] iwlwifi 0000:00:14.3: 0xC00834C2 | umac data2
[    3.436479] iwlwifi 0000:00:14.3: 0x00000000 | umac data3
[    3.436479] iwlwifi 0000:00:14.3: 0x0000003F | umac major
[    3.436480] iwlwifi 0000:00:14.3: 0xC04F3485 | umac minor
[    3.436481] iwlwifi 0000:00:14.3: 0x000F8C8C | frame pointer
[    3.436482] iwlwifi 0000:00:14.3: 0xC0887F28 | stack pointer
[    3.436483] iwlwifi 0000:00:14.3: 0x00000000 | last host cmd
[    3.436484] iwlwifi 0000:00:14.3: 0x00000004 | isr status reg
[    3.436502] iwlwifi 0000:00:14.3: IML/ROM dump:
[    3.436503] iwlwifi 0000:00:14.3: 0x00000003 | IML/ROM error/state
[    3.436510] iwlwifi 0000:00:14.3: 0x00005881 | IML/ROM data1
[    3.436517] iwlwifi 0000:00:14.3: 0x00000080 | IML/ROM WFPM_AUTH_KEY_0
[    3.436522] iwlwifi 0000:00:14.3: Fseq Registers:
[    3.436525] iwlwifi 0000:00:14.3: 0x20000021 | FSEQ_ERROR_CODE
[    3.436527] iwlwifi 0000:00:14.3: 0x80290033 | FSEQ_TOP_INIT_VERSION
[    3.436530] iwlwifi 0000:00:14.3: 0x00090006 | FSEQ_CNVIO_INIT_VERSION
[    3.436532] iwlwifi 0000:00:14.3: 0x0000A481 | FSEQ_OTP_VERSION
[    3.436535] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_TOP_CONTENT_VERSION
[    3.436537] iwlwifi 0000:00:14.3: 0x4552414E | FSEQ_ALIVE_TOKEN
[    3.436540] iwlwifi 0000:00:14.3: 0x20000302 | FSEQ_CNVI_ID
[    3.436542] iwlwifi 0000:00:14.3: 0x01300504 | FSEQ_CNVR_ID
[    3.436545] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP
[    3.436549] iwlwifi 0000:00:14.3: 0x01300504 | CNVR_AUX_MISC_CHIP
[    3.436554] iwlwifi 0000:00:14.3: 0x05B0905B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    3.436558] iwlwifi 0000:00:14.3: 0x0000025B | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    3.436561] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[    3.436563] iwlwifi 0000:00:14.3: WRT: Collecting data: ini trigger 13 fired (delay=0ms).
[    4.282401] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110
```

And some additional wireless info I've gathered since the wifi stopped working:



```
##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal


##### kernel ############################


Linux 5.13.0-28-generic #31~20.04.1-Ubuntu SMP Wed Jan 19 14:08:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:06f0]
	DeviceName: Onboard - Ethernet
	Subsystem: Intel Corporation Device [8086:4070]


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (11) I219-V [8086:0d4d]
	DeviceName: Onboard - Ethernet
	Subsystem: Dell Ethernet Connection (11) I219-V [1028:09c2]


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 005: ID 8087:0026 Intel Corp. 
Bus 001 Device 004: ID 0bda:565c Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 001 Device 003: ID 0a5c:5842 Broadcom Corp. 58200
Bus 001 Device 009: ID 18d1:4ee4 Google Inc. Nexus 4/5/7/10 (debug + tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


iwlmvm                421888  0
mac80211             1028096  1 iwlmvm
libarc4                16384  1 mac80211
iwlwifi               372736  1 iwlmvm
dell_laptop            24576  0
ledtrig_audio          16384  4 snd_ctl_led,snd_hda_codec_generic,snd_sof,dell_laptop
dell_wmi               20480  0
wl                   6455296  0
dell_smbios            28672  2 dell_wmi,dell_laptop
dell_wmi_descriptor    20480  2 dell_wmi,dell_smbios
wmi_bmof               16384  0
intel_wmi_thunderbolt    20480  0
mxm_wmi                16384  0
cfg80211              888832  4 wl,iwlmvm,iwlwifi,mac80211
sparse_keymap          16384  2 intel_hid,dell_wmi
wmi                    32768  6 intel_wmi_thunderbolt,dell_wmi,wmi_bmof,dell_smbios,dell_wmi_descriptor,mxm_wmi
video                  53248  3 dell_wmi,dell_laptop,i915


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno2' [IF1]> brd <MAC address>
    altname enp0s31f6
4: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'usb0' [IF2]> brd <MAC address>
    inet 192.168.24.50/24 brd 192.168.24.255 scope global dynamic noprefixroute usb0
       valid_lft 2530sec preferred_lft 2530sec
    inet6 fe80::e517:b1f5:a127:bd73/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


eno2      no wireless extensions.


usb0      no wireless extensions.


##### route #############################


default via 192.168.24.173 dev usb0 proto dhcp metric 100 
169.254.0.0/16 dev usb0 scope link metric 1000 
192.168.24.0/24 dev usb0 proto kernel scope link src 192.168.24.50 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad


##### network managers ##################


Installed:


	NetworkManager


Running:


root         996       1  0 12:35 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         Google Inc.
GENERAL.PRODUCT:                        Nexus 4/5/7/10 (debug + tether)
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 5.13.0-28-generic
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       0920af7a-2706-3988-8466-14bf1f70ae38
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.24.50/24
IP4.GATEWAY:                            192.168.24.173
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.24.173, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.24.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.24.173
DHCP4.OPTION[1]:                        dhcp_lease_time = 3599
DHCP4.OPTION[2]:                        domain_name_servers = 192.168.24.173
DHCP4.OPTION[3]:                        expiry = 1644245025
DHCP4.OPTION[4]:                        host_name = eesjb-Precision-3551
DHCP4.OPTION[5]:                        ip_address = 192.168.24.50
DHCP4.OPTION[6]:                        next_server = 192.168.24.173
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_domain_name_servers = 1
DHCP4.OPTION[10]:                       requested_domain_search = 1
DHCP4.OPTION[11]:                       requested_host_name = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[14]:                       requested_nis_domain = 1
DHCP4.OPTION[15]:                       requested_nis_servers = 1
DHCP4.OPTION[16]:                       requested_ntp_servers = 1
DHCP4.OPTION[17]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[18]:                       requested_root_path = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       requested_subnet_mask = 1
DHCP4.OPTION[22]:                       requested_time_offset = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       routers = 192.168.24.173
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::e517:b1f5:a127:bd73/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/31
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0920af7a-2706-3988-8466-14bf1f70ae38 | Wired connection 2


GENERAL.DEVICE:                         eno2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (11) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 5.13.0-28-generic
GENERAL.FIRMWARE-VERSION:               0.4-4
GENERAL.HWADDR:                         <MAC 'eno2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/eno2
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
```



What can I do to fix this?

---


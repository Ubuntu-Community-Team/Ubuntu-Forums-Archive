---
title: "[WIRELESS] HP14 ba0xx No Wifi Ubuntu 17.10"
date: 2017-11-03
forum: Networking &amp; Wireless
---

### Post by alphacentauri82 on 2017-11-03
HI! i have wired connection but no wireless. I ran the wireless wizard and also did the same commands when i had no connection. Will post both results. im not really sure if other post results will work for my case so this is why i am posting mine.

[B]Before connecting via wire
[/B]
```



cat /etc/lsb-release; uname -a


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
Linux AlphaCentauri 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux




lspci -nnk | grep -iA2 net


    Kernel modules: i2c_i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8320]
    Kernel driver in use: r8169
    Kernel modules: r8169


lsusb


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b5db Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 1bbb:af2b T & A Mobile Phones 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




 iwconfig
eno1      no wireless extensions.


lo        no wireless extensions.




rfkill list all


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


 lsmod


Module                  Size  Used by
bnep                   20480  2
nls_iso8859_1          16384  1
cmdlinepart            16384  0
intel_spi_platform     16384  0
intel_spi              20480  1 intel_spi_platform
spi_nor                28672  1 intel_spi
mtd                    57344  4 spi_nor,intel_spi,cmdlinepart
uvcvideo               90112  0
intel_rapl             20480  0
intel_powerclamp       16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
coretemp               16384  0
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
kvm                   581632  0
irqbypass              16384  1 kvm
snd_hda_codec_hdmi     49152  1
punit_atom_debug       16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
pcbc                   16384  0
aesni_intel           188416  0
bluetooth             540672  12 btrtl,btintel,bnep,btbcm,btusb
ecdh_generic           24576  1 bluetooth
aes_x86_64             20480  1 aesni_intel
snd_hda_intel          40960  6
crypto_simd            16384  1 aesni_intel
hp_wmi                 16384  0
input_leds             16384  0
joydev                 20480  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
glue_helper            16384  1 aesni_intel
sparse_keymap          16384  1 hp_wmi
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
serio_raw              16384  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
wmi_bmof               16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
int3400_thermal        16384  0
int3403_thermal        16384  0
processor_thermal_device    16384  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
intel_soc_dts_iosf     16384  1 processor_thermal_device
soc_button_array       16384  0
hp_wireless            16384  0
mei_txe                20480  0
soundcore              16384  1 snd
tpm_crb                16384  0
intel_int0002_vgpio    16384  1
mei                    98304  1 mei_txe
shpchp                 36864  0
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
i915                 1798144  25
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  81920  0
mii                    16384  1 r8169
drm                   356352  25 i915,drm_kms_helper
dwc3                  114688  0
psmouse               147456  0
wmi                    24576  2 wmi_bmof,hp_wmi
ulpi                   16384  1 dwc3
ahci                   36864  2
udc_core               49152  1 dwc3
video                  40960  1 i915
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
libahci                32768  1 ahci



```

After connecting and running the wireless wizard

```




########## wireless info START ##########


Report from: 03 Nov 2017 17:51 -03 -0300


Booted last: 03 Nov 2017 00:00 -03 -0300


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful


##### kernel ############################


Linux 4.13.0-16-generic #19-Ubuntu SMP Wed Oct 11 18:35:14 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu on Xorg


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8320]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b5db Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 1bbb:af2b T & A Mobile Phones 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    24576  2 wmi_bmof,hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    inet 192.168.1.139/24 brd 192.168.1.255 scope global dynamic eno1
       valid_lft 85658sec preferred_lft 85658sec
    inet6 lalalalalala scope link 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


##### route #############################


default via 192.168.1.1 dev eno1 proto static metric 100 
lalalalalala dev eno1 scope link metric 1000 
lalalalala  dev eno1 proto kernel scope link src 192.168.1.139 metric 100 


##### resolv.conf #######################


nameserver 127.0.0.53


search hidden by me


##### network managers ##################


Installed:


    NetworkManager


Running:


root       570     1  0 17:39 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       930d6c42-00d0-3d61-a4e9-0dd65920e33b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   930d6c42-00d0-3d61-a4e9-0dd65920e33b | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.139/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = none of your business!, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             hidden
IP4.DNS[2]:                             hidden
IP4.DOMAIN[1]:                          hidden by me!
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = hidden by me!
DHCP4.OPTION[5]:                        ip_address = 192.168.1.139
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = hidden by me!
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1509827955
DHCP4.OPTION[21]:                       host_name = ubuntu
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         (hidden)
IP6.GATEWAY:                            --


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: (hidden by me)


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    2.687633] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x6d4f02)
[   11.087837] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[   11.087843] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   11.213396] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   11.213403] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   25.908998] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   25.951184] r8169 0000:01:00.0 eno1: link down (repeated 2 times)
[   25.951862] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   27.570473] r8169 0000:01:00.0 eno1: link up
[   27.570513] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready


########## wireless info END ############



```

---

### Post by chili555 on 2017-11-03
Please note here: [https://ubuntuforums.org/showthread.php?t=2367405](https://ubuntuforums.org/showthread.php?t=2367405)

You have the same device:  Realtek Semiconductor Co., Ltd. Device [[COLOR="#FF0000"]10ec:d723[/COLOR]] The short answer is that there is no driver yet. Sorry.

---


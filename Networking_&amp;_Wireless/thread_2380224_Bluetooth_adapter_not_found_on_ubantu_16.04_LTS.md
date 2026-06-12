---
title: "Bluetooth adapter not found on ubantu 16.04 LTS"
date: 2017-12-14
forum: Networking &amp; Wireless
---

### Post by ankushmaherwal on 2017-12-14
Bluetooth adapter not fond on my HP 15-r062ut laptop

Bluetooth: Ralink corp. RT3290 Bluetooth is the hardware 

Plz help!

---

### Post by slickymaster on 2017-12-14
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2017-12-15
Hi,

please show the terminal outputs of these commands:

```
uname -a
lspci -nnk
lsusb
usb-devices
lsmod
dmesg | grep Blue
```

---

### Post by liveinasuitcase on 2018-06-13
After several weeks of not toying with any of my Bluetooth gadgets, I wanted to use headphones and discovered that my Bluetooth hardware had been stolen by space aliens!  I am running a MSI GT70 with the Killer E2200 networking hardware.

I have already tried solutions for similar problems, such as [https://askubuntu.com/questions/787023/bluetooth-not-working-on-ubuntu-16-04-lts](https://askubuntu.com/questions/787023/bluetooth-not-working-on-ubuntu-16-04-lts) , [https://askubuntu.com/questions/789088/bluetooth-headset-gives-error-connection-failed-blueman-bluez-errors-dbusfailed](https://askubuntu.com/questions/789088/bluetooth-headset-gives-error-connection-failed-blueman-bluez-errors-dbusfailed)  

```
hciconfig --all
lsmod
rfkill list
dmesg | grep blue
```

Output was:

```
robert@robert-msi-GT70-2OC-2OD:~$ hciconfig --all
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:0 acl:0 sco:0 commands:0 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 

robert@robert-msi-GT70-2OC-2OD:~$ lsmod
Module                  Size  Used by
btrfs                 991232  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   978944  0
libcrc32c              16384  1 xfs
nvram                  16384  0
msr                    16384  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               458752  3 vboxnetadp,vboxnetflt,vboxpci
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
usblp                  20480  0
ath3k                  20480  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  11 bnep,ath3k,btbcm,btrtl,btusb,btintel
msi_wmi                16384  0
sparse_keymap          16384  1 msi_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   548864  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_hda_codec_realtek    90112  1
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          40960  5
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           77824  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
arc4                   16384  2
snd_pcm               106496  4 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
ath9k                  98304  0
snd_seq_midi_event     16384  1 snd_seq_midi
ath9k_common           36864  1 ath9k
snd_rawmidi            32768  1 snd_seq_midi
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              655360  1 ath9k
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
cfg80211              557056  4 ath,ath9k_common,ath9k,mac80211
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
compat                 16384  4 cfg80211,ath9k_common,ath9k,mac80211
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
snd                    81920  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ie31200_edac           16384  0
mei_me                 36864  0
soundcore              16384  1 snd
edac_core              53248  1 ie31200_edac
shpchp                 36864  0
mei                    98304  1 mei_me
lpc_ich                24576  0
mac_hid                16384  0
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  20
xt_addrtype            16384  4
nf_conntrack_ipv4      20480  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_nat_pptp            16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_proto_gre       16384  1 nf_nat_pptp
nf_nat_ftp             16384  0
nf_conntrack_pptp      20480  1 nf_nat_pptp
nf_conntrack_proto_gre    16384  1 nf_conntrack_pptp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_nat                 28672  3 nf_nat_ftp,nf_nat_proto_gre,nf_nat_pptp
iptable_filter         16384  1
nf_conntrack          106496  11 nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_proto_gre,nf_nat,nf_nat_pptp,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6,nf_conntrack_pptp
ip_tables              24576  1 iptable_filter
parport_pc             32768  0
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 hid_generic,usbhid
i915                 1232896  2
rtsx_pci_sdmmc         24576  0
mxm_wmi                16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
psmouse               131072  0
drm                   364544  4 i915,drm_kms_helper
libahci                32768  1 ahci
alx                    36864  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mdio                   16384  1 alx
video                  40960  2 i915,msi_wmi
wmi                    20480  2 msi_wmi,mxm_wmi
fjes                   28672  0
robert@robert-msi-GT70-2OC-2OD:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
robert@robert-msi-GT70-2OC-2OD:~$ dmesg | grep blue
[   13.473746] audit: type=1400 audit(1528925773.052:182): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=3448 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.484695] audit: type=1400 audit(1528925773.064:183): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=3537 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   13.513564] audit: type=1400 audit(1528925773.092:184): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=3537 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.802952] audit: type=1400 audit(1528925773.380:185): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=4280 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.804987] audit: type=1400 audit(1528925773.384:186): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=4287 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   13.805234] audit: type=1400 audit(1528925773.384:187): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=4287 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.943444] audit: type=1400 audit(1528925773.520:188): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=4331 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[   13.943670] audit: type=1400 audit(1528925773.520:189): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=4331 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   13.954427] audit: type=1400 audit(1528925773.532:190): apparmor="DENIED" operation="connect" profile="snap.bluez.obex" name="/run/dbus/system_bus_socket" pid=4332 comm="obexd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[   14.116460] audit: type=1400 audit(1528925773.696:191): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=4372 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
robert@robert-msi-GT70-2OC-2OD:~$ 

```

I have seen recent complaints regarding 18.04 , but I haven't upgraded or done anything funky for years and every solution I have seen is related to the ath10k driver, which is not appropriate for my ancient hardware.  The only thing I can think of is that somehow Synaptic and the Ubuntu software updaters somehow corrupted a file someplace?

Wireless is working fine; only the Bluetooth hardware seems to have disappeared.  When I try to run Bluetooth Manager from the menu, it turns on, but crashes.  BlueWho crashes.  Devices and adapters cannot be found - when I click on the interface, I get null windows.  I have uninstalled and reinstalled all of the bluetooth components through Synaptic, to no avail.

Just to make sure I have included all of the data you might want, I ran

```
uname -a
lspci -nnk
lsusb
usb-devices
lsmod
dmesg | grep Blue
```


and got:


```
robert@robert-msi-GT70-2OC-2OD:~$ uname -a
Linux robert-msi-GT70-2OC-2OD 4.4.0-128-generic #154-Ubuntu SMP Fri May 25 14:15:18 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
robert@robert-msi-GT70-2OC-2OD:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller [8086:0c04] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller [1462:10ec]
    Kernel modules: ie31200_edac
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Micro-Star International Co., Ltd. [MSI] 4th Gen Core Processor Integrated Graphics Controller [1462:10e8]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB xHCI [1462:10ec]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family MEI Controller [1462:10ec]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB EHCI [1462:10ec]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset High Definition Audio Controller [1462:10ec]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family USB EHCI [1462:10ec]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM87 Express LPC Controller [8086:8c4b] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] HM87 Express LPC Controller [1462:10ec]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c03] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [1462:10ec]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] 8 Series/C220 Series Chipset Family SMBus Controller [1462:10ec]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106M [GeForce GTX 770M] [10de:11e0] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] GK106M [GeForce GTX 770M] [1462:10e8]
    Kernel modules: nvidiafb, nouveau
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller [1462:10ec]
    Kernel driver in use: alx
    Kernel modules: alx
04:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Bigfoot Networks, Inc. Killer Wireless-N 1202 Half-size Mini PCIe Card [1a56:2003]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader [10ec:5227] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTS5227 PCI Express Card Reader [1462:10ec]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
robert@robert-msi-GT70-2OC-2OD:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1770:ff00  
Bus 003 Device 005: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 003 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 002: ID 04f9:02e8 Brother Industries, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
robert@robert-msi-GT70-2OC-2OD:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-128-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-128-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=14
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-128-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04f9 ProdID=02e8 Rev=01.00
S:  Manufacturer=Brother
S:  Product=MFC-J470DW
S:  SerialNumber=BROE4F331631
C:  #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=03 Lev=01 Prnt=01 Port=09 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c077 Rev=72.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=01 Prnt=01 Port=10 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0cf3 ProdID=3004 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=03 Lev=01 Prnt=01 Port=07 Cnt=04 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1770 ProdID=ff00 Rev=01.10
S:  Manufacturer=MSI EPF USB
S:  Product=MSI EPF USB
S:  SerialNumber=MSI EPF USB
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-128-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
robert@robert-msi-GT70-2OC-2OD:~$ lsmod
Module                  Size  Used by
btrfs                 991232  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   978944  0
libcrc32c              16384  1 xfs
nvram                  16384  0
msr                    16384  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               458752  3 vboxnetadp,vboxnetflt,vboxpci
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
usblp                  20480  0
ath3k                  20480  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  11 bnep,ath3k,btbcm,btrtl,btusb,btintel
msi_wmi                16384  0
sparse_keymap          16384  1 msi_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   548864  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_hda_codec_realtek    90112  1
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          40960  5
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           77824  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
arc4                   16384  2
snd_pcm               106496  4 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
ath9k                  98304  0
snd_seq_midi_event     16384  1 snd_seq_midi
ath9k_common           36864  1 ath9k
snd_rawmidi            32768  1 snd_seq_midi
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              655360  1 ath9k
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
cfg80211              557056  4 ath,ath9k_common,ath9k,mac80211
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
compat                 16384  4 cfg80211,ath9k_common,ath9k,mac80211
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
snd                    81920  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ie31200_edac           16384  0
mei_me                 36864  0
soundcore              16384  1 snd
edac_core              53248  1 ie31200_edac
shpchp                 36864  0
mei                    98304  1 mei_me
lpc_ich                24576  0
mac_hid                16384  0
binfmt_misc            20480  1
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  20
xt_addrtype            16384  4
nf_conntrack_ipv4      20480  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_nat_pptp            16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_proto_gre       16384  1 nf_nat_pptp
nf_nat_ftp             16384  0
nf_conntrack_pptp      20480  1 nf_nat_pptp
nf_conntrack_proto_gre    16384  1 nf_conntrack_pptp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_nat                 28672  3 nf_nat_ftp,nf_nat_proto_gre,nf_nat_pptp
iptable_filter         16384  1
nf_conntrack          106496  11 nf_nat_ftp,nf_conntrack_netbios_ns,nf_conntrack_proto_gre,nf_nat,nf_nat_pptp,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6,nf_conntrack_pptp
ip_tables              24576  1 iptable_filter
parport_pc             32768  0
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 hid_generic,usbhid
i915                 1232896  2
rtsx_pci_sdmmc         24576  0
mxm_wmi                16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
psmouse               131072  0
drm                   364544  4 i915,drm_kms_helper
libahci                32768  1 ahci
alx                    36864  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mdio                   16384  1 alx
video                  40960  2 i915,msi_wmi
wmi                    20480  2 msi_wmi,mxm_wmi
fjes                   28672  0
robert@robert-msi-GT70-2OC-2OD:~$ dmesg | grep Blue
[    4.638252] Bluetooth: Core ver 2.21
[    4.638268] Bluetooth: HCI device and connection manager initialized
[    4.638271] Bluetooth: HCI socket layer initialized
[    4.638273] Bluetooth: L2CAP socket layer initialized
[    4.638278] Bluetooth: SCO socket layer initialized
[    4.647876] Bluetooth: hci0: don't support firmware rome 0x11020000
[    4.656587] Bluetooth: hci0: don't support firmware rome 0x11020000
[    4.725673] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.725676] Bluetooth: BNEP filters: protocol multicast
[    4.725680] Bluetooth: BNEP socket layer initialized
robert@robert-msi-GT70-2OC-2OD:~$ 


```

The only thing that jumped out at me, a non-techie, is this result:  hci0: don't support firmware rome 0x11020000

I didn't find it in the forums I searched, either.

Thanks for looking at my issue.  I'm willing to try most things.

Robert

---


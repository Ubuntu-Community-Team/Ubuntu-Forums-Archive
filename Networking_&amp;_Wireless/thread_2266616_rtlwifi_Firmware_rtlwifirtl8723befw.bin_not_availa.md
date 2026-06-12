---
title: "rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by bramantio_nugroho on 2015-02-24
Need help:
i have Lenovo G40-30
$ [rfkill list all]
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$ [dmesg | grep -e wlan -e rtl]
[   13.907376] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   14.049024] rtl8723be 0000:02:00.0: Direct firmware load failed with error -2
[   14.049030] rtl8723be 0000:02:00.0: Falling back to user helper
[   14.078364] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available
[   21.485737] r8169 0000:03:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-3.fw (-2)
[  646.958658] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[  646.958995] rtl8723be 0000:02:00.0: Direct firmware load failed with error -2
[  646.959000] rtl8723be 0000:02:00.0: Falling back to user helper
[  646.962213] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available

and my wireless is not show on network manager.

---

### Post by jeremy31 on 2015-02-24
If you have a wired connection, do ```
sudo apt-get install linux-firmware
``` Reboot

If you have no connection from the computer, choose a mirror site from [http://packages.ubuntu.com/trusty-updates/all/linux-firmware/download](http://packages.ubuntu.com/trusty-updates/all/linux-firmware/download) and copy the file onto a USB drive/CD/DVD and get it into the Ubuntu PC and double click on the file

---

### Post by bramantio_nugroho on 2015-02-25
I have

$ sudo apt-get install linux-firmware

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  java-common libavahi-core7 tzdata-java ca-certificates-java
  libavahi-gobject0 libnss3-1d openjdk-7-jre-headless
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ lsmod
> Module                  Size  Used by
cdc_ether              14400  0 
usbnet                 44000  1 cdc_ether
usb_storage            66714  0 
bnep                   19884  2 
rfcomm                 74748  12 
parport_pc             32866  0 
ppdev                  17711  0 
snd_hda_codec_hdmi     47006  1 
snd_hda_codec_conexant    57438  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18946  7 
nf_defrag_ipv6         34934  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
xt_LOG                 17829  9 
xt_limit               12711  12 
xt_tcpudp              12924  18 
xt_addrtype            12713  4 
nf_conntrack_ipv4      15063  7 
nls_iso8859_1          12713  1 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_state               12578  14 
ip6table_filter        12815  1 
ip6_tables             27502  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12825  0 
nf_nat                 26091  1 nf_nat_ftp
nf_conntrack_ftp       18715  1 nf_nat_ftp
nf_conntrack           97581  8 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27716  1 iptable_filter
x_tables               34194  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
rts5139               318332  0 
rtl8723be              91457  0 
rtl8723_common         23427  1 rtl8723be
uvcvideo               82247  0 
rtl_pci                27310  1 rtl8723be
snd_hda_intel          57302  3 
videobuf2_core         40972  1 uvcvideo
snd_hda_codec         199156  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
videodev              139761  2 uvcvideo,videobuf2_core
rtlwifi                64281  2 rtl8723be,rtl_pci
mac80211              658141  3 rtl8723be,rtl_pci,rtlwifi
videobuf2_vmalloc      13216  1 uvcvideo
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_midi           13324  0 
i915_bdw              885822  2 
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
intel_rapl             19228  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
btusb                  32519  0 
coretemp               17728  0 
snd_timer              30038  2 snd_pcm,snd_seq
cfg80211              502970  2 rtlwifi,mac80211
drm_kms_helper         59668  1 i915_bdw
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_intel             144664  0 
drm                   308868  3 i915_bdw,drm_kms_helper
kvm                   472641  1 kvm_intel
btcoexist              55886  1 rtl8723be
bluetooth             411194  24 bnep,rfcomm,btusb
psmouse               113331  0 
crct10dif_pclmul       14250  0 
i2c_algo_bit           13564  1 i915_bdw
serio_raw              13462  0 
video                  19914  1 i915_bdw
snd                    73890  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
intel_ips              18760  1 i915_bdw
shpchp                 37201  0 
crc32_pclmul           13160  0 
ghash_clmulni_intel    13216  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
cryptd                 20530  1 ghash_clmulni_intel
lp                     17799  0 
parport                42481  3 parport_pc,ppdev,lp
r8169                  73299  0 
ahci                   34159  3 
mii                    13981  2 usbnet,r8169
libahci                32825  1 ahci

$ nm-tool

> NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        34:4B:50:B7:EF:82

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.1*0
    Prefix:          2* (25*.255.25*.0)
    Gateway:         192.1**.*.*

    DNS:             192.16*.*.*


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        28:D2:44:A9:86:1F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

$ lshw -c network

> 
*-network               
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8723be latency=0
       resources: irq:18 ioport:2000(size=256) memory:90500000-90503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 28:d2:44:a9:86:1f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:105 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 34:4b:50:b7:ef:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.0.100 link=yes multicast=yes

$ lspci

> $ 00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

$  tail -f /var/log/dmesg

> [   21.792575] type=1400 audit(1424841070.812:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1176 comm="apparmor_parser"
[   21.792585] type=1400 audit(1424841070.812:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1176 comm="apparmor_parser"
[   21.793197] type=1400 audit(1424841070.816:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1176 comm="apparmor_parser"
[   21.796246] type=1400 audit(1424841070.816:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/bin/ping" pid=1173 comm="apparmor_parser"
[   23.673606] r8169 0000:03:00.0: Direct firmware load failed with error -2
[   23.673613] r8169 0000:03:00.0: Falling back to user helper
[   23.677287] r8169 0000:03:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-3.fw (-2)
[   23.684406] r8169 0000:03:00.0 eth0: link down
[   23.684462] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.685104] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

on [https://help.ubuntu.com/12.04/ubuntu-help/net-wireless-troubleshooting-device-drivers.html](https://help.ubuntu.com/12.04/ubuntu-help/net-wireless-troubleshooting-device-drivers.html)
[LIST]
[*] Use the Windows drivers for your adapter

 In general, you cannot use a device driver designed for one  operating system (like Windows) on another operating system (like  Linux). This is because they have different ways of handling devices.  For wireless adapters, however, you can install a compatibility layer  called NDISwrapper which lets you use some  Windows wireless drivers on Linux. This is useful because wireless  adapters almost always have Windows drivers available for them, whereas  Linux drivers are sometimes not available. You can learn more about how  to use NDISwrapper [here]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page"). Note that not all wireless drivers can be used through NDISwrapper.

 Full information on ndiswrapper kept on         [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")         including troubleshooting help specific to ndiswrapper.

Can ndiswarper help me?


[/LIST]

---

### Post by jeremy31 on 2015-02-25
You could look at this thread [http://ubuntuforums.org/showthread.php?t=2262957](http://ubuntuforums.org/showthread.php?t=2262957) and you could try what is on post 2 or post 11

Don't use ndiswrapper yet as there are other options

---


---
title: "MSI u160 Netbook, Wifi List not Showing to Connect"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by Zayed_Wazir on 2014-05-10
Hello Mates, 
I Have installed Ubuntu 12.4LT **Wifi List not Showing to Connect **ny Network , But the Wired network is Working and also Mobile network, Please Help Me, 

```

mady@Mady:~$ lsusb
Bus 001 Device 016: ID 19d2:0117 ZTE WCDMA Technologies MSM 
Bus 002 Device 003: ID 2188:0ae1  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
mady@Mady:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ae:f8:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:163927 (163.9 KB)  TX bytes:163927 (163.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:37.125.74.51  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:22256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:24641251 (24.6 MB)  TX bytes:1314719 (1.3 MB)


```

```
mady@Mady:~$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.


```

```
mady@Mady:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:ae:f8:25
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:e2110000-e2110fff memory:e2100000-e210ffff memory:fe000000-fe01ffff
  *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fd600000-fd60ffff


```
```
 mady@Mady:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
nls_utf8               12493  1 
isofs                  39589  1 
rfcomm                 59026  0 
bnep                   19210  2 
btusb                  23534  0 
bluetooth             341971  11 rfcomm,bnep,btusb
parport_pc             32114  0 
ppdev                  17423  0 
snd_hda_codec_realtek    50931  1 
uvcvideo               72275  0 
gpio_ich               13278  0 
msi_wmi                13130  0 
videobuf2_core         39385  1 uvcvideo
rt2800pci              18551  0 
snd_hda_intel          43326  5 
videodev              107944  2 uvcvideo,videobuf2_core
msi_laptop             15196  0 
snd_hda_codec         169608  2 snd_hda_codec_realtek,snd_hda_intel
option                 33960  2 
rt2x00mmio             13445  1 rt2800pci
sparse_keymap          13658  2 msi_wmi,msi_laptop
rt2800lib              71740  1 rt2800pci
usb_wwan               19721  1 option
snd_hwdep              13276  1 snd_hda_codec
videobuf2_vmalloc      13048  1 uvcvideo
crc_ccitt              12627  2 ppp_async,rt2800lib
usbserial              38859  7 option,usb_wwan
videobuf2_memops       13170  1 videobuf2_vmalloc
rt2x00pci              13111  1 rt2800pci
snd_pcm                94597  3 snd_hda_intel,snd_hda_codec
rt2x00lib              53673  4 rt2800pci,rt2x00mmio,rt2800lib,rt2x00pci
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
i915                  615880  3 
mac80211              534922  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         47306  1 i915
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17268  1 
psmouse                92648  0 
snd_timer              28930  2 snd_pcm,snd_seq
lpc_ich                16987  0 
serio_raw              13189  0 
cfg80211              416271  2 rt2x00lib,mac80211
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   247722  4 i915,drm_kms_helper
i2c_algo_bit           13316  1 i915
snd                    61270  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
eeprom_93cx6           13168  1 rt2800pci
wmi                    18744  1 msi_wmi
soundcore              12600  1 snd
video                  19046  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12492  0 
usbhid                 47620  0 
hid                    87771  2 hid_generic,usbhid
usb_storage            48631  1 
ahci                   25703  4 
libahci                30834  1 ahci
r8169                  62856  0 
mii                    13693  1 r8169
mady@Mady:~$ ^C
mady@Mady:~$ ^C
mady@Mady:~$ sudo modprobe -rfv rt2800pci
[sudo] password for mady: 
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.11.0-20-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
mady@Mady:~$ sudo modprobe -v rt2800pci nohwcrypt=Y
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko nohwcrypt=Y


```

```
 mady@Mady:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:104e]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:6891]
    Kernel modules: rt2800pci


```

```
 mady@Mady:~$ dmesg | grep -e rt2 -e wlan
[   11.179585] rt2800pci 0000:03:00.0: enabling device (0000 -> 0002)
[   11.179863] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[   11.179868] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device
[ 3022.540305] rt2800pci 0000:03:00.0: enabling device (0000 -> 0002)
[ 3022.540618] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[ 3022.540632] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device


```

```
mady@Mady:~$ dmesg | grep rt2
[   11.179585] rt2800pci 0000:03:00.0: enabling device (0000 -> 0002)
[   11.179863] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[   11.179868] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device
[ 3022.540305] rt2800pci 0000:03:00.0: enabling device (0000 -> 0002)
[ 3022.540618] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[ 3022.540632] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device
mady@Mady:~$ ^C
mady@Mady:~$ ^C
mady@Mady:~$ lspci -nn grep 0280
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
mady@Mady:~$ rfkill list all
0: msi-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: msi-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mady@Mady:~$ lsb release -d
No command 'lsb' found, did you mean:
 Command 'lsw' from package 'suckless-tools' (universe)
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'lb' from package 'live-build' (main)
 Command 'ls' from package 'coreutils' (main)
 Command 'lsh' from package 'lsh-client' (universe)
 Command 'jsb' from package 'jsonbot' (universe)
 Command 'sb' from package 'lrzsz' (universe)
lsb: command not found
mady@Mady:~$ lsb_release -d
Description:    Ubuntu 12.04.4 LTS
mady@Mady:~$ sudo rm /etc/modprobe.d/blacklist-rt2x00.conf
rm: cannot remove `/etc/modprobe.d/blacklist-rt2x00.conf': No such file or directory
mady@Mady:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

 
```


Please help me out in WIFI Connection Problem ..

---


---
title: "Slow speeds after upgrading to 13.10"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Jorge_Gonzalez on 2013-10-20
I have a desktop with a wired connection and before I upgraded from 13.04 to 13.10 I could stream 1080p video on YouTube quite easily and I could download torrents on Deluge at around 1Mb/s every time. Now I can't watch 1080p at all and torrents are downloading at around 100-200 Kb/s. Anyone know what might be the cause?

---

### Post by praseodym on 2013-10-20
Hi,

please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by Jorge_Gonzalez on 2013-10-20
```
jorge@desktop:~$ lspci -nnk | grep -iA2 net04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:2ae5]
    Kernel driver in use: r8169
--
06:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
jorge@desktop:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2149:2001  
Bus 001 Device 004: ID 04f2:b31f Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0461:4e0e Primax Electronics, Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jorge@desktop:~$ lsmod
Module                  Size  Used by
xt_tcpudp              12884  1 
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  3 ip_tables,xt_tcpudp,iptable_filter
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_idt      50341  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1 ghash_clmulni_intel
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
hid_multitouch         17407  0 
videodev              133390  2 uvcvideo,videobuf2_core
joydev                 17377  0 
snd_hda_intel          48171  4 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
arc4                   12608  2 
rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
microcode              23518  0 
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              479757  2 mac80211,rt2x00lib
psmouse                97626  0 
serio_raw              13413  0 
eeprom_93cx6           13344  1 rt2800pci
lpc_ich                21080  0 
crc_ccitt              12707  1 rt2800lib
jmb38x_ms              18670  0 
memstick               16760  1 jmb38x_ms
i915                  655752  4 
drm_kms_helper         52651  1 i915
drm                   296739  5 i915,drm_kms_helper
soundcore              12680  1 snd
mei_me                 18421  0 
i2c_algo_bit           13413  1 i915
mei                    77692  1 mei_me
video                  19318  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  3 hid_multitouch,hid_generic,usbhid
sdhci_pci              18985  0 
ahci                   25819  3 
sdhci                  42630  1 sdhci_pci
libahci                31898  1 ahci
r8169                  67341  0 
mii                    13934  1 r8169
jorge@desktop:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jorge@desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:ab:2f:25:0c  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:abff:fe2f:250c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7621048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8547890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6805144514 (6.8 GB)  TX bytes:3346384405 (3.3 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:615034 (615.0 KB)  TX bytes:615034 (615.0 KB)


wlan0     Link encap:Ethernet  HWaddr 9c:2a:70:3b:a5:3d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


jorge@desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Belkin
jorge@desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
jorge@desktop:~$ 
```

---

### Post by Jorge_Gonzalez on 2013-10-21
To make things more clear, I have a modem which I connect to a router, and then I connect the router to my desktop through an Ethernet cable (since Ubuntu never wants to connect to my wifi). If I connect my modem straight to my desktop, my speeds are back to how they used to be, so I'm thinking maybe it has something to do with the router? This was never an issue before I upgraded. Also, Ubuntu has been showing "device not ready" when I try to connect to a wifi network, and sometimes it goes away but when I try to connect to my own, it just disappears or says "out of range".

---

### Post by Jorge_Gonzalez on 2013-10-21
Does anyone have any advice?

---

### Post by Andy_Lee on 2013-10-22
Hi.
The ports of your router is gigabit ? If yes, I think the problem is caused by network cable, try connecting to router by Cat6 cable, don't use Cat5 cable.
you try to check the reliability of the cable by command:
```

ping ip_router
```
If there is any packet loss, the problem is caused by cable.

---

### Post by praseodym on 2013-10-22
Change the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/14/31/3005217-r8168-dkms-8.036.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.036.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.036.00
sudo dkms build -m r8168-dkms -v 8.036.00
sudo dkms install -m r8168-dkms -v 8.036.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
```

---

### Post by Jorge_Gonzalez on 2013-10-22
> **praseodym said:**
> Change the driver via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/14/31/3005217-r8168-dkms-8.036.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.036.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.036.00
sudo dkms build -m r8168-dkms -v 8.036.00
sudo dkms install -m r8168-dkms -v 8.036.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
```

Okay, I just put this in my terminal and it finished. What now?

---

### Post by praseodym on 2013-10-22
Now show
```

lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by Jorge_Gonzalez on 2013-10-22
> **praseodym said:**
> Now show
```

lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
```

```
jorge@desktop:~$ lsmodModule                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320455  3 vboxnetadp,vboxnetflt,vboxpci
btrfs                 815968  0 
raid6_pq               97812  1 btrfs
zlib_deflate           26885  1 btrfs
xor                    21411  1 btrfs
ufs                    74590  0 
qnx4                   13317  0 
hfsplus               102646  0 
hfs                    54590  0 
minix                  36111  0 
ntfs                   96882  0 
msdos                  17332  0 
jfs                   180909  0 
xfs                   884143  0 
libcrc32c              12615  2 xfs,btrfs
reiserfs              245794  0 
ext2                   72832  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  0 
bnep                   19564  2 
bluetooth             371874  10 bnep,rfcomm
nls_iso8859_1          12713  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1 ghash_clmulni_intel
snd_hda_codec_idt      50341  1 
hid_multitouch         17407  0 
joydev                 17377  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  3 
snd_hda_codec         188738  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
microcode              23518  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
arc4                   12608  2 
rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
psmouse                97626  0 
serio_raw              13413  0 
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              479757  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
jmb38x_ms              18670  0 
crc_ccitt              12707  1 rt2800lib
memstick               16760  1 jmb38x_ms
snd                    69141  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
soundcore              12680  1 snd
i915                  655752  4 
drm_kms_helper         52651  1 i915
drm                   296739  5 i915,drm_kms_helper
video                  19318  1 i915
mac_hid                13205  0 
mei_me                 18421  0 
mei                    77692  1 mei_me
i2c_algo_bit           13413  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  3 hid_multitouch,hid_generic,usbhid
r8169                  67341  0 
ahci                   25819  3 
libahci                31898  1 ahci
mii                    13934  1 r8169
sdhci_pci              18985  0 
sdhci                  42630  1 sdhci_pci
jorge@desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:ab:2f:25:0c  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:abff:fe2f:250c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2557940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2664557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2644981158 (2.6 GB)  TX bytes:836760244 (836.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1048524 (1.0 MB)  TX bytes:1048524 (1.0 MB)


wlan0     Link encap:Ethernet  HWaddr 9c:2a:70:3b:a5:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:814 (814.0 B)  TX bytes:4505 (4.5 KB)


jorge@desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Belkin
jorge@desktop:~$ route -n
```

---

### Post by praseodym on 2013-10-22
On-the-fly:
```

sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3290sta
```

---

### Post by Jorge_Gonzalez on 2013-10-22
Nothing seemed to happen. o.O 
```
jorge@desktop:~$ sudo modprobe -rfv rt2800pci
[sudo] password for jorge: 
jorge@desktop:~$ sudo modprobe -v rt3290sta
FATAL: Module rt3290sta not found.
jorge@desktop:~$ 
```

---

### Post by praseodym on 2013-10-23
Did the installation work? Outputs?

---

### Post by jdafoe1 on 2013-10-23
[COLOR=#000000]Workaround here: [/COLOR][https://bugs.launchpad.net/ubuntu/+s...x/+bug/1049466]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466")[COLOR=#000000]. Comment #116 & 117.[/COLOR]

---


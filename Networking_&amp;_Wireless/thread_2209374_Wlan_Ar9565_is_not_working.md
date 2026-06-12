---
title: "Wlan Ar9565 is not working"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by duenschiss on 2014-03-05
Hy everybody!

My system is running - even the Wlan is not!
Could you please help me?
```

[COLOR=#000000][FONT=Trebuchet MS]cat /etc/lsb-release [/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]DISTRIB_RELEASE=12.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]DISTRIB_CODENAME=precise[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"[/FONT][/COLOR]
```


```
[COLOR=#000000][FONT=Trebuchet MS]uname -a[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]Linux condorkueche 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:54:21 UTC 2014 i686 athlon i386 GNU/Linux[/FONT][/COLOR]
```[COLOR=#000000][FONT=Trebuchet MS]
[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Trebuchet MS]lspci -nn | grep -i net[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 13)[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]05:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)[/FONT][/COLOR]
```[COLOR=#000000][FONT=Trebuchet MS]
[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4
5
6
7
8
9[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"] lsusb 
Bus 002 Device 002: ID 04f2:b3d6 Chicony Electronics Co., Ltd 
Bus 004 Device 002: ID 04ca:300b Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 30:65:ec:23:70:66  
          inet Adresse:192.168.0.19  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::3265:ecff:fe23:7066/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:663 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:663 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:69239 (69.2 KB)  TX-Bytes:69239 (69.2 KB)[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1456"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]lsmod
Module                  Size  Used by
bnep                   19210  2 
rfcomm                 59026  12 
xt_hl                  12465  6 
ip6t_rt                13259  3 
parport_pc             32114  0 
nf_conntrack_ipv6      18458  7 
ppdev                  17423  0 
nf_defrag_ipv6         26204  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
xt_LOG                 17544  9 
xt_limit               12541  12 
xt_tcpudp              12788  18 
xt_addrtype            12625  4 
binfmt_misc            17268  1 
nf_conntrack_ipv4      14535  7 
snd_hda_codec_realtek    50931  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_hda_codec_hdmi     40881  1 
xt_state               12514  14 
snd_hda_intel          43326  5 
snd_hda_codec         169608  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ip6table_filter        12711  1 
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ip6_tables             18134  1 ip6table_filter
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nf_conntrack_netbios_ns    12585  0 
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
snd_timer              28930  2 snd_pcm,snd_seq
nf_nat_ftp             12692  0 
nf_nat                 25789  1 nf_nat_ftp
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_ftp       14117  1 nf_nat_ftp
nf_conntrack           83259  8 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ftp
dm_multipath           22754  0 
iptable_filter         12706  1 
uvcvideo               72275  0 
ip_tables              18302  1 iptable_filter
scsi_dh                14449  1 dm_multipath
x_tables               22178  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
fglrx                6182143  65 
videobuf2_core         39385  1 uvcvideo
videodev              107944  2 uvcvideo,videobuf2_core
snd                    61270  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  23534  0 
videobuf2_vmalloc      13048  1 uvcvideo
bluetooth             341971  24 bnep,rfcomm,btusb
videobuf2_memops       13170  1 videobuf2_vmalloc
psmouse                92648  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
k10temp                12997  0 
mac_hid                13077  0 
serio_raw              13189  0 
i2c_piix4              17843  0 
fam15h_power           12998  0 
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76513  0 
dm_mirror              21948  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18164  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 839461  0 
raid6_pq               97455  1 btrfs
xor                    26221  2 dm_raid45,btrfs
zlib_deflate           26622  1 btrfs
vesafb                 13540  1 
ahci                   25703  2 
sdhci_pci              18530  0 
libahci                30834  1 ahci
alx                    32016  0 
sdhci                  37958  1 sdhci_pci
video                  19046  0 
wmi                    18744  0 
mdio                   13559  1 alx[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"] cat /etc/network/interfaces
auto lo
iface lo inet loopback[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"] cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


[COLOR=#000000][FONT=Trebuchet MS][TABLE="width: 1064"]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"][IMG]http://www.ubuntu-forum.de/wcf/icon/codeS.png[/IMG][/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]**Quellcode**[/TD]
[/TR]
[TR]
[TD="class: codeLineNumbers container-3, bgcolor: #FFFFFF, align: right"]1
2
3
4[/TD]
[TD="class: codeLines container-4, bgcolor: #FFFFFF"]sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


Thank you soo much!


[SIZE=6]Edit:
[SIZE=4][SIZE=3]Now I´ve tried this:[/SIZE] 


```
[/SIZE][/SIZE]
[https://www.kernel.org/pub/linux/ker...kports/stable/]("https://www.kernel.org/pub/linux/kernel/projects/backports/stable/")
[COLOR=#000000]Downloaded and extracted; compat-drivers-3.9-rc4-2-s.tar.bz2[/COLOR]

[B]cd Desktop/compat-drivers-3.9-rc4-2-s
sudo su
./scripts/driver-select ath9k
make 
[/B][B]make install
[/B][B]
```
[/B][SIZE=6][SIZE=4]```

[/SIZE][/SIZE] make install


make -C /lib/modules/3.11.0-18-generic/build M=/home/condor/Downloads/compat-drivers-3.9-rc4-2-s modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
  Building modules, stage 2.
  MODPOST 10 modules
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
make -C /lib/modules/3.11.0-18-generic/build M=/home/condor/Downloads/compat-drivers-3.9-rc4-2-s "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/compat/compat.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_common.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-gpio.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/net/rfkill/rfkill-regulator.ko
Can't read private key
  INSTALL /home/condor/Downloads/compat-drivers-3.9-rc4-2-s/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  3.11.0-18-generic
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.11.0-18-generic'
depmod will prefer updates/ over kernel/ -- OK!


Now run:


sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules


Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.


root@condorkueche:/home/condor/Downloads/compat-drivers-3.9-rc4-2-s# make wlunload
root@condorkueche:/home/condor/Downloads/compat-drivers-3.9-rc4-2-s# modprobe ath9k
WARNING: Error inserting ath (/lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_hw (/lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.11.0-18-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/3.11.0-18-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Whats up now????
[SIZE=6][SIZE=4]

[/SIZE]
[/SIZE]

---

### Post by chili555 on 2014-03-05
By installing compat-drivers-3.9-rc4-2, you tried to install the ath9k driver from kernel 3.9 into your 3.11 system:```
3.11.0-18-generic
```It's sort of like trying to put the motor from a 1989 Ford into your 2014 Ford. Nothing matches. It won't work.

In 3.11, the ath9k driver claims your device:```
$ modinfo ath9k | grep 0036
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0036[/COLOR]sv*sd*bc*sc*i*
```Is it not working as expected? Is that why you wanted a 1989 motor?

---

### Post by duenschiss on 2014-03-05
Hy!
No I just want to get the Wlan working ;)

So what should I do?

---

### Post by chili555 on 2014-03-05
First, remove the incorrect driver:```
cd ~/Desktop/compat-drivers-3.9-rc4-2-s
sudo make uninstall
```Next, reboot. Then run and post:```
sudo modprobe ath9k
rfkill list all
iwconfig
```

---

### Post by duenschiss on 2014-03-05
Hey!

I´ve to use the 3.2.0-58-generich kernel, cause the 60 is stopping while loading cups....

```
sudo modprobe ath9k[sudo] password for condor: 
condor@condorkueche:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
condor@condorkueche:~$ iwconfig
lo        no wireless extensions.



```

---

### Post by chili555 on 2014-03-05
> **duenschiss said:**
> Hey!

I´ve to use the 3.2.0-58-generich kernel, cause the 60 is stopping while loading cups....

So you are not using 3.11.0-18-generic as mentioned above? Where did that come from then? It is helpful to me to get all the correct information before we both spend time on the wrong path.

---

### Post by DoodleDee on 2014-03-13
Hey,
 I am not new to ubuntu, but new to the forum.
   I have the exact same problem on Dell Latitude 3440, AR9565 wireless drivers are not working well. We got this machine with Ubuntu 12.04 LTS installed, and the wireless worked the first time. Now we reboot the machine and it doesnt detect or even save previous wireless configurations. Getting same messages as the user - duenschiss.
This is what I tried - 


sudo apt-get install linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
The following packages were automatically installed and are no longer required:
  mingw-w64 sbsigntool gir1.2-timezonemap-1.0 linux-image-3.5.0-22-generic realpath efibootmgr diffstat libdmraid1.0.0.rc16 libdebconfclient0
  binutils-mingw-w64-i686 kpartx-boot libopts25 gir1.2-json-1.0 quilt linux-headers-3.5.0-22-generic autogen gcc-mingw-w64 user-setup
  gcc-mingw-w64-i686 kpartx rdate binutils-mingw-w64-x86-64 libdebian-installer4 libopts25-dev btrfs-tools apt-clone localechooser-data
  linux-headers-3.5.0-22 gcc-mingw-w64-base gcc-mingw-w64-x86-64 archdetect-deb dmraid python-pyicu libkms1 mingw-w64-dev gir1.2-xkl-1.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-60 linux-headers-3.2.0-60-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-60 linux-headers-3.2.0-60-generic linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 180 not upgraded.
Need to get 12.7 MB of archives.
After this operation, 67.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-60 all 3.2.0-60.91 [11.7 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-60-generic amd64 3.2.0-60.91 [985 kB]                      
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic amd64 3.2.0.60.71 [2,364 B]                              
Fetched 12.7 MB in 29s (427 kB/s)                                                                                                              
Selecting previously unselected package linux-headers-3.2.0-60.
(Reading database ... 218986 files and directories currently installed.)
Unpacking linux-headers-3.2.0-60 (from .../linux-headers-3.2.0-60_3.2.0-60.91_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-60-generic.
Unpacking linux-headers-3.2.0-60-generic (from .../linux-headers-3.2.0-60-generic_3.2.0-60.91_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.60.71_amd64.deb) ...
Setting up linux-headers-3.2.0-60 (3.2.0-60.91) ...
Setting up linux-headers-3.2.0-60-generic (3.2.0-60.91) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-60-generic /boot/vmlinuz-3.2.0-60-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Error! Bad return status for module build on kernel: 3.2.0-60-generic (x86_64)
Consult /var/lib/dkms/oem-bt-dw1705/0.1/build/make.log for more information.
: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
Error! Bad return status for module build on kernel: 3.2.0-60-generic (x86_64)
Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.
Setting up linux-headers-generic (3.2.0.60.71) ...


Is that a problem ? Last time I tried to update kernela after this stage and machine wont even boot up well after that.

Thanks for the help. I hope to get this resolved here, or I am not sure if I can install newer versions of Ubuntu on this Dell laptop. Anyone has a suggestion for me ?

- DoodleDee

---

### Post by chili555 on 2014-03-13
> Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.Did you?```
cat /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log
```This little gem is a Dell creation: [COLOR="#FF0000"]oem-wireless-ath9k-3.9-rc4-2[/COLOR]. As I see it,you have two options; first, consult Dell and ask them. Second, you could try the live USB for Ubuntu 13.10 and, if all goes well, and I'm confident it will, install it and kiss Dell's pre-install goodbye.

We will be happy to help in any case. I'd call Dell first, a toll-free call is essentially free.

---


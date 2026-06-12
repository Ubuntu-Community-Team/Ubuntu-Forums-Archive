---
title: "Lost all Internet Connections."
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by donmor on 2008-04-24
Hope someone can help me. I upgraded to 8.04 and lost my wireless and also my 10/100 internet.

Dell 1501 Vista/Ubunto dual boot. Worked with both 7.01 and 7.10 without problems.

This is the results of lshw -C network.

don@don-vista:~$ sudo lshw -C network

*-network
description: Network controller
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb

*-network UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=64

*-network DISABLED
description: Wireless interface
physical id: 2
logical name: eth1
serial: 00:1c:26:30:f0:25
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11

I don't know what to try next to get either the wireless or the wired working.

NETWORK SETTINGS
Wireless Connection
Point to Point Connection.

Does not even show a Wired Connection

Thanks for any help

Don

---

### Post by dmizer on 2008-04-25
try this link: [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

---

### Post by donmor on 2008-04-25
Sorry for the long post but this is what happened when I tried all  the above from the thread mentioned.
How can I install ndiswrapper with no internet. My wired connection does not show up as if it is not there.


don@don-vista:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
don@don-vista:~$ sudo ifconfog
[sudo] password for don: 
sudo: ifconfog: command not found
don@don-vista:~$ sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18376 (17.9 KB)  TX bytes:18376 (17.9 KB)

don@don-vista:~$ sudo iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

don@don-vista:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

don@don-vista:~$ lsmod
Module                  Size  Used by
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
nfsd                  228848  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185884  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ppdev                  10372  0 
ipv6                  267780  12 
rfkill_input            5504  0 
powernow_k8            16704  1 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
ndiswrapper           192920  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344728  3 
b43                   131996  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
rfkill                  8592  2 rfkill_input,b43
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
usbhid                 31872  0 
mac80211              228596  1 b43
snd_seq_dummy           4868  0 
hid                    38784  1 usbhid
cfg80211               32480  1 mac80211
sr_mod                 17956  0 
snd_seq_oss            35584  0 
cdrom                  37408  1 sr_mod
led_class               6020  1 b43
snd_seq_midi            9376  0 
input_polldev           5896  1 b43
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
video                  19856  0 
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci                  19076  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pata_acpi               8320  0 
psmouse                40336  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
ata_generic             8324  0 
wmi_acer                9644  0 
ac                      6916  0 
battery                14212  0 
atiixp                  5648  0 [permanent]
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
dcdbas                  9504  0 
ati_agp                 9996  0 
agpgart                34760  1 ati_agp
ide_core              113996  1 atiixp
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
soundcore               8800  1 snd
evdev                  13056  7 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  6 
pata_atiixp             8960  0 
ohci_hcd               25348  0 
mii                     6400  0 
ehci_hcd               37900  0 
ahci                   28420  5 
ssb                    44292  1 b43
pcmcia                 40876  2 b43,ssb
usbcore               146028  5 ndiswrapper,usbhid,ohci_hcd,ehci_hcd
libata                159344  4 pata_acpi,ata_generic,pata_atiixp,ahci
pcmcia_core            40596  3 b43,ssb,pcmcia
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  5 
don@don-vista:~$ ndiswrapper -1
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
don@don-vista:~$ 


Thanks
Don

---

### Post by dmizer on 2008-04-25
you don't have ndiswrapper installed, which means that you missed this post: [http://ubuntuforums.org/showpost.php?p=4632889&postcount=9](http://ubuntuforums.org/showpost.php?p=4632889&postcount=9)

edit:
here's directions on how to install ndiswrapper without internet: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-715b64e4eb010761a0c694dde40d3a569f414b5e](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-715b64e4eb010761a0c694dde40d3a569f414b5e)

you'll only need these two packages:
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)

---

### Post by donmor on 2008-04-25
Thanks for all the help.
I reinstalled the new 8.04 over the old 7.10 and my internet is back. No wireless but I will work on it after reviewing the latest threads.
Thanks again
Don

---

### Post by brew1brew on 2008-04-26
these [instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") work with my BCM94311MCG wlan mini-PCI (rev 02). I had to compile ndiswraper in Feisty, after upgrading to Hardy I lost wireless and the "Hardy bug fix" took care of the issue.

Les

---


---
title: "Asus EEE/Ubuntu 8.10/Netgear Router Network Trouble"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by stroudma on 2009-02-14
Asus EEE PC 1000 HA laptop.  Dual booting Windows XP and Ubuntu 8.10

Netgear Wireless G Router WGR614 (is also running a wired connection to a Ubuntu desktop and a wireless connection to a PS3)

I can not access my wireless when i am booted into ubuntu.  It works fine, however, when i am booted into XP, I've been tinkering with it for around 5 hours now and i for whatever reason i just cant see what i'm doing wrong, i'm guessing it's something obvious but whatever it is is beyond me.  I tried to follow the protocol for how to post a wireless question thread and have tried to provide as much information as possible, if you have any other questions then feel free to ask, thanks in advance

Out Come to LSPCI

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

```

Outcome to LSUSB

```
Bus 005 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Outcome to ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:1f:f3:51  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe1f:f351/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7212 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:13052635 (13.0 MB)  TX bytes:822015 (822.0 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)
```

Outcome to iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

Outcome to lsmod

```
Module                  Size  Used by
af_packet              25728  2 
ipv6                  263972  10 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
evdev                  17696  11 
v4l1_compat            22404  2 uvcvideo,videodev
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
video                  25104  0 
output                 11008  1 video
psmouse                45200  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
battery                18436  0 
serio_raw              13444  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                     12292  0 
ath_pci                99096  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
atl1e                  40212  0 
pcspkr                 10624  0 
button                 14224  0 
eeepc_laptop           16528  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
soundcore              15328  1 snd
intel_agp              33724  1 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  3 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ata_piix               24580  1 
libata                177312  3 ata_generic,pata_acpi,ata_piix
ehci_hcd               43276  0 
scsi_mod              155212  3 sd_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
usbcore               148848  4 uvcvideo,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 
```

Outcome to sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:1f:f3:51
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.4 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:c8:c4:49:90:e6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Outcome to iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


Outcome to lsb_release -d

```
Description:	Ubuntu 8.10
```

Outcome to uname -mr

```
2.6.27-7-generic i686
```

Outcome to sudo /etc/init.d/networking restart

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

mark@ubuntu:~$ lsb_release -d
Description:	Ubuntu 8.10
mark@ubuntu:~$ uname -mr
2.6.27-7-generic i686
mark@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                      Ignoring unknown interface eth0=eth0.
                                                                     [ OK ]
```

---

### Post by tarps87 on 2009-03-12
This should install the driver for the network card. (You will be need to be connected to the internet for this)
```
sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid-generic
sudo modprobe ath5k

```

For other fixes/changes you may want to have a look here
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

Also if you experience problems with this driver you can use the latest madwifi driver. (I am using this on on my acer aspire one)

To install
```

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci

```

Now add the ath_pci module to the end of your modules list
```
sudo gedit /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
**ath_pci**

---


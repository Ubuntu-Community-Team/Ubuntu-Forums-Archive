---
title: "Problem with logical interface of my network Arcnet PCI20EX-CBX Card"
date: 2018-12-24
forum: Networking &amp; Wireless
---

### Post by sonbole on 2018-12-24
Hello,

I have a PCI Express card with BNC Port, its an Arcnet PCI20EX-CBX of Contemporary Controls, normally, ubuntu has its own driver for this card implemented in the kernel under the name of : Com20020 or Com20020pci (in an Arcnet folder), so i used modprobe to use it as a module, normally i can see the card as a network Card but there is no logical interface for it (for example "eth0" for my network ethernet card) as you can see below :

for info : I use Ubuntu 14.

[COLOR=#000000][FONT=Arial]sudo lshw -c network -businfo[/FONT][/COLOR]
```
[COLOR=#000000]Bus info          Périphérique  Classe      Description
=========================================================
pci@0000:00:19.0  eth0            network     82567V-4 Gigabit Network Connection
pci@0000:21:04.0                     network     Contemporary Controls
usb@1:4               wlan0           network     Interface réseau sans fil[/COLOR]
```

Here some command that you might need :


ifconfig -a

```
[COLOR=#000000]eth0      Link encap:Ethernet  HWaddr 78:ac:c0:bb:d1:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:19 Mémoire:f0500000-f0520000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:7258 erreurs:0 :0 overruns:0 frame:0
          TX packets:7258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1 
          Octets reçus:685300 (685.3 KB) Octets transmis:685300 (685.3 KB)

wlan0     Link encap:Ethernet  HWaddr 7c:dd:90:7e:51:80  
          inet adr:192.168.38.200  Bcast:192.168.38.255  Masque:255.255.255.0
          adr inet6: fe80::7edd:90ff:fe7e:5180/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:10580 erreurs:0 :0 overruns:0 frame:0
          TX packets:6800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:12021135 (12.0 MB) Octets transmis:874945 (874.9 KB)[/COLOR]
```

lsusb

```
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
```

Thank you.

---

### Post by praseodym on 2018-12-24
Lets see

```
lspci -nnk
lsmod

```

---

### Post by sonbole on 2018-12-24
hello,

lspci -nnk :```
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e40] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e42] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e43] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
00:19.0 Ethernet controller [0200]: Intel Corporation 82567V-4 Gigabit Network Connection [8086:1525] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 [8086:3a67] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 [8086:3a68] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 [8086:3a69] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 [8086:3a6c] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller [8086:3a6e] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 [8086:3a70] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 [8086:3a64] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 [8086:3a65] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 [8086:3a66] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 [8086:3a6a] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JD (ICH10D) LPC Interface Controller [8086:3a1a] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller [8086:3a02] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ahci
20:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8111 PCI Express-to-PCI Bridge [10b5:8111] (rev 21)
21:04.0 Network controller [0280]: Contemporary Controls Device [1571:a0e4] (rev aa)
    Subsystem: Contemporary Controls Device [1571:a0e4]
onee@onee-HP:~$ modprobe com20020
modprobe: ERROR: could not insert 'com20020': Operation not permitted
onee@onee-HP:~$ sudo modprobe com20020
[sudo] password for onee: 
Désolé, essayez de nouveau.
[sudo] password for onee: 
onee@onee-HP:~$ sudo modprobe arcnet
onee@onee-HP:~$ lsmod
Module                  Size  Used by
com20020               16384  0 
arcnet                 20480  1 com20020
drbg                   28672  1 
ansi_cprng             16384  0 
ctr                    16384  2 
ccm                    20480  2 
arc4                   16384  2 
rt2800usb              28672  0 
rt2x00usb              20480  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              49152  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              655360  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              487424  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               307200  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   20480  2 
rfcomm                 65536  0 
bluetooth             466944  10 bnep,rfcomm
coretemp               16384  0 
gpio_ich               16384  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_realtek    73728  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
i915                 1138688  2 
snd_hda_intel          36864  3 
kvm                   479232  0 
snd_hda_codec         114688  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           61440  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
input_leds             16384  0 
serio_raw              16384  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
drm_kms_helper        135168  1 i915
snd_seq_midi_event     16384  1 snd_seq_midi
lpc_ich                20480  0 
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm                   307200  4 i915,drm_kms_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    16384  1 hp_wmi
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
8250_fintek            16384  0 
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
shpchp                 32768  0 
soundcore              16384  1 snd
sysimgblt              16384  1 drm_kms_helper
video                  40960  1 i915
parport_pc             32768  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
psmouse               114688  0 
ahci                   36864  2 
libahci                32768  1 ahci
e1000e                217088  0 
fjes                   28672  0 
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
onee@onee-HP:~$ sudo modprobe com20020_pci
onee@onee-HP:~$ sudo modprobe com20020pci
modprobe: FATAL: Module com20020pci not found.
onee@onee-HP:~$ cls
La commande « cls » est introuvable, mais il y en a 18 similaires
cls : commande introuvable
onee@onee-HP:~$ clear

onee@onee-HP:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e40] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e42] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e43] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
00:19.0 Ethernet controller [0200]: Intel Corporation 82567V-4 Gigabit Network Connection [8086:1525] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 [8086:3a67] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 [8086:3a68] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 [8086:3a69] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 [8086:3a6c] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller [8086:3a6e] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 [8086:3a70] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 [8086:3a64] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 [8086:3a65] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 [8086:3a66] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 [8086:3a6a] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JD (ICH10D) LPC Interface Controller [8086:3a1a] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller [8086:3a02] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1493]
    Kernel driver in use: ahci
20:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8111 PCI Express-to-PCI Bridge [10b5:8111] (rev 21)
21:04.0 Network controller [0280]: Contemporary Controls Device [1571:a0e4] (rev aa)
    Subsystem: Contemporary Controls Device [1571:a0e4]

```

lsmod : 

```
Module                  Size  Used by
com20020_pci           16384  0 
com20020               16384  1 com20020_pci
arcnet                 20480  2 com20020,com20020_pci
drbg                   28672  1 
ansi_cprng             16384  0 
ctr                    16384  2 
ccm                    20480  2 
arc4                   16384  2 
rt2800usb              28672  0 
rt2x00usb              20480  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              49152  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              655360  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              487424  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               307200  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   20480  2 
rfcomm                 65536  0 
bluetooth             466944  10 bnep,rfcomm
coretemp               16384  0 
gpio_ich               16384  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_realtek    73728  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
i915                 1138688  2 
snd_hda_intel          36864  3 
kvm                   479232  0 
snd_hda_codec         114688  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           61440  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
input_leds             16384  0 
serio_raw              16384  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0 
drm_kms_helper        135168  1 i915
snd_seq_midi_event     16384  1 snd_seq_midi
lpc_ich                20480  0 
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm                   307200  4 i915,drm_kms_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    16384  1 hp_wmi
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
8250_fintek            16384  0 
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
shpchp                 32768  0 
soundcore              16384  1 snd
sysimgblt              16384  1 drm_kms_helper
video                  40960  1 i915
parport_pc             32768  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
psmouse               114688  0 
ahci                   36864  2 
libahci                32768  1 ahci
e1000e                217088  0 
fjes                   28672  0 
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
```

---

### Post by praseodym on 2018-12-24
Please show
```

sudo modprobe -rfv com20020_pci com20020 arcnet
sudo modprobe -v com20020_pci
sudo modprobe -v arcnet
dmesg | egrep 'key|20020|fail|arc'
```

---

### Post by sonbole on 2018-12-25
hi praseodym,

here :
sudo modprobe -rfv com20020_pci com20020 arcnet
```
rmmod com20020_pci
rmmod com20020
rmmod arcnet
```

sudo modprobe -v com20020_pci
```
insmod /lib/modules/4.4.0-140-generic/kernel/drivers/net/arcnet/arcnet.ko 
insmod /lib/modules/4.4.0-140-generic/kernel/drivers/net/arcnet/com20020.ko 
insmod /lib/modules/4.4.0-140-generic/kernel/drivers/net/arcnet/com20020-pci.ko
```

sudo modprobe -v arcnet
No output.

dmesg | egrep 'key|20020|fail|arc'
```
[    0.000000] e820: last_pfn = 0x7d9b8 max_arch_pfn = 0x1000000
[    0.000000] Hierarchical RCU implementation.
[    0.125081] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20150930/dsfield-211)
[    0.125086] ACPI Error: Method parse/execution failed [\_SB.PCI0._OSC] (Node f488e840), AE_ALREADY_EXISTS (20150930/psparse-542)
[    0.125094] acpi PNP0A08:00: _OSC failed (AE_ALREADY_EXISTS); disabling ASPM
[    0.527234] Initialise system trusted keyring
[    0.530053] Key type big_key registered
[    0.530068] Allocating IMA MOK and blacklist keyrings.
[    0.530458] Asymmetric key parser 'x509' registered
[    0.637699] Loaded X.509 cert 'Build time autogenerated kernel key: bb2a2ec6b9eac9bc1baeeccc4ab0a199cadc57db'
[    0.652439] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[   10.970642] input: HP WMI hotkeys as /devices/virtual/input/input9
[   12.533865] init: failsafe main process (622) killed by TERM signal
[   15.946934] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[ 6273.911887] arcnet: arcnet loaded
[ 6273.918806] arcnet:com20020: COM20020 chipset support (by David Woodhouse et al.)
[ 6339.198635] arcnet:com20020_pci: COM20020 PCI support
[82772.443544] arcnet: arcnet loaded
[82772.450120] arcnet:com20020: COM20020 chipset support (by David Woodhouse et al.)
[82772.456283] arcnet:com20020_pci: COM20020 PCI support
```

Thanks.

---


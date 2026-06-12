---
title: "DWA-140 on Ubuntu 8.10"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Wridmuld on 2008-11-18
Hi guys.

I have tried now for some time to get my DLINK DWA-140 to work with no results.

There are a number of posts about this specific device, and I have to my best knowledge (and with a little help from my friends... thanks again!) gone through these without any positive results.
My knowledge of Ubuntu and Linux generally is not that very great so I might very well have missed a few things.

I tried to make and install the Ralink 2870 driver according to the following instructions:

[http://sudan.ubuntuforums.com/showpost.php?p=5400203&postcount=6]("http://sudan.ubuntuforums.com/showpost.php?p=5400203&postcount=6")

 It did not work. So I made (maked???) the 2860 driver instead. It was possible to make and install, but the device still do not show up anywhere. In the desktop System - Administration - Network Tools, only the loopback and my normal ethernet card is visible.

The other posts I have looked at poses the following problems to me:


[http://ubuntuforums.org/showthread.php?t=766850&highlight=DWA-140]("http://ubuntuforums.org/showthread.php?t=766850&highlight=DWA-140")
There is no "RT2870_USB_DEVICES" - section in this file. 

[http://ubuntuforums.org/showthread.php?t=859177&highlight=DWA-140]("http://ubuntuforums.org/showthread.php?t=859177&highlight=DWA-140")
No wireless device shows up when I do ifconfig. And not in any other place either.

[http://ubuntuforums.org/showthread.php?t=683085&page=5]("http://ubuntuforums.org/showthread.php?t=683085&page=5")
I followed the instructions, but nothing happened. Most probably because the device have not been found yet, I would guess.

I have no clue how to solve this, and quite honestly I would not like to buy new hardware or change distro because of this. If it is possible to solve this, I would like to.

Is there any kind Ubuntu-expert-geek out there qualified and good-hearted enough to help me with this?

Best regards

/Wridmuld

---

### Post by Wridmuld on 2008-11-18
I think most information is already posted above, but just to be sure, I'll post some data here:

```
administrator@BURK:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
```

```
administrator@BURK:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1f:c6:66:98:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.199 latency=0 module=sky2 multicast=yes
```

```
/etc/Network/interfaces
auto lo
iface lo inet loopback
```

```
administrator@BURK:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:66:98:86  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe66:9886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70424473 (70.4 MB)  TX bytes:3308238 (3.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30456 (30.4 KB)  TX bytes:30456 (30.4 KB)
```

---

### Post by Wridmuld on 2008-11-18
Yet more information:

```
administrator@BURK:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 07d1:3c09 D-Link System DWA-140 802.11n Adapter [ralink rt2870]
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 001 Device 005: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
administrator@BURK:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
```


```
administrator@BURK:~$ lsmod
Module                  Size  Used by
ipv6                  263972  16 
af_packet              25728  2 
binfmt_misc            16904  1 
ppdev                  15620  0 
acpi_cpufreq           15500  3 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_usb_audio          89728  1 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_dummy          10884  0 
snd_pcm                83204  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_usb_lib            24192  1 snd_usb_audio
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
gspca_zc3xx            55936  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
gspca_main             29312  1 gspca_zc3xx
snd_hwdep              15236  1 snd_usb_audio
videodev               41344  1 gspca_main
v4l1_compat            22404  1 videodev
nvidia               6900560  36 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
evdev                  17696  8 
i2c_core               31892  1 nvidia
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
pcspkr                 10624  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13444  0 
iTCO_wdt               18596  0 
intel_agp              33724  0 
button                 14224  0 
psmouse                45200  0 
snd                    63268  19 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
agpgart                42184  2 nvidia,intel_agp
soundcore              15328  1 snd
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  5 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
sd_mod                 42264  7 
crc_t10dif              9984  1 sd_mod
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_marvell           11776  0 
ata_piix               24580  6 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
libata                177312  4 pata_marvell,ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
sky2                   53380  0 
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  8 snd_usb_audio,snd_usb_lib,gspca_zc3xx,gspca_main,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

/Wridmuld

---

### Post by Wridmuld on 2008-11-18
I solved it!

For your information:

There was nothing I could do to make it work until suddenly I decided to install the graphical Ndiswrapper "ndisgtk".
Then it just jumped on and started!

Well, folks, I got no idea why or how it started but now my DLINK DWA-140 works just fine without a glitch.

/Wridmuld

---


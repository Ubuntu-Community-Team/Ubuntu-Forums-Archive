---
title: "Wireless hangs after 5 seconds on Hardy 8.04 after updates last week"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Joshua66 on 2008-09-03
Hi,
I have a stock Ubuntu 8.04 installation on my home computer with a Zonet ZEW2500P USB wireless card.  It was working without issue until last week when I installed an update from update-manager.  I think it was a kernel update (how would I find out?).

The symptoms are: My home wireless network shows up under the networking icon in the task bar.  When I click on it, I see appropriate connection messages in /var/log/syslog and networking works, including email, ping and so forth for about 5 seconds.  After which connectivity is lost (e.g. ping stops working).  During all this time, the output of 'ifconfig' and 'iwconfig' does not change.  There do not appear to be any messages in /var/log/syslog around the moment the wireless stops working.  If I plug in a wired connection, it works without issue.  Both the wireless and wired connection are to the same router.  I can connect via wirelesss from a macbook (osx) without issue.

As requested at [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425),
here is some more detailed information.  Any tips?  I'm happy to rollback last-week's update but I don't remember what it was...

```
$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

```
$ sudo lsusb 
Bus 008 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Bus 004 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

```
$ sudo lsusb -s 004:003 -v

Bus 004 Device 003: ID 148f:2573 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 bg WLAN
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

```
$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:e9:0a:84
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.194 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:4c:18:c4:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

```
$ lsmod
Module                  Size  Used by
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  16 
acpi_cpufreq           10796  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  4 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
rt2500usb              24320  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
snd_usb_audio          83936  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_hda_intel         344728  3 
rt73usb                27136  0 
rt2x00usb              12800  2 rt2500usb,rt73usb
rt2x00lib              22528  3 rt2500usb,rt73usb,rt2x00usb
snd_pcm                78596  3 snd_usb_audio,snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
rfkill                  8592  1 rt2x00lib
snd_seq_dummy           4868  0 
snd_usb_lib            18432  1 snd_usb_audio
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
snd_seq_oss            35584  0 
mac80211              165652  2 rt2x00usb,rt2x00lib
snd_seq_midi            9376  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
usbhid                 31872  0 
nvidia               7825536  34 
uvcvideo               58116  0 
snd_timer              24836  2 snd_pcm,snd_seq
cfg80211               15112  1 mac80211
hid                    38784  1 usbhid
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
serio_raw               7940  0 
snd_hwdep              10500  2 snd_usb_audio,snd_hda_intel
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
i2c_core               24832  1 nvidia
parport_pc             36260  1 
intel_agp              25492  0 
snd                    56996  19 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_pcm,snd_seq_dummy,snd_usb_lib,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device,snd_hwdep
evdev                  13056  4 
button                  9232  0 
agpgart                34760  2 nvidia,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
floppy                 59588  0 
pata_jmicron            7040  0 
ata_piix               19588  2 
r8169                  32900  0 
libata                159344  4 ata_generic,pata_acpi,pata_jmicron,ata_piix
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  10 rt2500usb,snd_usb_audio,rt73usb,rt2x00usb,snd_usb_lib,usbhid,uvcvideo,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

```
$ uname -a
Linux rrrr-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

---


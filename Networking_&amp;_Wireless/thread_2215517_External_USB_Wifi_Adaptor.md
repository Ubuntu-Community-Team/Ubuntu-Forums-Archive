---
title: "External USB Wifi Adaptor"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by selcuk2 on 2014-04-07
Hello all.

I just installed Ubuntu 13.1 on my laptop, after installing the system everything works good.
There is an internal wifi card (eth1 rather than wlan0 and i dont know why) on my laptop which works fine but also i have external Usb Wifi Adaptor which is not detected by ubuntu 13.1.
Please i need some help about it..

Here is some informations:

USB Wifi Model: [Asus N-300 USB Adaptor (USB N-14)]("http://www.asus.com/Networking/USBN14/")
Laptop : HP Pavilion DV6


```

pasa@pasa-ubuntu:~$ **uname -r -m**
3.11.0-12-generic x86_64

pasa@pasa-ubuntu:~$ **cat /etc/lsb-release** 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

pasa@pasa-ubuntu:~$ **lsusb**
Bus 002 Device 003: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID e0ff:0005  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0b05:17e8 ASUSTek Computer, Inc. **(External Wifi)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

pasa@pasa-ubuntu:~$** lspci**
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730/M96 [Mobility Radeon HD 4650/5165]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]
**02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)** (Internal Wifi)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

pasa@pasa-ubuntu:~$ **lsmod**
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  2 hid_generic,usbhid
michael_mic            12612  4 
arc4                   12608  2 
btusb                  28267  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
bluetooth             371874  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     41276  1 
coretemp               13435  0 
joydev                 17377  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
gpio_ich               13476  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
psmouse                97626  0 
lib80211_crypt_tkip    17619  0 
microcode              23518  0 
wl                   4207474  0 
serio_raw              13413  0 
snd_hda_codec_idt      50341  1 
snd_hda_intel          48171  10 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
radeon               1402449  3 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              479757  1 wl
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ttm                    83995  1 radeon
lpc_ich                21080  0 
drm_kms_helper         52651  1 radeon
hp_accel               26012  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   296739  5 ttm,drm_kms_helper,radeon
wmi                    19070  1 hp_wmi
soundcore              12680  1 snd
lis3lv02d              20156  1 hp_accel
jmb38x_ms              18670  0 
memstick               16760  1 jmb38x_ms
input_polldev          13896  1 lis3lv02d
i2c_algo_bit           13413  1 radeon
ir_sanyo_decoder       12839  0 
ir_rc6_decoder         12874  0 
ir_rc5_decoder         12710  0 
ir_nec_decoder         12915  0 
ir_mce_kbd_decoder     13214  0 
ir_lirc_codec          13021  0 
lirc_dev               19980  1 ir_lirc_codec
ir_sony_decoder        12713  0 
ir_jvc_decoder         12751  0 
rc_rc6_mce             12502  0 
ene_ir                 28939  0 
video                  19318  0 
rc_core                27718  11 ir_lirc_codec,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,ene_ir,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder,rc_rc6_mce
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  2 
libahci                31898  1 ahci
firewire_ohci          40060  0 
sdhci_pci              18985  0 
firewire_core          64476  1 firewire_ohci
sdhci                  42630  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
r8169                  67341  0 
mii                    13934  1 r8169

pasa@pasa-ubuntu:~$ **sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 0c:ee:e6:b1:59:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.103 latency=0 wireless=IEEE 802.11abg
       resources: irq:16 memory:d9000000-d9003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:83:2f:1a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:5000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff



pasa@pasa-ubuntu:~$** iwconfig** (internal wifi works fine)
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"gorgulu"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 74:EA:3A:E6:BE:D5   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


pasa@pasa-ubuntu:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:26:9e:83:2f:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 0c:ee:e6:b1:59:5a  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eee:e6ff:feb1:595a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6739 errors:0 dropped:0 overruns:0 frame:25961
          TX packets:4672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7341211 (7.3 MB)  TX bytes:619424 (619.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100900 (100.9 KB)  TX bytes:100900 (100.9 KB)


```

---

### Post by ajgreeny on 2014-04-07
Why do you need the external USB adapter if the internal one is working properly?  Presumably you can just unplug the USB version, or is the problem that you can not actually find the USB adapter plugged in anywhere so can not remove it?

Tell us more about your difficulty as you seem to have wifi working, so what do you want from us?

---


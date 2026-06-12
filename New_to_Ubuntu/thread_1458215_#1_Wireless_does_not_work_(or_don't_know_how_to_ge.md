---
title: "#1 Wireless does not work (or don't know how to get it to work) on Toshiba L500D"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by s32ialx on 2010-04-19
Hi i'm currently running Ubuntu 10.04 I've read a fourm on how to download teh firmware for my RTL8192E wifi driver and i downloaded the firmware and put it in the directory and it said restart and it will work well nothing anyways here's all the info. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508746)
[B]
$ lspci[/B]
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```**$ lshw -C network**
```
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:e2:fa:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:18 ioport:a000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:ff:29:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.106 latency=0 multicast=yes
       resources: irq:28 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

```[B]
$ ifconfig[/B]
```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:ff:29:79  
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:feff:2979/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9402204 (9.4 MB)  TX bytes:1347795 (1.3 MB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```**$ iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```**$ iwconfig wlan0**
```
wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```**$ lsmod**
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   278794  1 
snd_hda_intel          25517  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
psmouse                64320  0 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4918  0 
i2c_piix4               9639  0 
fglrx                2353582  32 
soundcore               8052  1 snd
snd_page_alloc          8660  2 snd_hda_intel,snd_pcm
video                  20623  0 
r8192_pci             269338  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
edac_core              45423  0 
edac_mce_amd            9182  0 
vga16fb                12757  1 
output                  2503  1 video
vgastate                9857  1 vga16fb
shpchp                 33679  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
joydev                 11072  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
r8169                  39970  0 
mii                     5237  1 r8169
ahci                   37550  2 
pata_atiixp             4209  0 

```**$ dmesg**
```
[    8.051431] Linux kernel driver for RTL8192 based WLAN cards
[    8.051432] Copyright (c) 2007-2008, Realsil Wlan
[    8.051483] rtl819xE 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.051490] rtl819xE 0000:0e:00.0: setting latency timer to 64
[    8.053676] lp: driver loaded but no devices found
[    8.112196] Console: switching to colour frame buffer device 80x30
[    8.120527] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    8.132958] acpi device:35: registered as cooling_device2
[    8.133262] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:33/LNXVIDEO:01/input/input7
[    8.133347] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    8.169406] Dot11d_Init()
[    8.169423] IRQ 18
[    8.576339] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.576346] Disabling lock debugging due to kernel taint
[    8.656248] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[    8.658732] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
[    8.658767] [fglrx]   vendor: 1002 device: 9613 count: 1
[    8.659210] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[    8.659244] pci 0000:01:05.0: power state changed by ACPI to D0
[    8.659256] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.659262] pci 0000:01:05.0: setting latency timer to 64
[    8.659708] [fglrx] Kernel PAT support is enabled
[    8.659742] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   10.228124] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   10.347366] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.372050] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   10.715206] hda_codec: ALC272: BIOS auto-probing.
[   10.716901] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   12.491185] type=1505 audit(1271711458.023:5):  operation="profile_load" pid=929 name="/usr/share/gdm/guest-session/Xsession"
[   12.493541] type=1505 audit(1271711458.023:6):  operation="profile_replace" pid=930 name="/sbin/dhclient3"
[   12.493854] type=1505 audit(1271711458.023:7):  operation="profile_replace" pid=930 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.494035] type=1505 audit(1271711458.023:8):  operation="profile_replace" pid=930 name="/usr/lib/connman/scripts/dhclient-script"
[   12.904643] type=1505 audit(1271711458.433:9):  operation="profile_load" pid=931 name="/usr/bin/evince"
[   12.908496] type=1505 audit(1271711458.433:10):  operation="profile_load" pid=931 name="/usr/bin/evince-previewer"
[   12.910923] type=1505 audit(1271711458.443:11):  operation="profile_load" pid=931 name="/usr/bin/evince-thumbnailer"
[   13.038233] type=1505 audit(1271711458.563:12):  operation="profile_load" pid=935 name="/usr/lib/cups/backend/cups-pdf"
[   13.038621] type=1505 audit(1271711458.563:13):  operation="profile_load" pid=935 name="/usr/sbin/cupsd"
[   13.206469] type=1505 audit(1271711458.733:14):  operation="profile_load" pid=937 name="/usr/sbin/tcpdump"
[   13.883451] rtl819xE: PlatformInitFirmware()==>
[   13.883455] 
[   13.883466] rtl819xE 0000:0e:00.0: firmware: requesting RTL8192E/boot.img
[   13.992557] rtl819xE 0000:0e:00.0: firmware: requesting RTL8192E/main.img
[   14.130674] rtl819xE:Download Firmware: Put code fail!
[   14.130679] 
[   14.130683] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   14.130684] 
[   14.130686] rtl819xE:CPUcheck_maincodeok_turnonCPU fail!
[   14.130687] 
[   14.130689] rtl819xE:ERR in init_firmware()
[   14.130690] 
[   14.130693] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   14.130694] 
[   14.133308] r8169: eth0: link down

```**$ iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
``` lsb_release -d
Description:    Ubuntu lucid (development branch)

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

$ uname -a
Linux s32ialx-laptop 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux

---

### Post by cariboo on 2010-04-19
Go to /etc/NetworkManager/nm-system-settings.conf and change:

```
[ifupdown
managed=false
```

to

```
[ifupdown
managed=true
```

then restart networking:

```
sudo service networking restart
```

to see if that helps.

---

### Post by s32ialx on 2010-04-19
> **cariboo907 said:**
> Go to /etc/NetworkManager/nm-system-settings.conf and change:

```
[ifupdown
managed=false
```to

```
[ifupdown
managed=true
```then restart networking:

```
sudo service networking restart
```to see if that helps.

$ sudo service networking restart
restart: Unknown instance:

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.

---

### Post by s32ialx on 2010-04-19
I downloaded RutilT WLAN Manager using Ubuntu Software Centre and i get the error.

An error occured : Can't get frequency/channel code:1

dunno

---


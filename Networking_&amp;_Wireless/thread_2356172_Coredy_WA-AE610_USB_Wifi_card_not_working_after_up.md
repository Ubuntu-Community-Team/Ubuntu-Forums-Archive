---
title: "Coredy WA-AE610 USB Wifi card not working after update."
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by gogmilk on 2017-03-20
Hi everyone, first time posting, I've been using Ubuntu for years but I'm definitely no expert, I mostly use it for quite specific film/video stuff so apologies if there's not a lot of info initially to go on here or I'm slow on the uptake.

I've hit a snag with a fresh install of Ubuntu 16.04. After the initial install I have installed the latest driver for my wireless card a Coredy WA-AE610 ([http://www.coredytech.com/goods-99-Coredy+AE610+Nano+Dual+Band+USB+Wi-Fi+Adapter+with+External+Antenna.html?i=ManualsDrivers](http://www.coredytech.com/goods-99-Coredy+AE610+Nano+Dual+Band+USB+Wi-Fi+Adapter+with+External+Antenna.html?i=ManualsDrivers)). The driver install works perfectly, wifi network is functional and all good. As it's a fresh install there are a fair amount of updates required. After installing this big system update the wireless USB adapter no longer works, the green light on the device doesn't come on either. 

I was thinking that it's possible that the update included some wireless drivers that are now conflicting with the previously installed drivers from Coredy but I've not found anything on the forums or anywhere else that seems to have the answer I'm looking for.

As a start, here's the output from ```
sudo lshw -class network
``` it looks like the wireless interface is disabled but I'm not sure why or what's disabling it.

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 09
       serial: d8:50:e6:c0:12:94
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:26 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA
```

---

### Post by praseodym on 2017-03-20
Please check
```

uname -a
dpkg -l linux-image-* | grep ii
```

---

### Post by gogmilk on 2017-03-20
Thanks, here is the output...

```
ukgff@UKGFF:~$ uname -a
Linux UKGFF 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
ukgff@UKGFF:~$ dpkg -l linux-image-* | grep li
ii  linux-image-4.4.0-21-generic       4.4.0-21.37  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic 4.4.0-21.37  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.21.22  amd64        Generic Linux kernel image
```

---

### Post by praseodym on 2017-03-20
Strange, here kernel 4.4.0-67 is running?! Any chance to run
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
via cable? Please run
```

lspci -nnk 
lsusb
rfkill list
lsmod
iwconfig
dkms status
```
to show the exact hardware. Maybe reinstalling the driver helps because dkms is not working correctly (or is not installed?!).
```

sudo apt-get install dkms
```
According to the dkms.conf file it is driver mt7610u_sta. Use this PPA instead:

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi)
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi 
sudo apt-get update
sudo apt-get install mt7610u-dkms
```

---

### Post by gogmilk on 2017-03-20
I had done the initial update using sudo apt-get upgrade when I tried it this time it just had one small package update, sudo apt-get dist-upgrade did the following...

```

The following NEW packages will be installed
  libhardware2 libhybris libhybris-common1 libmedia1 libsnapd-glib1 linux-headers-4.4.0-66 linux-headers-4.4.0-66-generic linux-image-4.4.0-66-generic
  linux-image-extra-4.4.0-66-generic snap-confine snapd-login-service
The following packages will be upgraded:
  gnome-software gnome-software-common liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 linux-generic linux-headers-generic linux-image-generic oxideqt-codecs
  qml-module-ubuntu-web snapd ubuntu-core-launcher ubuntu-software webapp-container webbrowser-app
15 to upgrade, 11 to newly install, 0 to remove and 0 not to upgrade.
Need to get 115 MB of archives.
After this operation, 353 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
```

This is the output for the other commands...

```
ukgff@UKGFF:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
    Subsystem: ASUSTeK Computer Inc. 4th Gen Core Processor DRAM Controller [1043:8534]
    Kernel driver in use: hsw_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB xHCI [1043:8534]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family MEI Controller [1043:8534]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB EHCI [1043:8534]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset High Definition Audio Controller [1043:8576]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family USB EHCI [1043:8534]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation B85 Express LPC Controller [8086:8c50] (rev 05)
    Subsystem: ASUSTeK Computer Inc. B85 Express LPC Controller [1043:8534]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [1043:8534]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
    Subsystem: ASUSTeK Computer Inc. 8 Series/C220 Series Chipset Family SMBus Controller [1043:8534]
    Kernel modules: i2c_i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c82] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:6253]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fb9] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:6253]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:8505]
    Kernel driver in use: r8169
    Kernel modules: r8169
ukgff@UKGFF:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 05ac:0304 Apple, Inc. Mighty Mouse [Mitsumi, M1152]
Bus 003 Device 003: ID 0e8d:7610 MediaTek Inc. 
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ukgff@UKGFF:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ukgff@UKGFF:~$ lsmod
Module                  Size  Used by
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
ufs                    73728  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  36864  0
ntfs                   98304  0
msdos                  20480  0
jfs                   180224  0
xfs                   966656  0
libcrc32c              16384  1 xfs
cpuid                  16384  0
nls_iso8859_1          16384  0
uas                    24576  0
usb_storage            69632  1 uas
mt7610u_sta           892928  0
cfg80211              565248  1 mt7610u_sta
snd_hda_codec_hdmi     53248  1
nvidia_uvm            647168  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
hid_apple              16384  0
sparse_keymap          16384  1 asus_wmi
joydev                 20480  0
input_leds             16384  0
snd_hda_codec_realtek    81920  1
intel_rapl             20480  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   536576  0
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
irqbypass              16384  1 kvm
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       16384  0
snd_hwdep              16384  1 snd_hda_codec
crc32_pclmul           16384  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aesni_intel           167936  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 36864  0
soundcore              16384  1 snd
mei                    98304  1 mei_me
shpchp                 36864  0
lpc_ich                24576  0
wmi                    20480  1 asus_wmi
8250_fintek            16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid,hid_apple
nvidia_drm             53248  1
nvidia_modeset        790528  4 nvidia_drm
nvidia              12144640  60 nvidia_modeset,nvidia_uvm
drm_kms_helper        139264  1 nvidia_drm
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   360448  4 drm_kms_helper,nvidia_drm
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
fjes                   28672  0
video                  40960  1 asus_wmi
ukgff@UKGFF:~$ iwconfig
enp3s0    no wireless extensions.

ra0       Ralink STA  
          
lo        no wireless extensions.

ukgff@UKGFF:~$ dkms status
bbswitch, 0.8, 4.4.0-21-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-66-generic, x86_64: installed
nvidia-375, 375.39, 4.4.0-21-generic, x86_64: installed
nvidia-375, 375.39, 4.4.0-66-generic, x86_64: installed

```

dkms appears to be working ok... I've installed the driver you mentioned from the other PPA and nothing has changed. I'll reboot no though and post back in a minute if the problem is fixed.

---

### Post by gogmilk on 2017-03-20
No improvement after reboot... in fact I now can't see the option to enable/disable wifi networks. iwconfig now outputs...
```

ukgff@UKGFF:~$ iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

ukgff@UKGFF:~$ 
```

---

### Post by praseodym on 2017-03-21
Driver load
```

sudo modprobe -v mt7610u_sta
dmesg | grep mt7
iwconfig
```

---

### Post by gogmilk on 2017-03-21
Thanks again, but I'm getting errors loading the driver too...

```
ukgff@UKGFF:~$ sudo modprobe -v mt7610u_sta
[sudo] password for ukgff: 
insmod /lib/modules/4.4.0-66-generic/updates/dkms/mt7610u_sta.ko 
modprobe: ERROR: could not insert 'mt7610u_sta': Exec format error
ukgff@UKGFF:~$ dmesg | grep mt7
[   79.357776] mt7610u_sta: disagrees about version of symbol module_layout
[  108.999980] mt7610u_sta: disagrees about version of symbol module_layout
[  142.045916] mt7610u_sta: disagrees about version of symbol module_layout
ukgff@UKGFF:~$ iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

ukgff@UKGFF:~$ 


```

---

### Post by gogmilk on 2017-03-23
Bumping as still unresolved - it's a strange one because everything was working perfectly before the update so it seems there should be a way to make this work again.

---

### Post by praseodym on 2017-03-23
Please show
```

modinfo mt7610u_sta
```

---

### Post by gogmilk on 2017-03-23
Thanks, here's the result...

```
ukgff@UKGFF:~$ modinfo mt7610u_sta
filename:       /lib/modules/4.4.0-66-generic/updates/dkms/mt7610u_sta.ko
version:        3.0.0.2
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     75BC5DA09129BFDB11A12A5
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v20F4p806Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v293Cp5702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8502d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3425d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3D02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0075d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2357p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp760Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp761Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pB711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           mac:wireless mac addr (charp)
parm:           debug:log verbosity level (0: off, 1: error only [default], 2: warnings, 3: trace, 4: info, 5: loud) (long)

```

---

### Post by praseodym on 2017-03-23
Ok, the driver is there. Lets see
```

dmesg | egrep 'mt7|rt2|firm|error|country'
```
Did you try an earlier kernel?

---

### Post by gogmilk on 2017-03-23
I haven't, although it was broken before doing the dist-upgrade you mentioned the other day, which, unless I'm misunderstanding (quite possible) I think updated the kernel?

```
ukgff@UKGFF:~$ dmesg | egrep 'mt7|rt2|firm|error|country'
[    1.797354] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    3.011173] mt7610u_sta: disagrees about version of symbol module_layout
[62827.666007] usb 3-1: device not accepting address 7, error -71
[64232.287096] multiqueue0:src[13343]: segfault at 18 ip 00007f38060b8196 sp 00007f37eaa88380 error 4 in libgstvideo-1.0.so.0.803.0[7f380608f000+7c000]
[64268.576182] multiqueue0:src[13408]: segfault at 18 ip 00007fb09b9a2196 sp 00007fb07bffe380 error 4 in libgstvideo-1.0.so.0.803.0[7fb09b979000+7c000]
[68865.234045] blk_update_request: I/O error, dev sdc, sector 242614264
[68865.254096] blk_update_request: I/O error, dev sdc, sector 242614264
[68865.254098] Buffer I/O error on dev sdc1, logical block 30326779, async page read
[69177.043958] multiqueue0:src[14765]: segfault at 18 ip 00007f8b5cf87196 sp 00007f8b41912380 error 4 in libgstvideo-1.0.so.0.803.0[7f8b5cf5e000+7c000]
[99765.394929] mt7610u_sta: disagrees about version of symbol module_layout

```

---

### Post by gogmilk on 2017-03-24
I just did another clean install, this time running updates before installing the drivers. Same result. Losing patience here, I've managed to get a cable running from a mac mini I have in the same room which is working fine but definitely not a long term solution.

Installing the driver from ppa:hanipouspilot/rtlwifi seems to disable any wireless options in Ubuntu.

---

### Post by gogmilk on 2017-03-24
I removed the driver from ppa:hanipouspilot/rtlwifi and tried again installing the drivers from Coredy, although this restores the ability to enable wifi in Ubuntu it also causes an internal error when the device is plugged in, the error report lists this as a crash of the modem manager. I'm guessing this means the device is now being recognised but something is stopping it from functioning as it should be. No wireless networks are listed and light indicator on the device is still off.

---

### Post by gogmilk on 2017-03-25
So I thought I had this cracked using the solution on the link below, I was able to get the wireless card activated and connected to the internet with a stable connection...

[http://askubuntu.com/questions/71159/network-manager-says-device-not-managed](http://askubuntu.com/questions/71159/network-manager-says-device-not-managed)

The process...
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```
  change the line *managed=false* to *managed=true*

  Save, stop and start network manager:

  ```
sudo service network-manager restart
```
  [HR][/HR]
Unfortunately though, my machine now won't restart/shut down. It hangs on a black screen every time I restart. After a hard reset, when I log back in I have the same problem (device not managed) even though I can see that the networkmanager.conf file is still set to managed=true.

Manually resetting the network manager after reboot using...
```
sudo service network-manager restart
```

... gives me properly functioning wifi. Close but not quite, also a bit concerned about the restart/shutdown hangs. Any ideas?

---

### Post by fredericklowe63 on 2017-03-25
I figured this out after trying everything I could to get my wifi up on the server version. In install it hooked to wifi fine. After install no luck. So after looking and looking with no success. I did sometime go kicks. I rebooted, but this time when grub came up I scrolled down to advance ubuntu option. Loaded the first ubuntu choice there. Booted up logged in. And wifi was working. I did updates upgrades rebooted. And this time let it boot up like after install the top choice. Logged in and wifi worked there to. That was the most confusing thing I went through. 1. Why would it hook to wifi while in install but after install no go? They need to set it up where install saves your wifi config that you used in install. I did do all the things all the post I read. I did change the interfaces to
Auto <my_wifiname>  (mine is wlp3s2)
Iface  wlp3s2 inlet static
address <my router ip>
netmask 255.255.255.0
gateway  <my router gateway>
wpa-ssid  <my router's name>
wpa-psi <my router's pass key
dns-nameserver  <my nameserver 1>
Added space did second nameserver and third. Saved and rebooted.
I done this before I tried the advance ubuntu option.  
I hope this helped, because for me was the only solution.

---


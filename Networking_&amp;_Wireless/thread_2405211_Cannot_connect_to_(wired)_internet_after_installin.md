---
title: "Cannot connect to (wired) internet after installing PCI network card and r8168"
date: 2018-11-02
forum: Networking &amp; Wireless
---

### Post by zachtheperson on 2018-11-02
My internet was working fine on an almost clean installation of ubuntu using the onboard LAN, when I installed a Rosewill RC-411v3 wired ethernet card and attempted to install the r8168 driver from the [official website]("https://www.rosewill.com/product/rosewill-rc-411-network-adapter-10-100-1000-mbps-pci-express-1-x-rj45/") it ran into some errors when trying to compile, but the new ethernet card worked perfectly until I rebooted the system, at which point I now receive a "Activation of network failed," error. 

I tried downloading the driver as a .deb which installed perfectly, but still no internet. [This forum thread]("https://ubuntuforums.org/showthread.php?t=2383612") is one of the only ones I could find that was similar, and even after trying everything I am still at square one.

I've googled like crazy but most people seem to be trying to fix wireless internet and mine is wired. Similar to the thread above, I have tried to fix it myself in a bunch of ways (most of which I don't even remember due to my inexperience) and feel like I am at the point where I am probably just breaking things even more.

Here is my info when I run these commands

lspci | grep -i net
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```

ifconfig
```
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.10.151  netmask 255.255.255.0  broadcast 192.168.10.255
        inet6 fe80::6a1c:a2ff:fe12:c7f7  prefixlen 64  scopeid 0x20<link>
        ether 68:1c:a2:12:c7:f7  txqueuelen 1000  (Ethernet)
        RX packets 243  bytes 66231 (66.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 27  bytes 3440 (3.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 31  base 0x1000

enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 94:de:80:73:a5:a3  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 33  base 0x1000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 458  bytes 35807 (35.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 458  bytes 35807 (35.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

sudo lshw -C network
  ```
*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: 68:1c:a2:12:c7:f7
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.046.00-NAPI duplex=full ip=192.168.10.151 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:31 ioport:d000(size=256) memory:d2204000-d2204fff memory:d2200000-d2203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 06
       serial: 94:de:80:73:a5:a3
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.046.00-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 ioport:c000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
```

cat /etc/NetworkManager/NetworkManager.conf 
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

[device]
wifi.scan-rand-mac-address=no
```

sudo modprobe -v r8168
```
immediately returns to prompt
```

Here are my system specs:
```
Mobo: Gigabyte 970a-d3
CPU:   AMD FX-6350
GPU:   GTX 970
ETH:   Rosewill RC-411v3 (wired)
```

If worse comes to worse my contingency plan preference is as follows:[INDENT]1. Reinstall default driver (mobo website only provides windows drivers, so I don't know how to do this)
2. Reinstall ubuntu (Getting the NVIDIA drivers to install and not prevent Ubuntu from starting was a PITA so this is a last resort)
[/INDENT]

At this point I don't even know where to start looking for solutions, so any help is appreciated

---

### Post by praseodym on 2018-11-03
Please show
```

lsmod
dmesg | grep r8
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by zachtheperson on 2018-11-03
lsmod
```
Module                  Size  Used by
nls_iso8859_1          16384  2
edac_mce_amd           28672  0
snd_hda_codec_hdmi     49152  1
kvm                   598016  0
snd_hda_codec_via      24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_via
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
joydev                 24576  0
input_leds             16384  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
nvidia_uvm            757760  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
k10temp                16384  0
fam15h_power           16384  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
dm_mirror              24576  1
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  3 dm_region_hash,dm_mirror
nvidia_drm             40960  2
nvidia_modeset       1114112  11 nvidia_drm
hid_logitech_hidpp     32768  0
nvidia              14364672  484 nvidia_uvm,nvidia_modeset
hid_generic            16384  0
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
hid_logitech_dj        20480  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
uas                    24576  0
drm                   401408  5 drm_kms_helper,nvidia_drm
r8168                 528384  0
usb_storage            69632  2 uas
ahci                   36864  2
i2c_piix4              24576  0
ipmi_devintf           20480  0
libahci                32768  1 ahci
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
usbhid                 49152  0
hid                   118784  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp

```

dmesg | grep r8
```
[    0.000000] percpu: Embedded 46 pages/cpu @        (ptrval) s151552 r8192 d28672 u262144
[    0.000000] pcpu-alloc: s151552 r8192 d28672 u262144 alloc=1*2097152
[    2.226533] r8168: loading out-of-tree module taints kernel.
[    2.226699] r8168: module verification failed: signature and/or required key missing - tainting kernel
[    2.228326] r8168 Gigabit Ethernet driver 8.046.00-NAPI loaded
[    2.250289] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    2.250293] r8168  Copyright (C) 2018  Realtek NIC software team <nicfae@realtek.com> 
[    2.251159] r8168 Gigabit Ethernet driver 8.046.00-NAPI loaded
[    2.273190] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    2.273194] r8168  Copyright (C) 2018  Realtek NIC software team <nicfae@realtek.com> 
[    2.342226] r8168 0000:03:00.0 enp3s0: renamed from eth0
[    2.468442] r8168 0000:04:00.0 enp4s0: renamed from eth1
[   36.874304] r8168: enp3s0: link up
[   37.884063] r8168: enp3s0: link down
[   51.242347] r8168: enp3s0: link up
[   51.467534] r8168 0000:03:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0011 address=0x0000000000000000 flags=0x0000]

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    20100  0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.10.0    0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
```

cat /etc/resolv.conf
```
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
```

---

### Post by praseodym on 2018-11-04
SecureBoot is turned off?

---

### Post by zachtheperson on 2018-11-04
Yes, secure boot is off

---

### Post by praseodym on 2018-11-04
Lets see
```

modinfo r8168
locate r8168.ko | grep lib
dkms status
uname -a
```

---

### Post by zachtheperson on 2018-11-04
modinfo r8168
```
filename:       /lib/modules/4.15.0-38-generic/updates/dkms/r8168.ko
version:        8.046.00-NAPI
license:        GPL
description:    RealTek RTL-8168 Gigabit Ethernet driver
author:         Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion:     1B7F4580601BCFA0300F9D2
alias:          pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
alias:          pci:v000010ECd00008161sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:        
retpoline:      Y
name:           r8168
vermagic:       4.15.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           speed_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           duplex_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           autoneg_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           advertising_mode:force phy operation. Deprecated by ethtool (8). (uint)
parm:           aspm:Enable ASPM. (int)
parm:           s5wol:Enable Shutdown Wake On Lan. (int)
parm:           s5_keep_curr_mac:Enable Shutdown Keep Current MAC Address. (int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           timer_count:Timer Interrupt Interval. (int)
parm:           eee_enable:Enable Energy Efficient Ethernet. (int)
parm:           hwoptimize:Enable HW optimization function. (ulong)
parm:           s0_magic_packet:Enable S0 Magic Packet. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)
```

locate r8168.ko | grep lib
```
/lib/modules/4.15.0-38-generic/updates/dkms/r8168.ko
/var/lib/dkms/r8168/8.046.00/4.15.0-38-generic/x86_64/module/r8168.ko
```

dkms status
```
nvidia, 390.87, 4.15.0-38-generic, x86_64: installed
r8168, 8.046.00, 4.15.0-38-generic, x86_64: installed
```

uname -a
```
Linux SHARD1 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by praseodym on 2018-11-05
Did you install the driver with both versions: DEB package and self-compiled?

---

### Post by zachtheperson on 2018-11-05
I attempted to self compile, but it threw an error because of some missing libraries during compile time, so I then installed using the .DEB

---

### Post by praseodym on 2018-11-05
So uninstall this one

```
sudo modprobe -rfv r8168
sudo dkms remove -m r8168 -v 8.046.00 --all
sudo rm -r /usr/src/r8168-8.046.00 
```
Reboot and check again
```

locate r8168.ko | grep lib
lsmod
dmesg | grep r8
```

---

### Post by zachtheperson on 2018-11-06
Ran the code, rebooted and got these results

locate r8168.ko | grep lib
```
/lib/modules/4.15.0-38-generic/updates/dkms/r8168.ko
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          16384  2
joydev                 24576  0
input_leds             16384  0
edac_mce_amd           28672  0
kvm                   598016  0
snd_hda_codec_hdmi     49152  1
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
snd_hda_codec_via      24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_via
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
fam15h_power           16384  0
k10temp                16384  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
shpchp                 36864  0
soundcore              16384  1 snd
nvidia_uvm            757760  0
mac_hid                16384  0
sch_fq_codel           20480  1
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
dm_mirror              24576  1
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  3 dm_region_hash,dm_mirror
hid_logitech_hidpp     32768  0
hid_logitech_dj        20480  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  5 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
nvidia_drm             40960  2
nvidia_modeset       1114112  11 nvidia_drm
nvidia              14364672  484 nvidia_uvm,nvidia_modeset
uas                    24576  0
usb_storage            69632  2 uas
drm_kms_helper        172032  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  5 drm_kms_helper,nvidia_drm
ahci                   36864  2
i2c_piix4              24576  0
ipmi_devintf           20480  0
libahci                32768  1 ahci
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
```

dmesg | grep r8
```
[    0.000000] percpu: Embedded 46 pages/cpu @        (ptrval) s151552 r8192 d28672 u262144
[    0.000000] pcpu-alloc: s151552 r8192 d28672 u262144 alloc=1*2097152
```

---


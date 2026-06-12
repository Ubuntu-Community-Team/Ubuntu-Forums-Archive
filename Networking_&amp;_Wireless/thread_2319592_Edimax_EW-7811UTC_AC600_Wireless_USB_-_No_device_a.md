---
title: "Edimax EW-7811UTC AC600 Wireless USB - No device after installing driver"
date: 2016-04-05
forum: Networking &amp; Wireless
---

### Post by skinnyquiver on 2016-04-05
I am not getting a device when i install the driver for EW-7811UTC

Let me know what else i can try

STEPS TO REPRODUCE:
Boot to a live kubuntu 15:10 distro
run apt-get update && apt get install rtl8812au-dkms

HELPFUL INFO:
############################################################################################
root@kubuntu:~# cat /etc/issue
Ubuntu 15.10 \n \l
############################################################################################
root@kubuntu:~# uname -a
Linux kubuntu 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
############################################################################################
root@kubuntu:~# lsusb
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 7392:a811 Edimax Technology Co., Ltd 
Bus 003 Device 002: ID abcd:1234 Unknown 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 003: ID 05ac:0201 Apple, Inc. USB Keyboard [Alps or Logitech, M2452]
Bus 001 Device 002: ID 05ac:1001 Apple, Inc. Keyboard Hub [ALPS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
############################################################################################
root@kubuntu:~# lsmod
Module                  Size  Used by
8812au                909312  0
input_leds             16384  0
snd_hda_codec_via      20480  1
snd_hda_codec_generic    77824  1 snd_hda_codec_via
snd_hda_codec_hdmi     49152  1
snd_hda_intel          36864  5
kvm                   512000  0
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_hda_core           65536  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
saa7164               126976  0
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
glue_helper            16384  1 aesni_intel
tveeprom               24576  1 saa7164
snd_rawmidi            32768  1 snd_seq_midi
ablk_helper            16384  1 aesni_intel
dvb_core              122880  1 saa7164
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
v4l2_common            16384  1 saa7164
snd                    81920  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videodev              172032  2 saa7164,v4l2_common
asus_atk0110           20480  0
edac_core              53248  0
serio_raw              16384  0
fam15h_power           16384  0
8250_fintek            16384  0
edac_mce_amd           24576  0
media                  24576  1 videodev
soundcore              16384  1 snd
i2c_piix4              24576  0
shpchp                 36864  0
k10temp                16384  0
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
squashfs               49152  1
overlay                49152  1
nls_iso8859_1          16384  1
btrfs                 970752  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
uas                    24576  0
usb_storage            69632  2 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
pata_acpi              16384  0
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
radeon               1519616  6
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
psmouse               126976  0
drm_kms_helper        126976  1 radeon
pata_atiixp            16384  0
drm                   356352  9 ttm,drm_kms_helper,radeon
ahci                   36864  1
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    20480  0
############################################################################################
root@kubuntu:~# dmesg | grep usbcore
[    0.368921] usbcore: registered new interface driver usbfs
[    0.368930] usbcore: registered new interface driver hub
[    0.368956] usbcore: registered new device driver usb
[    5.954541] usbcore: registered new interface driver usbhid
[   20.740444] usbcore: registered new interface driver usb-storage
[   20.741650] usbcore: registered new interface driver uas
[  421.764291] usbcore: registered new interface driver rtl8812au
############################################################################################
root@kubuntu:~# ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 2c:56:dc:79:df:97 brd ff:ff:ff:ff:ff:ff
############################################################################################
root@kubuntu:~# ifconfig -a
enp5s0    Link encap:Ethernet  HWaddr 2c:56:dc:79:df:97  
          inet addr:192.168.10.115  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2e56:dcff:fe79:df97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37390819 (37.3 MB)  TX bytes:1446906 (1.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141464 (141.4 KB)  TX bytes:141464 (141.4 KB)

---

### Post by skinnyquiver on 2016-04-05
UPDATE

  When i follow  these steps: [http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)

I get an interface but the system does not show it as a wifi
3: enx801f02ddb536: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT gr
    link/ether 80:1f:02:dd:b5:36 brd ff:ff:ff:ff:ff:ff

---

### Post by skinnyquiver on 2016-04-05
Apparently 15:10 uses a strange nameing scheme and the enx801f02ddb536 interface is the wireless

So only note here is it appears that you still have to install from source

---


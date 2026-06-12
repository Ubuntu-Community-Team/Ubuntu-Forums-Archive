---
title: "Internet not working in my ubuntu.."
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by harishankar on 2007-10-01
Hi all
I tried both ubuntu feisty fawn and also edubuntu..in both platform my internet is not working...which is working well in windows...i've attached the msgs which obviously many will ask me..pls refer to it...

root@edubuntu:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


root@edubuntu:~# lsmod
Module                  Size  Used by
isofs                  36284  1
udf                    85252  0
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0
ipv6                  268704  12
nfsd                  218992  17
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
i915                   24448  2
drm                    81044  3 i915
ppdev                  10116  0
acpi_cpufreq           10056  0
cpufreq_powersave       2688  0
cpufreq_userspace       5408  0
cpufreq_ondemand        9228  2
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0
pcc_acpi               13184  0
tc1100_wmi              8068  0
dev_acpi               12292  0
battery                10756  0
ac                      6020  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0
video                  16388  0
container               5248  0
button                  8720  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
nls_iso8859_1           5120  5
nls_cp437               6784  6
vfat                   14208  5
fat                    53916  1 vfat
fuse                   46612  1
lp                     12452  0
snd_intel8x0           34204  1
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0
shpchp                 34324  0
soundcore               8672  1 snd
pcspkr                  4224  0
pci_hotplug            32576  1 shpchp
intel_agp              25116  1
agpgart                35400  3 drm,intel_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  8
generic                 5124  0 [permanent]
8139too                27648  0
ata_piix               15492  8
ehci_hcd               34188  0
ata_generic             9092  0
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
8139cp                 25088  0
mii                     6528  2 8139too,8139cp
uhci_hcd               25360  0
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0




root@edubuntu:~# dmesg | grep eth
[    4.732048] eth0: RealTek RTL8139 at 0xdf84cc00, 00:19:d1:2d:d0:6f, IRQ 19
[    4.732052] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   14.728815] eth0: link down
[   48.402301] ADDRCONF(NETDEV_UP): eth0: link is not ready




root@edubuntu:~# sudo modprobe e100
WARNING: /etc/modprobe.d/blacklist line 31: ignoring bad line starting with 'Â´blacklist'



root@edubuntu:~# dmesg | tail
[   51.223071] Bluetooth: RFCOMM TTY layer initialized
[   51.223075] Bluetooth: RFCOMM ver 1.8
[   82.643908] ISO 9660 Extensions: Microsoft Joliet Level 3
[   82.759995] ISO 9660 Extensions: RRIP_1991A
[ 2108.817197] ppdev0: registered pardevice
[ 2108.817226] ppdev0: unregistered pardevice
[ 2109.334477] ppdev0: registered pardevice
[ 2109.383600] ppdev0: unregistered pardevice
[ 2664.152499] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[ 2664.152507] e100: Copyright(c) 1999-2006 Intel Corporation


root@edubuntu:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp




root@edubuntu:~# cat /etc/resolv.conf
root@edubuntu:~# 
root@edubuntu:~# 
root@edubuntu:~# 
root@edubuntu:~# lsmod | grep 8139too
8139too                27648  0 
mii                     6528  3 e100,8139too,8139cp

---

### Post by dmizer on 2007-10-01
this will seem strange, but i've seen this as a potential fix elsewhere.  if you're interested, i'll send you a link.

power off your computer, and unplug the power for at least 10 - 20 seconds.  if it's a laptop, that includes removing the battery.

then power it back on, and see if you get connected then.

---

### Post by noob12 on 2007-10-01
See this for an explanation and a more permanent workaround:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---


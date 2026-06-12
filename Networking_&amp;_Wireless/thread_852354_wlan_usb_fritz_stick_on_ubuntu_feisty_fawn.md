---
title: "wlan usb fritz stick on ubuntu feisty fawn"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by linuxorwindows on 2008-07-07
hello,

can somebody tell me whats the problem with internet connection on my laptop.

i can't open any internet sites

here is the information about my system:

```

daniel@daniel-laptop:~$ sudo ifconfig
Password:
eth0      Protokoll:Ethernet  Hardware Adresse 00:16:36:DC:25:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:39020 (38.1 KiB)  TX bytes:39020 (38.1 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:1A:4F:4A:31:90  
          inet6 Adresse: fe80::21a:4fff:fe4a:3190/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:144 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:30862 (30.1 KiB)

wlan0:ava Protokoll:Ethernet  Hardware Adresse 00:1A:4F:4A:31:90  
          inet Adresse:169.254.5.43  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1






daniel@daniel-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36284  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
i915                   24448  2 
drm                    81044  3 i915
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
ac                      6020  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
video                  16388  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
af_packet              23816  4 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 10816  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
pcmcia                 39212  0 
fwlanusb              607776  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
sky2                   43528  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
intel_agp              25244  1 
psmouse                38920  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35400  3 drm,intel_agp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
usb_storage            72256  1 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
generic                 5124  0 [permanent]
libusual               17936  1 usb_storage
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sg,usb_storage,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 fwlanusb,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability





daniel@daniel-laptop:~$ lsusb
Bus 005 Device 006: ID 057c:6201 AVM GmbH 
Bus 005 Device 002: ID 058f:6387 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 



```



thank you very much

---


---
title: "Realtek RTL8139 PCI Fast Ethernet Adapter Problems"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by BerinHardt on 2008-09-08
I'm new on linux and im running KUbuntu 7.04 & Windows XP on the same machine, but i'm unable to set up the network settings to connect Kubuntu to the router. btw, XP connects without any problem.
I know that there are lots of threads about this very problem, but i'll tried everything and i couldn't even make eth0 apear under ifconfig... can somebody help me?

lspci output:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
```

lsmod output:
```
Module                  Size  Used by
rfcomm                 40856  0
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_ondemand        9228  0
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0
sony_acpi               6284  0
pcc_acpi               13184  0
dev_acpi               12292  0
tc1100_wmi              8068  0
button                  8720  0
asus_acpi              17308  0
ac                      6020  0
container               5248  0
battery                10756  0
sbs                    15652  0
i2c_ec                  5888  1 sbs
video                  16388  0
backlight               7040  1 asus_acpi
dock                   10268  0
af_packet              23816  0
nls_utf8                3072  1
ntfs                  107764  1
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14208  1
fat                    53916  1 vfat
8139too                27648  0
mii                     6528  1 8139too
lp                     12452  0
fuse                   46612  0
snd_ens1371            27552  1
snd_ac97_codec         98336  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 12832  0
snd_timer              23684  2 snd_pcm,snd_seq
serio_raw               7940  0
gameport               16520  2 snd_ens1371,analog
pcspkr                  4224  0
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd_mpu401              9256  0
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  3 snd_ens1371,snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
xpad                    9988  0
psmouse                38920  0
snd                    54020  14 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm
i2c_viapro             10132  0
via_ircc               27540  0
irda                  201276  1 via_ircc
via_agp                11264  1
agpgart                35400  1 via_agp
i2c_core               22784  2 i2c_ec,i2c_viapro
crc_ccitt               3072  1 irda
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
evdev                  11008  5
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ide_disk               17024  6
ata_generic             9092  0
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
generic                 5124  0 [permanent]
usbhid                 26592  0
hid                    27392  1 usbhid
floppy                 59524  0
via82cxxx              10372  0 [permanent]
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
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
```

---

### Post by BerinHardt on 2008-09-15
I've just installed KUbuntu 8.04.1 and i'm still unable to use the realtek, does anybody knows what's happening?

---

### Post by stjalsma on 2008-09-16
I had this problem for a couple weeks with my realtek rtl8185 and almost made me give up.  It is very simple once you realize what to do.

Go to Realteks website and download the XP version of your wireless card drivers.  

Extract the file and keep the .inf file somewhere where you can target it.

In Ubuntu and I think Kubuntu also, just go to System>Administration>Windows Wireless Driver.  Click the Browse button and target the .inf file.  Reboot

That is all I had to do to get mine to work.

---

### Post by BerinHardt on 2008-09-16
well
i could make it work

I did this:

1) remove 8139too or 8139cp with $sudo modprobe -r 8139...

2) install the other with $sudo modprobe 8139...

3) then eth0 should appear in $sudo ifconfig -a

4) and when you type $sudo lshw -C network it saiys something like *-network DISABLED

5) Type $sudo ifconfig eth0 up

6) and finally $sudo dhclient eth0

---

### Post by BerinHardt on 2008-09-16
Well, that almost worked, my quiestion now is if i can make Kubuntu run ifconfig eth0 up and dhclient eth0 at startup and how to do it

---

### Post by caddict on 2008-09-19
If you haven't seen them, these two threads may help

[http://http://ubuntuforums.org/showthread.php?t=922873&highlight=8139]("http://ubuntuforums.org/showthread.php?t=922873&highlight=8139")

[http://http://ubuntuforums.org/showthread.php?t=918195&page=2]("http://ubuntuforums.org/showthread.php?t=918195&page=2")

---


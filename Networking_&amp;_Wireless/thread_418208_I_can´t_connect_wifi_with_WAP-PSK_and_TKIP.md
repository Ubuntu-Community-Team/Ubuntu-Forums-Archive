---
title: "I can´t connect wifi with WAP-PSK and TKIP"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by diediaga on 2007-04-22
Hi

I install the ubuntu 7.04
and I used the network-manager-gnome to configure to a wireless network with WAP-PSK and TKIP
but I can connect to it.

down there is information about my computer, please can anybody help me. I am new in linux

I am trying to connect since 2 months to this network.Now I can only connect to internet using windows and I would like totally to move to use ubuntu.

I already google a lot and read post about this problem, but I can´t find a solution that works for me.

thanks

diego

diediaga@diediaga-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   

          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



diediaga@diediaga-laptop:/$ lspci

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



diediaga@diediaga-laptop:/$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dock                   10268  0 
sbs                    15652  0 
battery                10756  0 
container               5248  0 
i2c_ec                  5888  1 sbs
ac                      6020  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
button                  8720  0 
nls_iso8859_1           5120  3 
nls_cp437               6784  3 
vfat                   14208  3 
fat                    53916  1 vfat
ipv6                  268704  10 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
irtty_sir               9600  0 
sir_dev                17156  1 irtty_sir
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bcm43xx               125332  0 
ieee80211softmac       31232  1 bcm43xx
irda                  201276  2 irtty_sir,sir_dev
pcmcia                 39212  0 
sdhci                  18700  0 
mmc_core               26756  1 sdhci
crc_ccitt               3072  1 irda
ieee80211              34760  2 bcm43xx,ieee80211softmac
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9740  0 
ieee80211_crypt         7040  1 ieee80211
ati_agp                10124  0 
agpgart                35400  1 ati_agp
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  6 
pcspkr                  4224  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
serio_raw               7940  0 
i2c_core               22784  2 i2c_ec,i2c_piix4
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  6 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
8139too                27648  0 
generic                 5124  0 [permanent]
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ehci_hcd               34188  0 
atiixp                  7440  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
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
commoncap               8192  1 capability

---

### Post by spd106 on 2007-04-22
Have you tried installing the bcm43xx-fwcutter package, it should download the firmware that you need. Then restart and you should be ok to use Network-Manager.

---

### Post by H.E. Pennypacker on 2007-04-25
Having the same issue, but with WPA2.  By the way, it is WPA-PSK.

---


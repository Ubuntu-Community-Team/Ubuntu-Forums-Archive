---
title: "problems with wda-1320 in dapper"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by camlost on 2007-02-06
Hey  I was hoping some one could help me. I'm running on dapper and my d-link wda-1320 pci card is not working. Here are the output of a couple commands

 uname -r
2.6.15-27-386

lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a33 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a61
0000:02:02.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
fglrx                 388908  8
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265856  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  4
lp                     11844  0
snd_atiixp             19724  1
snd_ac97_codec         93216  1 snd_atiixp
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
8139cp                 22528  0
8139too                26880  0
ath_hal               148816  3 ath_pci,ath_rate_sample
mii                     5888  2 8139cp,8139too
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_atiixp,snd_pcm
tsdev                   8000  0
rtc                    13492  0
pcspkr                  2180  0
floppy                 62148  0
usbhid                 39904  0
psmouse                36100  0
serio_raw               7300  0
ati_agp                 9100  0
agpgart                34888  2 fglrx,ati_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130820  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
atiixp                  6800  1
sd_mod                 19984  3
generic                 5124  0
sata_sil                9348  4
libata                 78992  1 sata_sil
scsi_mod              139496  3 sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

when I go to configure the wireless connection I can see the network. But I'm not connecting. I'm new to ubunto, the only thing I can think of is the my roomate changed the wep and didn't tell me. I have seen him in a couple weeks. *Edit* nope talked to roommate wep is right. Thanks for any help,

---

### Post by camlost on 2007-02-21
bump

anyone have any ideas

---

### Post by camlost on 2007-08-01
Bump 
I'm still lost here. I just moved across the country so I thought I've give it another shot.

I can see networks in Network Manager. But when I connect, the connection says active but I can't load pages or access anything online

If anyone can help me I'd be very greatful

---


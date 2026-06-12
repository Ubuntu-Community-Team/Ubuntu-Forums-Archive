---
title: "Internet Speed Fluctiations with Wireless"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Guardian-Mage on 2008-10-30
I am really happy that my wireless is working at all, but it still has major issues. My wireless is getting speeds from 0 - 650 KiB/s. 650, being my max internet speed anyways. But, more often, the speed is under 30KiB/s. This is not acceptable. In Windows Vista I get full speed. I have disabled Ip v6 in Firefox, and in ubuntu using the following:

> 
Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though.):

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then to have the settings take effect immediately, run:

sudo sysctl -p


I have also deleted all IP V6 related entries from my hosts file. All I want is my internet to work, so if anyone can help my, I would much appreciate it.

My wireless card is a D'Link DWA-542 Wireless N PCI adapter in a full tower workstation. 

The relative output of "sudo lspci -v" is:

```

05:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a69
	Flags: bus master, 66MHz, medium devsel, latency 168, IRQ 16
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] #80 [0000]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

The relative output of "sudo lsmod" is:
```

Module                  Size  Used by
ipv6                  263972  18 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  3 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              11520  0 
sbs                    19464  0 
wmi                    14504  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
ath9k                 274232  0 
snd_seq_dummy          10884  0 
mac80211              216820  1 ath9k
snd_seq_oss            38528  0 
pcspkr                 10624  0 
cfg80211               32392  1 mac80211
iTCO_wdt               18596  0 
snd_hda_intel         381488  2 
evdev                  17696  10 
snd_pcm_oss            46848  0 
usblp                  20480  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi           14336  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
fglrx                1813960  31 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_seq_oss,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
intel_agp              33724  0 
agpgart                42184  2 fglrx,intel_agp
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
sd_mod                 42264  11 
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
ata_generic            12932  0 
pata_acpi              12160  0 
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            81728  1 
libusual               27156  1 usb_storage
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
ata_piix               24580  6 
ahci                   37132  0 
pata_jmicron           11136  0 
atl1                   40968  0 
mii                    13440  1 atl1
libata                177312  5 ata_generic,pata_acpi,ata_piix,ahci,pata_jmicron
scsi_mod              155212  6 sbp2,sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  7 usblp,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  9 

```

---


---
title: "Cant Access the Internet DSL with Marvell"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by crazygerad on 2006-11-09
I recently installed Dapper Drake but its not recognizing my ADSL internet connection which worked fine in my other computer but that one is dead due to age. So I checked around and read the usual commands to diagnose this problem. What I read so far its that I need Sky2 driver or something and would sincerely appreciate if anybody can tell me how to install it if you are so kind.

Thank you for reading.

```
--lsmod 
Module
Size  Used by ipv6 272288  10 
binfmt_misc 13448  1 rfcomm 42260  0 l2cap
27136  5 rfcomm
bluetooth 53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  0 
lp                     12964  0 
tsdev                   9152  0 
usb_storage            75072  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
libusual               17040  1 usb_storage
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
usblp                  15488  0 
sg                     37404  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
usbhid                 45152  1 
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
intel_agp              26012  1 
i2c_core               23424  1 i2c_ec
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
psmouse                41352  0 
parport_pc             37796  1 
agpgart                34888  1 intel_agp
serio_raw               8452  0 
hw_random               7320  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
parport                39496  2 lp,parport_pc
pcspkr                  4352  0 
floppy                 63044  0 
evdev                  11392  3 
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
ehci_hcd               34696  0 
usbcore               134912  8 usb_storage,libusual,usblp,usbhid,uhci_hcd,ehci_hcd
ide_generic             2432  0 
ide_disk               18560  3 
jmicron                 5504  0 [permanent]
ahci                   20228  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sd_mod                 22656  0 
generic                 5764  0 
ata_piix               11780  0 
libata                 74892  2 ahci,ata_piix
scsi_mod              144648  6 usb_storage,sg,ahci,sr_mod,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

lspci | grep Eth

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



```

---


---
title: "Intel 82573L Gigabit ethernet controller"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by dthbrd on 2008-07-23
Hi,

I'm having a problem getting my NIC to work in Ubuntu 8.04. I am very new to linux. In system > administration > network tools it is listed as "unknown interface." 

Here is lshw -C network

*-network UNCLAIMED 
description: Ethernet controller
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 02
serial: 00:13:02:31:19:ff
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g



Here is ifconfig



lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:106944 (104.4 KB) TX bytes:106944 (104.4 KB)

wlan0 Link encap:Ethernet HWaddr 00:13:02:31:19:ff 
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::213:2ff:fe31:19ff/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3419 errors:0 dropped:0 overruns:0 frame:0
TX packets:3210 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3359906 (3.2 MB) TX bytes:598033 (584.0 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-13-02-31-19-FF-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


Here is lsmod


Module Size Used by
ipv6 267780 10 
radeon 124192 0 
drm 82452 1 radeon
rfcomm 41744 2 
l2cap 25728 13 rfcomm
bluetooth 61156 4 rfcomm,l2cap
uinput 10240 1 
ppdev 10372 0 
acpi_cpufreq 10796 1 
cpufreq_powersave 2688 0 
cpufreq_userspace 5284 0 
cpufreq_ondemand 9740 2 
cpufreq_stats 7104 0 
freq_table 5536 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative 8712 0 
bay 6912 0 
sbs 15112 0 
sbshc 7680 1 sbs
dock 11280 1 bay
container 5632 0 
iptable_filter 3840 0 
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
nls_iso8859_1 4992 1 
nls_cp437 6656 1 
vfat 14464 1 
fat 54556 1 vfat
af_packet 23812 2 
parport_pc 36260 0 
lp 12324 0 
parport 37832 3 ppdev,parport_pc,lp
arc4 2944 2 
ecb 4480 2 
blkcipher 8324 1 ecb
joydev 13120 0 
pcmcia 40876 0 
snd_hda_intel 344728 3 
snd_pcm_oss 42144 0 
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
snd_hwdep 10500 1 snd_hda_intel
snd_seq_dummy 4868 0 
snd_seq_oss 35584 0 
snd_seq_midi 9376 0 
snd_rawmidi 25760 1 snd_seq_midi
battery 14212 0 
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
iwl3945 89844 0 
ac 6916 0 
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 24836 2 snd_pcm,snd_seq
iwlwifi_mac80211 219108 1 iwl3945
evdev 13056 9 
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
serio_raw 7940 0 
irtty_sir 9728 0 
video 19856 0 
output 4736 1 video
cfg80211 15112 1 iwlwifi_mac80211
e1000e 119336 0 
thinkpad_acpi 51836 0 
yenta_socket 27276 1 
rsrc_nonstatic 13696 1 yenta_socket
pcmcia_core 40596 3 pcmcia,yenta_socket,rsrc_nonstatic
snd 56996 17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_ seq,snd_timer,snd_seq_device
psmouse 40336 0 
button 9232 0 
nvram 9992 2 thinkpad_acpi
sir_dev 17412 1 irtty_sir
nsc_ircc 24208 0 
irda 203068 3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt 3072 1 irda
soundcore 8800 1 snd
intel_agp 25492 0 
iTCO_wdt 13092 0 
iTCO_vendor_support 4868 1 iTCO_wdt
shpchp 34452 0 
pci_hotplug 30880 1 shpchp
agpgart 34760 2 drm,intel_agp
pcspkr 4224 0 
ext3 136712 1 
jbd 48404 1 ext3
mbcache 9600 1 ext3
sg 36880 0 
sr_mod 17956 0 
cdrom 37408 1 sr_mod
sd_mod 30720 4 
ata_generic 8324 0 
pata_acpi 8320 0 
ata_piix 19588 3 
ehci_hcd 37900 0 
libata 159344 3 ata_generic,pata_acpi,ata_piix
scsi_mod 151436 4 sg,sr_mod,sd_mod,libata
uhci_hcd 27024 0 
usbcore 146028 3 ehci_hcd,uhci_hcd
e1000 126016 0 
thermal 16796 0 
processor 36872 4 acpi_cpufreq,thermal
fan 5636 0 
fbcon 42912 0 
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 3 


Thanks in advance for any advice.

---

### Post by Lipaugus Vociferans on 2008-09-14
[SIZE="3"]Hola, Well after reading here and there I've got my ethernet intel pro1000 (82573l) working... 

1- unmount driver...
  > sudo modprobe -r e1000

2- Mount it again with this parameter... 
  >  sudo modprobe e1000 eeprom_bad_csum_allow=1
   Ethernet should be now working!!!!

3-Download this script  from Ibm 
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/vidalia-eeprom-mod-script]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/vidalia-eeprom-mod-script") 

4. Run that script...
   > sudo ./vidalia-eeprom-mod-script eth0

Ready, that's how I've got mine working...

I hope it Helps...:)[/SIZE]

---


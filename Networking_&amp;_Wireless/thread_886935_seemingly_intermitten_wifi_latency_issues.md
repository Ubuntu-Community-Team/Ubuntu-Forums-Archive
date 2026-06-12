---
title: "seemingly intermitten wifi latency issues"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by leetleo on 2008-08-11
I've recently installed Ubuntu 8.04 (dual boot with Vista) on an Inspiron 1720. I managed to get everything up and running and I'm actually really happy with Ubuntu so far, but I've run into an issue. I am able to connect to my wifi with ease, and when connected, I notice normal download speeds, but I find that after a while, the connection will experience spikes of high latency. It's usually only a temporary spike, but it becomes a problem when I'm trying to play WoW, as it interrupts gameplay and eventually ends up causing me to be kicked from the server. I've also noticed some significant latency (roughly 3-6 seconds) when resolving URLS.  

I've ruled out hardware issues as Vista does not have this problem.
The machine is a Dell Inspiron 1720.
I'm using Broadcom BCM94311MCG for wifi.


BTW: I am posting from work ATM, so I won't be able to post any terminal output for a few hours, but I'm hoping I can get some general info or advice regarding this issue. Thanks in advance!

---

### Post by leetleo on 2008-08-12
Anyone?

---

### Post by leetleo on 2008-08-15
I guess nobody knows anything about this issue. Glad I dual booted lol. It was an interesting experience, but I'll just stick with Vista. Thanks anyway!

---

### Post by iobyte4 on 2008-08-19
I have the EXACT same problem with the EXACT same hardware as well. Can anybody help, I really don't want to reinstall vista :(

---

### Post by iobyte4 on 2008-08-19
I installed wicd in place of network manager but I'm still having the same problems. I'll be playing for a little while, then sooner or later I notice that I am not receiving any response from the server. I start to receive data VERY delayed (like 30 seconds) and then I get disconnected after a few minutes. If after noticing the latency, I close WoW, reopen it and reconnect, it goes back to normal, so it seems like the ping spikes really high and screws up my synchronization with the server. Is there a wine/ubuntu system configuration setting having to do with network traffic or latency that might be set incorrectly and causing this problem as a result?

I didn't have this problem in Vista. Please help!

---

### Post by iobyte4 on 2008-08-19
bump

---

### Post by iobyte4 on 2008-08-19
bump

---

### Post by rocklee on 2008-08-19
Unfortunately the people with previous wireless problems and have managed to solve it are as good as we are, they got lucky.

I'm trying to understand how to get my wireless working reliably but no dice, I don't want to keep booting in windows just to access ubuntu.  Otherwise I'll have to do a reinstallation of ubuntu again.

It is disappointing though that no mods can help but that's ubuntu for you.

---

### Post by caljohnsmith on 2008-08-19
What driver are you guys using for your wireless card? And does your card use the BCM4311 chipset like the OP? Please post the output of:
```
sudo lshw -C network
lsmod
```

---

### Post by iobyte4 on 2008-08-20
> **caljohnsmith said:**
> What driver are you guys using for your wireless card? And does your card use the BCM4311 chipset like the OP? Please post the output of:
```
sudo lshw -C network
lsmod
```

```

 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:99:35:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:60:51:ac:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g

Module                  Size  Used by
af_packet              23812  2 
binfmt_misc            12808  1 
rfkill_input            5504  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
hci_usb                16540  2 
dcdbas                  9504  0 
b43                   144420  0 
bluetooth              61156  7 rfcomm,l2cap,hci_usb
rfkill                  8592  3 rfkill_input,b43
evdev                  13056  11 
mac80211              165652  1 b43
snd_usb_audio          83936  2 
snd_usb_lib            18432  1 snd_usb_audio
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
sdhci                  19076  0 
snd_hda_intel         344728  2 
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
nvidia               7825536  36 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0 
snd_pcm                78596  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
i2c_core               24832  1 nvidia
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
video                  19856  14 
output                  4736  1 video
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
wmi_acer                9644  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
button                  9232  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                40336  0 
snd                    56996  21 snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      6916  0 
intel_agp              25492  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
agpgart                34760  2 nvidia,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
b44                    28432  0 
ahci                   28420  2 
ata_generic             8324  0 
ohci1394               33584  0 
libata                159344  4 pata_acpi,ata_piix,ahci,ata_generic
mii                     6400  1 b44
ieee1394               93752  2 sbp2,ohci1394
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ssb                    34308  2 b43,b44
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  7 hci_usb,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


```

---

### Post by caljohnsmith on 2008-08-20
Since the b43 linux driver for your bcm4311 wireless card is not working well, your other option is ndiswrapper. Do you have the Windows wireless drivers for your wireless card, maybe on a CD that came with the wireless card? If you don't, you will need to download them from either the manufacturer of you wireless card, or possibly from the Broadcom website. You'll want to use the Windows XP wireless drivers, not Vista, and you will need the .inf and .sys driver files for ndiswrapper.

---

### Post by iobyte4 on 2008-08-25
> **caljohnsmith said:**
> Since the b43 linux driver for your bcm4311 wireless card is not working well, your other option is ndiswrapper. Do you have the Windows wireless drivers for your wireless card, maybe on a CD that came with the wireless card? If you don't, you will need to download them from either the manufacturer of you wireless card, or possibly from the Broadcom website. You'll want to use the Windows XP wireless drivers, not Vista, and you will need the .inf and .sys driver files for ndiswrapper.

Switched to ndiswrapper using XP drivers and as of yet the latency/disconnects have not recurred. Thanks!

---


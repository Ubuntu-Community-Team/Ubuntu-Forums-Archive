---
title: "Wireless Not Working correctly"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by diesel7186 on 2008-03-20
Hello, I am having a major problem with my wireless card.

Here is my problem. I downloaded Ubuntu, and installed everything. The only way that I can get my wireless working when I start my computer is if I go to Manual Network Configuration> Wireless Properties>Password Type : and change it from WPA Personal to WPA2 Personal

Then my wireless works. Its just a pain to do that every time I start up my computer. Is there a way to get around that.

Here is my information when I type in terminal lspci:

donkey@donkey-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)



Hope you can help me!!!!

---

### Post by Pres-Gas on 2008-03-20
Can you post the output from "lsmod"?

---

### Post by diesel7186 on 2008-03-20
Module                  Size  Used by
i915                   25856  2 
drm                    83348  3 i915
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
sony_laptop            32088  0 
sonypi                 23960  0 
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_ondemand        9612  2 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
container               5504  0 
battery                11012  0 
ac                      6148  0 
video                  18060  0 
dock                   10656  0 
button                  8976  0 
sbs                    19592  0 
ipv6                  273892  10 
af_packet              24840  2 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  4 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
ipw3945               119840  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 11328  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 41388  0 
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211              35656  1 ipw3945
snd                    54660  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
sky2                   46852  0 
soundcore               8800  2 snd
ieee80211_crypt         7040  1 ieee80211
psmouse                39952  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
serio_raw               8068  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
shpchp                 34580  0 
agpgart                35016  3 drm,intel_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  8 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
usbhid                 29536  0 
hid                    28928  1 usbhid
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
uhci_hcd               26640  0 
usbcore               138632  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by Pres-Gas on 2008-03-20
What happens when you select the wireless network from the list in nm-applet instead of the manual opton?

---

### Post by diesel7186 on 2008-03-20
nm-aplet? im not great at ubuntu! do you have aim so we can talk faster. mine is Diesel7186

---


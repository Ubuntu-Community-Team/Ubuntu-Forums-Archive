---
title: "Feisty Fawn Beta wireless ndis x64 problem"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by shofetim on 2007-04-03
I have installed Feisty Fawn beta (20070322) x64 and am trying to get wireless networking to function. I have a netgear pci WG311v3 wireless card. lspci lists it as: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
I downloaded the drivers from netgear's site, and installed the latest build of ndiswrappers (1.41). After I install the driver with ndiswrapper, I do a ndiswrapper -l
and it says: 
wg311v3 : driver installed
	device (11AB:1FAA) present
the driver wont work this way, and it wont allow me to assign it to device 11AB:1FAA.
The driver is listed as working on ndiswrapper's wiki.
I am at a loss....
How do I get this driver to work?
thx

---

### Post by shofetim on 2007-04-04
More information:
System:
CPU: AMD 64 3800
HD: 250GB
RAM 2GB
Nvidia 6150 LE chipset

It seems to me that the driver should be working, but yet doesn't. I don't know how to fix it, and can't find the answer.
 
Here is the output of ndiswrapper -l
wg311v3 : driver installed
        device (11AB:1FAA) present

lsmod:
Module                  Size  Used by
ipv6                  307072  10 
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16480  0 
cpufreq_conservative     9736  0 
cpufreq_stats           8416  0 
cpufreq_userspace       6176  0 
cpufreq_ondemand       10640  1 
freq_table              6336  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3072  0 
tc1100_wmi              9224  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
sony_acpi               7064  0 
dock                   11992  0 
ac                      6920  0 
asus_acpi              19756  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6784  1 sbs
container               6144  0 
battery                12040  0 
backlight               8448  1 asus_acpi
button                 10016  0 
ndiswrapper           240104  0 
nls_iso8859_1           6528  3 
nls_cp437               8192  3 
vfat                   16256  3 
fat                    58672  1 vfat
nls_utf8                3456  1 
ntfs                  101960  1 
sbp2                   26628  0 
parport_pc             40104  0 
lp                     15048  0 
parport                43404  3 ppdev,parport_pc,lp
fuse                   51888  0 
snd_hda_intel          23968  1 
snd_hda_codec         261632  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4736  0 
serio_raw               9092  0 
psmouse                43536  0 
k8temp                  7552  0 
snd                    68904  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
af_packet              27020  4 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
i2c_nforce2             7680  0 
i2c_core               26624  2 i2c_ec,i2c_nforce2
tsdev                  10112  0 
evdev                  13056  3 
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
sd_mod                 23808  9 
ata_generic            10628  0 
usb_storage            80448  2 
libusual               22056  1 usb_storage
sata_nv                24580  4 
libata                130728  2 ata_generic,sata_nv
scsi_mod              166968  5 sbp2,sg,sd_mod,usb_storage,libata
amd74xx                16944  0 [permanent]
forcedeth              48776  0 
ehci_hcd               37004  0 
ohci1394               38088  0 
ieee1394              369272  2 sbp2,ohci1394
generic                 6788  0 [permanent]
ohci_hcd               24196  0 
usbcore               154416  6 ndiswrapper,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability

lspci:
03:08.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

Any help would be appreciated

---

### Post by shofetim on 2007-04-05
Solution:
Netgear does not make x64 drivers, and I was unable to find any x64 drivers for my hardware. So it is back to i386.

---

### Post by k5cqb on 2007-04-06
Were you able to get this working in the i386?  I have the same results but have not been able to get it working on i386.

---

### Post by shofetim on 2007-04-07
I didn't try it again in Feisty, but It works fine in Edgy i386.
Only trouble I had was that I used KDE instead of gnome, and KDE's gui wasn't doing what it said it was, so I had to set it up from the terminal.

This howto was very helpful:
[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

What does sudo iwconfig say?
And sudo iwlist?

---


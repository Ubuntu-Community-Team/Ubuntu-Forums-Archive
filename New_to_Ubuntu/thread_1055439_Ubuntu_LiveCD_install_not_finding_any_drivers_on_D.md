---
title: "Ubuntu LiveCD install not finding any drivers on Dell Inspiron 1525"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by SlingerXL on 2009-01-30
I just got a 1525 with Vista installed and I just installed 8.04 from a Live CD and System>Administration>Hardware Drivers finds no proprietary drivers. Does anyone know why or where I can find the drivers? I have the CD with all the drivers on it but I don't know how to install them in Ubuntu. I should note I'm not a complete noob, I've been using Ubuntu for a few years, but I'm still pretty novice.

EDIT: Here's my lspci and lsmod

~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12) 
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01) 


~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat 
mmc_block              14980  2 
ipv6                  267780  10 
i915                   32512  2 
drm                    82580  3 i915 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm 
bluetooth              61156  4 rfcomm,l2cap 
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
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
dcdbas                  9504  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm 
snd_hwdep              10500  1 snd_hda_intel 
pcspkr                  4224  0 
psmouse                40336  0 
serio_raw               7940  0 
snd_seq_dummy           4868  0 
evdev                  13056  7 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi 
sky2                   47492  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi 
sdhci                  19076  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24836  2 snd_pcm,snd_seq 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               58116  0 
mmc_core               51460  2 mmc_block,sdhci 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
compat_ioctl32          2304  1 uvcvideo 
videodev               29440  1 uvcvideo 
v4l1_compat            15492  2 uvcvideo,videodev 
v4l2_common            18304  2 uvcvideo,videodev 
soundcore               8800  1 snd 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp 
video                  19856  0 
output                  4736  1 video 
wmi_acer                9644  0 
button                  9232  0 
battery                14212  0 
ac                      6916  0 
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp 
ext3                  136712  1 
jbd                    48404  1 ext3 
mbcache                 9600  1 ext3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod 
sg                     36880  0 
ata_piix               19588  0 
sd_mod                 30720  3 
pata_acpi               8320  0 
ahci                   28420  2 
ata_generic             8324  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394 
libata                159344  4 ata_piix,pata_acpi,ahci,ata_generic 
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 uvcvideo,ehci_hcd,uhci_hcd 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal 
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon 
font                    9472  1 fbcon 
bitblit                 6784  1 fbcon 
softcursor              3072  1 bitblit 
fuse                   50580  3

---

### Post by avtolle on 2009-01-30
What drivers are you looking for?

---

### Post by SlingerXL on 2009-01-30
I guess all of them if it doesn't find any drivers. Well, I guess the mouse and graphics drivers must be working if they're working; but then why doesn't it list them in the Hardware Drivers app?

---

### Post by avtolle on 2009-01-30
Looking at your post, as edited, there would not be any drivers listed in System>Administration>Hardware Drivers. 

It appears the one driver you need is for the Broadcom card, which is not included in the proprietary drivers under that app. Broadcom cards are problematic within Ubuntu, at least, if not throughout various distros of Linux. There are many threads on what is to be done to install such a card. May I suggest you do a forum search. I don't have such a card (having fought the Atheros battle, successfully for now) and cannot give you even a place to start off the top of my head.

---

### Post by avtolle on 2009-01-30
Take a look at [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) as one possible way to proceed.

Edit: I believe you will need the b43 driver, included within the package that may be downloaded from the linked site, for your card.

Edit 2: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) gives additional information.

---

### Post by SlingerXL on 2009-01-30
I should add that my ethernet doesn't work either.

---

### Post by Sealbhach on 2009-01-30
> 09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12) 

That should work right out of the box, try to dhcp your router:
```

sudo dhclient eth0
```


.

---

### Post by SlingerXL on 2009-01-30
Ah! That did it. Why did I have to do that to make it work?

---

### Post by Sealbhach on 2009-01-30
> **SlingerXL said:**
> Ah! That did it. Why did I have to do that to make it work?

That commands makes your PC ask the router for an IP address, it should happen automatically when you connect the cable, hopefully it should work straightaway from now on.


.

---

### Post by newbee70 on 2009-01-30
> **avtolle said:**
> Take a look at [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) as one possible way to proceed.

Edit: I believe you will need the b43 driver, included within the package that may be downloaded from the linked site, for your card.

Edit 2: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) gives additional information.

b43-fwcutter is in the repositories.

make sure you are online through eth0

do a::     sudo apt-get install b43-fwcutter 

it will install and ask you if you want it to retrieve the drivers, 
answer yes or "y" and it will fetch and install it.  reboot and your wireless light should light up. you may have to left click your network icon and enable your wireless to connect on wireless. disconnect your hardwire and enjoy the wireless.

---


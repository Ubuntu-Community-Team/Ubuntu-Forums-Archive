---
title: "Networking suddenly stops working"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by orbital on 2006-08-29
I'm running dapper with xgl/compiz and everything was working fine, but suddenly today, for some reason, I can't get online. I think something is seriously messed up with the recognition of my network card (I also dual-boot XP and everything works fine with it).

I post my lspci and lsmod if they give any clues what's wrong.

**lspci**

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:04:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


**lsmod**

Module                  Size  Used by
ipv6                  286976  22 
rfcomm                 43604  0 
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
fglrx                 391756  26 
speedstep_centrino      8752  1 
cpufreq_userspace       6496  2 
cpufreq_stats           6688  0 
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        7752  0 
cpufreq_conservative     9000  0 
video                  16324  0 
tc1100_wmi              6884  0 
sony_acpi               5580  0 
pcc_acpi               12416  0 
hotkey                 11492  0 
dev_acpi               11236  0 
container               4608  0 
button                  6704  0 
acpi_sbs               20172  0 
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
dm_mod                 63256  1 
md_mod                 76052  0 
af_packet              24520  2 
sr_mod                 17988  0 
sbp2                   25060  0 
parport_pc             37988  0 
lp                     12356  0 
parport                39400  2 parport_pc,lp
r1000                  17984  0 
joydev                 10432  0 
spca5xx               653808  0 
tsdev                   8032  0 
videodev               10144  1 spca5xx
usbhid                 42752  0 
ipw3945               132348  1 
r8169                  31336  0 
ieee80211              38952  1 ipw3945
ieee80211_crypt         6528  1 ieee80211
ieee80211_1_1_13       39880  0 
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
snd_hda_intel          20468  1 
snd_hda_codec         163088  1 snd_hda_intel
psmouse                40004  0 
serio_raw               7748  0 
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
intel_agp              24700  1 
agpgart                36784  2 fglrx,intel_agp
shpchp                 49504  0 
pci_hotplug            30788  1 shpchp
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
evdev                  10176  2 
sg                     40160  0 
ext3                  148104  2 
jbd                    65876  1 ext3
ide_generic             1504  0 
ohci1394               37524  0 
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0 
uhci_hcd               35408  0 
usbcore               139076  5 spca5xx,usbhid,ehci_hcd,uhci_hcd
sd_mod                 20448  4 
ahci                   18020  7 
libata                 83440  1 ahci
scsi_mod              145960  6 sr_mod,sbp2,sg,sd_mod,ahci,libata
ide_cd                 35780  0 
cdrom                  41408  2 sr_mod,ide_cd
piix                   11652  1 
generic                 5124  0 
thermal                13768  0 
processor              26888  2 speedstep_centrino,thermal
fan                     4836  0 
capability              4968  0 
commoncap               7328  1 capability
vga16fb                13992  1 
vgastate               10208  1 vga16fb
fbcon                  43904  72 
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

Any ideas what to do??

---

### Post by funchords on 2006-08-29
no clues there.  How about the results of ...

**sudo ifconfig **

and 

**sudo iwconfig**

and using the device name of the missing device (e.g. eth1)
[B]
sudo ifconfig eth1 up
sudo ifup eth1[/B]

and if that doesn't help
[B]
sudo dmesg | grep eth1
sudo dmesg | grep ipw[/B]

---


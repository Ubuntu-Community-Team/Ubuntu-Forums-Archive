---
title: "laptop integrated bluetooth not found"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by benjietan on 2006-11-14
good day

have an acer travelmate 3282 who's integrated bluetooth i've been trying to activate. tried it out under windows xp and was able to get it to work. checking the driver under window xp system, turned out it was a broadcom 2035 chip

to get things going, here's the output of uname -r :

Linux tm3282 2.6.18.2 #1 SMP Sat Nov 11 04:49:31 PHT 2006 i686 GNU/Linux

i had originally installed dapper but upgraded the kernel to 2.6.18.2 to come up with an optimized kernel for centrino duo and to be sure the bcm203x driver was installed


**here's the output of lspci :**


0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c5
0000:02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
0000:0a:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:0a:06.3 0805: Texas Instruments: Unknown device 803c


**bluetooth output from dmesg :**

Bluetooth: Core ver 2.11
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.8-rfc
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM ver 1.8
eth0: no IPv6 routers present


**lsmod :**

Module                  Size  Used by
rfcomm                 33496  0
l2cap                  27776  5 rfcomm
crc16                   2240  1 l2cap
bluetooth              46948  4 rfcomm,l2cap
ppdev                   7620  0
speedstep_centrino      7680  1
cpufreq_userspace       3680  2
cpufreq_stats           5220  0
freq_table              4192  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5708  0
cpufreq_conservative     6408  0
video                  13892  0
sbs                    12324  0
i2c_ec                  4288  1 sbs
i2c_core               17088  1 i2c_ec
button                  5264  0
container               3520  0
ac                      3908  0
battery                 8132  0
af_packet              17096  0
ipv6                  237824  12
snd_hda_intel          14676  1
snd_hda_codec         148592  1 snd_hda_intel
joydev                  8384  0
tsdev                   6400  0
pcmcia                 32700  0
usbhid                 38816  0
irda                  190972  0
snd_pcm_oss            39520  0
snd_mixer_oss          14912  1 snd_pcm_oss
tg3                   101892  0
crc_ccitt               2304  1 irda
snd_pcm                69252  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              19268  1 snd_pcm
yenta_socket           23820  3
rsrc_nonstatic         11392  1 yenta_socket
pcmcia_core            35864  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  16076  0
mmc_core               19136  1 sdhci
serio_raw               5700  0
snd                    42944  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7584  1 snd
shpchp                 34400  0
pcspkr                  2816  0
snd_page_alloc          8072  2 snd_hda_intel,snd_pcm
intel_agp              20060  1
sbp2                   20488  0
pci_hotplug            13512  1 shpchp
psmouse                36168  0
agpgart                25992  1 intel_agp
parport_pc             31920  0
lp                      9568  0
evdev                   8064  2
sr_mod                 13540  0
cdrom                  34992  1 sr_mod
sg                     30940  0
parport                31752  3 ppdev,parport_pc,lp
ext3                  123976  1
jbd                    52456  1 ext3
mbcache                 7108  1 ext3
ide_generic             1472  0 [permanent]
ohci1394               31408  0
ieee1394              285560  2 sbp2,ohci1394
ehci_hcd               29448  0
uhci_hcd               21068  0
usbcore               113056  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 16832  3
generic                 4996  0 [permanent]
ata_piix               10696  2
libata                 87956  1 ata_piix
scsi_mod              118572  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                11400  0
processor              21064  2 speedstep_centrino,thermal
fan                     3844  0
vga16fb                11276  0
cfbcopyarea             4032  1 vga16fb
vgastate                9152  1 vga16fb
cfbimgblt               3136  1 vga16fb
cfbfillrect             4224  1 vga16fb



haven't touched any of the default bluetooth configs and checked the kernel settings to include the bcm203x driver. had googled around for activating bcm203x devices but found users mostly asking about usb based devices and not integrated ones on laptops

hope someone can give me suggestions on what i may be overlooking to get the kernel to load the driver for the broadcom 2035 chip

thanks in advance

---


---
title: "DWL G650 restart problem"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by mxgods on 2007-06-11
I have a D-Link DWL G650 rev B1, previously had edgy worked fine.  I recently did a freshdual boot of xp pro and fiesty.  Since i installed fiesty i have had wireless problems.  When i am connected wirelessly with the dlink card, my computer will reset after about 5 minutes of internet use.  If i am hard wired into the wall i have no problems.  Is there something i could do about my wireless problem?

---

### Post by dannyboy79 on 2007-06-12
please post the output of the following commmands:

lspci -v

lsusb

lsmod

We need to see if any wireless modules are conflicting with one another. Also, are you saying that your computer just completely shuts off, no shutting down messages or nothing???? just plain, BOOM, it's off????? This would lead me to believe that your CPU is overheating but then of course that you mention that everything is fine when using hard wired so this is very very weird!!! I will also need to know the rest of your setup, hardware and what all you have installed. Also, please post the reults of dmesg at a website that hosts free text files and paste the link here. you can get the ouput of

dmesg
ported to a tecxt file by issuing this command
dmesg > dmesg.log
and then they''ll be that log file located witin whatever your current direcotry was, you can find that out by issuing 
pwd

good luck and in order to help i'll need all the info I have asked for and I don't want to ask for it twice.

---

### Post by mxgods on 2007-06-12
mxg0d@mxg0d-laptop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1671 Super P4 Northbridge [AGP4X,PCI and SDR/DDR] (rev 02)
        Flags: bus master, medium devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e0100000-e01fffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1000 [size=256]
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
        Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: medium devsel, IRQ 10
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1400 [size=256]
        Capabilities: <access denied>

00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Unknown device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 10
        Memory at e0004000 (32-bit, non-prefetchable) [size=8K]

00:0a.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50010000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

00:0a.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50011000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 48000000-4bfff000 (prefetchable)
        Memory window 1: 4c000000-4ffff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0003000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0008000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 8000
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1800 [size=16]
        Capabilities: <access denied>

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Unknown device 3c08:9400
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 1c00 [size=256]
        Memory at e0007000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 50000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at e0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 (Rev B3,B5) Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 44000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

mxg0d@mxg0d-laptop:~$ lsusb
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
mxg0d@mxg0d-laptop:~$ lsmod
Module                  Size  Used by
nls_cp437               6784  0 
isofs                  36284  0 
udf                    85252  0 
snd_rtctimer            4384  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                31620  0 
ppdev                  10116  0 
radeon                124576  5 
drm                    81044  6 radeon
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268960  173 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  3 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
snd_ali5451            24460  1 
snd_ac97_codec         98464  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
pcmcia                 39212  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_ali15x3             8964  0 
bcm43xx               126824  0 
xpad                    9988  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_ali1535             8324  0 
ieee80211softmac       31360  1 bcm43xx
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
i2c_core               22656  3 i2c_ec,i2c_ali15x3,i2c_ali1535
ieee80211              34760  2 bcm43xx,ieee80211softmac
ali_agp                 8064  1 
agpgart                35400  2 drm,ali_agp
psmouse                38920  0 
serio_raw               7940  0 
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54020  12 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
ieee80211_crypt         7040  1 ieee80211
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd_page_alloc         10888  1 snd_pcm
af_packet              23816  2 
joydev                 10816  0 
evdev                  11008  6 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
usbhid                 26592  0 
hid                    27392  1 usbhid
alim15x3               13196  0 [permanent]
floppy                 59524  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
natsemi                29408  0 
generic                 5124  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  4 xpad,usbhid,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


it will jump to the command line but it goes so fast that i cant read anything...so it normally shuts off about 10 secs after the gui dissappears.

other than that i have only installed automatix2 and about half the progs off there....and i do remember seeinga  cpu overheating error, but i never get that when im hard wired..im hard wired all day at work and never once has my comp died.  installed list im not really sure how to get you that, its a hp pavilion ze5185

i just now i have a p4 2.4ghz
ati mobility m6
768 mbs ram
and my dlink card

i do use a fan pad with my laptop also

dmesg log is
[http://www7.rapidupload.com/d.php?file=dl&filepath=30537]("http://www7.rapidupload.com/d.php?file=dl&filepath=30537")

---

### Post by dannyboy79 on 2007-06-12
well you have 2 wireless cards within your laptop so why don't you first try to blacklist the one you don't use. currently it's loading a wifi driver for your atheros chipset which is what Ihave and works out of the box, ath_pci, for the AR5212, then you also have the driver bcm43xx loading for your Broadcom wirless chip that's most likely built into your laptop. can you diable it within your bios maybe? This is just a start.  also, can you please be more specific about it crashing, all you stated above was "it will jump to the command line but it goes so fast that i cant read anything...so it normally shuts off about 10 secs after the gui dissappears." and something about you seeing a overheating issue but I need more specifics.

For some reason wireless cards have been the cause of freezing and other stuff and the solution has been to blacklist it so as I said we'll start there.

I checked out your dmesg, it looks alright other than it loading oth wifi modules which hopefully is the cause but I can't say for sure. It's also very weird that it doesn't shut off when using hard wired which again leads me to the wireless issue.

---

### Post by mxgods on 2007-06-13
Ok, i physically removed the internal card, which i forgot i still had in my computer (has no antenna), and i let my computer run all night long as a test and it seemed to work great, no problems thus far.  So im pretty sure that that fixed my problem, thanks a bunch.

---

### Post by dannyboy79 on 2007-06-13
no problem, glad to have helped!! so which card did you remove??? let me see all the stuff I asked for AGAIN but make sure you restarted your machine so we see the new dmesg and lsmod, i am curious about this and would maybe like to post a helpful tip about mulitple wireless cards and what it can cause.

---

### Post by mxgods on 2007-06-13
mxg0d@mxg0d-laptop:~$ lspci -v
00:00.0 Host bridge: ALi Corporation M1671 Super P4 Northbridge [AGP4X,PCI and SDR/DDR] (rev 02)
        Flags: bus master, medium devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e0100000-e01fffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1000 [size=256]
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
        Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: medium devsel, IRQ 10
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1400 [size=256]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50010000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

00:0a.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50011000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 48000000-4bfff000 (prefetchable)
        Memory window 1: 4c000000-4ffff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0003000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 8000
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0008000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if b0)
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1800 [size=16]
        Capabilities: <access denied>

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
        Subsystem: Unknown device 3c08:9400
        Flags: bus master, medium devsel, latency 90, IRQ 11
        I/O ports at 1c00 [size=256]
        Memory at e0009000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 50000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 0029
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at e0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 (Rev B3,B5) Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 44000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

mxg0d@mxg0d-laptop:~$ lsusb
Bus 002 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  
mxg0d@mxg0d-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                31620  0 
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
container               5248  0 
dock                   10268  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  3 
snd_ali5451            24460  2 
snd_ac97_codec         98464  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ath_pci                97312  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
xpad                    9988  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39212  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  13 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3             8964  0 
i2c_ali1535             8324  0 
pcspkr                  4224  0 
psmouse                38920  0 
ali_agp                 8064  1 
agpgart                35400  2 drm,ali_agp
soundcore               8672  1 snd
i2c_core               22656  3 i2c_ec,i2c_ali15x3,i2c_ali1535
serio_raw               7940  0 
snd_page_alloc         10888  1 snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
af_packet              23816  8 
joydev                 10816  0 
evdev                  11008  6 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
usbhid                 26592  0 
hid                    27392  1 usbhid
alim15x3               13196  0 [permanent]
floppy                 59524  0 
natsemi                29408  0 
generic                 5124  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ohci_hcd               22532  0 
usbcore               134280  4 xpad,usbhid,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
mxg0d@mxg0d-laptop:~$ 

dmesg log is here
[http://www6.rapidupload.com/d.php?file=dl&filepath=37654](http://www6.rapidupload.com/d.php?file=dl&filepath=37654)

i removed the dell wireless card

---

### Post by dannyboy79 on 2007-06-13
yeah, that's the one within the broadcom chipset. atheros work out of the box all the time, they use the madwifi drivers.

---


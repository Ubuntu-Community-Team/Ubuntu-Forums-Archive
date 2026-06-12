---
title: "Another laptop wireless issue... Toshiba A215-S7413"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by atx85 on 2007-12-18
Hi everyone! First I would like to say hello!!

I purchased my Toshiba Satellite A215-S7413 laptop on Black Friday. I figured since I have my desktop a dual-boot between Vista and Gutsy (spending most of the time in Gutsy) I would go ahead and make the transition to Gutsy on my laptop.

Well, for about the last 3 weeks I've been trying to get wireless working on this laptop. I have had absolutely no success. All of my friends (including Linux fans) have told me to give up, I can't get it working. Well, I'm sure you guys understand that this has now become my 'obsession/goal' and I don't want to give up until I figure it out, haha!!

Considering there is absolutely _no_ support from Toshiba for Linux I've run out of ideas. I've been surfing the forums for about a year now and never had to post because I could _always_ find the help I needed. So, in advance I wanted to thank everyone out there!!

I was curious to know though, if I do an **lspci** this is the result....

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Correct me if I'm wrong, but there is nothing in there about any wireless card? 

**lsmod**

Module                  Size  Used by
fglrx                 656352  11 
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               5504  0 
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
joydev                 11328  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
uvcvideo               48644  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
sdhci                  18828  0 
pcspkr                  4224  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               28420  1 sdhci
serio_raw               8068  0 
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
psmouse                39952  0 
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
k8temp                  6656  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ati_agp                10124  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 fglrx,ati_agp
evdev                  11136  5 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ata_generic             8452  0 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ehci_hcd               36492  0 
r8169                  32260  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
atiixp                  7056  0 [permanent]
ide_core              116804  2 ide_cd,atiixp
ohci_hcd               22916  0 
usbcore               138632  4 uvcvideo,ehci_hcd,ohci_hcd
ahci                   23300  3 
libata                125168  2 ata_generic,ahci
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

**lsusb**

Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  

**lspci | grep -i net**

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

Just a few things that might help you guys. I've looked through so many threads and still no success, maybe it's just me doing something wrong?! Any other information, **please** let me know!! Thank you again!

---

### Post by kevdog on 2007-12-19
Do you know if you internal wireless card is connected via the PCI bus of USB??

What is this device listed under USB??

Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

---

### Post by atx85 on 2007-12-19
To be honest I'm not sure if that's the case with my wireless card. How can I go about checking?

I'm unsure as to what that device is. I do not have any peripheral devices attached to the laptop. The only added thing is my Ethernet cable.

I was thinking, the physical switch is definitely turned to the 'On' position. However, I don't notice any of my Fn keys to properly work. Could this be the root of the problem? Though, the card would still show up, just appear to be off?

---

### Post by kevdog on 2007-12-19
Google is your friend -- use it to find out about your computer :)

---

### Post by buccaneere on 2007-12-19
There's a recent thread in here somewhere about targeting the wireless card driver (ndiswrapper, I think) to a USB address, as opposed to a PCI address.

Look for toshiba threads

Here it is
[http://ubuntuforums.org/showthread.php?t=619955&highlight=toshiba&page=4](http://ubuntuforums.org/showthread.php?t=619955&highlight=toshiba&page=4)

see post 40. Run [HTML]lsusb[/HTML] to get address of your card

---

### Post by atx85 on 2007-12-20
Thanks for that thread! It was quite a help. However, I've come to the conclusion that it's just so much easier to just buy a new card... ugh who knows... damnit I want Ubuntu working on this laptop!!

---

### Post by The Tronyx on 2007-12-21
> **atx85 said:**
> Thanks for that thread! It was quite a help. However, I've come to the conclusion that it's just so much easier to just buy a new card... ugh who knows... damnit I want Ubuntu working on this laptop!!

I have that exact same laptop and I wish I hadn't bought it.  The ATI drivers have been hell as apparently the X1200 isn't supported for some reason.  In addition to that, your hda_intel support for sound is terrible and if your situation ends up anything like mine, you may get sound but using headphones will not mute the speaker.  And on a final note, that realtek wireless card is a brick.  I ended up buying a D-link usb wireless and it's worked great.  

I didn't come here to complain about laptops though, simply to let you know that getting that Realtek working has been a major problem for a lot of people.  Many people who found some modified drivers also had trouble authenticating to encrypted networks (myself included)

If you ever need someone to share troubleshooting with, feel free to send me a PM.:)

---

### Post by buccaneere on 2007-12-26
> **2point0 said:**
> I have that exact same laptop and I wish I hadn't bought it.  The ATI drivers have been hell as apparently the X1200 isn't supported for some reason.  In addition to that, your hda_intel support for sound is terrible and if your situation ends up anything like mine, **[COLOR="Red"]you may get sound but using headphones will not mute the speaker[/COLOR]**.  And on a final note, that realtek wireless card is a brick.  I ended up buying a D-link usb wireless and it's worked great.  

I didn't come here to complain about laptops though, simply to let you know that getting that Realtek working has been a major problem for a lot of people.  Many people who found some modified drivers also had trouble authenticating to encrypted networks (myself included)

If you ever need someone to share troubleshooting with, feel free to send me a PM.:)

I would pay to be able know how to configure that!

That would allow my desktop speakers to play, while the other sound output is still hardwired to the entertainment system!

Right now, I've got the mini-port split with a mini Y-splitter; one to the desktop speakers, and the other through the floor to the entertainer. Pain in the backside:(

---

### Post by maldaer on 2008-03-08
A less than elegant solution I found.  I would like to preface that this is the only way I could get it all working without buying new hardware.

1) Strip all pre installed software from the vista OS.  This has all fully functional drivers for everything.

2) Install VMWare Server (free)

3) Make VM sizes large enough (hard disk, mem etc)

4) Install Ubuntu into VM

You now have wireless etc. courtesy of Vista drivers.

Its not ideal (I just found out that Lenovo laptops are inadvertently 100% Ubuntu compatible) but it got it all working as I wanted.

---


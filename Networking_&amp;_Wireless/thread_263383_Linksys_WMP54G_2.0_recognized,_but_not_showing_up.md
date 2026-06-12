---
title: "Linksys WMP54G 2.0 recognized, but not showing up"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by MatRitz on 2006-09-23
Hello,

I'm having a strange problem

Ubuntu 2.6.15-26-386

wireless card is recognized in device manager, but not showing up in "networking"

lsmod lists a rt2500

lshw doesn't worl (IDE, then nothing)

Mainboard is K9N Neo, NVidia M1697 Chipset

The card worked without a problem with an older Mainboard.

Pretty much all the other posts I have found assumed that the card showed up in System/Administration/Networking, but unfortunately mine doesn't.

I cannot help but think that I have missed a very simple fix since the card should "just work" TM.

lspci lists a RaLink... Network Controller

Thanks in advance for your help, I am in a hurry right now, that's why the post is very much in telegram style.

I'll be back about 20:00 CET to answer further questions

---

### Post by JebusWankel on 2006-09-23
Does it work with the live cd?

---

### Post by MatRitz on 2006-09-24
If "Live CD" means starting from the 6.06.1 CD directly, then no. I'm downloading a 5.10 Live CD right now just because I have no better idea what to do next.

---

### Post by MatRitz on 2006-09-24
Here's the console output produced by some commands, let me know if I missed something important or if I need to post some logs as well

sudo lspci

0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1697
0000:00:01.0 PCI bridge: ALi Corporation: Unknown device 524b
0000:00:02.0 PCI bridge: ALi Corporation: Unknown device 524c
0000:00:03.0 PCI bridge: ALi Corporation: Unknown device 524d
0000:00:04.0 PCI bridge: ALi Corporation: Unknown device 524e
0000:00:11.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
0000:00:12.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 60)
0000:00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:14.0 0403: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 01)
0000:00:15.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 10)
0000:00:15.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:16.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
0000:00:16.1 IDE interface: ALi Corporation ULi M5288 SATA
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)
0000:05:0c.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

sudo iwconfig

lo        no wireless extensions.

sit0      no wireless extensions.

sudo ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:41572 (40.5 KiB)  TX bytes:41572 (40.5 KiB)


sudo lsmod

Module                  Size  Used by
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
af_packet              22920  0
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   13440  2
fat                    53020  1 vfat
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
psmouse                36100  0
uli526x                17684  0
rt2500                176612  0
serio_raw               7300  0
snd_hda_intel          18964  0
snd_hda_codec         154672  1 snd_hda_intel
i2c_ali1535             7428  0
i2c_ali15x3             7940  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
pcspkr                  2180  0
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i2c_core               21904  3 i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
rtc                    13492  0
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
ali_agp                 7168  0
agpgart                34888  1 ali_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  3 ehci_hcd,ohci_hcd
ahci                   17284  0
libata                 78992  1 ahci
scsi_mod              139496  2 ahci,libata
ide_cd                 33028  4
cdrom                  38560  1 ide_cd
ide_disk               17664  7
generic                 5124  0
alim15x3               12428  0 [permanent]
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

sudo lshw

IDE (stays like that for several minutes, I end it sooner or later)

network-admin
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

then the graphical user interface pops up, only the modem connection shows up

In Device Manager, an M5249 HTT to PCI Bridge shows up, as a subpoint the Ralink RT2500 802.11 Cardbus, identified with OEM product: Linksys WMP54G 2.0 PCI Adapter

Hope this helps a bit

---

### Post by MatRitz on 2006-09-30
As I should have guessed in the first place, the problem was with the Mainboard, not the wireless card.

I installed the current Kernel for the Edgy Eft Beta from the alternate install CD, with this Kernel the Wireless PCI card works as it should.

---


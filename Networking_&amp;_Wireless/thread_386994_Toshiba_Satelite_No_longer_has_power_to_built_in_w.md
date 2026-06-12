---
title: "Toshiba Satelite No longer has power to built in wireless"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by timmahhny on 2007-03-17
I am now experiencing problems with my Toshiba Satelite M45 laptop. It was running fine, no problems, until about two or three days ago, at which point the wireless would not work. 
 The problem is that the wireless is not getting power. I have tried to turn it on with the buttons on the laptop, which did not work. 
 Command line sudo ifup eth1
did not do anything.
Tried everything that I could think of. 
Looked for two days for anyone else in this forum, experiencing the same problems, and so far, it seems I am the only one. 
 
 I am going to try hooking up the ethernet cable and reinstall some of the wireless stuff in an attempt to see if that will help.

 I did read on another post of someone having problems with their wireless when they updated a kernel, but they did not post if the power was going to the built-in card or not. 
Thanks for your help!!
timmahhny

---

### Post by gradedcheese on 2007-03-17
No power to it?  Unless you own some test equipment, I don't believe you :)

Anyhow... lets try some troubleshooting:

```

iwconfig

```

...lists eth1 as having wireless extensions?

```

iwlist eth1 scan

```

...performs a successful scan?  What chipset is this, Intel ipw wireless?

---

### Post by timmahhny on 2007-03-18
> No power to it? Unless you own some test equipment, I don't believe you

I wouldn't believe it either if it did not happen to me. When I run wireless assistant, I get a message box that asks me if I want to turn the "radio on". I click on yes and nothing happens. 

```
iwconfig
```
Return says:
eth1 Radio off ESSID: off /any
Power management off no signal level.
Pretty much everything says off.

```
iwlist eth1 scan
```
Produces no scan results.

 Could it have been an update?
I used synaptic package manager, typed in wireless and reinstalled all programs, except scanners, that I could find; that did not help either. 

 I can turn on the eth0 which is the ethernet hook up, if that helps you out. 

 This is very interesting.
Thanks for your reply hope the above helps some.
timmahhny:lolflag:

---

### Post by Austin_KW on 2007-03-18
lspci?
lsmod?

---

### Post by timmahhny on 2007-03-18
```
lspci
```
lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)
0000:05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:05:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

```
lsmod
```
  lsmod
Module                  Size  Used by
arc4                    2048  2
ieee80211_crypt_wep     5120  1
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
nfsd                  228612  13
exportfs                6272  1 nfsd
lockd                  62216  2 nfsd
sunrpc                150332  8 nfsd,lockd
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
acpi_cpufreq            6792  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 acpi_cpufreq,cpufreq_stats
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265856  12
af_packet              22920  6
dm_mod                 58936  1
sk98lin               201812  0
pcmcia                 40508  0
md_mod                 72532  0
joydev                 10048  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
ipw2200               107308  0
tsdev                   8000  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
sdhci                  14848  0
mmc_core               30104  1 sdhci
rtc                    13492  0
sky2                   39940  0
sbp2                   24196  0
psmouse                36100  0
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
parport_pc             35780  0
lp                     11844  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
serio_raw               7300  0
parport                36296  3 ppdev,parport_pc,lp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
sr_mod                 16932  0
sg                     37920  0
evdev                   9856  2
cdrom                  38560  1 sr_mod
ext3                  135944  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  3 ehci_hcd,uhci_hcd
sd_mod                 19984  3
generic                 5124  0
ata_piix               11012  4
ahci                   17284  0
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sr_mod,sg,sd_mod,ahci,libata
thermal                13576  0
processor              23360  2 acpi_cpufreq,thermal
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

I have been looking at other posts and have tried many things.
```
iwlist eth1 scan
```
Returns:
No scan results
I figure this had to have happened after an update was done. 
 But am unsure of what I would have to do to "undo" that update.

 I tired this as well:
```
sudo iwconfig eth1 power on
```
Returns:
Error for wireless request "Set Power Management" (8B2C)
Set failed on device eth1 ; Input/output error

I don't know if this added information will help.

 Still very interesting.....

---

### Post by Austin_KW on 2007-03-18
Your card is alive enough to read the type and load the drivers. anthing interesting/errors from dmesg |grep ipw2200

---

### Post by chili555 on 2007-03-18
This is from ipw2200.sourceforge.net: > For the device level files, see /sys/bus/pci/drivers/ipw2200:

rf_kill

	read - 
	0 = RF kill not enabled (radio on)
	1 = SW based RF kill active (radio off)
	2 = HW based RF kill active (radio off)
	3 = Both HW and SW RF kill active (radio off)
	write -
	0 = If SW based RF kill active, turn the radio back on
	1 = If radio is on, activate SW based RF kill

	NOTE: If you enable the SW based RF kill and then toggle the HW
  	based RF kill from ON -> OFF -> ON, the radio will NOT come back on
You might also check in the BIOS to see if there is an option to disable the hardware switch I'm assuming you have.

---

### Post by timmahhny on 2007-03-18
> For the device level files, see /sys/bus/pci/drivers/ipw2200:

 I don't have that file. Should I create one?
I have read this in the some posts, but assumed that it did not apply to my laptop, as they were all talking about other cards. 

 I will try the bios first, then continue to look for the solution to this problem.
Thanks for the tip. 
I will try it and get back to you.
Agian for everyone who has helped, thanks
timmahhny

---

### Post by timmahhny on 2007-03-19
:lolflag: 
**Want to hear something real, real, real, funny?**

 This is a very good lesson to everyone.

** [COLOR="Red"]KNOW YOUR MACHINE!!!!![/COLOR]**

 After a week of trying to fix the problem I went and reinstalled Windows back onto
my mothers laptop. (She is 80). And loves Ubuntu!!
 Windows would also not connect to the interent. I asked her if she had dropped the laptop. Yeah, she did, but a long time ago.
 Long story short, on the Toshiba there is a tiny little switch that she had turned off.

 Wham back online. 

 How stupid am I?
Man is that embar**assing**!!!!!!
:lolflag:

 Thanks for everyone's help!!! This is a very good learning lesson!!!
Timmahhny

---


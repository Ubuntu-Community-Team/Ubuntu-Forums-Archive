---
title: "Compiz Cube"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-04-08
Hi,
After a resetting of the xserver this morning, I find that the compiz cube isn't working. So I reset the desks to '4' and had a look in advanced desktop effects but everything was as I'd left it yesterday. I tried to start compiz in terminal, dunno if that's possible but I got this:

```
gen@gen:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

please could someone offer some advice:)
TFC
Robin

---

### Post by Michael.Godawski on 2009-04-08
hi hungryOrb,

what is your video card? An ATI?

Have you tried to install the xserver-xgl package?
```
sudo apt-get install xserver-xgl
```

---

### Post by hungryOrb on 2009-04-08
> **Michael.Godawski said:**
> hi hungryOrb,

what is your video card? An ATI?

Have you tried to install the xserver-xgl package?
```
sudo apt-get install xserver-xgl
```

Thanks! I'll try that right away!
It's an nvidia laptop GO! card. Sec, here's my lspci list:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

8400M GS, not good :/
Ok, the thing just finished installing, I'll restart and reply :D
Thanks again.

---

### Post by hungryOrb on 2009-04-08
Avast!
It didn't work ;(

The terminal still says:
```
gen@gen:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```
when trying to run compiz. Not sure if I actually want to do that though! Just want my desktop cube to work, so I can drag apps to another bench and make everything easier :D
Everything was fine yesterday, and the new kernel and maybe some other update today reset stuff, and not sure how to get back. Eek.

Any advice would be nice.
TFC
Rb

---

### Post by hungryOrb on 2009-04-08
Ahh.. Also when i try to enable 'Normal' or 'Extra' visual effects under the simple 'Appearance' window, then I get a popup:

```
Desktop effects could not be enabled
```

OH MY!

---

### Post by neu2buntu on 2009-04-08
i think this post [here]("http://ubuntuforums.org/archive/index.php/t-596927.html") will help you especially the part about "whitelisting" your driver

---

### Post by hungryOrb on 2009-04-08
> **neu2buntu said:**
> i think this post [here]("http://ubuntuforums.org/archive/index.php/t-596927.html") will help you especially the part about "whitelisting" your driver

Thanks for reply!
I checked the whitelist and it already features an flgxr element. 
Can't help thinking that the problem is super simple and is going to be a couple of clicks away.. :(
The question is, what did the update do, which could've upset the graphic settings.?

---

### Post by tarps87 on 2009-04-08
> **hungryOrb said:**
> Thanks for reply!
I checked the whitelist and it already features an flgxr element. 
Can't help thinking that the problem is super simple and is going to be a couple of clicks away.. :(
The question is, what did the update do, which could've upset the graphic settings.?

Update, did it include a kernel update/upgrade. Did you have to install extra graphic drivers? If you did you will need to install them again, try booting the older kernel (the entry should still be in the grub menu list). You can also check under restricted drivers under system -> administration

---

### Post by neu2buntu on 2009-04-08
...maybe nautilus(file browse) to your /etc/x11/xorg.conf file/files and see if there is a backup which was made before the update and look for any changes to compare.... the backups will be dated something like 20090407142732 as in year/month/day/hour/min/sec ...   so will look like xorg.conf.20090407123456

---

### Post by hungryOrb on 2009-04-08
> **tarps87 said:**
> Update, did it include a kernel update/upgrade. Did you have to install extra graphic drivers? If you did you will need to install them again, try booting the older kernel (the entry should still be in the grub menu list). You can also check under restricted drivers under system -> administration

Thanks for replies guys, yes included kernel update. I just clicked update and it did it all automatically. I can try booting 19, I was using that for a long time.
The Hardware Drivers box tells me that there are "No proprietary drivers in use on this system."

Regarding the x11 backups, there are 2. Both from yesterday :)
They are quite different! :O
I'm not sure if that means anything though..
Is it ok to post both?

---

### Post by tarps87 on 2009-04-09
It is but can you wrap them in code tags. Looking at you graphics card the driver should already be built into the kernel, the xorg config should show us if it is using it

---

### Post by hungryOrb on 2009-04-09
First the oldest one:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

And then the current (xorg.conf):

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
``` 

Really thanks for looking :)

---

### Post by neu2buntu on 2009-04-09
from the older .conf file one thing that looks it could be the problem 
```
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
``` was loading the drivers ,whereas i dont see this in the new .conf file.... things to try
(1)check modules already loaded to look for these 3 above... ```
lsmod
```
(2)manually load these drivers if they are not listed to see if they are in the kernel ```
gksu modprobe glx
``` ```
gksu modprobe GLcore
``` ```
gksu modprobe v4l
``` ,if no error returns they are being loaded .... then try compiz again!!!     and if all is well with this just remove your newest .conf file and reboot!!!   
(3)another option is to rename the latest .conf file and reboot (you may have to boot in repair mode to use the next backup xorg.conf file, not sure)
(4) yet another possibility if part(2) happens to work.... add the 3 modules to /etc/modules where they will be loaded at boot............  hope some/any of this helps!!!!!:lolflag:

---

### Post by hungryOrb on 2009-04-09
Wow man.. thanks!
This is what happened:

```
gen@gen:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
snd_rtctimer            4640  1 
ipv6                  267908  17 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
joydev                 13120  0 
psmouse                40336  0 
pcspkr                  4224  0 
serio_raw               7940  0 
evdev                  13056  7 
sdhci                  19076  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_hda_intel         346136  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
battery                14212  0 
ac                      6916  0 
iwl3945                89840  0 
snd_seq_dummy           4868  0 
iwlwifi_mac80211      219108  1 iwl3945
snd_seq_oss            35584  0 
cfg80211               15112  1 iwlwifi_mac80211
snd_seq_midi            9376  0 
sky2                   47620  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  0 
output                  4736  1 video
snd                    56996  17 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0 
intel_agp              25492  0 
soundcore               8800  2 snd
agpgart                34760  1 intel_agp
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  4 
ata_piix               19588  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ata_generic             8324  0 
ahci                   28548  3 
libata                159600  4 pata_acpi,ata_piix,ata_generic,ahci
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 
gen@gen:~$ gksu modprobe glx
gen@gen:~$ gksu modprobe GLcore
FATAL: Module GLcore not found.gen@gen:~$ gksu modprobe v4l
FATAL: Module v4l not found.gen@gen:~$ 
gen@gen:~$ 

```

The first mod was loaded successfully, no errors, and the 2nd two failed. 
Thanks very much for help!

---

### Post by neu2buntu on 2009-04-10
searched a bit there and it seems nvidia doesnt use GLcore... 

did the "glx" driver get compiz up and running...if so just either just add it to /etc/modules (no need for the other 2 drivers) and if you have already swapped your xorg.conf files around you could either leave it alone or comment out "#" or remove the other 2 drivers to load it wont really matter as "glx" is the first one to load,the other 2 will just be for fallback on error....

---

### Post by hungryOrb on 2009-04-13
Desktop effects could still not be enabled after that no..
But don't worry! I'm going to reinstall when 9.04 launches. 

I just hope.. that, one day I can begin to understand what does what!

---


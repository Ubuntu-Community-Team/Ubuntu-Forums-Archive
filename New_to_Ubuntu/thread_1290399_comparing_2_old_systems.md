---
title: "comparing 2 old systems"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-10-13
I have two old systems laying around.
I'm thinking about combining thm into one good system.

I have 2 things I'd like to do...

1. do some kind of bechmark test.
Where would i find that.

2. look at the "system" equivalent.
Where can i find, the processor speed, sys bus, ram,  ect.

---

### Post by lavinog on 2009-10-13
#1 Phoronix test suite should be available in the repos.
or use the live cd:
[http://www.phoronix-test-suite.com/?k=pts_desktop_live](http://www.phoronix-test-suite.com/?k=pts_desktop_live)

#2
```
lshw
```
Lists hardware

---

### Post by wlraider70 on 2009-10-13
That code spit out so much data that my terminal couldn't even save it.

is there a way filter a bit or just capture all the info?

---

### Post by diesch on 2009-10-13
hardinfo (not installed by default) gives you a nice GUI with system information and some CPU benchmarks.

---

### Post by wlraider70 on 2009-10-13
OK would anyone care to way in on the better system.
they seem rather close. 


Dell intell

```


Computer
Summary
Computer
Processor	Intel(R) Pentium(R) 4 CPU 2.00GHz
Memory	767MB (192MB used)
Operating System	Ubuntu 9.04
User Name	luke (Luke)
Date/Time	Tue 13 Oct 2009 04:00:16 PM PDT
Display
Resolution	1920x1200 pixels
OpenGL Renderer	Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	EMU10K1 - SBLive! Value [CT4780]
Input Devices
Power Button (FF)	
Sleep Button (CM)	
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Dell Premium USB Optical Mouse	
PC Speaker	
Printers
No printers found	
IDE Disks
SCSI Disks
ATA MAXTOR 6L080J4	
HL-DT-ST CD-RW GCE-8400B	
Memorex TRAVELDRIVE 005B	
Operating System
Version
Kernel	Linux 2.6.28-15-generic (i686)
Compiled	#52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009
C Library	GNU C Library version 2.9 (stable)
Distribution	Ubuntu 9.04
Current Session
Computer Name	luke-media
User Name	luke (Luke)
Home Directory	/home/luke
Desktop Environment	GNOME 2.26 (session name: this-is-deprecated)
Misc
Uptime	7 hours, 25 minutes
Load Average	0.50, 0.16, 0.05
Kernel Modules
Loaded Modules
nls_iso8859_1	
nls_cp437	
vfat	VFAT filesystem support
fat	
usb_storage	USB Mass Storage driver for Linux
binfmt_misc	
radeon	ATI Radeon
drm	DRM shared core routines
bridge	
stp	
bnep	Bluetooth BNEP ver 1.3
input_polldev	Generic implementation of a polled input device
video	ACPI Video Driver
output	Display Output Switcher Lowlevel Control Abstraction
lp	
snd_emu10k1_synth	Routines for control of EMU10K1 WaveTable synth
snd_emux_synth	Routines for control of EMU WaveTable chip
snd_seq_virmidi	Virtual Raw MIDI client on Sequencer
snd_seq_midi_emul	Advanced Linux Sound Architecture sequencer MIDI emulation.
snd_emu10k1	EMU10K1
snd_ac97_codec	Universal interface for Audio Codec '97
ac97_bus	
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
snd_page_alloc	Memory allocator for ALSA system.
snd_util_mem	Generic memory management routines for soundcard memory allocation
snd_hwdep	Hardware dependent layer
snd_seq_dummy	ALSA sequencer MIDI-through client
snd_seq_oss	OSS-compatible sequencer module
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
ppdev	
dcdbas	Dell Systems Management Base Driver (version 5.6.0-3.2)
emu10k1_gp	EMU10k1 gameport driver
snd	Advanced Linux Sound Architecture driver for soundcards.
pcspkr	PC Speaker beeper driver
iTCO_wdt	Intel TCO WatchDog Timer Driver
iTCO_vendor_support	Intel TCO Vendor Specific WatchDog Timer Driver Support
gameport	Generic gameport layer
soundcore	Core sound module
intel_agp	
agpgart	AGP GART driver
shpchp	Standard Hot Plug PCI Controller Driver
parport_pc	PC-style parallel port driver
parport	
usbhid	USB HID core driver
sundance	Sundance Alta Ethernet driver
mii	MII hardware support library
dmfe	Davicom DM910X fast ethernet driver
floppy	
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
Boots
Boots
Tue Oct 13 08:35 - 16:00 (07:25)	Kernel 2.6.28-15-generi
Mon Oct 12 09:23 - 19:29 (10:05)	Kernel 2.6.28-11-generi
Languages
Available Languages
en_AU.utf8	English locale for Australia
en_BW.utf8	English locale for Botswana
en_CA.utf8	English locale for Canada
en_DK.utf8	English locale for Denmark
en_GB.utf8	English locale for Britain
en_HK.utf8	English locale for Hong Kong
en_IE.utf8	English locale for Ireland
en_IN	English language locale for India
en_NG	English locale for Nigeria
en_NZ.utf8	English locale for New Zealand
en_PH.utf8	English language locale for Philippines
en_SG.utf8	English language locale for Singapore
en_US.utf8	English locale for the USA
en_ZA.utf8	English locale for South Africa
Filesystems
Mounted File Systems
/dev/sda1	71.3 GiB total, 64.8 GiB free
tmpfs	374.6 MiB total, 374.6 MiB free
proc	0.0 B total, 0.0 B free
sysfs	0.0 B total, 0.0 B free
varrun	374.6 MiB total, 374.5 MiB free
varlock	374.6 MiB total, 374.6 MiB free
udev	374.6 MiB total, 374.5 MiB free
tmpfs	374.6 MiB total, 374.5 MiB free
devpts	0.0 B total, 0.0 B free
fusectl	0.0 B total, 0.0 B free
lrm	374.6 MiB total, 372.5 MiB free
securityfs	0.0 B total, 0.0 B free
binfmt_misc	0.0 B total, 0.0 B free
gvfs-fuse-daemon	0.0 B total, 0.0 B free
Shared Directories
SAMBA
NFS
Display
Display
Resolution	1920x1200 pixels
Vendor	The X.Org Foundation
Version	1.6.0
Monitors
Monitor 0	1920x1200 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
DRI2	
GLX	
Generic Event Extension	
MIT-SCREEN-SAVER	
MIT-SHM	
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-DRI	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	Tungsten Graphics, Inc.
Renderer	Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
Version	1.3 Mesa 7.4
Direct Rendering	Yes
Network Interfaces
Network Interfaces
lo	Sent 0.00MiB, received 0.00MiB (127.0.0.1)
eth0	Sent 2.29MiB, received 65.34MiB (10.10.10.64)
eth1	Sent 0.00MiB, received 0.00MiB
pan0	Sent 0.00MiB, received 0.00MiB
Users
Human Users
luke	Luke
System Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
syslog	
klog	
hplip	HPLIP system user
avahi-autoipd	Avahi autoip daemon
gdm	Gnome Display Manager
saned	
pulse	PulseAudio daemon
messagebus	
polkituser	PolicyKit
avahi	Avahi mDNS daemon
haldaemon	Hardware abstraction layer
mythtv	
Devices
Processor
Processor
Name	Intel(R) Pentium(R) 4 CPU 2.00GHz
Family, model, stepping	15, 2, 4 (Pentium 4)
Vendor	Intel Corp.
Configuration
Cache Size	512kb
Frequency	1993.47MHz
BogoMIPS	3986.94
Byte Order	Little Endian
Features
FDIV Bug	no
HLT Bug	no
F00F Bug	no
Coma Bug	no
Has FPU	yes
Capabilities
fpu	Floating Point Unit
vme	Virtual 86 Mode Extension
de	Debug Extensions - I/O breakpoints
pse	Page Size Extensions (4MB pages)
tsc	Time Stamp Counter and RDTSC instruction
msr	Model Specific Registers
pae	Physical Address Extensions
mce	Machine Check Architeture
cx8	CMPXCHG8 instruction
apic	Advanced Programmable Interrupt Controller
sep	Fast System Call (SYSENTER/SYSEXIT)
mtrr	Memory Type Range Registers
pge	Page Global Enable
mca	Machine Check Architecture
cmov	Conditional Move instruction
pat	Page Attribute Table
pse36	36bit Page Size Extensions
clflush	Cache Line Flush instruction
dts	Debug Store
acpi	Thermal Monitor and Software Controlled Clock
mmx	MMX technology
fxsr	FXSAVE and FXRSTOR instructions
sse	SSE instructions
sse2	SSE2 (WNI) instructions
ss	Self Snoop
ht	HyperThreading
tm	Thermal Monitor
up	
pebs	
bts	
Memory
Memory
Total Memory	767180 kB
Free Memory	414784 kB
Buffers	17576 kB
Cached	160812 kB
Cached Swap	25204 kB
Active	108052 kB
Inactive	206804 kB
Active(anon)	31796 kB
Inactive(anon)	106900 kB
Active(file)	76256 kB
Inactive(file)	99904 kB
Unevictable	0 kB
Mlocked	0 kB
High Memory	0 kB
Free High Memory	0 kB
Low Memory	767180 kB
Free Low Memory	414784 kB
Virtual Memory	2241028 kB
Free Virtual Memory	2181308 kB
Dirty	148 kB
Writeback	0 kB
AnonPages	119956 kB
Mapped	23608 kB
Slab	16160 kB
SReclaimable	8832 kB
SUnreclaim	7328 kB
PageTables	2172 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	2624616 kB
Committed_AS	429928 kB
VmallocTotal	242424 kB
VmallocUsed	8016 kB
VmallocChunk	227828 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	4096 kB
DirectMap4k	40192 kB
DirectMap4M	745472 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge 
PCI bridge	Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge 
USB Controller	Intel Corporation 82801DB/DBL/DBM 
USB Controller	Intel Corporation 82801DB/DBL/DBM 
USB Controller	Intel Corporation 82801DB/DBL/DBM 
USB Controller	Intel Corporation 82801DB/DBM 
PCI bridge	Intel Corporation 82801 PCI Bridge 
ISA bridge	Intel Corporation 82801DB/DBL 
IDE interface	Intel Corporation 82801DB 
SMBus	Intel Corporation 82801DB/DBL/DBM 
VGA compatible controller	ATI Technologies Inc Radeon R100 QD [Radeon 7200]
Ethernet controller	Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet 
Ethernet controller	D-Link System Inc DL10050 Sundance Ethernet
Multimedia audio controller	Creative Labs SB Live! EMU10k1 
Input device controller	Creative Labs SB Live! Game Port 
USB Devices
Printers
Printers
No printers found	
Battery
No batteries
No batteries found on this system	
Sensors
Input Devices
Input Devices
Power Button (FF)	
Sleep Button (CM)	
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Dell Premium USB Optical Mouse	
PC Speaker	
Storage
IDE Disks
SCSI Disks
ATA MAXTOR 6L080J4	
HL-DT-ST CD-RW GCE-8400B	
Memorex TRAVELDRIVE 005B	
Benchmarks
CPU ZLib
CPU ZLib
This Machine	0.000
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561
CPU Fibonacci
CPU Fibonacci
This Machine	7.381
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682
CPU MD5
CPU MD5
This Machine	24.394
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998
CPU SHA1
CPU SHA1
This Machine	29.384
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776
CPU Blowfish
CPU Blowfish
This Machine	26.843
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713
FPU Raytracing
FPU Raytracing
This Machine	36.049
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647


```


Hp AMD

```


Computer
Summary
Computer
Processor	AMD Athlon(tm) XP 2800+
Memory	703MB (298MB used)
Operating System	Ubuntu 9.04
User Name	luke (Luke Monahan)
Date/Time	Tue 13 Oct 2009 04:18:27 PM PDT
Display
Resolution	1024x768 pixels
OpenGL Renderer	Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	VIA8237 - VIA 8237
Input Devices
Power Button (FF)	
Power Button (CM)	
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Dell Dell USB Mouse	
PC Speaker	
Printers (CUPS)
Business-Inkjet-1100	(Default)
DESKJET-950C	
hp-business-inkjet-1100	
lpcs-printer	
IDE Disks
SCSI Disks
ATA WDC WD800BB-22FJ	
LITE-ON COMBO SOHC-4832K	
Generic USB SD Reader	
Generic USB CF Reader	
Generic USB SM Reader	
Generic USB MS Reader	
Operating System
Version
Kernel	Linux 2.6.28-13-generic (i686)
Compiled	#44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009
C Library	GNU C Library version 2.9 (stable)
Distribution	Ubuntu 9.04
Current Session
Computer Name	LPCC.LOCAL
User Name	luke (Luke Monahan)
Home Directory	/home/luke
Desktop Environment	GNOME 2.26 (session name: this-is-deprecated)
Misc
Uptime	4 minutes
Load Average	1.70, 0.82, 0.32
Kernel Modules
Loaded Modules
binfmt_misc	
via	VIA Unichrome / Pro
drm	DRM shared core routines
bridge	
stp	
bnep	Bluetooth BNEP ver 1.3
video	ACPI Video Driver
output	Display Output Switcher Lowlevel Control Abstraction
sbp2	IEEE-1394 SBP-2 protocol driver
lp	
snd_via82xx	VIA VT82xx audio
gameport	Generic gameport layer
snd_mpu401_uart	Routines for control of MPU-401 in UART mode
snd_via82xx_modem	VIA VT82xx modem
snd_seq_dummy	ALSA sequencer MIDI-through client
snd_ac97_codec	Universal interface for Audio Codec '97
arc4	ARC4 Cipher Algorithm
snd_seq_oss	OSS-compatible sequencer module
ac97_bus	
snd_pcm_oss	PCM OSS emulation for ALSA.
ecb	ECB block cipher algorithm
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_seq_device	ALSA sequencer device management
b43	Broadcom B43 wireless driver
snd_pcm	Midlevel PCM code for ALSA.
ppdev	
pcspkr	PC Speaker beeper driver
snd_timer	ALSA timer interface
snd_page_alloc	Memory allocator for ALSA system.
usb_storage	USB Mass Storage driver for Linux
usbhid	USB HID core driver
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
i2c_viapro	vt82c596 SMBus driver
usblp	USB Printer Device Class driver
mac80211	IEEE 802.11 subsystem
cfg80211	wireless configuration support
led_class	LED Class Interface
input_polldev	Generic implementation of a polled input device
shpchp	Standard Hot Plug PCI Controller Driver
via_agp	
parport_pc	PC-style parallel port driver
parport	
agpgart	AGP GART driver
via_rhine	VIA Rhine PCI Fast Ethernet driver
mii	MII hardware support library
ohci1394	Driver for PCI OHCI IEEE-1394 controllers
ieee1394	
ssb	Sonics Silicon Backplane driver
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
Boots
Boots
Tue Oct 13 16:14 - 16:18 (00:04)	Kernel 2.6.28-13-generi
Languages
Available Languages
en_AU.utf8	English locale for Australia
en_BW.utf8	English locale for Botswana
en_CA.utf8	English locale for Canada
en_DK.utf8	English locale for Denmark
en_GB.utf8	English locale for Britain
en_HK.utf8	English locale for Hong Kong
en_IE.utf8	English locale for Ireland
en_IN	English language locale for India
en_NG	English locale for Nigeria
en_NZ.utf8	English locale for New Zealand
en_PH.utf8	English language locale for Philippines
en_SG.utf8	English language locale for Singapore
en_US.utf8	English locale for the USA
en_ZA.utf8	English locale for South Africa
Filesystems
Mounted File Systems
/dev/sda1	72.1 GiB total, 64.1 GiB free
tmpfs	343.4 MiB total, 343.4 MiB free
proc	0.0 B total, 0.0 B free
sysfs	0.0 B total, 0.0 B free
varrun	343.4 MiB total, 343.1 MiB free
varlock	343.4 MiB total, 343.4 MiB free
udev	343.4 MiB total, 343.2 MiB free
tmpfs	343.4 MiB total, 343.3 MiB free
devpts	0.0 B total, 0.0 B free
fusectl	0.0 B total, 0.0 B free
lrm	343.4 MiB total, 341.2 MiB free
securityfs	0.0 B total, 0.0 B free
binfmt_misc	0.0 B total, 0.0 B free
gvfs-fuse-daemon	0.0 B total, 0.0 B free
Shared Directories
SAMBA
NFS
Display
Display
Resolution	1024x768 pixels
Vendor	The X.Org Foundation
Version	1.6.0
Monitors
Monitor 0	1024x768 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
DRI2	
GLX	
Generic Event Extension	
MIT-SCREEN-SAVER	
MIT-SHM	
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-DRI	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	VIA Technology
Renderer	Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE
Version	1.2 Mesa 7.4
Direct Rendering	Yes
Network Interfaces
Network Interfaces
lo	Sent 0.00MiB, received 0.00MiB (127.0.0.1)
eth0	Sent 0.02MiB, received 0.33MiB (10.10.10.72)
wmaster0	Sent 0.00MiB, received 0.00MiB
wlan0	Sent 0.00MiB, received 0.00MiB
pan0	Sent 0.01MiB, received 0.00MiB
Users
Human Users
luke	Luke Monahan
mark	
comp3	
System Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
syslog	
klog	
messagebus	
polkituser	PolicyKit
hplip	HPLIP system user
avahi-autoipd	Avahi autoip daemon
avahi	Avahi mDNS daemon
gdm	Gnome Display Manager
haldaemon	Hardware abstraction layer
pulse	PulseAudio daemon
saned	
xrdp	
Devices
Processor
Processor
Name	AMD Athlon(tm) XP 2800+
Family, model, stepping	6, 10, 0 (AMD Athlon XP/MP (Barton))
Vendor	AuthenticAMD
Configuration
Cache Size	512kb
Frequency	2082.97MHz
BogoMIPS	4165.94
Byte Order	Little Endian
Features
FDIV Bug	no
HLT Bug	no
F00F Bug	no
Coma Bug	no
Has FPU	yes
Capabilities
fpu	Floating Point Unit
vme	Virtual 86 Mode Extension
de	Debug Extensions - I/O breakpoints
pse	Page Size Extensions (4MB pages)
tsc	Time Stamp Counter and RDTSC instruction
msr	Model Specific Registers
pae	Physical Address Extensions
mce	Machine Check Architeture
cx8	CMPXCHG8 instruction
apic	Advanced Programmable Interrupt Controller
sep	Fast System Call (SYSENTER/SYSEXIT)
mtrr	Memory Type Range Registers
pge	Page Global Enable
mca	Machine Check Architecture
cmov	Conditional Move instruction
pat	Page Attribute Table
pse36	36bit Page Size Extensions
mmx	MMX technology
fxsr	FXSAVE and FXRSTOR instructions
sse	SSE instructions
syscall	SYSCALL and SYSEXIT instructions
mmxext	Extended MMX Technology
3dnowext	Extended 3DNow! Technology
3dnow	3DNow! Technology
up	
Memory
Memory
Total Memory	703240 kB
Free Memory	135648 kB
Buffers	22404 kB
Cached	269756 kB
Cached Swap	0 kB
Active	355420 kB
Inactive	146052 kB
Active(anon)	215016 kB
Inactive(anon)	8 kB
Active(file)	140404 kB
Inactive(file)	146044 kB
Unevictable	8 kB
Mlocked	8 kB
High Memory	0 kB
Free High Memory	0 kB
Low Memory	703240 kB
Free Low Memory	135648 kB
Virtual Memory	1309256 kB
Free Virtual Memory	1309256 kB
Dirty	1492 kB
Writeback	0 kB
AnonPages	209372 kB
Mapped	47584 kB
Slab	20076 kB
SReclaimable	13060 kB
SUnreclaim	7016 kB
PageTables	2720 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	1660876 kB
Committed_AS	524592 kB
VmallocTotal	307256 kB
VmallocUsed	5880 kB
VmallocChunk	292340 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	4096 kB
DirectMap4k	57280 kB
DirectMap4M	663552 kB
PCI Devices
PCI Devices
Host bridge	VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
PCI bridge	VIA Technologies, Inc. VT8237/VX700 PCI Bridge
Network controller	Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller 
Communication controller	Agere Systems V.92 56K WinModem 
FireWire (IEEE 1394)	VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller 
IDE interface	VIA Technologies, Inc. VIA VT6420 SATA RAID Controller 
IDE interface	VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE 
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller	VIA Technologies, Inc. USB 2.0 
ISA bridge	VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
Multimedia audio controller	VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller 
Communication controller	VIA Technologies, Inc. AC'97 Modem Controller 
Ethernet controller	VIA Technologies, Inc. VT6102 [Rhine-II] 
VGA compatible controller	VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] 
USB Devices
Printers
Printers (CUPS)
Business-Inkjet-1100	(Default)
DESKJET-950C	
hp-business-inkjet-1100	
lpcs-printer	
Battery
No batteries
No batteries found on this system	
Sensors
ACPI Thermal Zone
THRM	52°C
Input Devices
Input Devices
Power Button (FF)	
Power Button (CM)	
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Dell Dell USB Mouse	
PC Speaker	
Storage
IDE Disks
SCSI Disks
ATA WDC WD800BB-22FJ	
LITE-ON COMBO SOHC-4832K	
Generic USB SD Reader	
Generic USB CF Reader	
Generic USB SM Reader	
Generic USB MS Reader	
Benchmarks
CPU ZLib
CPU ZLib
This Machine	0.000
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561
CPU Fibonacci
CPU Fibonacci
This Machine	4.234
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682
CPU MD5
CPU MD5
This Machine	58.639
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998
CPU SHA1
CPU SHA1
This Machine	61.565
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776
CPU Blowfish
CPU Blowfish
This Machine	19.052
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713
FPU Raytracing
FPU Raytracing
This Machine	25.248
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647

```

Im thinking I'll take the hard drive and ram from the dell and make it the 2nd in the hp. I havent check the ram size but i think it will fit.

---

### Post by ace007 on 2009-10-13
After just a quick scan...the HP seems like a better starting place. Try to take the RAM and HDD from the dell and add it to the HP.

And I resent the `old system' tag. Either of those make my box look ancient.

---

### Post by lavinog on 2009-10-13
> **wlraider70 said:**
> That code spit out so much data that my terminal couldn't even save it.

is there a way filter a bit or just capture all the info?

```

lshw>filename.txt

```
redirects the output to a text file named filename.txt

---

### Post by lavinog on 2009-10-13
I would use memtest (part of the boot menu in the live cd or the install) to see which processor has a larger L2 cache, That would make a huge difference

---

### Post by wlraider70 on 2009-10-13
I'm vaguly familar with the memtest. 
Is there an option to test L2 or is it automatic.

---

### Post by tgalati4 on 2009-10-13
It's automatic.

cat /proc/cpuinfo

---


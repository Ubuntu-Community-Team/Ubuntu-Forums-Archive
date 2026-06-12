---
title: "No internet connection on fresh install (16.04 LTS)"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by jfcarrer on 2017-09-08
Today i installed Lubuntu 16.04 LTS on my Lenovo Thinkcentre M58, but for my surprise it can't access the internet for some reason. (it worked fine under Linux Mint 18.2, which was installed before)

The computer is connected to my modem via a regular cat 5e ethernet cable.

Image of the screen:

[https://imgur.com/rANfu5H](https://imgur.com/rANfu5H)

p.s. the network connection list was empty, i manually created that ethernet connection, nothing changed.

System report:

```


Computer
********




Summary
-------


-Computer-
Processor        : 2x Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
Memory        : 866MB (264MB used)
Operating System        : Ubuntu 16.04.2 LTS
User Name        : jorno (jorno)
Date/Time        : Sex 08 Set 2017 18:40:18 BRT
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
Audio Adapter        : SAA7134 - SAA7134
-Input Devices-
 Power Button
 Power Button
 Video Bus
 Microsoft  Microsoft Basic Optical Mouse v2.0
   USB Keyboard
   USB Keyboard
 saa7134 IR (Avermedia PCI M733A
 HDA Intel Front Mic
 HDA Intel Rear Mic
 HDA Intel Line
 HDA Intel Line Out
 HDA Intel Front Headphone
-Printers-
No printers found
-SCSI Disks-
ATA WDC WD1600AAJS-0
ATAPI DVD A  DH16AAS


Operating System
----------------


-Version-
Kernel        : Linux 4.8.0-36-generic (x86_64)
Compiled        : #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017
C Library        : Unknown
Default C Compiler        : Unknown
Distribution        : Ubuntu 16.04.2 LTS
-Current Session-
Computer Name        : jorno-ThinkCentre-M58p
User Name        : jorno (jorno)
Home Directory        : /home/jorno
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 6 minutes
Load Average        : 0,00, 0,00, 0,00


Kernel Modules
--------------


-Loaded Modules-
saa7134_alsa
tda18271        : NXP TDA18271HD analog / digital tuner driver
snd_hda_codec_analog        : Analog Devices HD-audio codec
snd_hda_codec_generic        : Generic HD-audio codec parser
tda8290        : Philips/NXP TDA8290/TDA8295 analog IF demodulator driver
ir_lirc_codec        : LIRC IR handler bridge
tuner        : device driver for various TV and TV+FM radio tuners
snd_hda_intel        : Intel HDA driver
input_leds        : Input -&gt; LEDs Bridge
lirc_dev        : LIRC base driver module
snd_hda_codec        : HDA codec core
rc_avermedia_m733a_rm_k6
snd_hda_core        : HD-audio bus
saa7134        : v4l2 driver module for saa7130/34 based TV cards
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
tveeprom        : i2c Hauppauge eeprom decoder driver
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
rc_core
ppdev
gpio_ich        : GPIO interface for Intel ICH series
v4l2_common        : misc helper functions for v4l2 device drivers
videobuf2_dma_sg        : dma scatter/gather memory handling routines for videobuf2
videobuf2_memops        : common memory handling routines for videobuf2
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
videobuf2_v4l2        : Driver helper framework for Video for Linux 2
snd_rawmidi        : Midlevel RawMidi code for ALSA.
videobuf2_core        : Media buffer core framework
videodev        : Device registrar for Video4Linux drivers v2
snd_seq        : Advanced Linux Sound Architecture sequencer.
media        : Device node registration for media drivers
snd_seq_device        : ALSA sequencer device management
snd_timer        : ALSA timer interface
coretemp        : Intel Core temperature monitor
serio_raw        : Raw serio driver
snd        : Advanced Linux Sound Architecture driver for soundcards.
soundcore        : Core sound module
lpc_ich        : LPC interface for Intel ICH
mei_me        : Intel(R) Management Engine Interface
mei        : Intel(R) Management Engine Interface
parport_pc        : PC-style parallel port driver
parport
mac_hid
autofs4
hid_generic        : HID generic driver
usbhid        : USB HID core driver
hid
i915        : Intel Graphics
psmouse        : PS/2 mouse driver
ahci        : AHCI SATA low-level driver
i2c_algo_bit        : I2C-Bus bit-banging algorithm
libahci        : Common AHCI SATA low-level routines
drm_kms_helper        : DRM KMS helper
syscopyarea        : Generic copyarea (sys-to-sys)
floppy
sysfillrect        : Generic fill rectangle (sys-to-sys)
sysimgblt        : 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
fb_sys_fops        : Generic file read (fb in system RAM)
drm        : DRM shared core routines
video        : ACPI Video Driver
fjes        : FUJITSU Extended Socket Network Device Driver
pata_acpi        : SCSI low-level driver for ATA in ACPI mode
wmi        : ACPI-WMI Mapping Driver


Boots
-----


-Boots-
Fri Sep 8 1:34        : 44..8.0-36-generic|stilll
Fri Sep 8 1:44        : 44..8.0-36-generic|stilll
Fri Sep 8 1:39        : 44..8.0-36-generic|stilll
Fri Sep 8 1:52        : 44..8.0-36-generic|-
Fri Sep 8 1:37        : 44..8.0-36-generic|-
Fri Sep 8 1:31        : 44..8.0-36-generic|-


Languages
---------


-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AG.utf8        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IN        : English language locale for India
en_IN.utf8        : English language locale for India
en_NG        : English locale for Nigeria
en_NG.utf8        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa
en_ZM        : English locale for Zambia
en_ZM.utf8        : English locale for Zambia
en_ZW.utf8        : English locale for Zimbabwe
pt_BR.utf8        : Portuguese locale for Brasil


Filesystems
-----------


-Mounted File Systems-
udev    /dev    0,00 % (402,6 MiB of 402,6 MiB)    
tmpfs    /run    3,89 % (81,4 MiB of 84,7 MiB)    
/dev/sda1    /    6,80 % (135,8 GiB of 145,7 GiB)    
tmpfs    /dev/shm    0,00 % (423,3 MiB of 423,3 MiB)    
tmpfs    /run/lock    0,08 % (5,0 MiB of 5,0 MiB)    
tmpfs    /sys/fs/cgroup    0,00 % (423,3 MiB of 423,3 MiB)    
tmpfs    /run/user/1000    0,01 % (84,6 MiB of 84,7 MiB)    


Display
-------


-Display-
Resolution        : 1920x1080 pixels
Vendor        : The X.Org Foundation
Version        : 1.18.4
-Monitors-
Monitor 0        : 1920x1080 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
DRI3
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
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
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No


Environment Variables
---------------------


-Environment Variables-
USER        : jorno
LANGUAGE        : pt_BR:
XDG_SEAT        : seat0
XDG_SESSION_TYPE        : x11
SSH_AGENT_PID        : 864
SHLVL        : 0
HOME        : /home/jorno
DESKTOP_SESSION        : Lubuntu
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-uSa7APhALt,guid=26c4913beac3aec9b0ac97ef59b30ced
MANDATORY_PATH        : /usr/share/gconf/Lubuntu.mandatory.path
LOGNAME        : jorno
DEFAULTS_PATH        : /usr/share/gconf/Lubuntu.default.path
XDG_SESSION_ID        : c2
PATH        : /home/jorno/bin:/home/jorno/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
GDM_LANG        : pt_BR
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR        : /run/user/1000
DISPLAY        : :0.0
LANG        : pt_BR.UTF-8
XDG_SESSION_DESKTOP        : Lubuntu
XAUTHORITY        : /home/jorno/.Xauthority
XDG_GREETER_DATA_DIR        : /var/lib/lightdm-data/jorno
SSH_AUTH_SOCK        : /tmp/ssh-N5h8urlDBCEx/agent.818
SHELL        : /bin/bash
GDMSESSION        : Lubuntu
XDG_VTNR        : 7
PWD        : /home/jorno
XDG_CONFIG_DIRS        : /etc/xdg/lubuntu:/etc/xdg/xdg-Lubuntu:/etc/xdg
XDG_DATA_DIRS        : /etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share/:/usr/share/
XDG_CURRENT_DESKTOP        : LXDE
_LXSESSION_PID        : 818
XDG_CONFIG_HOME        : /home/jorno/.config
XDG_MENU_PREFIX        : lxde-
SAL_USE_VCLPLUGIN        : gtk
QT_PLATFORM_PLUGIN        : lxqt
QT_QPA_PLATFORMTHEME        : lxqt


Users
-----


-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
nobody        : nobody
systemd-timesync        : systemd Time Synchronization
systemd-network        : systemd Network Management
systemd-resolve        : systemd Resolver
systemd-bus-proxy        : systemd Bus Proxy
syslog
_apt
messagebus
uuidd
lightdm        : Light Display Manager
ntp
whoopsie
dnsmasq        : dnsmasq
jorno        : jorno


Devices
*******




Processor
---------


-Processors-
Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz        : 2500,00MHz
Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz        : 1200,00MHz


Memory
------


-Memory-
Total Memory        : 866836 kB
Free Memory        : 404080 kB
MemAvailable        : 479016 kB
Buffers        : 27296 kB
Cached        : 198980 kB
Cached Swap        : 0 kB
Active        : 251300 kB
Inactive        : 142616 kB
Active(anon)        : 168660 kB
Inactive(anon)        : 45312 kB
Active(file)        : 82640 kB
Inactive(file)        : 97304 kB
Unevictable        : 32 kB
Mlocked        : 32 kB
Virtual Memory        : 912380 kB
Free Virtual Memory        : 912380 kB
Dirty        : 68 kB
Writeback        : 0 kB
AnonPages        : 161644 kB
Mapped        : 76672 kB
Shmem        : 46324 kB
Slab        : 39000 kB
SReclaimable        : 21460 kB
SUnreclaim        : 17540 kB
KernelStack        : 3744 kB
PageTables        : 10936 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 1345796 kB
Committed_AS        : 1132112 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 0 kB
VmallocChunk        : 0 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 75776 kB
ShmemHugePages        : 0 kB
ShmemPmdMapped        : 0 kB
CmaTotal        : 0 kB
CmaFree        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 62080 kB
DirectMap2M        : 835584 kB


PCI Devices
-----------


-PCI Devices-
Host bridge        : Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
VGA compatible controller        : Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Display controller        : Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
Communication controller        : Intel Corporation 4 Series Chipset HECI Controller (rev 03)
IDE interface        : Intel Corporation 4 Series Chipset PT IDER Controller (rev 03) (prog-if 85 [Master SecO PriO])
Serial controller        : Intel Corporation 4 Series Chipset Serial KT Controller (rev 03) (prog-if 02 [16550])
Ethernet controller        : Intel Corporation Device 0000 (rev 02)
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
Audio device        : Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
PCI bridge        : Intel Corporation 82801 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
ISA bridge        : Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
SATA controller        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
SMBus        : Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
Multimedia controller        : Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


USB Devices
-----------




Printers
--------


-Printers-
No printers found


Battery
-------


-No batteries-
No batteries found on this system


Sensors
-------


-Cooling Fans-
-Temperatures-
-Voltage Values-


Input Devices
-------------


-Input Devices-
 Power Button
 Power Button
 Video Bus
 Microsoft  Microsoft Basic Optical Mouse v2.0
   USB Keyboard
   USB Keyboard
 saa7134 IR (Avermedia PCI M733A
 HDA Intel Front Mic
 HDA Intel Rear Mic
 HDA Intel Line
 HDA Intel Line Out
 HDA Intel Front Headphone


Storage
-------


-SCSI Disks-
ATA WDC WD1600AAJS-0
ATAPI DVD A  DH16AAS


DMI
---


-BIOS-
Date        : 11/18/2008
Vendor        : LENOVO
Version        : 5CKT34AUS
-Board-
Name        : LENOVO
Vendor        : LENOVO


Resources
---------


-I/O Ports-
<tt>0000-0000 </tt>        : pnp 00:00
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>0000-0000 </tt>        : pnp 00:00
<tt>0000-0000 </tt>        : pnp 00:00
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>      0000-0000 </tt>        : GPIO interface for Intel ICH series
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>  0000-0000 </tt>        : Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
<tt>    0000-0000 </tt>        : AHCI SATA low-level driver
<tt>0000-0000 </tt>        : pnp 00:00
-Memory-
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>00000000-00000000 </tt>        : reserved
<tt>  00000000-00000000 </tt>        : reserved
<tt>    00000000-00000000 </tt>        : PCI Bus 0000:00
<tt>    00000000-00000000 </tt>        : PCI Bus 0000:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>          00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>          00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
<tt>        00000000-00000000 </tt>        : reserved
<tt>          00000000-00000000 </tt>        : pnp 00:00
<tt>      00000000-00000000 </tt>        : pnp 00:00
-DMA-
<tt> 2</tt>        : floppy
<tt> 4</tt>        : cascade


Network
*******




Interfaces
----------


-Network Interfaces-
lo    0,04MiB    0,04MiB    127.0.0.1    


IP Connections
--------------


-Connections-
127.0.0.1:123        0.0.0.0:*    udp    
0.0.0.0:123        0.0.0.0:*    udp    
::1:123        :::*    udp6    
:::123        :::*    udp6    


Routing Table
-------------


-IP routing table-


ARP Table
---------


-ARP Table-


DNS Servers
-----------


-Name servers-


Statistics
----------


-IP-
484        : Requests sent out
0        : Incoming packets discarded
0        : Incoming packets discarded
484        : Requests sent out
484        : Requests sent out
120        : Outgoing packets dropped
-ICMP-
240        : ICMP messages sent
0        : ICMP messages failed
240        : ICMP messages sent
0        : ICMP messages failed
-ICMPMSG-
-TCP-
3        : Resets sent
0        : Bad segments received.
3        : Resets sent
0        : Bad segments received.
0        : Bad segments received.
6        : Segments send out
6        : Segments send out
0        : Bad segments received.
0        : Bad segments received.
3        : Resets sent
-UDP-
0        : Packet receive errors
240        : Packets sent
0        : Packet receive errors
240        : Packets sent
-UDPLITE-
-TCPEXT-
0        : Packet headers predicted
-IPEXT-


Shared Directories
------------------


-SAMBA-
Cannot open /etc/samba/smb.conf
-NFS-


Benchmarks
**********




CPU Blowfish
------------


-CPU Blowfish-
<big><b>This Machine</b></big>    2500 MHz    6,932    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    


CPU CryptoHash
--------------


-CPU CryptoHash-
<big><b>This Machine</b></big>    2500 MHz    199,023    


CPU Fibonacci
-------------


-CPU Fibonacci-
<big><b>This Machine</b></big>    2500 MHz    3,107    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    


CPU N-Queens
------------


-CPU N-Queens-
<big><b>This Machine</b></big>    2500 MHz    9,057    


FPU FFT
-------


-FPU FFT-
<big><b>This Machine</b></big>    2500 MHz    3,406    


FPU Raytracing
--------------


-FPU Raytracing-
<big><b>This Machine</b></big>    2500 MHz    6,263    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647    



```

Same report on pastebin: [https://pastebin.com/FEtEzANZ](https://pastebin.com/FEtEzANZ)

HTML version of the same report is attached to this post in a zip file.

Thanks for your attention.

---

### Post by BenginM on 2017-09-09
Hiya , please share the output of the following commands under a CODE tag:

$ sudo lshw -C network

$ lspci -nnk | grep -iA2 eth

$ ifconfig -a

$ cat /etc/network/interfaces

---

### Post by jfcarrer on 2017-09-09
sudo lshw -C network

```
*-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fc600000-fc61ffff memory:fc627000-fc627fff ioport:1820(size=32)

```

lspci -nnk|grep -iA2 eth

```
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:0000] (rev 02)
    Subsystem: Intel Corporation Device [8086:0000]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 [8086:3a67] (rev 02)

```

ifconfig -a

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:54768 (54.7 KB)  TX bytes:54768 (54.7 KB)

```

cat /etc/network/interfaces

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by BenginM on 2017-09-10
Well, there is no kernel module driver loaded with the current kernel 4.8 , the Ethernet card driver would be e1000e , and the Ethernet NIC might be Intel 82567LM.

since you installed a day ago , you used the iso for Ubuntu 16.04.2 LTS , try using the updated 16.04.3 LTS [here]("http://releases.ubuntu.com/16.04/") , which should have a newer kernel and hopefully the driver for the NIC is loaded . 

I might be wrong! So, if you don't mind waiting, then wait for others to chime in.
please share the result with us. Thanks.

---

### Post by jfcarrer on 2017-09-12
Installed the 16.04.3 version, but the situation didn't change.

I also ran the commands again:

```
jorno@jorno-ThinkCentre-M58p:~$ sudo lshw -C network[sudo] password for jorno: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fc600000-fc61ffff memory:fc627000-fc627fff ioport:1820(size=32)




jorno@jorno-ThinkCentre-M58p:~$ lspci -nnk|grep -iA2 eth
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:0000] (rev 02)
    Subsystem: Intel Corporation Device [8086:0000]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 [8086:3a67] (rev 02)


jorno@jorno-ThinkCentre-M58p:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117344 (117.3 KB)  TX bytes:117344 (117.3 KB)


jorno@jorno-ThinkCentre-M58p:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

---

### Post by jeremy31 on 2017-09-12
I would try booting the Linux Mint ISO and see if that ethernet controller works.  I don't think the info from the lspci results is valid with [8086:0000] being the result for the main and subsytem ID but I doubt Linux Mint can change that

---

### Post by jfcarrer on 2017-09-13
Today i plugged in my phone to the computer and used USB tethering to get internet on it, so i was able to install the Intel CPU Microcode thing and run the Software Updater.

After doing this and restarting the machine, the ethernet connection was working perfectly, so some update between the last LTS and the current version available fixed this problem.


p.s. is there an update log where i can see exactly what was updated?

---


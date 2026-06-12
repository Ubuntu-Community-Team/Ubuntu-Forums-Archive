---
title: "How to install atheros driver from source code?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by kramer65 on 2009-10-06
Hello,

My wireless internet doesn't work so I looked what the problem was. After doing the command "lspci" i got the following line:

```
05:01.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01) 
```

So I searched for the drivers for my card and found the [madwifi-project]("http://madwifi-project.org/") which has open source drivers for Atheros cards. I don't really know what version of Atheros card I've got (any tips on how to find out..?), but I decided I would give it a try anyway. So I downloaded the tar.gz file. It has a file called "INSTALL" which explains how to install the driver. I got as far as running "make" on the terminal, but after this I am totally lost.

Could anybody help me out here? Any help appreciated!

[EDIT]
I just searched for a "madwifi deb", and found [this page]("http://www.marlow.dk/site.php/tech/madwifi"). However, I am totally lost after the first few commands.

---

### Post by mikeyphi on 2009-10-06
Read all about it here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

It can be difficult, especially since one tiny mistake in entering code in a terminal will cause the whole process to fail!
You've got to keep trying and make sure the data is input exactly as in the guide.

Good luck!

---

### Post by 3rdalbum on 2009-10-06
Madwifi goes into the kernel. Every version of the kernel changes, so a newer kernel will require the driver to be recompiled, so a "madwifi deb" will not be of any use unless you're running the exact correct kernel version.

You need the "linux-headers-generic" and "build-essential" packages, and I highly recommend the "nautilus-open-terminal" package. When you have those packages, right-click inside the extracted archive (the folder that has the "INSTALL" file) and choose "Open in Terminal".

Run these commands in the terminal:

```
./configure
make
sudo make install
```

Reboot.

The first command, "./configure", might not be necessary. The "make" command does the compiling, and the "sudo make install" copies the compiled driver into the necessary place. As root, of course, because it's a system-wide change.

When you upgrade your kernel, the new kernel will not work with the old driver. You would need to compile and install the driver again. The linux-headers-generic package will automatically bring in the new kernel headers, so you don't need to worry about keeping that up to date.

---

### Post by lkraemer on 2009-10-06
3rdalbum is correct.  I suggest you add a few lines because most likely
you are going to be compiling for a second time.....or third.....or just
doing an update of the madwifi drivers.

cd madwifi-hal-0.10.5.6-r4100-20090929
make clean
make
sudo make install
sudo modprobe ath_pci
echo ath_pci | sudo tee -a /etc/modules
sudo /etc/init.d/networking restart
sudo ifconfig ath0 up

lk

---

### Post by kramer65 on 2009-10-06
Wait, I just see all these replies above. I'll give it another try.. :-)

EDIT

Alright. I tried installing it using the tips from 3rd album. 
running ./configure gives me a message saying that the folder or file doesn't exist.
I then ran make and sudo make install and it all seemed to work. 

However, the wireless card still doesn't seem to be recognised. 

I also installed ndiswrapper which seems to make it possible to install windows drivers. However, I wouldn't know where to get that driver or how to install it using that system.. either.


Conclusion. I'm kinda lost again. Any tipes that would get me further in installing the correct driver..?

---

### Post by lkraemer on 2009-10-06
kraemer65,
If you asked for help in compiling and installing the madwifi drivers,
why would you proceed with installing ndiswrapper, and not have a clue
as to what windows driver would work, after you were finished?

I don't understand.....

Now you need to do this as we have taken a Giant step backwards.
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat/etc/modprobe.d/blacklist.conf

iwconfig

```
and post the results....

lk

---

### Post by 3rdalbum on 2009-10-06
My first thought was that your card might be damaged.

---

### Post by ptn107 on 2009-10-06
A much simpler method:

System -> Administration -> Hardware Drivers.  Enable the atheros chipset there.  That will use the madwifi ath_pci driver in favor of the ath5k one.

---

### Post by kramer65 on 2009-10-08
@lkraemer
I got a tip about ndiswrapper before, so I thought I would try that. I ran all the commands you gave and pasted the results below. I hope this tells you anything, since it is like Chinese to me.. :confused:
```
kramer@kramer-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:01.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01)
05:02.0 PCI bridge: Pericom Semiconductor Unknown device 8140
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

kramer@kramer-desktop:~$ lsusb
Bus 008 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 03f0:5c11 Hewlett-Packard 
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c043 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

kramer@kramer-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:c6:a4:92:3d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A ip=192.168.1.71 latency=0 module=atl1 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

kramer@kramer-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  268164  14 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
vboxnetflt             89736  0 
vboxdrv               116008  1 vboxnetflt
ppdev                  10372  0 
acpi_cpufreq           10796  4 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         346264  6 
wm8775                  6924  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
cx25840                28176  0 
snd_pcm                78724  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
ivtv                  140608  0 
i2c_algo_bit            7300  1 ivtv
joydev                 13120  0 
cx2341x                13444  1 ivtv
tveeprom               16656  1 ivtv
atl1                   36364  0 
nvidia               7106084  34 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
videodev               29440  1 ivtv
mii                     6400  1 atl1
usblp                  15872  0 
ath_pci               101024  0 
wlan                  207216  1 ath_pci
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               24832  12 wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,i2c_algo_bit,tveeprom,nvidia
v4l2_common            18304  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15492  2 ivtv,videodev
button                  9232  0 
evdev                  13056  4 
intel_agp              25492  0 
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath_hal               192592  1 ath_pci
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
agpgart                34760  2 nvidia,intel_agp
soundcore               8800  1 snd
ext3                  136968  4 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  7 
ata_piix               19588  5 
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            73792  0 
libusual               19236  1 usb_storage
pata_jmicron            7040  0 
pata_acpi               8320  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ahci                   28548  0 
ata_generic             8324  0 
libata                159728  5 ata_piix,pata_jmicron,pata_acpi,ahci,ata_generic
scsi_mod              151692  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  7 usblp,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36616  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

kramer@kramer-desktop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

kramer@kramer-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

@ ptn107
I already did that, and that looks fine. Have a look at the attached image..

---

### Post by lkraemer on 2009-10-08
Well, from here on you're in for some work.  I suspect that your version
is not supported, but google found this site that says it works.

[http://forum.soft32.com/linux/Unsupported-ath5k-card-alias-ftopict475166.html](http://forum.soft32.com/linux/Unsupported-ath5k-card-alias-ftopict475166.html)


The second link describes making ndiswrapper work for 64 bit.  It should work on 32 bit also.
I guess you can try the madwifi drivers first and if that doesn't work, you can always
use ndiswrapper.

Good luck..... it' over my head now....

lkraemer

---


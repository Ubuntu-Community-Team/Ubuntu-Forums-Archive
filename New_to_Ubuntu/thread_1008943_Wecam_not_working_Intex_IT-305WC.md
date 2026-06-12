---
title: "Wecam not working Intex IT-305WC"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by phoenix_abhi on 2008-12-12
Before making this thread I have searched and tried almost every thread related.
Intrepid x64, Intex IT-305WC (Z-Star Microelectronics corp. ZC0303)USB Webam. Following the details:

> abhi@phoenixabhi:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0a5c:2035 Broadcom Corp. BCM2035 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

> abhi@phoenixabhi:~$ lsmod
Module Size Used by
ipv6 314312 10
af_packet 29568 2
binfmt_misc 18700 1
i915 44544 2
drm 110304 3 i915
rfcomm 51104 2
bridge 64544 0
stp 11268 1 bridge
bnep 23168 2
sco 20612 2
l2cap 33280 16 rfcomm,bnep
ppdev 16904 0
acpi_cpufreq 16400 0
cpufreq_userspace 12420 0
cpufreq_stats 14468 0
cpufreq_powersave 10368 0
cpufreq_ondemand 16400 2
freq_table 13568 3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative 16392 0
wmi 15808 0
video 28948 0
output 11776 1 video
sbs 22288 0
sbshc 14592 1 sbs
pci_slot 13704 0
container 12288 0
battery 21128 0
iptable_filter 11520 0
ip_tables 28176 1 iptable_filter
x_tables 31752 1 ip_tables
ac 13448 0
lp 19588 0
snd_hda_intel 489264 2
snd_pcm_oss 52608 0
snd_mixer_oss 25088 1 snd_pcm_oss
evdev 20512 6
psmouse 51612 0
snd_pcm 99208 2 snd_hda_intel,snd_pcm_oss
serio_raw 14596 0
snd_seq_dummy 11524 0
snd_seq_oss 42368 0
btusb 21912 3
pcspkr 11136 0
snd_seq_midi 15872 0
bluetooth 70820 11 rfcomm,bnep,sco,l2cap,btusb
snd_rawmidi 34176 1 snd_seq_midi
snd_seq_midi_event 16768 2 snd_seq_oss,snd_seq_midi
snd_seq 67168 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 34320 2 snd_pcm,snd_seq
snd_seq_device 16404 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
parport_pc 44200 1
parport 50096 3 ppdev,lp,parport_pc
zc0301 60804 0
compat_ioctl32 18176 1 zc0301
videodev 46720 2 zc0301,compat_ioctl32
snd 79432 13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
v4l1_compat 24580 1 videodev
soundcore 16800 1 snd
snd_page_alloc 17680 2 snd_hda_intel,snd_pcm
button 15904 0
intel_agp 39280 1
shpchp 42140 0
pci_hotplug 39472 1 shpchp
iTCO_wdt 21072 0
iTCO_vendor_support 12420 1 iTCO_wdt
jfs 199248 2
sr_mod 24644 0
cdrom 47784 1 sr_mod
sd_mod 45864 5
crc_t10dif 10240 1 sd_mod
sg 45408 0
pata_acpi 13568 0
ata_piix 29444 4
ata_generic 14212 0
libata 200160 3 pata_acpi,ata_piix,ata_generic
scsi_mod 183160 4 sr_mod,sd_mod,sg,libata
dock 18464 1 libata
r8169 40196 0
ehci_hcd 48908 0
uhci_hcd 34336 0
usbcore 175376 5 btusb,zc0301,ehci_hcd,uhci_hcd
thermal 27424 0
processor 47800 2 acpi_cpufreq,thermal
fan 13576 0
fbcon 51200 0
tileblit 11264 1 fbcon
font 17152 1 fbcon
bitblit 14592 1 fbcon
softcursor 10496 1 bitblit
fuse 68288 5

I have tried the following also
> abhi@phoenixabhi:~$ sudo chmod a+rw /dev/video0
[sudo] password for abhi:
chmod: cannot access `/dev/video0': No such file or directory
abhi@phoenixabhi:~$ lsmod | grep video
video 28948 0
output 11776 1 video

Cheese not detected any Webcam. 
Camorama giving error
> Could not connect to Video device (/dev/video0). Please check connection

EasyCam2 detects the Cam as Vimicro 0x303b (same driver for Vista), failed to install drivers 
>  gksudo 'python /usr/share/EasyCam2/core.py --gtk'
GO !
ln: creating symbolic link `/lib/modules/2.6.27-9-generic/build/include/linux/config.h': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-9-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/share/EasyCam2/drivers/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/share/EasyCam2/drivers/gspca/gspca_core.o
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/share/EasyCam2/drivers/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2464: error: implicit declaration of function ‘video_usercopy’
/usr/share/EasyCam2/drivers/gspca/gspca_core.c: At top level:
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2605: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2610: error: unknown field ‘owner’ specified in initializer
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2610: warning: initialization from incompatible pointer type
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2612: error: unknown field ‘type’ specified in initializer
/usr/share/EasyCam2/drivers/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2770: error: implicit declaration of function ‘video_device_create_file’
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:2781: error: implicit declaration of function ‘video_device_remove_file’
/usr/share/EasyCam2/drivers/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/share/EasyCam2/drivers/gspca/gspca_core.c:4310: error: incompatible types in assignment
make[2]: *** [/usr/share/EasyCam2/drivers/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2




This web cam working under Vista. Please someone help. My main OS is Ubuntu Intrepid x64

---

### Post by phoenix_abhi on 2008-12-12
F***k,, no answer ???????????

---

### Post by phoenix_abhi on 2008-12-12
B u m p

---

### Post by phoenix_abhi on 2008-12-12
Someone pls answer

---

### Post by farlo144 on 2008-12-12
I've got the same exact problem.  I'm on a 64 bit Intrepid.  I'm trying to use the "Philips SPC 700 NC" Webcam.

---

### Post by phoenix_abhi on 2008-12-13
lsmod shows a little more now

> abhi@phoenixabhi:~$ lsmod | grep video
video                  28948  0 
output                 11776  1 video
videodev               46720  2 zc0301,compat_ioctl32
v4l1_compat            24580  1 videodev


---

### Post by phoenix_abhi on 2008-12-13
*bump*

---

### Post by farlo144 on 2008-12-13
FYI.   From what I've found, we're both trying to build easycam2 on Intrepid, which just doesn't work.  The "Official" easycam2 ubuntu page instructs to get 8.04 .deb files... so it's no wonder why they don't work on 8.10.

Apparently our webcams should work right out of the box, but something broke between 8.04 and 8.10.  Meaning, we shouldn't have to compile easycam2... 

The link below is a good starting point for finding links to a plethora of other similar bugs - webcams don't work on 8.10.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657/)

---

### Post by farlo144 on 2008-12-14
Hey man, I got this sorted out.  Download the following:

[http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2)

Untar it:
  tar xjvf tip.tar.bz2

Build it:
  make

Install it:
  sudo make install

Reboot, and you should be good to go.  If not, read up in the following link:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657)

---

### Post by phoenix_abhi on 2008-12-20
Can u explain more about the installation procedure ? I was used to windows way. How to Untar, Build and Install

---

### Post by buzz57 on 2010-04-06
> **farlo144 said:**
> Hey man, I got this sorted out.  Download the following:

[http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2)



Archive does not exist
Having issues with INTEX IT-305WC usb Webcam. no drivers

---

### Post by buzz57 on 2010-04-06
Using 9.10 had problem
Found my answer by installing cheese which picked up generic usb 2.0 video driver.
then to get it working in SKype needed to run following in applications..accesories..terminal..
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

[http://ubuntuforums.org/showthread.php?t=993262](http://ubuntuforums.org/showthread.php?t=993262) explains

---


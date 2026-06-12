---
title: "wireless driver ndiswrapper problem"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by mymaydayya on 2009-05-01
I'm so far following this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


In 3.2. Identifying Wireless Adapter
I typed lspci
Find "04:00.0 Network controller: RaLink Device 0781"

Then I typed lspci -n
Find "04:00.0 0280: 1814:0781"

So PCI (chipset) ID is 1814:0781

Now where can I find Windows driver corresponding to 1814:0781?

Help please

---

### Post by lkraemer on 2009-05-01
You aren't giving us any information to work with.

If you have Windows running on your computer, you most
likely had a LAN and Wifi card.  What is the Brand Name?
Is it a PCI or USB Dongle?  You obviously purchased the
Hardware and have the Drivers on CD or Floppy for Windows,
or have the website to download the updates.

That is your Hardware and you are going to have to dig deeper
to find out what you are using.

That said, Open a Terminal Window and DO:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 


```
Then post the output all, separated so we can see each grouping.

Having the hardware information will give you a clue as to using the
Windows Drivers for Wifi, or using just the firmware (by downloading),
or installing drivers like the MadWifi ones.

lkraemer

---

### Post by mymaydayya on 2009-05-02
*-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:52:94:6f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=140.112.248.174 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:7c:b2:14:38:96
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



--------------------------------------------------------------------

Module                  Size  Used by
usbhid                 39648  0 
hid                    58944  1 usbhid
ipv6                  314312  14 
af_packet              29568  2 
i915                   44928  2 
drm                   110304  3 i915
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  17032  0 
acpi_cpufreq           16400  1 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  1 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              12288  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ndiswrapper           253824  0 
parport_pc             44200  0 
lp                     19588  0 
parport                49968  3 ppdev,parport_pc,lp
joydev                 20736  0 
led_class              13192  0 
serio_raw              14596  0 
evdev                  20512  13 
psmouse                51612  0 
pcspkr                 11136  0 
uvcvideo               70024  0 
compat_ioctl32         18304  1 uvcvideo
videodev               46720  2 uvcvideo,compat_ioctl32
v4l1_compat            24580  2 uvcvideo,videodev
snd_hda_intel         492208  5 
snd_pcm_oss            52608  0 
snd_mixer_oss          25216  1 snd_pcm_oss
sdhci_pci              17024  0 
sdhci                  27396  1 sdhci_pci
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
mmc_core               67168  1 sdhci
snd_seq_dummy          11524  0 
snd_seq_oss            42496  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                21128  0 
ac                     13448  0 
wmi                    15808  0 
video                  29204  0 
output                 11776  1 video
button                 15904  0 
snd                    79432  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
intel_agp              39152  1 
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
loop                   26380  2 
sd_mod                 45864  2 
crc_t10dif             10240  1 sd_mod
sr_mod                 24644  0 
cdrom                  47656  1 sr_mod
sg                     45408  0 
ahci                   43148  1 
libata                201184  1 ahci
scsi_mod              183288  4 sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
r8169                  40452  0 
mii                    14592  1 r8169
ehci_hcd               49420  0 
uhci_hcd               34336  0 
usbcore               175760  6 usbhid,ndiswrapper,uvcvideo,ehci_hcd,uhci_hcd
thermal                27552  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 

----------------------------------------------------------------------
rt2860 : driver installed
	device (1814:0781) present

-----------------------------------------------------------------------

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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

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

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist rt2500usb
blacklist rt2500pci
blacklist rt2500
blacklist rt2570
blacklist rt73usb
blacklist rt73pci
blacklist rt73
blacklist rt61usb
blacklist rt61pci
blacklist rt61
blacklist rt2860
blacklist rt2860sta
blacklist rt2x00usb
blacklist rt2x00lib

--------------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

-------------------------------------------------------------------

What should I do next?

thanks

---

### Post by lkraemer on 2009-05-02
Well, with this information I did a SEARCH for...  RaLink Device 0781 & HOWTO:
and this thread popped up.  I'd suggest you read it through,
then compare what you have already done, with what might be
missing from this post.  You can Open a Terminal Window,
type History, and you can see what commands you have executed,
as compared to the new post.  It should get you going.


[http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+Device+0781+HOWTO%3A](http://ubuntuforums.org/showthread.php?t=563547&highlight=RaLink+Device+0781+HOWTO%3A)

lkraemer

---


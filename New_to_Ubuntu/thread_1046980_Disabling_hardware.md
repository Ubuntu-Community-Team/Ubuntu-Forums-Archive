---
title: "Disabling hardware"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by spidermagicat on 2009-01-21
I keep getting drawn to the absolute beginners thread for things that I expect to be blindingly obvious so sorry if that's the case :-)

My laptop has had a rough life. Recently the touchscreen broke. Now another problem cause by someone (not me >:-() ) shoving a mini SD card into the card reader and hacking it out very roughly with a piece of wire. 

Both devices are broken and I would like to disable them, especially the card reader as it now has the light on all the time and appears in nautilus as the ultimately useless USB Drive.

Both are registered as usb devices and here is my "lsusb" output with what I want to disable in bold

**Bus 002 Device 006: ID 058f:6366 Alcor Micro Corp. ** (the card reader)
**Bus 002 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen**
Bus 002 Device 004: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by emarkd on 2009-01-21
This one's probably not so obvious.  First, use the 'lsmod' command to list all the modules being loaded by the system.  Then, once you know which modules you don't want to load, add them to the /etc/modprobe.d/blacklist file and reboot.

---

### Post by spidermagicat on 2009-01-22
Thanks for the swift responce! I've done as you said for the touch screen as it was handily named "usbtouchscreen"but I have no idea what the card reader would be unless it's "usb_storage". I know I don't want to disable that as I often use usb memory sticks and things like that. The "lsmod" output is below. I have no real way of knowing if the touch screen is disabled apart from the fact that it's gone from the list.

The card reader has a light on the whole time and appears in the nautilus menu so I don't mind a little trial and error, any ideas what it could be?

Module                  Size  Used by
af_packet              29568  4 
vboxnetflt            109164  0 
vboxdrv              1707948  1 vboxnetflt
ppdev                  16904  0 
powernow_k8            23684  1 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  1 
cpufreq_powersave      10368  0 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
pci_slot               13704  0 
container              12288  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
ipt_REJECT             11776  1 
ipt_LOG                14468  4 
xt_limit               11268  4 
ipt_addrtype           11136  4 
xt_state               10752  2 
xt_tcpudp              11776  12 
xt_conntrack           13184  2 
ip6table_filter        11392  1 
ip6_tables             29712  1 ip6table_filter
ipv6                  314312  14 
nf_nat_irc             10880  0 
nf_conntrack_irc       14776  1 nf_nat_irc
nf_nat_ftp             11648  0 
nf_nat                 29080  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      24856  6 nf_nat
nf_conntrack_ftp       17720  1 nf_nat_ftp
nf_conntrack           84512  8 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         11520  1 
ip_tables              28176  1 iptable_filter
x_tables               31752  9 ipt_REJECT,ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
vhba                   18304  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
loop                   26380  0 
joydev                 20736  0 
uvcvideo               68616  0 
snd_hda_intel         489264  2 
compat_ioctl32         18176  1 uvcvideo
videodev               46720  2 uvcvideo,compat_ioctl32
v4l1_compat            24580  2 uvcvideo,videodev
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
btusb                  21912  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
bluetooth              70820  1 btusb
evdev                  20512  14 
serio_raw              14596  0 
snd_seq_dummy          11524  0 
psmouse                51612  0 
snd_seq_oss            42368  0 
video                  28948  9 
output                 11776  1 video
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt_tkip    18048  0 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
wl                   1085520  0 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
battery                21128  0 
wmi                    15808  0 
ac                     13448  0 
snd                    79432  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 13568  0 
button                 15904  0 
nvidia               8115824  26 
i2c_nforce2            15752  0 
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
i2c_core               36128  2 nvidia,i2c_nforce2
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  2 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usb_storage            92864  0 
libusual               31784  1 usb_storage
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
usbhid                 39776  0 
hid                    59072  1 usbhid
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sg                     45408  0 
sata_nv                35208  2 
ata_generic            14212  0 
pata_amd               22020  0 
pata_acpi              13568  0 
libata                200160  4 sata_nv,ata_generic,pata_amd,pata_acpi
scsi_mod              183160  6 vhba,usb_storage,sd_mod,sr_mod,sg,libata
ohci_hcd               34972  0 
ehci_hcd               48908  0 
dock                   18464  1 libata
forcedeth              68112  0 
usbcore               175376  8 uvcvideo,btusb,usb_storage,libusual,usbhid,ohci_hcd,ehci_hcd
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  1

---

### Post by linux_tech on 2009-01-22
To show cardreader name try ```
lsusb
```

---

### Post by spidermagicat on 2009-01-22
yes I have, :-)

It's "Bus 002 Device 006: ID 058f:6366 Alcor Micro Corp"

but I can't spot anything similar anywhere in the modules

---

### Post by spidermagicat on 2009-01-22
anyone else? Is there a way to disable hardware by ID number?

I've had a look and it's soldered to the motherboard so no luck there. I'm considering removing the touch screen as it's possible. means a little less protection for my LCD from knocks but I'll manage

---


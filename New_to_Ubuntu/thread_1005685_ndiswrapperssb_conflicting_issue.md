---
title: "ndiswrapper/ssb conflicting issue"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Dark006 on 2008-12-08
Hello again, I'm back with yet another headache inducing problem. I just posted yesterday ([http://ubuntuforums.org/showthread.php?t=1004882](http://ubuntuforums.org/showthread.php?t=1004882)) about an nVidia driver issue I was having. Turns out I had the newest kernel but wasn't running it:confused:. Once I got the new kernel running the driver worked fine. 

Now my other issue I'm having is that ndiswrapper no longer works for my wireless adapter. I've tried a complete un-install and re-install with no success.

When I run 
```
ndiswrapper -l
```
I get
```
bcmwl5 : driver installed
	device (14E4:4329) present (alternate driver: ssb)

```

I've been looking around on the internet for this issue and found that this SSB with ndiswrapper is a common problem. I've tried a few fixes that I've seen and none have work. 

Network Manager doesn't even give a "Show Wireless C```

```onnections" option or anything like that.

Here is the latest "fix" I've tried (located in /etc/init.d/wirelessfix.sh)
```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44

```
Which I then ran:
```
sudo update-rc.d wirelessfix.sh defaults
```
and restarted afterwards but still I can't get this thing to work.

Does anyone know of anything else I should try? Anyone run into this problem and manage to fix it? Any help is greatly appreciated.

---

### Post by SPr on 2008-12-08
Can you post the result of lsmod?

---

### Post by Dark006 on 2008-12-08
Here is the output of lsmod:
```

Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
b44                    35984  0 
ssb                    40580  1 b44
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
container              11520  0 
pci_slot               12552  0 
battery                18436  0 
ipt_LOG                13700  3 
xt_limit               10372  3 
ipt_addrtype           10496  4 
xt_state               10112  2 
xt_tcpudp              11008  7 
xt_conntrack           11904  2 
ip6table_filter        10624  1 
ip6_tables             21008  1 ip6table_filter
ipv6                  263972  21 
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_nat                 25368  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      21900  6 nf_nat
nf_conntrack_ftp       15652  1 nf_nat_ftp
nf_conntrack           72032  8 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         10752  1 
ip_tables              19600  1 iptable_filter
x_tables               22916  8 ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
snd_intel8x0           37532  2 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
joydev                 18368  0 
evdev                  17696  8 
usb_storage            81728  0 
libusual               27156  1 usb_storage
wl                   1076372  0 
psmouse                45200  0 
snd_seq_oss            38528  0 
ieee80211_crypt        13572  1 wl
serio_raw              13444  0 
snd_seq_midi           14336  0 
nvidia               6900560  0 
snd_rawmidi            29824  1 snd_seq_midi
i2c_core               31892  1 nvidia
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
intel_agp              33724  1 
agpgart                42184  2 nvidia,intel_agp
usbhid                 35840  0 
hid                    50560  1 usbhid
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  3 
ata_generic            12932  0 
8139cp                 27520  0 
pata_acpi              12160  0 
ohci1394               37936  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
8139too                31616  0 
mii                    13440  3 b44,8139cp,8139too
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fuse                   60828  3 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by SPr on 2008-12-08
I'm stuck. Hopefully someone else will come along and help you. Sorry.

---

### Post by Dark006 on 2008-12-08
*bump* 

Anyone have an idea?

---

### Post by adult swim on 2008-12-08
did you make the wirelessfix.sh executable before you stuck it in init.d?

---

### Post by Dark006 on 2008-12-08
Yup, I did 'sudo chmod 755 /etc/init.d/wirelessfix.sh' before typing 'sudo update-rc.d wirelessfix.sh defaults'. And whats kinda weird is that, when booting into the older kernel (where ndiswrapper works) it displays that "driver installed, device present", whereas in the newest kernel it gives that "alternate driver: ssb" message.

---

### Post by adult swim on 2008-12-08
run from a terminal ```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper

sudo modprobe ndiswrapper
```
then see if ndiswrapper -l still shows ssb as an alternate
EDIT: if you are using your wired internet connection on this machine and this doesnt get ndiswrapper working youll need to run ```
sudo modprobe b44
``` to get your ethernet back

---

### Post by Dark006 on 2008-12-09
@adult swim
I tried what you suggested, here is the output (after I modprobe -r everthing)

```

blake@linux-desktop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4329) present (alternate driver: ssb)
blake@linux-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
blake@linux-desktop:~$ 

```

---

### Post by bobnutfield on 2008-12-09
How did you install ndiswrapper?  This error appears when, even though ndiswrapper is installed, it is not compiled for the kernel you are using.

---

### Post by Dark006 on 2008-12-10
I installed ndisgtk, ndiswrapper-common, and ndiswrapper-utils-1.9 through Synpatic while booted into the newest kernel, but I'm still running the older one (2.6.24-19-generic) becuase ndiswrapper works with that one.

---

### Post by bobnutfield on 2008-12-10
Well, there is your problem.  You have installed ndiswrapper for a kernel you have not booted into.  Ndiswrapper must be used with the kernel it was compiled for.  If you will boot into the kernel that you installed ndiswrapper with, I believe you will get a different result.

---


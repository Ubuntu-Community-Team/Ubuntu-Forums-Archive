---
title: "LAN not working. (has a mind of its own?)"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by legomind on 2008-08-29
OK, Ive tried everything I possibly could think of, but to no avail. Heres the deal: Sometimes my internal wired lan card is not detected by the network manager. It will sometimes contain no option to connect to my wired network, somtimes it will; but when it does, it is grayed out and I can not click on it. The same goes for when I boot up with a network cable connected. It is just unpredictable. When I shutdown my computer I get these errors for a second or two:

ETH0: TX_MODE_ENABLE will not clear
bug#4: SoftLockup- CPU froze for 11s

Heres my setup:

for a while I dual booted windows xp, then I formatted my whole HD installed ubuntu hardy fresh and switched to xp in vmware. I enabled and disabled wake on lan and all of that but it still doesn't work. Ideas anyone?

I have a Latitude d600 (Wireless works just fine)

---

### Post by itsjareds on 2008-08-29
Are you sure when it is grayed out that you have unlocked it?

You might want to switch to another manager like Wicd. Someone told me to switch to that when my internet wasn't working, and it seemed to fix the problem. Network Manager sometimes changes more than you want to, while Wicd changes only what you tell it to.

---

### Post by legomind on 2008-08-31
I tried Wicd, but the same thing happens. I think is has somthing to do with the driver.

Any more ideas?

---

### Post by legomind on 2008-08-31
Help? :confused:

---

### Post by legomind on 2008-09-09
A reinstall of ubuntu dosnt help. 

lspci | grep -i 'ethernet'

sometimes returns:
	[INDENT]02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev ff)
[/INDENT]
sometimes nothing

ifconfig eth0

sometimes
	[INDENT]eth0      Link encap:Ethernet  HWaddr 00:0d:56:e7:d9:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 [/INDENT]
sometimes
[INDENT]eth0: error fetching interface information: Device not found[/INDENT]

---

### Post by sheagk0 on 2008-12-17
I've been having the same problem on my Dell Inspiron 600m.  My network card is a Broadcom NetXtreme BCM5705M.  The driver I'm using is tg3 version 3.86.  The only way to reliably fix this (though only for a short time) is to completely reboot--a huge pain, to say the least.

I did find this bug report, but there's been no activity on it for awhile:
[https://bugs.launchpad.net/ubuntu/+bug/234738](https://bugs.launchpad.net/ubuntu/+bug/234738)

---

### Post by Achetar on 2008-12-17
First: make sure it is enabled in the BIOS. (I have personally forgotten to enable netcards in the BIOS on my laptop and the trouble has no end until you check that). Not all BIOSs have an option to disable netcards, but most laptops do.

When it works do the following WHILE IT IS WORKING:

```

$ lsmod >> ~/working.mods
$ lspci >> ~/working.pci

```

While it is not working do the following:
```

$ lsmod >> ~/notworking.mods
$lspci >> ~/notworking.pci

```

And then post the files' (working.mods, notworking.mods, working.pci, notworking.pci) contents here (best if in quote blocks with appropriate titles so we can tell easily which is which).

It may be that sometimes a modules is being loaded and sometimes it isnt.

---

### Post by sheagk0 on 2008-12-17
Ok.  Here are the outputs.  Additionally, the grayed out "auto eth0" is no longer showing up when I left click on Network Manager.

working.mods:
```

Module                  Size  Used by
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
ipv6                  267780  8 
speedstep_centrino      9152  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
af_packet              23812  2 
pcmcia                 40876  0 
joydev                 13120  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
ipw2200               146120  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
yenta_socket           27276  4 
rsrc_nonstatic         13696  1 yenta_socket
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
evdev                  13056  6 
serio_raw               7940  0 
dcdbas                  9504  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
battery                14212  0 
ac                      6916  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36260  1 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                37832  3 ppdev,lp,parport_pc
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usb_storage            73664  0 
libusual               19108  1 usb_storage
ata_piix               19588  3 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
scsi_mod              151436  5 sg,sr_mod,sd_mod,usb_storage,libata
usbcore               146412  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

working.pci:
```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```


notworking.mods:
```

Module                  Size  Used by
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
usb_storage            73664  0 
libusual               19108  1 usb_storage
tun                    12672  0 
ipv6                  267780  8 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
af_packet              23812  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
pcmcia                 40876  0 
joydev                 13120  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
ipw2200               146120  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
yenta_socket           27276  4 
rsrc_nonstatic         13696  1 yenta_socket
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  19856  0 
output                  4736  1 video
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
evdev                  13056  6 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
dcdbas                  9504  0 
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
ac                      6916  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
intel_agp              25492  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
ata_generic             8324  0 
pata_acpi               8320  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```


notworking.pci:```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

---

### Post by Achetar on 2008-12-18
Apparently it's just plain disapearing. No modules are different. Different order, but they are all there. This means it is probably a hardware or kernel issue.Neither of which I can tell you much more about.

EDIT: The working.pci shows the network card, but the notworking.pci doesn't. Could you try one more thing? 
While it's working:
```

$ sudo ifconfig >> ~/working.ifconfig

```
While it's not working:
```

$sudo ifconfig >> ~/notworking.ifconfig

```

Same drill for posting. It probably won't reveal anything, but you never know. YOu may be getting the symptoms of a network card about to die.

---

### Post by sheagk0 on 2008-12-18
working.ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:11:43:43:96:0c  
          inet addr:165.82.108.17  Bcast:165.82.111.255  Mask:255.255.252.0
          inet6 addr: fe80::211:43ff:fe43:960c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:879998 (859.3 KB)  TX bytes:157375 (153.6 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:11:96:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108700 (106.1 KB)  TX bytes:108700 (106.1 KB)

```

notworking.ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:11:43:43:96:0c  
          inet addr:165.82.108.17  Bcast:165.82.111.255  Mask:255.255.252.0
          inet6 addr: fe80::211:43ff:fe43:960c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51589 errors:4294967149 dropped:4294967149 overruns:0 frame:4294966561
          TX packets:20096 errors:4294967149 dropped:0 overruns:0 carrier:0
          collisions:4294967149 txqueuelen:1000 
          RX bytes:30104147 (28.7 MB)  TX bytes:3355704 (3.2 MB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:11:96:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115811 (113.0 KB)  TX bytes:115811 (113.0 KB)

```

Based on the bug report that I posted above, I tried running rmmod tg3 and modprobe tg3.  This sometimes works and brings my network back.  Sometimes I have to restart, and sometime a restart doesn't bring it back either, so I suspect that the problem is with my driver.  I cannot find an alternative driver for my card, a Broadcom NetXtreme BCM5705M--does anyone have any recommendations?  I love Ubuntu, but this is such a pain that I'm thinking of going back to Windows (which sucks).

---

### Post by Achetar on 2008-12-19
Well, it looks like eth0 while not working is having a lot of collisions. Probably someone else on you network (?) has the same IP address that is causing the collisions (I think that is what that means, [citation needed]).

You could try using Wicd and setting up a static IP address instead of a dhcp'd one.

---

### Post by racerraul on 2009-02-25
Well I'm a new user and been doing some serious diggin around.

I had this same problem, where I had th unlock button in users & groups grayed out.

I found that through the add\remove app utility I didn't have Authorizations installed... once I istalled that, the problems managing users via the guy went away, although I had already man addusers and added them that way...

---


---
title: "ADDRCONF(NETDEV_UP): eth0: link is not ready"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by ensis2k on 2008-08-21
My network card is not working. How can I tell which kernel module matches my card so I can look for it in lsmod?

Kernel log tells me:
ADDRCONF(NETDEV_UP): eth0: link is not ready

lspci is:
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 6c)

```

lsmod is:
```

Module                  Size  Used by
3c59x                  40232  0 
agpgart                31024  3 drm,intel_agp
ata_generic             7044  0 
ata_piix               15748  2 
bluetooth              50920  4 rfcomm,l2cap
cdrom                  32796  1 sr_mod
drm                    73620  3 i915
ehci_hcd               28300  0 
evdev                  10752  1 
ext3                  118920  1 
fuse                   43284  5 
hid                    33092  1 usbhid
i915                   28416  2 
intel_agp              22804  1 
iptable_filter          2816  0 
ip_tables              12232  1 iptable_filter
ipv6                  221780  8 
iTCO_vendor_support     3716  1 iTCO_wdt
iTCO_wdt               11296  0 
jbd                    38036  1 ext3
l2cap                  21124  13 rfcomm
libata                134452  2 ata_generic,ata_piix
lp                     10636  0 
mbcache                 7808  1 ext3
mii                     5248  1 3c59x
parport                33224  2 ppdev,lp
pcspkr                  3072  0 
ppdev                   8580  0 
psmouse                35728  0 
rfcomm                 34580  2 
scsi_mod              139988  4 sd_mod,sg,sr_mod,libata
sd_mod                 26640  3 
serio_raw               6660  0 
sg                     33312  0 
snd                    48564  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_intel         310012  3 
snd_hwdep               8836  1 snd_hda_intel
snd_mixer_oss          15744  1 snd_pcm_oss
snd_page_alloc          9992  2 snd_hda_intel,snd_pcm
snd_pcm                65416  2 snd_hda_intel,snd_pcm_oss
snd_pcm_oss            37920  0 
snd_rawmidi            22560  1 snd_seq_midi
snd_seq                44956  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8076  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy           3844  0 
snd_seq_midi            8096  0 
snd_seq_midi_event      6912  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            30740  0 
snd_timer              21252  2 snd_pcm,snd_seq
soundcore               7108  1 snd
sr_mod                 15396  0 

uhci_hcd               21392  0 
usbcore               119348  4 usbhid,ehci_hcd,uhci_hcd
usbhid                 27748  0 
x_tables               13700  1 ip_tables

```

---

### Post by sdide on 2008-08-21
I think you need the atlk1 module.

[http://javier.rodriguez.org.mx/index.php/2007/07/20/attansic-l1-gigabit-ethernet-driver-for-debian](http://javier.rodriguez.org.mx/index.php/2007/07/20/attansic-l1-gigabit-ethernet-driver-for-debian)

---

### Post by ensis2k on 2008-08-22
Thank you.

So google is the only way to find out which hardware matches which kernel module? Is there no official list?

---

### Post by sdide on 2008-08-25
> **ensis2k said:**
> So google is the only way to find out which hardware matches which kernel module? Is there no official list?

Well, not that I know of.
Google is a great tool, both as a first shot, and as a last resort.

---


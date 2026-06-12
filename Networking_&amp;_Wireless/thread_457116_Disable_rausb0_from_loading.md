---
title: "Disable rausb0 from loading"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by alfredska on 2007-05-28
OS: Ubuntu 7.04 with all updates as of May 27, 2007.
Wireless Network Card: D-Link DWL-G122 rev B1 (Uses rt2570 kernel driver)

I have read the sticky about rt2570 devices, my problem differs slightly.

I am trying to disable the built in driver and use ndiswrapper.

I can't seem to completely blacklist rt2570 from loading, as every time I start up the computer, rausb0 still appears.

Here's a few of my configuration files:
/etc/network/interfaces```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
/etc/modprobe.d/blacklist (these lines were added)```
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib
```
/etc/modprobe.d/ndiswrapper
```
alias wlan0 ndiswrapper
```

When I run ```
lsmod | grep rt
``` nothing related to rt2xxx shows up.

Any tips on how I can prevent rausb0 from loading?

~Matt

---

### Post by Bachstelze on 2007-05-28
Try to blacklist rt73 too. *lsmod* will show you a list of all loaded modules.

---

### Post by alfredska on 2007-05-28
I just added much more than should be needed to my blacklist, and still when I plug in the USB adapter, rausb0 shows up:

/etc/modprobe.d/blacklist (these were added):```
blacklist rt73
blacklist rt61
blacklist rt2570
blacklist prism2
blacklist prism54
blacklist rt2500
blacklist rt73usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt61pci
blacklist prism2_pci
blacklist prism2_usb
blacklist prism54pci
blacklist prism2_plx
blacklist prism54common
blacklist prism54usb
```

I've tried reinstalling network-manager as well, having it remove all configuration files during installation (synaptic's "complete removal").

Running lsusb shows:
```
Bus 003 Device 004: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
```

And if you're interested, here's lsmod:
```
Module                  Size  Used by
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
video                  16388  0 
battery                10756  0 
button                  8720  0 
asus_acpi              17308  0 
dock                   10268  0 
container               5248  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ndiswrapper           194608  0 
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
pcmcia                 39212  0 
snd_atiixp             20620  1 
snd_atiixp_modem       17160  0 
snd_ac97_codec         98464  2 snd_atiixp,snd_atiixp_modem
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                79876  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
pcspkr                  4224  0 
snd_timer              23684  2 snd_seq,snd_pcm
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                38920  0 
serio_raw               7940  0 
snd                    54020  13 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
i2c_piix4               9740  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
ati_agp                10124  1 
snd_page_alloc         10888  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_core               22656  2 i2c_ec,i2c_piix4
agpgart                35400  2 drm,ati_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
8139too                27648  0 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
usbhid                 26592  0 
hid                    27392  1 usbhid
atiixp                  7440  0 [permanent]
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
```

I'm using a clean install of Ubuntu 7.04 with all official updates installed.

---

### Post by alfredska on 2007-05-28
I would also like to add that running:
```
ndiswrapper -l
```

results in:
```
netrtusb : driver installed
        device (2001:3C00) present (alternate driver: rt2570)
```

Notice the (alternative driver).  Is there  a way to force ndiswrapper to ignore the alternate?

---

### Post by alfredska on 2007-05-28
My latest status:

1) Removed network card from usb port
2) Uninstalled network-manager and ndiswrapper (along with all installed drivers).
3) Rebooted, installed ndiswrapper from their sourceforge page (1.45stable released on May 27th, 2007).
4) Installed windows network driver, added alias file for ndiswrapper
5) depmod -a
6) Rebooted, setup manual configuration for wlan0 in /etc/network/interfaces
7) Rebooted, installed network-manager from synaptic, removed manual configuration from /etc/network/interfaces

Now about half the time I boot up, wlan0 is correctly associated with the windows driver via ndiswrapper.  The other half the time rt2570 is used even though it is blacklisted, and ifconfig shows rausb0 instead of wlan0.  When the rt2570 driver is loaded, the network card does not work.  When the ndiswrapper driver is loaded, networking works great (I'm using it right now).

Here's my latest config files:

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

/etc/modprobe.d/blacklist
```
blacklist rt2570
```

/etc/modprobe.d/ndiswrapper
```
alias wlan0 ndiswrapper
```

/etc/modprobe.d/rt2570 - deleted
/etc/modprobe.conf - deleted (only contained rt2570 alias)

Again, can anyone give me a suggestion about how to force ndiswrapper to ignore the alternative driver (rt2570) it sees (and sometimes uses)?

---

### Post by alfredska on 2007-05-29
Still no one has a suggestion of how to force ndiswrapper to use win-driver rather than kernel driver?

A couple of things to add: When I
```
lsmod | grep usb
``` after rt2570 has been blacklisted and ndiswrapper is installed (as well as windows driver), rt2570 actually does not show up, ndiswrapper does.  The thing is, I think ndiswrapper is loading the rt2570 driver manually, otherwise I can't see how rausb0 would show up rather than wlan0.  This is also apparent from the network working when wlan0 is shown, and not working when rausb0 is shown.

I have since renamed all instances (2) of 'rt2570.ko' to 'rt2570.bak'.  So far, it has not loaded.  This is by no means conclusive though, as it has only been tested a few times.

I am still open to any cleaner solutions.  Anyone?

---


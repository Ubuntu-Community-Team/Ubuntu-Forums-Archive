---
title: "Network connections are lost"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by craigsn on 2008-03-23
I have Feisty 64bit installed, and until last night the networking/internet "stuff" was working fine. The last thing I did was to install the released version of Skype, using the directions by Cappy's post. The installation went fine. When I got up this morning and started Feisty, I no longer have a network connection, it was on eth0, with IPv4, but now there is only the IPv6 protocol installed.Not sure what happened, or when it happened. Any suggestions would be great to get back up and working again.

Thanks
Craig

---

### Post by keratos on 2008-03-23
post all output from the following commands, run them as root user in a Terminal window.

lspci
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /proc/net/dev
lsmod

---

### Post by craigsn on 2008-03-26
Ok Keratos, here is the information you requested.

root@Greezy:/home/craig# lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

root@Greezy:/home/craig# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth1
#iface eth1 inet dhcp
auto eth2
#iface eth2 inet dhcp
auto ath0
#iface ath0 inet dhcp
auto wlan0
#iface wlan0 inet dhcp
iface eth0 inet dhcp
auto eth0

root@Greezy:/home/craig# cat /etc/resolv.conf
search Colina
nameserver 200.248.106.7
nameserver 200.248.106.8

root@Greezy:/home/craig# cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:   82967    1078    0    0    0     0          0         0    82967    1078    0    0    0     0       0          0
  eth0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
vmnet8:       0       0    0    0    0     0          0         0        0      28    0    0    0     0       0          0
vmnet1:       0       0    0    0    0     0          0         0        0      28    0    0    0     0       0          0

root@Greezy:/home/craig# lsmod
Module                  Size  Used by
binfmt_misc            14860  1 
vmnet                  45344  13 
vmmon                 150508  0 
ipv6                  317192  18 
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_ondemand       10896  1 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_userspace       6048  0 
sbs                    21520  0 
container               6400  0 
button                 10400  0 
video                  21140  0 
ac                      7304  0 
dock                   12264  0 
battery                12424  0 
smsc47m1               13192  0 
smsc47m192             20624  0 
hwmon_vid               4864  1 smsc47m192
sbp2                   27144  0 
lp                     15048  0 
snd_atiixp             24084  1 
snd_ac97_codec        122200  1 snd_atiixp
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_usb_audio          96640  0 
snd_usb_lib            20352  1 snd_usb_audio
snd_pcm                94344  4 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_hwdep              12168  1 snd_usb_audio
xpad                   11400  0 
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                1740124  18 
snd                    69288  14 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
i2c_piix4              11020  0 
i2c_core               30208  2 smsc47m192,i2c_piix4
k8temp                  7680  0 
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_atiixp,snd_pcm
af_packet              28172  4 
pcspkr                  4608  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  4 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
usb_storage            81728  0 
ide_disk               20352  3 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
libusual               22824  1 usb_storage
usbhid                 32576  0 
hid                    33408  1 usbhid
sg                     41384  0 
sd_mod                 32512  0 
8139too                31232  0 
atiixp                  7824  0 [permanent]
ide_core              141200  4 usb_storage,ide_disk,ide_cd,atiixp
ohci1394               38984  0 
sata_sil               14472  0 
ieee1394              109528  2 sbp2,ohci1394
8139cp                 28032  0 
mii                     7424  2 8139too,8139cp
ata_generic             9988  0 
libata                138928  2 sata_sil,ata_generic
scsi_mod              172856  5 sbp2,usb_storage,sg,sd_mod,libata
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  9 snd_usb_audio,snd_usb_lib,xpad,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor

---

### Post by keratos on 2008-03-26
Are you trying to do this inside vmware ?

---

### Post by craigsn on 2008-03-26
Nope, this is a clean Gutsy 64 bit install, that used to work fine, then a couple of days ago, the network stopped working. To the best of my knowledge, nothing changed except installing Skype using the method that Cappy has put up on the forums. And I don't believe that caused any problems because I have run his script before on the betas of Skype, and everything worked fine.

Craig

---

### Post by superprash2003 on 2008-03-26
i've had that problem sometimes..a reboot used to fix it for me!!

---

### Post by keratos on 2008-03-26
your above posts from lsmod indicates use of VMWARE , as given by the certain modules and network drivers.

there is NO WAY that certain modules are loaded by a "Clean Install" of ubuntu.

If you are being honest, then I'm at a lost. I would say this is related to VMWARE and I can help you anymore if you insist this is a clean install.

---

### Post by craigsn on 2008-03-26
Keratos, it is a clean install, but I do have VM Server installed on ubuntu as an application, but ubuntu is not installed in a Virtual VM Server. I'll try to remove VM Server from the computer to see if that does anything. And then post again.

Appreciate the assistance in this.
Craig

---

### Post by keratos on 2008-03-26
> **craigsn said:**
> Keratos, it is a clean install, but I do have VM Server installed on ubuntu as an application, but ubuntu is not installed in a Virtual VM Server. I'll try to remove VM Server from the computer to see if that does anything. And then post again.

Appreciate the assistance in this.
Craig

Okay. Sorry

As an app, thats fine.

But if its a clean install, then you must have added VMserver at some point.

Can we just clarify because I'm trying my best here but becoming slightly confused...

Is this a clean install , or not. An by clean install I mean you have downloaded an ISO, installed from it and have done NOTHING however are receiving the errors you refer to.

So far as I can deduce your ethernet card is not being recognised however your RealTekRT8139 is serviced by the 8139too module (the driver!) which is loaded as I can see in your post but ... has no usage (use count = 0).

We need to figure our why the card is not recognised.

so, post output of
```

dmesg | grep eth0
lspci -vvv -nn

```

---


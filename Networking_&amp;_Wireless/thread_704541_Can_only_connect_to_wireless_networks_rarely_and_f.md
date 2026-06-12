---
title: "Can only connect to wireless networks rarely and for a couple of minutes"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by superstead on 2008-02-22
Hi, I'm a total newcomer to Ubuntu so forgive me if I'm being totally stupid! I've found a few posts with similar problems but nothing that really seems to help me. Ive got a Dell Inspiron 6400 with a BCM4311 / BCM2050 chipset and a Dell wireles 1390 WLAN Mini-card. I've managed to get the driver and things and I've managed to get it to work twice with the record being about 5 minutes on the net before it all stopped. Also, the internet never loads to 100% it normally gets to about 50%. After it stops working, it says the signal strength is still good etc, just stops! The computer is dual booted, vista/ubuntu gutsy gibbon and the internet works fine on vista, any ideas would be greatly appreciated! cheers, david

---

### Post by nixscripter on 2008-02-22
Try connecting again, and after it stops, open a terminal window, run these two commands, and post their output: ```
iwconfig
``` and ```
ifconfig -a
```.

Also, make sure to post it in a [code] block so that the formatting remains intact.

---

### Post by superstead on 2008-02-23
Okay, cheeers for answering my call for help! I did what you said, and this time was one of the rare times i got onto google! It then, like normal, stopped workinf, heres the results of typing iwconfig

```
 lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"linksys" 
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

and the results of ifconfig -a

```
 eth0      Link encap:Ethernet  HWaddr 00:1C:23:8A:75:00  
          inet addr:172.16.61.125  Bcast:172.16.61.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1C:26:1A:DB:83  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:479 errors:0 dropped:194 overruns:0 frame:0 
          TX packets:1016 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:224709 (219.4 KB)  TX bytes:79162 (77.3 KB) 
          Interrupt:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:25160 (24.5 KB)  TX bytes:25160 (24.5 KB) 
```

Also, one thing that I think may well be to do with it (but I'm not sure, dont really understand much of this) is that everytime I succeed in connecting to the internet, I get asked for a password in a box with the heading 'Unlock keyring', it then says in the title 'Enter password for default keyring to unlock' then says 'The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked'. I'm guessing this is to do with network manager and could be the problem but I've entered m computer (or administrator) password, the network password and my internet user password and it just keeps popping back up, I've run out of passwords to put in! Any idea what it's asking me for (which password) or if this is the source of my problem? I always have to click deny which I don't think is what I should be doing, but I will stress, I dont get this message all the time, only when it actually connects, so maybe there is another problem, thanks again for answering me! David

---

### Post by nixscripter on 2008-02-24
> **superstead said:**
> Also, one thing that I think may well be to do with it (but I'm not sure, dont really understand much of this) is that everytime I succeed in connecting to the internet, I get asked for a password in a box with the heading 'Unlock keyring', it then says in the title 'Enter password for default keyring to unlock' then says 'The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked'. I'm guessing this is to do with network manager and could be the problem but I've entered m computer (or administrator) password, the network password and my internet user password and it just keeps popping back up,

Ah, that is probably the problem.

When you priginally set up the machine, you should have been asked to specify a password for your keyring. The keyring is just a password storage manager. I am not familiar with all of its details, but in general, it is a way that Ubuntu can store passwords for many applications under one mechanism. If your wireless network required an encryption key, Ubuntu would store that in the keyring the first time you typed it.

If you didn't recognize the dialog to set the keyring password the first time you saw it, you probably did what I did: just typed the password you picked for your machine. If you're lucky, the keyring password will therefore be the first password you ever set for your user account on that machine. Give it a try.

Good luck.

---

### Post by superstead on 2008-02-24
Ok, that's brilliant! got around that one, I've changed my password since I loaded Ubuntu, it was the original, thanks. The original problem still remains though, it doesn't always get as far as asking for the keyring password. I tried a few times but got nowhere. It keeps asking me for the network password, which i type in correctly, then the internet loads to as far as 66% (but normally around 50%), then resets and goes back to 0% and you have to do the whole password input again. Any ideas? thankyou so much for your help so far, it's much appreciated! David

---

### Post by nixscripter on 2008-02-24
The diagnostic information you provided earlier indicates this sort of pattern:

1. Your computer connects successfully.
2. Your computer talks to the access point, and negotiates routing and IP information.
3, Your computer disconnect suddenly, and (correctly) clears all of the information.

Since software usually doesn't fail in this manner, so I'm now wondering about the hardware. Are there any indicators on the card, in terms of connectivity or power lights? If so, what do they do?

Also, next time it fails, run these commands and post their output: ```
lspci
``` to verify that the card is still in the machine (it should be), and ```
sudo lsmod
``` to ensure that the kernel driver isn't being unloaded or something.

I'm grasping at straws. I expect these two will indicate the card is being operated.

---

### Post by superstead on 2008-02-25
Ok, I did that. The light for the wifi stayed on, then blinked when i tried to connect, but this was for only a fraction on a second. Normally the wifi card works because I'm on the same computer now, it's dual booted. The internet works on vista. I did what you said,

lspci came back with

```
 Module                  Size  Used by 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat 
usb_storage            73024  1 
ide_core              116804  1 usb_storage 
libusual               18448  1 usb_storage 
af_packet              24840  0 
i915                   25856  2 
drm                    83348  3 i915 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm 
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand 
battery                11012  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
video                  18060  0 
button                  8976  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp 
snd_hda_intel         263712  1 
snd_seq_dummy           4740  0 
joydev                 11328  0 
snd_seq_oss            33152  0 
snd_usb_audio          81024  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss 
snd_pcm                80388  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss 
snd_usb_lib            17920  1 snd_usb_audio 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi 
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24324  2 snd_pcm,snd_seq 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
sdhci                  18828  0 
mmc_core               28420  1 sdhci 
hci_usb                18332  2 
snd_hwdep              10244  1 snd_usb_audio 
bluetooth              57060  7 rfcomm,l2cap,hci_usb 
gspca                 608336  0 
videodev               29312  1 gspca 
v4l2_common            18432  1 videodev 
v4l1_compat            15364  1 videodev 
iTCO_wdt               11940  0 
usbhid                 29536  0 
hid                    28928  1 usbhid 
bcm43xx               127336  0 
snd                    54660  13 snd_hda_intel,snd_seq_oss,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep 
iTCO_vendor_support     4868  1 iTCO_wdt 
ieee80211softmac       31360  1 bcm43xx 
ieee80211              35656  2 bcm43xx,ieee80211softmac 
soundcore               8800  1 snd 
pcspkr                  4224  0 
serio_raw               8068  0 
psmouse                39952  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm 
ieee80211_crypt         7040  1 ieee80211 
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp 
ipv6                  273892  10 
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3 
mbcache                 9732  1 ext3 
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod 
sd_mod                 30336  6 
ata_piix               17540  3 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic 
scsi_mod              147084  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata 
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394 
b44                    28300  0 
mii                     6528  1 b44 
uhci_hcd               26640  0 
usbcore               138632  10 usb_storage,libusual,snd_usb_audio,snd_usb_lib,hci_usb,gspca,usbhid,ehci_hcd,uhci_hcd 
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal 
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor 
```

and sudo lsmod came back with

```
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller 
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
```

Hope this is helping, another little bit of info, I'm not using ndiswrapper like most people, I have the drivers loaded, they seem to have worked (as it has connected a couple of times) but not as I'd hope. Cheers. David

---

### Post by nixscripter on 2008-02-25
Yep, the driver is loaded, and the card is detected.

I'm afriad I'm out of ideas for now. If I think of anything, I'll let you know. :-|

---

### Post by superstead on 2008-02-26
Cheers for your advice, I appreciate the time you spent helping me. Not to worry, I have an external USB wifi adapter. I'm going to get that back and give that a bash, maybe that'll work!

---


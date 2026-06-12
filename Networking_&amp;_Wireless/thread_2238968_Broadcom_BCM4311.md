---
title: "Broadcom BCM4311"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by 4dr14n on 2014-08-11
Good morning all,

I have a problem I don't know hot to resolve, even if I was reading some other post relating similar cases.
When I updated my old laptop from Lubuntu 13.10 to 14.04 it, suddenly, stopped recognising new wifis, it could connect to known ones but no to new ones... but you tried it, it didn't connect nor a message appear (it just happened nothing). It allowed me to work at home so I could live with it. 
But now, after something I did, it doesn't connect to any wifi, so I must use a wire to use internet. 

I don't know what I should do.
I have the linux-firmware-nonfree on the latest version.


Thank you so much for the help.

---

### Post by kc1di on 2014-08-11
Could you go to a terminal and post the outputs of these commands
```
lspci
```
```
lsmod
```

---

### Post by 4dr14n on 2014-08-11
Here we go:
> adrian@adrian-Latitude-D531:~$ lspci00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


adrian@adrian-Latitude-D531:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48417  1 
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
zram                   18032  2 
snd_hda_codec_idt      48877  1 
joydev                 17101  0 
snd_hda_intel          42730  5 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
arc4                   12536  2 
b43                   356470  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec,snd_hda_intel
bcma                   42043  1 b43
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
mac80211              546051  1 b43
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
cfg80211              409394  2 b43,mac80211
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
kvm_amd                50537  0 
kvm                   388083  1 kvm_amd
radeon               1420526  3 
pcmcia                 51828  0 
snd                    60871  19 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    72698  1 radeon
rfcomm                 53664  8 
yenta_socket           40201  0 
bnep                   18895  2 
btusb                  27580  0 
psmouse                91329  0 
bluetooth             342206  22 bnep,btusb,rfcomm
pcmcia_rsrc            18319  1 yenta_socket
serio_raw              13230  0 
drm_kms_helper         47182  1 radeon
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
sp5100_tco             13643  0 
k8temp                 12842  0 
soundcore              12600  1 snd
i2c_piix4              17723  0 
ssb_hcd                12749  0 
drm                   244037  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
wmi                    18673  1 dell_wmi
mac_hid                13037  0 
shpchp                 32128  0 
ati_agp                13177  0 
binfmt_misc            13140  1 
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
ahci                   25579  2 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
libahci                27082  1 ahci
pata_atiixp            13058  0 
tg3                   152132  0 
ptp                    18445  1 tg3
pps_core               18799  1 ptp
ssb                    51854  2 b43,ssb_hcd
adrian@adrian-Latitude-D531:~$ 




---

### Post by kc1di on 2014-08-12
you are loading the correct driver for that card.  so not sure what the issue may be.
you might want to try reinstalling the driver. 
you should purge the old one first. ```
sudo apt-get purge b43
```
then you'll need a ethernet connection to reinstall the dirver - use the additional driver tool. 
Good luck

Additional :  check software center see if any of the following are installed
```
b43-fwcutter firmware-b43-installer firmware-b43legacy-installer
```
if they are or any are remove them and reinstall.

---

### Post by kd5mkv on 2014-08-12
This something similar to a problem I had with BCM4306, I tried all the driver supprt and the wireless adaptor on my work machine would not work. I had to install 10.04 and keep previous driver support and use 3.2 kernel on 12.04.4.
It appears Ubuntu doesn't support BCM43xx drivers or there omitted from the kernel. The latest kernel didn't like the wireless card and it would crash on every startup until I reverted to older setup.

---


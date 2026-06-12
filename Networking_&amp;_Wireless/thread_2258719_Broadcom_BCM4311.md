---
title: "Broadcom BCM4311"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by kevin136 on 2014-12-29
I installed Ubuntu 14.04.1 on an Acer Extensa 5420.
I tried Peppermint, and a couple other distros...to no avail.

Everything works out of the box except the wireless card...

This issue is driving me crazy!!! 

I tried to switch out drivers....no dice

I tried legacy drivers....no dice

I tried ndiswrapper....no dice



Specs:


john@john-Extensa-5420:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
Linux john-Extensa-5420 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
john@john-Extensa-5420:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0124]
    Kernel driver in use: sky2
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: b43-pci-bridge
john@john-Extensa-5420:~$ iwconfig
irda0     no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

john@john-Extensa-5420:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
john@john-Extensa-5420:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  8 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_realtek    61438  1 
pcmcia                 62299  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
kvm_amd                59987  0 
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
kvm                   451511  1 kvm_amd
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
yenta_socket           41027  0 
joydev                 17381  0 
b43                   387371  0 
serio_raw              13462  0 
pcmcia_rsrc            18407  1 yenta_socket
k8temp                 12978  0 
radeon               1522422  3 
bcma                   52096  1 b43
edac_core              62291  0 
edac_mce_amd           22617  0 
ttm                    85115  1 radeon
mac80211              630653  1 b43
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper         53081  1 radeon
btusb                  32412  0 
bluetooth             391196  22 bnep,btusb,rfcomm
snd                    69238  16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,   snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,sn   d_seq_device,snd_seq_midi
drm                   303102  5 ttm,drm_kms_helper,radeon
cfg80211              484040  2 b43,mac80211
soundcore              12680  1 snd
sp5100_tco             13979  0 
i2c_piix4              22155  0 
ssb_hcd                12869  0 
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
wmi                    19177  1 acer_wmi
nsc_ircc               22963  0 
irda                  129246  1 nsc_ircc
crc_ccitt              12707  1 irda
video                  19476  1 acer_wmi
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
firewire_ohci          40409  0 
firewire_core          68769  1 firewire_ohci
psmouse               106678  0 
crc_itu_t              12707  1 firewire_core
sdhci_pci              23172  0 
ahci                   25819  2 
sdhci                  43015  1 sdhci_pci
pata_atiixp            13271  0 
libahci                32560  1 ahci
ssb                    62379  2 b43,ssb_hcd
sky2                   58191  0 
john@john-Extensa-5420:~$ 


What am I doing wrong?
 Please help.

---

### Post by praseodym on 2014-12-30
Just install the missing firmware

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by kevin136 on 2014-12-30
Thank you it worked perfectly.
Have a great new years.

---


---
title: "Acer Extensa 5420 wireless problems with 14.04"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by wjbite-gmail on 2015-08-18
I have the exact problem answered by WILD MAN for 11.04
[http://ubuntuforums.org/showthread.php?t=1777990](http://ubuntuforums.org/showthread.php?t=1777990)
if WILD MAN is still watching he may be able to help.
If not I will expand on this post to make  my problem more clear for others who might potentially help.

So I blindly followed the solution instructions except this is 14.04
The result was that the last instruction caused a hang up - the cursor never came back.
The last instruction was:
sudo modprobe 43

The following is the result of the first print outs:

************** start of printout
wjbite@wjbite-Extensa-5420:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux wjbite-Extensa-5420 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
wjbite@wjbite-Extensa-5420:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0124]
    Kernel driver in use: sky2
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: wl
wjbite@wjbite-Extensa-5420:~$ iwconfig
eth0      no wireless extensions.

irda0     no wireless extensions.

lo        no wireless extensions.

wjbite@wjbite-Extensa-5420:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
wjbite@wjbite-Extensa-5420:~$ lsmod
Module                  Size  Used by
ssb                    65536  1 
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
wl                   6369280  1 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    69632  2 snd_hda_codec_realtek
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
amdkfd                 81920  1 
amd_iommu_v2           20480  1 amdkfd
snd_rawmidi            32768  1 snd_seq_midi
radeon               1552384  4 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
pcmcia                 65536  0 
kvm_amd                61440  0 
kvm                   479232  1 kvm_amd
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
joydev                 20480  0 
serio_raw              16384  0 
ttm                    94208  1 radeon
snd                    86016  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
k8temp                 16384  0 
edac_core              53248  0 
drm_kms_helper        126976  1 radeon
edac_mce_amd           24576  0 
yenta_socket           45056  0 
drm                   344064  7 ttm,drm_kms_helper,radeon
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_piix4              24576  0 
soundcore              16384  2 snd,snd_hda_codec
i2c_algo_bit           16384  1 radeon
cfg80211              524288  1 wl
nsc_ircc               32768  0 
shpchp                 40960  0 
irda                  200704  1 nsc_ircc
wmi                    20480  1 acer_wmi
crc_ccitt              16384  1 irda
video                  20480  1 acer_wmi
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
firewire_ohci          40960  0 
psmouse               114688  0 
firewire_core          69632  1 firewire_ohci
sdhci_pci              24576  0 
crc_itu_t              16384  1 firewire_core
sdhci                  45056  1 sdhci_pci
ahci                   36864  2 
libahci                32768  1 ahci
pata_atiixp            16384  0 
sky2                   61440  0 
**************end of printouts

The first difference that I see is that 
Soft Blocked = yes
instead of no.

I hope I have made it clear enough to allow someone to help.
Thanks,

---

### Post by wjbite-gmail on 2015-08-18
Whooooo HOOOOOO!
Even though the terminal window hung up, the driver seems to be working after I rebooted.
So the procedure for 11.04 works for 14.04, too.
Thank you so much WILD MAN

---


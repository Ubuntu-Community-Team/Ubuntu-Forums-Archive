---
title: "Problem getting Ubuntu 14.04 to recognize RaLink USB wireless adapter"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by jes649 on 2015-10-03
I have been struggling to get my Dell E6400 laptop with Ubuntu 14.04 to recognize a RaLink USB wireless adapter.  I know the wireless adapter is in good working order, as it works well on Windows machines.  I have researched my heart out trying to find, and understand, info on this forum but my lack of a good understanding of Linux limits me.  However, I am very impressed with the posts and replies I see on this forum.  What a great group!

I am able to use an ethernet connection for internet on the computer in question but hopefully I can get this wireless adapter working and not need to.

Per the forum recommendation, I'm attaching my wireless script info.

Any and all help is much appreciated!  Really, thank you in advance!

[ATTACH]264809[/ATTACH]

---

### Post by Bucky Ball on 2015-10-03
Welcome. Online with the ethernet cable, do an update and then check 'Additional Drivers'. Do you see a driver there called STA? If so, enable it, wait till that's finished, pull the ethernet and reboot. Wireless?

If still nothing or no STA driver in Additional Drivers, open a terminal while online with cable and

```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
```

Pull the cable, reboot.

---

### Post by jes649 on 2015-10-04
Thank you Bucky.  There is an STA driver in the Additional Drivers section.  It reads Broadcom 802.11 Linix STA wireless driver.  I ran an update, then selected the STA driver and applied the changes to no avail.  After trying that I ran the code you posted above.  Still no luck.  

I see in lsusb that it sees that the RaLink is connected.  I just don't understand why it won't use it.  

In the Network section of my Settings it gives me two 'wireless' options since I am now using the Broadcom STA driver.  Before there was only one.  However, neither of them allow me to turn them on.

---

### Post by praseodym on 2015-10-04
Hi,

```
0: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: [COLOR="#FF0000"]yes[/COLOR]
```
The internal card is turned off, this also affects the stick (driver rt2800usb is loaded!). Lets install the missing firmware for the native driver b43:

```
sudo apt-get remove --purge bcmwl-kernel-source
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:
```

lsmod
iwconfig
rfkill list
```

---

### Post by jes649 on 2015-10-04
thank you praseodym.  Here are the results:

stellar@Stellar:~$ lsmod
Module                  Size  Used by
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
uvcvideo               90112  0 
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
rt2800usb              28672  0 
gpio_ich               16384  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
videobuf2_core         53248  1 uvcvideo
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
v4l2_common            16384  1 videobuf2_core
arc4                   16384  4 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
crc_ccitt              16384  1 rt2800lib
media                  24576  2 uvcvideo,videodev
nouveau              1368064  3 
dell_rbtn              16384  0 
coretemp               16384  0 
b43                   421888  0 
kvm                   479232  0 
dell_laptop            16384  0 
bcma                   53248  1 b43
dcdbas                 16384  1 dell_laptop
mxm_wmi                16384  1 nouveau
ttm                    94208  1 nouveau
mac80211              708608  4 b43,rt2x00lib,rt2x00usb,rt2800lib
i8k                    16384  0 
snd_hda_codec_idt      61440  1 
drm_kms_helper        126976  1 nouveau
snd_hda_codec_generic    69632  2 snd_hda_codec_idt
pcmcia                 65536  0 
snd_hda_intel          36864  3 
drm                   344064  6 ttm,drm_kms_helper,nouveau
cfg80211              524288  3 b43,mac80211,rt2x00lib
i2c_algo_bit           16384  1 nouveau
snd_hda_controller     32768  1 snd_hda_intel
yenta_socket           45056  0 
joydev                 20480  0 
snd_hda_codec         143360  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
serio_raw              16384  0 
snd_hwdep              20480  1 snd_hda_codec
pcmcia_rsrc            20480  1 yenta_socket
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
lpc_ich                24576  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
wmi                    20480  3 dell_wmi,mxm_wmi,nouveau
mac_hid                16384  0 
snd                    86016  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
8250_fintek            16384  0 
shpchp                 40960  0 
video                  20480  1 nouveau
soundcore              16384  2 snd,snd_hda_codec
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
psmouse               114688  0 
firewire_ohci          40960  0 
sdhci_pci              24576  0 
ahci                   36864  2 
firewire_core          69632  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
sdhci                  45056  1 sdhci_pci
libahci                32768  1 ahci
ssb                    65536  1 b43
e1000e                237568  0 
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
stellar@Stellar:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
stellar@Stellar:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2015-10-04
Any button, switch or key combo?

---

### Post by jes649 on 2015-10-04
I'm sorry but I don't understand the question.  What does switch or key combo mean?

---

### Post by jes649 on 2015-10-04
Well, I feel like an idiot.  There is a switch on the side of the laptop.  I switched it and now when I run rfkill list it shows hard blocked: no.  

In my Network window, I'm now able to turn my wireless on.  However, it is still not showing any networks.  I will update soon with more information.

Thank you very much for getting me this far.  I never knew laptops had physical wireless switches on them.

---

### Post by jes649 on 2015-10-04
Praseodym,

     Thank you for your help.  It's people like you that make learning things like Linux possible, and more fun.  I rebooted and my wireless is up and running!  Maybe I should have known about a physical wireless switch, but if I had, I would not have learned what I now know about using the terminal, among other things.  

Best wishes

---

### Post by praseodym on 2015-10-05
You're welcome. Enjoy the Linux world :-)

---


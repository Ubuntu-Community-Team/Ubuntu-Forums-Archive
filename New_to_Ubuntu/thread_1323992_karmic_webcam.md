---
title: "karmic webcam?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-11-12
I have a Logitech external webcam and Karmic can't seem to detect it.

I've tried Cheese and Skype. No luck.

---

### Post by 3rdalbum on 2009-11-12
What is the chipset? (i.e. what is the output of the "lspci" command)

---

### Post by infernus_crusher on 2009-11-12
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by ukripper on 2009-11-12
> **infernus_crusher said:**
> I have a Logitech external webcam and Karmic can't seem to detect it.

I've tried Cheese and Skype. No luck.

Can you run below command and post here, I believe it is a usb webcam:
```
lsusb
```

---

### Post by infernus_crusher on 2009-11-12
Yes it is a USB webcam, as you can see below, Device 005.

```

~$ lsusb
Bus 003 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bc2:2100 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by ukripper on 2009-11-12
Can you plug your cam and reboot and see if it works then. i rember having this sort of problem with another webcam and it worked when you plug it in before boot.

---

### Post by infernus_crusher on 2009-11-12
> **ukripper said:**
> Can you plug your cam and reboot and see if it works then. i rember having this sort of problem with another webcam and it worked when you plug it in before boot.

No, it doesn't. My webcam is always plugged in all the time and I've restarted a gazillion times with it intact.

Plugging in before booting works for my Seagate external HDD, but not the webcam for some reason.

Kind of a shame that the past two days I've been dealing with myriads of problems with Karmic. All seem sorted out except for this. But I'm not giving up just yet; Jaunty on ext4 is sluggish compared to Karmic and I plan to migrate to Karmic as soon as possible

---

### Post by RichardCL on 2009-11-12
I have the same camera (at least it seems). Also a logitech.

I just plugged it in, installed Karmic x64 from the USB key (running the try-it module and then selecting install from the desktop). I then installed Skype (from Multiverse, I think) and the camera worked automatically in Skype.

If it helps, I could send you any info you need from the system. Just let me know what commands I should enter to report out.

---

### Post by infernus_crusher on 2009-11-12
> **RichardCL said:**
> 
I just plugged it in, installed Karmic x64 from the USB key (running the try-it module and then selecting install from the desktop). I then installed Skype (from Multiverse, I think) and the camera worked automatically in Skype.


Karmic x64? I don't remember having to install anything like that on Jaunty to get the webcam working. How do I do it?

BTW, my Karmic is 32-bit, and I installed Skype from a debian package from the website, if it even makes any difference.

---

### Post by ukripper on 2009-11-12
> **infernus_crusher said:**
> No, it doesn't. My webcam is always plugged in all the time and I've restarted a gazillion times with it intact.

Plugging in before booting works for my Seagate external HDD, but not the webcam for some reason.

Kind of a shame that the past two days I've been dealing with myriads of problems with Karmic. All seem sorted out except for this. But I'm not giving up just yet; Jaunty on ext4 is sluggish compared to Karmic and I plan to migrate to Karmic as soon as possible

Ok. Let us try this approach then:
In terminal type this command:
```
gstreamer-properties
```

and select "**Video**" tab and from there "**Plugin:**" drop down - choose "**[COLOR="Blue"]Video for linux(V4l)[/COLOR]**". 

Then try your cam again with package cheese:
```
sudo apt-get install cheese
```

---

### Post by infernus_crusher on 2009-11-12
Nope. No luck either.

This is the output at the command line as I was executing what you told me.

```

~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2:
system error: Cannot send after transport endpoint shutdown]

```

I tried running gstreamer-properties both on sudo and normal mode.

---

### Post by ukripper on 2009-11-12
> **infernus_crusher said:**
> Nope. No luck either.

This is the output at the command line as I was executing what you told me.

```

~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2:
system error: Cannot send after transport endpoint shutdown]

```

I tried running gstreamer-properties both on sudo and normal mode.


install cheese first and then 
try this in terminal:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

---

### Post by infernus_crusher on 2009-11-12
> **ukripper said:**
> install cheese first and then 
try this in terminal:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

Cheese was installed. The command above opened up cheese, but no camera was detected either. :|

---

### Post by ukripper on 2009-11-13
Can you try the same command wth skype and test webcam in skype as below:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

and if the above doesn't work then try below:

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype 
```

---

### Post by infernus_crusher on 2009-11-13
> **ukripper said:**
> Can you try the same command wth skype and test webcam in skype as below:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

and if the above doesn't work then try below:

```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype 
```

In both cases, 'no device found' was displayed on the Video Devices tab in Options. :(

---

### Post by ukripper on 2009-11-13
can you post output of the following commands with webcam already attached (before boot):
```
lsmod
```

```
dmesg | grep usb
```

and output of this command after unplugging and plugging webcam back again:
```
tail -n 30 /var/log/messages
```

---

### Post by ukripper on 2009-11-13
If nothing else works, we may have to take the longer route:
[http://ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam](http://ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam)

---

### Post by infernus_crusher on 2009-11-15
Neither works...

I wonder if it has to do with the fact that I do not have permission to read and write the webcam.

```

Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing.

```

---

### Post by starcannon on 2009-11-15
Not that you should run cheese as root outside of trouble shooting, but try this, just to determine a permissions issue:
```

gksudo cheese

```

---

### Post by infernus_crusher on 2009-11-15
No camera found either. Does it have anything to do with the kernel?

---

### Post by ukripper on 2009-11-16
you need drivers to be loaded first before using your webcam.

Can you  run this command in terminal and post output here:
```
lsmod
```

---

### Post by infernus_crusher on 2009-11-20
```

~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
joydev                 10272  0 
pcmcia                 36808  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
iwl3945                77212  0 
iwlcore               112508  1 iwl3945
mac80211              181236  2 iwl3945,iwlcore
snd_usb_audio          84224  0 
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
snd_pcm_oss            37920  1 
snd_seq_oss            28576  0 
uvcvideo               59080  0 
ip_tables              11692  1 iptable_filter
snd_mixer_oss          16028  1 snd_pcm_oss
x_tables               16544  1 ip_tables
snd_pcm                75296  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_usb_lib            16284  1 snd_usb_audio
snd_hwdep               7200  2 snd_hda_codec,snd_usb_audio
snd_seq_midi            6432  0 
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
tifm_7xx1               5372  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core               7832  1 tifm_7xx1
cfg80211               93052  3 iwl3945,iwlcore,mac80211
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
led_class               4096  3 iwl3945,iwlcore,sdhci
psmouse                56500  0 
serio_raw               5280  0 
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  2 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
usb_storage            52576  1 
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  4 
drm                   159584  4 i915
i2c_algo_bit            5760  1 i915
e1000e                122124  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```

---

### Post by ukripper on 2009-11-20
> videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev


I can see your drivers are loaded just fine.

Ok i think it could be persmission issue. Let see if you are in video group can you type this command and post output here:
```
id **[COLOR="Red"]your_username[/COLOR]**
```
replace your_username

---

### Post by GooglieS on 2009-11-20
I have the same camera. It works in 9.04, but only once. After each usage you need to reboot to use the camera again. In karmic only microphone in camera is working. I have this in /var/log/messages :
```
Nov 20 21:54:34 guggiland kernel: [178834.132601] usb 1-4: new high speed USB device using ehci_hcd and address 18
Nov 20 21:54:35 guggiland kernel: [178834.453283] usb 1-4: configuration #1 chosen from 1 choice
Nov 20 21:54:35 guggiland kernel: [178834.453936] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
Nov 20 21:54:36 guggiland kernel: [178835.452324] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.

```And camera does not working at all.

```
googlies@guggiland:~$ id googlies
uid=1000(googlies) gid=1000(googlies) &#1075;&#1088;&#1091;&#1087;&#1087;&#1099;=1000(googlies),4(adm),20(dialout),24(cdrom),46(plugdev),107(lpadmin),115(admin),120(sambashare)
```
I added myself to video group, but that does not help.

---

### Post by infernus_crusher on 2009-11-21
```

~$ id andrew
uid=1000(andrew) gid=1000(andrew) groups=1000(andrew),4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare)

```

---

### Post by ukripper on 2009-11-21
Here is the bug report for this webcam on launchpad - [https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723)

---

### Post by infernus_crusher on 2009-11-22
Okay, it seems that Skype is to blame for this. I installed a fresh Fedora 12 whose webcam worked perfectly in Cheese until I unpacked the .rpm files, after which it stopped working. In addition, my external HDD unmounted itself and refused to mount afterwards. These were exactly the same problems that I had in Karmic (but not in Jaunty).

So apparently I'll be switching to Jaunty from now on until this is resolved.

---

### Post by drbsjtmndl on 2009-11-22
it worked fine with my hp laptop. thanks pal.

---


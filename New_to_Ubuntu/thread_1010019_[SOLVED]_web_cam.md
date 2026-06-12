---
title: "[SOLVED] web cam"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by jboy012000 on 2008-12-13
Hi All,

I have a logitech web cam and I am not sure how to get it working, has anyone any idea's.

I am using Ubuntu 8.10

Thanks

---

### Post by bloodymind on 2008-12-13
Hey there,
I've got the same problem with webcam Creative Vista
I've googled and found this link [http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

but had problems with installation I downloaded the drivers and couldn't install them I've read how to install It said the build folder which does not exist or maybe they are referring to something I don't know , anyone can help ?

---

### Post by spiderbatdad on 2008-12-13
Hi. what applications are you trying to run?
there have been a number of issues with webcams in 8.10, but most can be resolved. Also make sure your system is up to date.```
sudo apt-get update && sudo apt-get upgrade
```Then install cheese ```
sudo apt-get install cheese
```try launching cheese from the terminal or from the applications menu under graphics. If you need help with an application like skype, try: ```
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

```

---

### Post by jboy012000 on 2008-12-14
I do want my web cam mainly for skype, but what is cheese

John

---

### Post by Tom--d on 2008-12-14
Cheese is just a program which you can take pictures and videos of you webcam (also put effects on it as well).

I use it to see if a webcam works.

---

### Post by jboy012000 on 2008-12-14
ok scratch that last one, I tried cheese it does not recognise my carmera, I have installed all the codecs and whatever for gstreamer and it still doesn't work.

Is there anybody in the forum that has a web cam that works with Ubuntu 8.10, if so what is it lol.

Cheers

---

### Post by xarte on 2008-12-14
I had gotten the webcam working, but something - either something I installed or one of the performance tweaks I tried - made the image turn out black. I SUSPECT that the desktop effects program Compiz MAY have been the culprit but I also did a few command line things as well.

I re-installed Ubuntu, enabled the ATI proprietary drivers, downloaded and installed camorama (think that was via synaptic package manager, but you still just click on it and it unpacks itself for you). Then I plugged in the webcam and turned camorata on. It worked fine, though not the best picture; had to increase brightness and you need good light.

 I downloaded and installed skype, and when I tested the videocam on it, it worked perfectly with a good clear picture.

What I'm saying is, it SHOULD run out-of-the-box but possibly you're getting some sort of third-party interference from some other package/program/tweak/setting ajustment. So maybe check for that. Unfortunately I'm a noob so can't offer much more than that. I'm going to keep a eye on it to see if I can pinpoint what the problem is.

---

### Post by jboy012000 on 2008-12-14
cheers for that I will try the software you suggested.

---

### Post by jboy012000 on 2008-12-14
Ok, I tried changing my effects to standard and also changing the web cam I also changed the usb port I was using and the software won't see the camera, I have checked that Ubuntu has seen the camera by checking the system log which it has so I am not sure were to go from here.

John

---

### Post by richg on 2008-12-14
With Cheese, I have the same issue with a Logitech Quick Cam Communicate Deluxe webcam.
With 8.10 no video or audio. Ubuntu does see the webcam though.

With Ubuntu 8.04, Cheese does see the camera with good video but no sound. Go figure.

Rich

---

### Post by spiderbatdad on 2008-12-14
> **jboy012000 said:**
> ok scratch that last one, I tried cheese it does not recognise my carmera, I have installed all the codecs and whatever for gstreamer and it still doesn't work.

Is there anybody in the forum that has a web cam that works with Ubuntu 8.10, if so what is it lol.

Cheers

I have several webcams that work with 8.10 using cheese, skype, gyachi.
Are you still having a problem?
Try posting the output of some commands and we will try to help you:
```
lsusb
lsmod
```
You need to verify that you are running libv4l-0 0.5.6.1 or drooz.
Your particular cam may require the gspca driver, called gspca-source in synaptic. Then you would install that package and run: ```
sudo modprobe gspca_main
```unplug your cam and plug it in again. Try your application. If it doesn't work, run ```
dmesg | tail
```and post that output here. If worse comes to worse you might have to compile your own module from this guide...read all the comment too: [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

Read the bug reports and possible fixes here: [https://bugs.launchpad.net/debian/+bug/260918](https://bugs.launchpad.net/debian/+bug/260918)

---

### Post by spiderbatdad on 2008-12-14
mis

---

### Post by jboy012000 on 2008-12-16
Hi Spiderbatdad,

Ok Please see results for lsusb in cammand line

john@three-peaks:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:089d Logitech, Inc. 
Bus 005 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

As you can see Ubuntu 8.10 can see my camera.

Please see results from lsmod in cammand line

john@three-peaks:~$ lsmod
Module                  Size  Used by
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
ipv6                  263972  10 
michael_mic            10496  4 
arc4                    9984  4 
ecb                    10880  4 
crypto_blkcipher       25476  1 ecb
usbhid                 35840  0 
hid                    50560  1 usbhid
i915                   38144  2 
drm                    86056  3 i915
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
dcdbas                 15008  0 
snd_hda_intel         381488  5 
evdev                  17696  13 
psmouse                45200  0 
serio_raw              13444  0 
pcspkr                 10624  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_pcm                83204  4 snd_usb_audio,snd_hda_intel,snd_pcm_oss
ricoh_mmc              11904  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_dummy          10884  0 
ieee80211_crypt_tkip    17024  0 
snd_seq_oss            38528  0 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
video                  25104  0 
snd_seq_midi           14336  0 
output                 11008  1 video
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
snd                    63268  22 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
button                 14224  0 
battery                18436  0 
intel_agp              33724  1 
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  3 drm,intel_agp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
ata_generic            12932  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ahci                   37132  2 
libata                177312  4 ata_generic,ata_piix,pata_acpi,ahci
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
sky2                   53380  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

Not a clue what all that means, does it help, I am going to do the rest of that stuff you put in your post, if you don't get back to me first I will let you know how I get on.

Cheers

Johno

---

### Post by jboy012000 on 2008-12-16
Guess I got back first,

Ok I did all that stuff you said to do and my web cam is still not working, please see below the result of dmesg tail

john@three-peaks:~$ dmesg | tail
[ 2555.602611]  domain 0: span 0-1 level MC
[ 2555.602614]   groups: 1 0
[ 2770.073043] usb 5-1: new full speed USB device using uhci_hcd and address 3
[ 2770.265486] usb 5-1: configuration #1 chosen from 1 choice
[ 2771.037308] usbcore: registered new interface driver snd-usb-audio
[ 3479.209704] Linux video capture interface: v2.00
[ 3479.224282] gspca: main v2.2.0 registered
[ 3506.145086] usb 5-1: USB disconnect, address 3
[ 3510.601062] usb 5-1: new full speed USB device using uhci_hcd and address 4
[ 3510.802503] usb 5-1: configuration #1 chosen from 1 choice


Let me know if you see anything in that lot to work with.

Cheers

John

---


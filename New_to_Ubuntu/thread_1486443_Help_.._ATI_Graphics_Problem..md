---
title: "Help .. ATI Graphics Problem."
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Orejon on 2010-05-17
Hello all. First time post here.

I must say that I love Ubuntu and 9 was my first Linux OS ever.
I am sorry for posting this being there so many Ati driver posts already. However, I cannot find the help that I need. I have tried since Saturday (3 days) to fix my problem.

Here it is:
I have a nice Lenovo laptop with an ATI Radeon 3400 card running windows 7 and 10.04 (fresh install).
When ever I boot into Ubuntu the screen goes black.
I am able to get in if I edit the grub entry and use "nomodeset".
This puts me in "low resolution mode". 

Right now my system uses the Proprietary drivers from ATI, but those are the ones that are causing me the problem.

If I go to ATI web page I do not know what to choose (I chose what I thought was best and only made it worse .. had to delete the xorg.conf from the live CD).


How do I install Open source drivers if there are any.
Or a more broad approach, how can I make ATI Radeon 3400 work properly in ubuntu 10.04?

thanks in advance.

---

### Post by jbrown96 on 2010-05-17
The best way to install them is to use the hardware drivers utility. Use the nomodeset option to get into low graphics mode and go to System-->Administration-->Hardware drivers. It should allow you to install the driver. Reboot and everything should work. 

You probably don't want the open source drivers on a laptop since they don't have proper powersaving features yet.

---

### Post by Orejon on 2010-05-17
> **jbrown96 said:**
> The best way to install them is to use the hardware drivers utility. Use the nomodeset option to get into low graphics mode and go to System-->Administration-->Hardware drivers. It should allow you to install the driver. Reboot and everything should work. 

You probably don't want the open source drivers on a laptop since they don't have proper powersaving features yet.


Thanks Jbrown.

However, I already have the drivers. Those are the ones causing trouble. The only way I get in is using the "nomodeset". When I activate the proprietary drivers and reboot, I get stuck.


Oh and I really do not mind the "no powersaving" feature as I usually am connected anyways.

---

### Post by jbrown96 on 2010-05-17
Try downloading the drivers from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English") Then you can run ```
sudo sh Desktop/ati-driver-installer-10-4-x86.x86_64.run

``` If you downloaded it to your desktop (Firefox default). Just do a normal installation. 

If that doesn't work, then go back into low graphics mode and post the output to the following please. 
```
lspci | grep VGA
```
```
lsmod
```
```
cat /etc/X11/xorg.conf
```

---

### Post by Orejon on 2010-05-17
[B]Jbrown, 

[/B]Thanks for taking the time**. **Sorry to post and run, but have a cab waiting for me. [B]


lspci | grep VGA[/B]
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series


**lsmod**
Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513712  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_conexant    22577  1 
rfcomm                 33421  4 
sco                     7885  2 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
thinkpad_acpi          68083  0 
l2cap                  30624  16 rfcomm,bnep
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 33152  0 
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                2031  1 fbcon
iwlagn                105886  0 
i915                  283218  1 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore               106434  1 iwlagn
uvcvideo               57022  0 
font                    7557  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
bitblit                 4707  1 fbcon
snd                    54148  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20536  1 
sdhci_pci               5502  0 
videodev               34361  1 uvcvideo
softcursor              1189  1 bitblit
mac80211              204922  2 iwlagn,iwlcore
rsrc_nonstatic         10559  1 yenta_socket
soundcore               6620  1 snd
psmouse                63245  0 
v4l1_compat            13251  2 uvcvideo,videodev
sdhci                  15654  1 sdhci_pci
drm                   163143  3 i915,drm_kms_helper
nvram                   6171  1 thinkpad_acpi
vga16fb                11385  1 
led_class               2864  3 thinkpad_acpi,iwlcore,sdhci
serio_raw               3978  0 
ricoh_mmc               2923  0 
i2c_algo_bit            5028  1 i915
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
vgastate                8961  1 vga16fb
cfg80211              126517  3 iwlagn,iwlcore,mac80211
video                  17375  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
intel_agp              24473  2 i915
lp                      7028  0 
btusb                  10925  2 
parport                32635  2 ppdev,lp
agpgart                31788  3 drm,intel_agp
output                  1871  1 video
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
ohci1394               27238  0 
ahci                   32040  1 
ieee1394               81213  1 ohci1394
e1000e                120400  0 


**Cat /etc/X11/xorg.conf**
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by jbrown96 on 2010-05-17
It looks like you have two graphics cards, and the Intel driver is loading but not the ATI driver. You should try to blacklist the intel driver by putting > blacklist i915 anywhere in > /etc/modprobe.d/blacklist.conf Then try rebooting. If that isn't working, then repost ```
lsmod
```

---

### Post by TheMustangZone on 2010-05-17
> **jbrown96 said:**
> Try downloading the drivers from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) Then you can run ```
sudo sh Desktop/ati-driver-installer-10-4-x86.x86_64.run

``` If you downloaded it to your desktop (Firefox default). Just do a normal installation. 

If that doesn't work, then go back into low graphics mode and post the output to the following please. 
```
lspci | grep VGA
``````
lsmod
``````
cat /etc/X11/xorg.conf
```

Does this new driver work?  I noticed the release date says 4/28/2010.  I've been reading on here for some time that the older proprietary ATI drivers do not work.  I've been trying to get my video card working better, as well.  I tried installing the older driver and it crashed my video.  I had to revert back to the default settings, which I'm still using.  I would like to install this new driver, if will actually work.  Thanks.

Rob

---

### Post by ranch hand on 2010-05-17
I would, if you haven't, try the open driver.  It works better on my box than the ATI driver.

---

### Post by jbrown96 on 2010-05-17
> **TheMustangZone said:**
> Does this new driver work?  I noticed the release date says 4/28/2010.  I've been reading on here for some time that the older proprietary ATI drivers do not work.  I've been trying to get my video card working better, as well.  I tried installing the older driver and it crashed my video.  I had to revert back to the default settings, which I'm still using.  I would like to install this new driver, if will actually work.  Thanks.

Rob

Ubuntu 10.04 uses the 1.7 X-server, which was incompatible with ATI drivers before 4/28. During the development of 10.04, ATI made some drivers available for Ubuntu that were not available on ati.com. The drivers that the "hardware drivers" tool uses is 10.04, so there's no advantage to downloading the drivers from ati.com now. However, Ubuntu will stay on the 4/28 drivers for some time (not sure how long) whereas ati.com will have new drivers available near the end of May (they do monthly releases).

---

### Post by TheMustangZone on 2010-05-17
> **jbrown96 said:**
> Ubuntu 10.04 uses the 1.7 X-server, which was incompatible with ATI drivers before 4/28. During the development of 10.04, ATI made some drivers available for Ubuntu that were not available on ati.com. The drivers that the "hardware drivers" tool uses is 10.04, so there's no advantage to downloading the drivers from ati.com now. However, Ubuntu will stay on the 4/28 drivers for some time (not sure how long) whereas ati.com will have new drivers available near the end of May (they do monthly releases).

I haven't switched to 10.04, yet.  I'm still using 9.04.  Does this mean I can use this driver?  Thanks for the great info.

---

### Post by jbrown96 on 2010-05-18
> **TheMustangZone said:**
> I haven't switched to 10.04, yet.  I'm still using 9.04.  Does this mean I can use this driver?  Thanks for the great info.

9.04 should continue to work with new ATI drivers for the forseable future. ATI supports three distributions natively: Ubuntu, RHEL, and OpenSUSE (or maybe just SUSE). Ubuntu tends to be far more current with its X-server, so you should be fine with old Ubuntu versions for about 2 years with current ATI drivers. No guarantees.

---

### Post by Orejon on 2010-05-18
jbrown96,

Thanks for all your help so far.

I did all that you suggested, but nothing worked.
I tried so many things that I could no longer go back so I decided to wipe the partition and install 10.04 again.

So far I tried to install the driver from the link you suggested and also blacklist the intel card. Nothing has worked, the only way to get to my system is using "nomodeset".

**Here is the result from lsmod**

Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513712  0 
exportfs                3437  1 xfs
reiserfs              225633  0 
binfmt_misc             6587  1 
i915                  283218  1 
joydev                  8708  0 
usbhid                 36174  0 
hid                    67032  1 usbhid
rfcomm                 33421  4 
snd_hda_codec_conexant    22577  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
sco                     7885  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70886  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
bridge                 45582  0 
stp                     1655  1 bridge
snd_seq_dummy           1338  0 
bnep                    9436  2 
snd_seq_oss            26726  0 
l2cap                  30624  16 rfcomm,bnep
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 33152  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
thinkpad_acpi          68083  0 
radeon                694521  0 
snd_timer              19098  2 snd_pcm,snd_seq
iwlagn                105886  0 
iwlcore               106434  1 iwlagn
fbcon                  35102  71 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tileblit                2031  1 fbcon
ppdev                   5259  0 
ttm                    50071  1 radeon
font                    7557  1 fbcon
yenta_socket           20536  1 
mac80211              204922  2 iwlagn,iwlcore
video                  17375  1 i915
drm_kms_helper         29297  2 i915,radeon
bitblit                 4707  1 fbcon
uvcvideo               57022  0 
sdhci_pci               5502  0 
rsrc_nonstatic         10559  1 yenta_socket
psmouse                63245  0 
nvram                   6171  1 thinkpad_acpi
parport_pc             26250  1 
snd                    54148  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
softcursor              1189  1 bitblit
ricoh_mmc               2923  0 
sdhci                  15654  1 sdhci_pci
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
videodev               34361  1 uvcvideo
output                  1871  1 video
led_class               2864  3 thinkpad_acpi,iwlcore,sdhci
v4l1_compat            13251  2 uvcvideo,videodev
drm                   163143  5 i915,radeon,ttm,drm_kms_helper
serio_raw               3978  0 
intel_agp              24473  2 i915
cfg80211              126517  3 iwlagn,iwlcore,mac80211
agpgart                31788  3 ttm,drm,intel_agp
i2c_algo_bit            5028  2 i915,radeon
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               27238  0 
ieee1394               81213  1 ohci1394
ahci                   32040  1 
e1000e                120400  0

---

### Post by ranch hand on 2010-05-18
I really think you ought to try the open driver and if that isn't up to in try this ppa;

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

They are basically supplying the next version or so of th open driver.  Real nice the way it is going for ATI.

---

### Post by Orejon on 2010-05-18
> **ranch hand said:**
> I really think you ought to try the open driver and if that isn't up to in try this ppa;

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

They are basically supplying the next version or so of th open driver.  Real nice the way it is going for ATI.

Ranch,

How to I go about doing that (installing open Drivers)?

---

### Post by ranch hand on 2010-05-18
Well they should be on your box.  If you do have the ATI driver installed and then enable "desktop effects" to "normal" or "extra" you should get whatever version is in the repo installed right then.

My card (see sig) is not well supported at all.  There has only been an ATI driver for it for about 6 months or so.  I do not really like having my settings at anything but "none" but I wanted to test Gnome Shell last testing round (10.04).

I could not run compiz (don't like it but if that doesn't run GS probably won't) and I added the ppa to my sources list and their stuff just comes in and installs when you upgrade (I use apt but I am sure Update Mangler will do the job).

There are directions on the page that I sent the link for that will tell you how to install the ppa.  I do not have it on right now because the one in the repo caught up as far as letting things like compiz and GS to run on here.

I would give it a try.

There is also a link on the xorg.edgers page for "ppa-purge" or some such name.  Install it and it makes it easy to get rid of any ppa that you no longer want and revert you to the default.  That makes it easy to try something and get rid of it if it doesn't work for you.

I am on 10.10-testing right now.  This is pretty much just 10.04 with the 2.6.34 kernel right now.  The drivers that are on here are probably what the edgers bunch is packaging for 2.6.32 right now.

As I am typing this I just switched my effects to extra.  The OS searched for the driver and switched me to that from none.  This used to freeze the box so tight I had to unplug the sucker to reboot if I was doing nothing at all on it.  Right now my cpus (see sig) are cranked out at 99 to 100% because of the way I have boinc set up to crunch numbers.  The box is running fine.  I will switch back directly but I can do this.

---

### Post by Orejon on 2010-05-18
After trying pretty much anything I could get my hands on without luck:

I reinstalled 10.04 without a network connection so it did not "load" the latest drivers for my card during install. Everything seems to be working and I am keeping away from installing any video drivers. The one that is using seems to be working ok (if not a little slugish), but they will do.


I wish I knew what the deal really is. But for now I will keep whatever default driver is using.

thanks for all your help.

---

### Post by jbrown96 on 2010-05-19
It looks like the Intel driver (i915) and open source ATI driver (radeon) are being loaded, but the correct ATI driver (fglrx) is not. Perhaps, there is a way to disable the Intel card in your BIOS.

Other than that, I don't have any suggestions.

---


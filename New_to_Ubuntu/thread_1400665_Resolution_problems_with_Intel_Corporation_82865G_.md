---
title: "Resolution problems with Intel Corporation 82865G Integrated Graphics Controller."
date: 2010-02-07
forum: New to Ubuntu
---

### Post by sigurdkaare on 2010-02-07
I have just upgraded to Ubuntu 9.10. Everything worked out well. But then I made the first updates in update manager. I restarted after the updates and then suddenly the resolution turned out to be 1024x768, but the desktop was only visible in a 1/4 of the screen. Everything else was just black. I tried to go back to the old resolution 800x600. Then the desktop turned out to fill 2/5 of the screen. I'm now stocked with a resoluton of 640x480. 

What can I do?

My graphic card is 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)  

My xorg.conf is empty.

And there is nothing visible when i Open system -> Admin -> hardware drivers

---

### Post by Leppie on 2010-02-07
is your xorg.conf really empty, or does it not exist? if it does exist and is empty, try deleting it.

---

### Post by sigurdkaare on 2010-02-07
It does not exist.

Any suggestion for a solution?

---

### Post by Leppie on 2010-02-07
could you post the output of the command:
```
lsmod
```

---

### Post by sigurdkaare on 2010-02-07
> **Leppie said:**
> could you post the output of the command:
```
lsmod
```

Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
iptable_filter          3100  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
ppdev                   6688  0 
joydev                 10240  0 
zd1211rw               45472  0 
mac80211              181140  1 zd1211rw
cfg80211               93052  2 zd1211rw,mac80211
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
vesafb                  5696  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
e1000                 119264  0 
floppy                 54916  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by jward3010 on 2010-02-07
Something that can fix resolution problems in Ubuntu is this command:
```
sudo dpkg-reconfigure xserver-xorg
```
You'll have to do a restart afterwards.

---

### Post by sigurdkaare on 2010-02-07
I tried it. I don't think it fixed anything. I just typed it in to the terminal and then it asked for my password. I wrote it and then nothing more happend. I restarted and I stil have the same issue with the resolutions.


ps.
My monitor is: AOC LCD monitor LM520A

---

### Post by jward3010 on 2010-02-07
> **sigurdkaare said:**
> I tried it. I don't think it fixed anything. I just typed it in to the terminal and then it asked for my password. I wrote it and then nothing more happend. I restarted and I stil have the same issue with the resolutions.


ps.
My monitor is: AOC LCD monitor LM520A
As you wrote that, I've been reading around that the command no longer does resolution detection or resolution fix problems, sorry about wasting your time - it used to be the handiest command ever. There has been a bunch of complaints about that.

---

### Post by sigurdkaare on 2010-02-07
> **jward3010 said:**
> As you wrote that, I've been reading around that the command no longer does resolution detection or resolution fix problems, sorry about wasting your time - it used to be the handiest command ever. There has been a bunch of complaints about that.



Hey. Thanks for trying. You don't have any more ideas?

---

### Post by falconindy on 2010-02-07
> **jward3010 said:**
> As you wrote that, I've been reading around that the command no longer does resolution detection or resolution fix problems, sorry about wasting your time - it used to be the handiest command ever. There has been a bunch of complaints about that.
Complaints should be directed to the 'sudo Xorg -configure' command.

@OP: Try [enabling KMS]("https://wiki.ubuntu.com/X/KernelModeSetting").

---

### Post by sigurdkaare on 2010-02-08
> **falconindy said:**
> Complaints should be directed to the 'sudo Xorg -configure' command.

@OP: Try [enabling KMS]("https://wiki.ubuntu.com/X/KernelModeSetting").

Hi

Have do I make sure that I have the intel driver:

"Make sure you are using:

   1. The -intel driver 2.8.1-1ubuntu3 or later (note that UXA is enabled by default).
   2.

      Or a newer -intel from the xorg-edgers PPA"

---

### Post by Grenage on 2010-02-08
Try this as your xorg.conf:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "AOC"
	ModelName "LM520A"
	HorizSync 30 - 60
	VertRefresh 55 - 75
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82865G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

---

### Post by Leppie on 2010-02-08
> **sigurdkaare said:**
> Have do I make sure that I have the intel driver:

"Make sure you are using:

   1. The -intel driver 2.8.1-1ubuntu3 or later (note that UXA is enabled by default).
   2.

      Or a newer -intel from the xorg-edgers PPA"
you are actually using the kernel module:
```
Module                  Size  Used by
[COLOR=Red]i915[/COLOR]                  221320  3 
drm                   159584  3 [COLOR=Red]i915[/COLOR]
i2c_algo_bit            5760  1 [COLOR=Red]i915[/COLOR]
[COLOR=Red]intel_agp[/COLOR]              27484  2[COLOR=Red] i915[/COLOR]
agpgart                34988  2 drm,[COLOR=Red]intel_agp[/COLOR]
video                  19380  1 [COLOR=Red]i915[/COLOR]
output                  2780  1 video
```

---

### Post by sigurdkaare on 2010-02-08
To Grenage

I tried it as my xorg.conf. I dont think it changed anyting. The same problem as described in my first post.

I dont know if it changed anything but i installed StartUp-manager to try to fix the problem. It did not fix anything, but I managaned to put the 640x480 resolution as default. I have know removed the program, but the resolution is still 640x480 after restarting etc.

---

### Post by Grenage on 2010-02-08
Try putting this in the *device* section of xorg.conf:

```
Option "ModeValidation" "NoTotalSizeCheck"
```

---

### Post by sigurdkaare on 2010-02-08
> **falconindy said:**
> Complaints should be directed to the 'sudo Xorg -configure' command.

@OP: Try [enabling KMS]("https://wiki.ubuntu.com/X/KernelModeSetting").

Dear falconindy

I have now done this that yout link suggested:

>  b. Or, to turn it on permanently, create (if necessary) /etc/modprobe.d/i915-kms.conf with this line:

 options i915 modeset=1 

After that I tried to Verify that KMS is loaded:

```
sigurd@sigurd-desktop:~$ dmesg | grep drm
[    1.627632] [drm] Initialized drm 1.1.0 20060810
[    1.824407] [drm] fb0: inteldrmfb frame buffer device
[    1.824477] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.927826] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    1.940213] [drm] DAC-5: set mode 1024x768 14
[   48.748354] [drm] DAC-5: set mode  15
[   79.194121] [drm] DAC-5: set mode  17
[   83.437784] [drm] DAC-5: set mode  18
[   87.901046] [drm] DAC-5: set mode  1b
[   91.493462] [drm] DAC-5: set mode  1c
[  101.894157] [drm] DAC-5: set mode  1e
[  119.747934] [drm] DAC-5: set mode  1f
```

Is this good or bad?

---

### Post by sigurdkaare on 2010-02-08
This is a screenshot og my problem. Maybe it can help you to help me:)

---

### Post by sigurdkaare on 2010-02-08
> **Grenage said:**
> Try putting this in the *device* section of xorg.conf:

```
Option "ModeValidation" "NoTotalSizeCheck"
```

It did't change anything.

---

### Post by Grenage on 2010-02-08
That screenshot is certainly funky, I wonder if it's an EDID issue?

---

### Post by sigurdkaare on 2010-02-08
> **Grenage said:**
> That screenshot is certainly funky, I wonder if it's an EDID issue?


How can I tell if it is a EDID issue and what can I do about it, if it is?

---

### Post by Grenage on 2010-02-08
Unfortunately I only know how to grab EDID settings on an nvidia card, but maybe someone else will chime in with more intel experience.

---

### Post by sigurdkaare on 2010-02-08
> **Grenage said:**
> Unfortunately I only know how to grab EDID settings on an nvidia card, but maybe someone else will chime in with more intel experience.


Ok. I will cross my fingers.

But thanks for the help anyway!

---

### Post by sigurdkaare on 2010-02-10
I now think I find out where the problem is located. I reinstalled 9.10 and everyting worked out fine. I copy pasted the visible conten of my old home folder(from 8.10) from an external harddisk. Everying was stil fine, but then I remembered that I wanted my old settings for ktorrent, filezilla etc so I copy pasted all the invisible files from aswell. After this my problem was there again. Se attached file.

I think that there is some graphic files in my home folder that is ******* it up. Any suggestion for what to delete?

This is my homefolder 

/home/sigurd/autosave
/home/sigurd/Desktop
/home/sigurd/Documents
/home/sigurd/download
/home/sigurd/Downloads
/home/sigurd/Music
/home/sigurd/Pictures
/home/sigurd/Public
/home/sigurd/Templates
/home/sigurd/Videos
/home/sigurd/WEBBANK
/home/sigurd/.adobe
/home/sigurd/.audacity1.3-sigurd
/home/sigurd/.audacity-data
/home/sigurd/.azureus
/home/sigurd/.cache
/home/sigurd/.compiz
/home/sigurd/.config
/home/sigurd/.dbus
/home/sigurd/.evolution
/home/sigurd/.filezilla
/home/sigurd/.fontconfig
/home/sigurd/.fr-8JigAa
/home/sigurd/.fr-WKnMxx
/home/sigurd/.gconf
/home/sigurd/.gconfd
/home/sigurd/.gegl-0.0
/home/sigurd/.gimp-2.6
/home/sigurd/.gnome
/home/sigurd/.gnome2
/home/sigurd/.gnome2_private
/home/sigurd/.gnupg
/home/sigurd/.gstreamer-0.10
/home/sigurd/.gvfs
/home/sigurd/.icedteaplugin
/home/sigurd/.icons
/home/sigurd/.java
/home/sigurd/.kde
/home/sigurd/.local
/home/sigurd/.lordsawar
/home/sigurd/.macromedia
/home/sigurd/.mcop
/home/sigurd/.metacity
/home/sigurd/.mozilla
/home/sigurd/.mplayer
/home/sigurd/.nautilus
/home/sigurd/.netx
/home/sigurd/.nexuiz
/home/sigurd/.openoffice.org2
/home/sigurd/.pulse
/home/sigurd/.purple
/home/sigurd/.qt
/home/sigurd/.sane
/home/sigurd/.serpentine
/home/sigurd/.Skype
/home/sigurd/.ssh
/home/sigurd/.themes
/home/sigurd/.thumbnails
/home/sigurd/.ultamatix
/home/sigurd/.update-manager-core
/home/sigurd/.update-notifier
/home/sigurd/.w3m
/home/sigurd/.wapi
/home/sigurd/.warzone2100-2.1
/home/sigurd/david
/home/sigurd/examples.desktop
/home/sigurd/The_protest_guide(2).odt
/home/sigurd/.bash_history
/home/sigurd/.bash_logout
/home/sigurd/.bashrc
/home/sigurd/.compiz-gnomecompat
/home/sigurd/.disk-manager.conf
/home/sigurd/.dmrc
/home/sigurd/.esd_auth
/home/sigurd/.gksu.lock
/home/sigurd/.gnomad2rc
/home/sigurd/.grisbirc
/home/sigurd/.gtk-bookmarks
/home/sigurd/.gtkrc-1.2-gnome2
/home/sigurd/.ICEauthority
/home/sigurd/.lordsawarrc
/home/sigurd/.mcoprc
/home/sigurd/.netxrc
/home/sigurd/.profile
/home/sigurd/.pulse-cookie
/home/sigurd/.recently-used
/home/sigurd/.recently-used.xbel
/home/sigurd/.sudo_as_admin_successful
/home/sigurd/.usb-creator.log
/home/sigurd/.xsession-errors
/home/sigurd/.xsession-errors.old

---

### Post by sigurdkaare on 2010-02-10
> **Grenage said:**
> Unfortunately I only know how to grab EDID settings on an nvidia card, but maybe someone else will chime in with more intel experience.



I now think I find out where my resolution problem is located. I reinstalled 9.10 and everyting worked out fine. I copy pasted the visible conten of my old home folder(from 8.10) from an external harddisk. Everying was stil fine, but then I remembered that I wanted my old settings for ktorrent, filezilla, firefox etc. so I copy-pasted all the invisible files from the home folder aswell. After this my problem was there again. (Se attached file.)

I think that there is some graphic files in my home folder that is ******* it up. Any suggestion for what to delete?

This is my homefolder

/home/sigurd/autosave
/home/sigurd/Desktop
/home/sigurd/Documents
/home/sigurd/download
/home/sigurd/Downloads
/home/sigurd/Music
/home/sigurd/Pictures
/home/sigurd/Public
/home/sigurd/Templates
/home/sigurd/Videos
/home/sigurd/WEBBANK
/home/sigurd/.adobe
/home/sigurd/.audacity1.3-sigurd
/home/sigurd/.audacity-data
/home/sigurd/.azureus
/home/sigurd/.cache
/home/sigurd/.compiz
/home/sigurd/.config
/home/sigurd/.dbus
/home/sigurd/.evolution
/home/sigurd/.filezilla
/home/sigurd/.fontconfig
/home/sigurd/.fr-8JigAa
/home/sigurd/.fr-WKnMxx
/home/sigurd/.gconf
/home/sigurd/.gconfd
/home/sigurd/.gegl-0.0
/home/sigurd/.gimp-2.6
/home/sigurd/.gnome
/home/sigurd/.gnome2
/home/sigurd/.gnome2_private
/home/sigurd/.gnupg
/home/sigurd/.gstreamer-0.10
/home/sigurd/.gvfs
/home/sigurd/.icedteaplugin
/home/sigurd/.icons
/home/sigurd/.java
/home/sigurd/.kde
/home/sigurd/.local
/home/sigurd/.lordsawar
/home/sigurd/.macromedia
/home/sigurd/.mcop
/home/sigurd/.metacity
/home/sigurd/.mozilla
/home/sigurd/.mplayer
/home/sigurd/.nautilus
/home/sigurd/.netx
/home/sigurd/.nexuiz
/home/sigurd/.openoffice.org2
/home/sigurd/.pulse
/home/sigurd/.purple
/home/sigurd/.qt
/home/sigurd/.sane
/home/sigurd/.serpentine
/home/sigurd/.Skype
/home/sigurd/.ssh
/home/sigurd/.themes
/home/sigurd/.thumbnails
/home/sigurd/.ultamatix
/home/sigurd/.update-manager-core
/home/sigurd/.update-notifier
/home/sigurd/.w3m
/home/sigurd/.wapi
/home/sigurd/.warzone2100-2.1
/home/sigurd/david
/home/sigurd/examples.desktop
/home/sigurd/The_protest_guide(2).odt
/home/sigurd/.bash_history
/home/sigurd/.bash_logout
/home/sigurd/.bashrc
/home/sigurd/.compiz-gnomecompat
/home/sigurd/.disk-manager.conf
/home/sigurd/.dmrc
/home/sigurd/.esd_auth
/home/sigurd/.gksu.lock
/home/sigurd/.gnomad2rc
/home/sigurd/.grisbirc
/home/sigurd/.gtk-bookmarks
/home/sigurd/.gtkrc-1.2-gnome2
/home/sigurd/.ICEauthority
/home/sigurd/.lordsawarrc
/home/sigurd/.mcoprc
/home/sigurd/.netxrc
/home/sigurd/.profile
/home/sigurd/.pulse-cookie
/home/sigurd/.recently-used
/home/sigurd/.recently-used.xbel
/home/sigurd/.sudo_as_admin_successful
/home/sigurd/.usb-creator.log
/home/sigurd/.xsession-errors
/home/sigurd/.xsession-errors.old

---

### Post by Grenage on 2010-02-10
Honestly, I don't know.  I imagine it will be one of the Gnome folders, but I can't say for sure.

---

### Post by Leppie on 2010-02-10
if you still have the old folders backed up, try removing the following:
```
/home/sigurd/.compiz
/home/sigurd/.config
/home/sigurd/.gconf
/home/sigurd/.gconfd
/home/sigurd/.gnome
/home/sigurd/.gnome2
/home/sigurd/.gnome2_private
```

---


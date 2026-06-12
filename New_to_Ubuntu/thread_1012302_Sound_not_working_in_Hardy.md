---
title: "Sound not working in Hardy"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by markc7 on 2008-12-15
Hi,

Yesterday I finally got around to upgrading to Hardy.  Now my sound has disappeared!  I had previously been running gutsy.  My computer is a Dell Inspiron 1525.  Here's what I've tried and found so far:

The volume control icon shows mute, but when I click it, it says "No volume control GStreamer plugins and/or devices found."  

GStreamer shows up as being installed in synaptic.  I tried reinstalling it, and this had no effect.

I went to the [Comprehensive Sound Problems Solution Guide](http://ubuntuforums.org/showthread.php?t=205449) and followed the steps there.  

aplay -l gives me:
"aplay: device_list:205: no soundcards found..."

lspci -v gives me:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Unknown device 022f
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

Looking on the ALSA website doesn't seem to help.  There is no listing for the driver for this particular device.  

I then followed the advice on getting ALSA drivers from a fresh kernel:

> 
(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop

After rebooting, there was still no sound.

A google search for my sound card revealed that this is similar to a known bug [(#122560)](https://bugs.launchpad.net/ubuntu/+bug/122560) but that one seems to be affecting Gutsy.  My sound had worked fine on gutsy.  

When I try: "find /lib/modules/`uname -r` | grep snd" I get a whole long list of modules, so I believe that the modules are installed properly.

Hmm, I think that's all I've tried so far.  Does anyone else have any suggestions?  Is there something I'm missing here?  Thanks!

---

### Post by markc7 on 2008-12-15
Found a solution here:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

---


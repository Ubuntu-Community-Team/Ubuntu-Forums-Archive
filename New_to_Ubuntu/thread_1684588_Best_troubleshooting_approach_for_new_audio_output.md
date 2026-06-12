---
title: "Best troubleshooting approach for new audio output problem?"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by carbon512 on 2011-02-09
I've asked for help in the [How to Karmic Koala on Acer 1410...]("http://ubuntuforums.org/showpost.php?p=10440947&postcount=186") thread, but I am trying to learn more. Fairly new to Ubuntu, very forgetful so I may as well be a brand new newbie.

Some update caused my Intel ICH9 82801 sound card to now fail to mute when I plug in speakers or headphones to the analog out jack. I don't know when this stopped working, only that it used to work and now doesn't. I seem to recall doing some audio related patch or update to fix a microphone issue... as well as several kernel updates... Not a hardware failure -- it still works properly if I boot into Windows.

I am trying to read through this bug report [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154/+index?comments=all"), that seems to address the same issue, but I think it is a little over my head. The main thing I gleaned from it was that having linux-backports-modules-alsa-lucid-generic installed is essential, and I do have that installed (with linux-backports-modules-alsa-2.6.32-28-generic there as well). 

Should I go back and boot in to previous kernels to find out if a particular kernel made it stop working? (I am running 2.6.32.68 but have a few previous ones in my boot menu.) I don't really want to revert, though - this update works fine otherwise.

Should I find and mess around in my configuration file for the Intel sound card?

Should I keep a written list of all the patches/updates I do in my late night bursts of amateur geekdom? [YES].

Should I have made a new thread in the Hardware and Laptops forum, since it might be more about the Intel sound card than my specific laptop, rather than posting the problem in the enormously long (but very helpful) "**How to: Karmic Koala on Acer 1410 / 1810T/       1810TZ"** thread specific to my laptop?

Thanks for helping a new one get more Ubuntu savvy. It is fun, except when it is a PITA and you just want to listen to music through headphones...

---

### Post by migs73 on 2011-02-09
Try looking through the generic Audio trouble shooting guide here;

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by carbon512 on 2011-02-09
Great resource. But ack, be careful what you ask for... heh.

I think this might shed light on my problem, but I am not sure what exactly ---

it looks like there is some kind of conflict here maybe?

```
xxx@xxx:~$ sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```but the physical PCI check shows just the one: (I did not copy all the other non-sound devices returned)

```

xxx@xxxx:~$ lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 029b
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at 94500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```Given that I know the card is supported because it works, does this look like it could be the problem? In the GUI sound preferences, there is only one device listed.

I am slowly trying to go through the other steps now (checking chipset, model, module, etc.)  it is a BIG mouthful and I need to take it bit by bit. Slog along on my own and learn a little, get a little help, repeat, etc. If you could point me in the right direction that would be great.

edited to add: I got as far as getting my alsa-info.txt file, noting that my alsa driver version is 1.0.23, different from the alsa library and utility version - 1.0.22. But from there I am over my head I am afraid.

---


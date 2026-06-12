---
title: "no sound when running gnometris game"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by GMachine_24 on 2010-08-21
Hi - I feel kind of silly about this but I cannot get the sound to work again on gnometris. The sound seems to work on everything else . . . I almost never play games but this is kind of annoying.

Thanks.


Sorry - I am running KK 9.10 on a Compaq Presario C500 laptop. The sound seems to work for everything else - movies, mp3 files, streaming audio from the Internet, etc.

I have gone through most of the steps here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

made a couple slight modifications but nothing major.

Running in a terminal the following nets the subsequent info for the Audio device (I left out all the other output):

```

uname@uname-laptop:/etc$ lspci -v | less


00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

Hope this helps.

---


---
title: "Lost all sound after installing a few audio production programs"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by coaxihuitl on 2011-03-11
I know this is a super common problem and I promise I have spent hours going through others posts, trying different fixes with no results whatsoever. I have two sound cards in my computer; one is on-board but turned off through the bios normally (I have it on right now) and the other is a pci soundcard which I know is supported by alsa as it worked until recently and this link [URL="http://www.alsa-project.org/main/index.php/Matrix:Main"]confirms.

Here is some other relevant information I've gathered so far:

My computer's motherboard is an Intel(R) Pentium(R) 4 CPU 3.20GHz running with 2 Gb of memory and two hard drives, one of 80 Gb running Ubuntu Intrepid the other of 160 Gb running Lucid Ubuntu Studio (the one I'm having sound issues with now). 

The kernel I'm working with right now is 2.6.32-29-generic and I've confirmed that the alsa modules match the kernel; I even followed the directions at [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules") to uninstall and reinstall the matching alsa module. I also seem to have the correct soundcore installed.

I also ran through the basic terminal commands to try and characterize what is going on:

**$ lspci -v | grep audio**

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Device 0179
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at ec00 [size=256]
        I/O ports at e8c0 [size=64]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel modules: snd-intel8x0

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
04:02.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)

04:02.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
        Subsystem: Device 4942:4c4c
        Flags: bus master, slow devsel, latency 64, IRQ 3
        I/O ports at ccc0 [size=64]
        Kernel modules: snd-ens1370

Audio-relevent info from:
**$ sudo lshw **
*-multimedia UNCLAIMED
                description: Multimedia audio controller
                product: ES1370 [AudioPCI]
                vendor: Ensoniq
                physical id: 2
                bus info: pci@0000:04:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: latency=64 maxlatency=128 mingnt=12
                resources: ioport:ccc0(size=64)
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: ioport:ec00(size=256) ioport:e8c0(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff

alsa-relevent information from the following:
**$ dmesg**
[  108.173964] gnome-alsamixer[1801]: segfault at 0 ip 0804cd44 sp bfcc75f0 error 4 in gnome-alsamixer[8048000+c000]
[  119.929474] lo: Disabled Privacy Extensions
[ 1064.635116] gnome-alsamixer[3548]: segfault at 0 ip 0804cd44 sp bff1a5e0 error 4 in gnome-alsamixer[8048000+c000]


**$ cat /proc/asound/modules**
-this does nothing for me as I seem to be missing the asound directory

Yet when I try aplay no sound cards are found:
**$ aplay**
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:608: audio open error: No such file or directory

I've tried running the gnome alsamixergui, but it crashes when I try to select sound card properties.

Finally I would like to include further information obtained by 
**$ wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh**
The results are at:
[http://www.alsa-project.org/db/?f=5fe9b8671fe95ca3d2119e459c913cae1c711b03]("http://www.alsa-project.org/db/?f=5fe9b8671fe95ca3d2119e459c913cae1c711b03")


At this point I'm starting to think I may need to do a fresh lucid install. If anyone could suggest anything more I'd be so grateful.

-coaxihuitl

---

### Post by coaxihuitl on 2011-03-11
I decided to try wiping all the alsa programs and reinstall them. There was a very helpful thread here:

[URL="http://ubuntuforums.org/showthread.php?t=1152630"]http://ubuntuforums.org/showthread.php?t=1152630
[/URL]
Now my sound card is recognized by all the alsa software; I'm back in business; it took me two days to finally post here and two hours more to find a decent answer...ha!

---


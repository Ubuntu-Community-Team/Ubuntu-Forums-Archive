---
title: "Odd sound issue"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by lckeeper1 on 2009-01-03
Hello all,

I'm having a very strange sound issue. I recently took out my SB Live 5.1 card in order to go to onboard sound due to a bug that was stated at the Wine site regarding ventrilo, right here: [http://bugs.winehq.org/show_bug.cgi?id=5178]("http://bugs.winehq.org/show_bug.cgi?id=5178")

Now I recompiled my alsa driver to include my onboard sound off of my nvidia nforce4 (CK804).

When I do aplay -l, I get the following:

```
dan@dan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So I know that my card is recognized. I was able to run ventrilo last night while playing WoW and to talk without a problem. There was no PTT bug either.

Now the only problem is that I have no sound out at all. I can't hear anything at all. So I can have my mic working and sound in, but nothing coming from my speakers.

I'm kind of at a loss that I have the mic and sound out working, but nothing on sound in. If anyone has an idea of where to go with this, it would be much appreciated. I miss my music :P

Thanks again!

---

### Post by lckeeper1 on 2009-01-04
Just bumping.

No success yet editing the asound.conf file.

Does anyone have a configuration that might work? I'm pretty new to this, especially the sound stuff.

Thanks!

---

### Post by gettinoriginal on 2009-01-04
There may be an answer in one of these:
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506),
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012),
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by lckeeper1 on 2009-01-04
Thanks a ton for pointing me in that direction. I'll be going through all those when I get back tonight!

Hope you had a great new year!

---

### Post by linux_tech on 2009-01-04
Also good to check is the comprehensive sound solutions guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and pulseaudio how-to here:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by lckeeper1 on 2009-01-06
First of all, thanks for all the help so far. Unfortunately, it's not helped my lack of sound. Now I don't even have my onboard sound recognized.

I have enabled the onboard sound via the BIOS. It is the Nvidia CK804 onboard card, which requires the snd-intel8x0 module.

I know I have that module installed because of the output in the following box: (I also compiled it from source with no errors)
```

dan@dan-desktop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/snd-bt-sco.ko
```

The snd-intel8x0 is right there on the bottom. 

Now when I try to put it into the kernel with modprobe, I get the following error:

```
dan@dan-desktop:~$ sudo modprobe snd-intel8x0
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I'm not sure what that means, or where to go from there. If I enter the plain sudo modprobe snd-, I get an error: 

```
dan@dan-desktop:~$ sudo modprobe snd-
FATAL: Module snd_ not found.
```

Oh yah, almost forgot. Here is the output from my lspci -v command. I assume this means that Ubuntu recognizes that my card is in there somewhere:

```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: DFI Inc Device 1001
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	I/O ports at f000 [size=256]
	I/O ports at ec00 [size=256]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0
```



Thanks for the help thus far. It's much appreciated. I've read the how-tos posted above and I'm still a bit stumped.

Thanks again!

---

### Post by lckeeper1 on 2009-01-07
Just a little bump.

Been working all morning and came up with the same problems.

---

### Post by king2007 on 2009-01-07
I have been searching and searching too since I upgraded to Intrepid Ibex... 
Windows XP and Vista no problem - then I considered returning to Hardy Heron... still have not found how to return to an older version of Ubuntu..... 
- when I boot I see a list of several items of Ubuntu with at the bottom windows - when I choose the last item I can go to XP or Vista.
Now when I use the second line it reads : 
kernel 2.6.27-10
SOUND !!
I just booted in : kernel 2.6.27-11 : NO SOUND.....
restarted in : kernel 2.6.27-10
SOUND
I do not know why, but maybe you can try too ?

---

### Post by lckeeper1 on 2009-01-07
Hey, thanks for the advice. I didn't have kernel 2.6.27-10 on my grub menu unfortunately.

Still no luck, but thanks!

---

### Post by gettinoriginal on 2009-01-07
> dan@dan-desktop:~$ sudo modprobe snd-intel8x0
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
I am not savvy about theses things, but usually when I get that message, I either did a typo, or inserted the wrong "symbol".  Since I do not know how to make modules, I have no idea how they should read, but these two read nothing alike:
```
/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/snd-intel8x0.ko
```  :confused:

Have you checked your dmesg log to see ??  Sorry, just observing, not suggesting there is a mistake there.  :P

---


---
title: "Microphone troubles, hissing sound and no recording."
date: 2010-12-15
forum: New to Ubuntu
---

### Post by ewpaisley on 2010-12-15
Hi everbody,

I'm pretty new to Ubuntu, and I've recently switched to Ubuntu 10.10. Which is great, except I can't my microphone(s) to work. I have of course plowed around the various forum threads, but can't seem to fix the problem. 

I'm on an Amilo Pa3515 with what I believe to be an Intel HDA sound card. My sound preferences refer to two microphones and a line-in (or they began to after I installed pavucontrol), so I guess I have two internal microphones, right and left.

At first, my computer didn't seem to detect any form of audio input, but I was somehow able to get it to recognize it, but it still doesn't record anything but a hissing, buzzing sound.
I've tried: 

[LIST]Unmuting everything in sound preferences and pavucontrol[/LIST]
[LIST]Telling Skype not to "automatically adjust my mixer settings"[/LIST]
[LIST]Opening alsamixer and trying to adjust the volume on the mic's[/LIST]
[LIST]Changing configurations in sound preferences, e.g. to "Analog Stereo Duplex". In "Digital Stereo Output (IEC958) + Analog Stereo Input" there's no sound at all. I have other options, but the closest to functioning sound seems to be "analog stereo duplex", but again -- just the hissing.[/LIST]
[LIST]Muting the right microphone[/LIST]
[LIST]Muting the left microphone[/LIST]

I also have an external, analog microphone from Logitech ([http://www.amazon.com/Logitech-Labtec-Desktop-Microphone-600/dp/B000O7K4LO/ref=dp_ob_title_ce](http://www.amazon.com/Logitech-Labtec-Desktop-Microphone-600/dp/B000O7K4LO/ref=dp_ob_title_ce)), but it doesn't seem to make much difference if it's plugged in or not.

I'd gladly post a screendump or something from the terminal, but I'm not sure what you'd need.

Thanks world.

---

### Post by helbent forleder on 2010-12-15
You don't probably won't manage to fix much by messing with the sound preferences.
You should have the Realtek ALC888 soundchip, so... I think  that your best bet is to try some to change a line in your /etc/modprobe.d/alsa-base file. Follow the instructions  in the second post here: [http://ubuntuforums.org/showthread.php?t=820959]("gksudo gedit /etc/modprobe.d/alsa-base")

But I recommend that you first back up the file. In a terminal simply type ```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
``` That way if everything goes wrong you can do ```
sudo rm /etc/modprobe.d/alsa-base
``` and then ```
sudo cp /etc/modprobe.d/alsa-base.bak /etc/modprobe.d/alsa-base
``` and be back at square one.

I'd bet that adding a line like```
options snd-hda-intel model=fujitsu-pi2515
```to the alsa-base file will do the trick, but there's no reason not to experiment.

Good luck!

---

### Post by ewpaisley on 2010-12-15
Thanks Helbent!

My file wasn't called .../alsa-base but /alsa-base.conf, but I was able to add the line you suggested, so it now picks up sound. 

( I also backed up the .conf-file )

However, the recordings are very low and there is still that strange hissing sound. Any ideas?

Also, the sound the microphone is recording is now being played by my loudspeakers - hissing and my voice, making for a strange echo and background noise.

---


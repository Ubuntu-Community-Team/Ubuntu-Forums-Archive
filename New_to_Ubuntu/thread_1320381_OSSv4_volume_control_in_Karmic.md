---
title: "OSSv4 volume control in Karmic"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by pzs on 2009-11-09
I just did dist-upgrade and, as usual, I need to fix my broken sound.

I have two sound cards, an Intel HDA and a Sound Blaster X-Fi. I've never been able to get anything out of the SB, but I can make the Intel HDA work with OSS. Sound works, but the Gnome volume control (connected to the media keys) does not change the volume. I can change the volume using the vmix0-outvol control in the ossxmix mixer, I just need to connect that to the gnome sound control. 

Under "Sound Preferences", there are no entries under hardware and "Dummy Output" in the Output tab, so not much to change there. I've tried the advice here:

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer)

and setting OSS there. The test buttons only produce continuous beeps. The volume control still doesn't work.

Previously, I had horrible shell scripts setting the volume in ossmix, but it worked with the nice Gnome control in Ubuntu 9.04, I think by setting things up in gstreamer. Not in 9.10 though. Any ideas?

---

### Post by Mornedhel on 2009-11-09
Hi,

Not 100% sure, but the volume control in Karmic seems to support PulseAudio only. It probably won't change until Lucid, too.

I toyed with the idea of writing a simple shell script to call ALSA's command-line mixer (most likely how you apparently did with OSS) and notify-send to display the results but never got around to it.

---


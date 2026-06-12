---
title: "Totem plays video but, no sound."
date: 2010-02-17
forum: New to Ubuntu
---

### Post by JerichoKru on 2010-02-17
Jeez, I think this might be my 3rd thread for the day!


Well, I'm not sure why (since it was working the last time I used it), Totem doesn't play sound.  However, as the title says, you can see the video fine.

In the audio section of the preferences, there is only the option of "Audio output type".  Additionally, the volume control is grey'd out.

I have all alsa channels un-muted and maxed.

---

### Post by mikewhatever on 2010-02-17
Can you start Totem from Terminal simply by typing **totem**, and post the output.
What about other apps, do they produce sound?

---

### Post by JerichoKru on 2010-02-17
> **mikewhatever said:**
> Can you start Totem from Terminal simply by typing **totem**, and post the output.
What about other apps, do they produce sound?

This is what I get after opening, playing a video, then closing Totem.

```
 jericho@JerichoXubuntuNote  ~  >  totem

** (totem:7014): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
/usr/lib/totem/plugins/bbc/installablecodecs.py:57: DeprecationWarning: Accessed deprecated property Package.candidateDownloadable, please see the Version class for alternatives.
  not pkg.candidateDownloadable):
/usr/lib/totem/plugins/bbc/installablecodecs.py:59: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  record = pkg.candidateRecord
 jericho@JerichoXubuntuNote  ~  >  

```

My music player, Exaile, plays sound and so does Flash in Firefox.  This also includes a few games I installed.

---

### Post by warp99 on 2010-02-17
With the video file can you post the output of this command:

```
ffmpeg -i $your_file
```

Just the parts below "built on Oct 13 2009 22:35:00, gcc: 4.4.1" or something similar.

---

### Post by JerichoKru on 2010-02-18
> **warp99 said:**
> With the video file can you post the output of this command:

```
ffmpeg -i $your_file
```

Just the parts below "built on Oct 13 2009 22:35:00, gcc: 4.4.1" or something similar.

My "test" video:

```
Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/jericho/Videos/MIRRORED THEORY - "Bring It Back".mp4':
  Duration: 00:04:29.08, start: 0.000000, bitrate: 816 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 1280x720, 25 tbr, 25 tbn, 50 tbc
At least one output file must be specified

```

---

### Post by warp99 on 2010-02-18
I think I know what the problem is. You codec for the audio is AAC and I believe this codec is in a different plugin set. You need to install the following packages in Synaptic or use "sudo apt-get install $name_of_package":

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Make sure that in your software sources you have the universe and multiverse repositories enabled.

---

### Post by JerichoKru on 2010-02-18
> **warp99 said:**
> I think I know what the problem is. You codec for the audio is AAC and I believe this codec is in a different plugin set. You need to install the following packages in Synaptic or use "sudo apt-get install $name_of_package":

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Make sure that in your software sources you have the universe and multiverse repositories enabled.

Nope, I already had them.  I even purged them and re-installed, no go.

---

### Post by warp99 on 2010-02-18
Try copying the file using mencoder:

```
mencoder "Bring It Back".mp4 -ovc copy -oac copy -o test.mp4
```

---

### Post by samantha_ on 2010-02-18
You need to have faac installed
click [here]("apt:/faac") to install.

---

### Post by JerichoKru on 2010-02-19
> **warp99 said:**
> Try copying the file using mencoder:

```
mencoder "Bring It Back".mp4 -ovc copy -oac copy -o test.mp4
```

The output video had no sound either.

> **samantha_ said:**
> You need to have faac installed
click [here]("apt:/faac") to install.

Nope, this did nothing.


In my original post, I mentioned that th volume control is greyed out, whether playing or not, and is set to mute.

I installed Gnome-Mplayer, to test if it was just Totem related or not.  Gnome-MPlayer has no problems whatsoever playing video OR sound.  So it has to be some issue with Totem.

If we can't figure this out, I'll just switch to Gnome-Mplayer.

---

### Post by kmaliagkas on 2010-11-22
I confirm the same problem. The VLC, xine and mplayer had no problem with sound at all. Only totem has gray out the volume bar and doesn't play any sound.

---


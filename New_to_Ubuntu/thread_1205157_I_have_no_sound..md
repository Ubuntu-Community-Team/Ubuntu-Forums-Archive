---
title: "I have no sound."
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Essar Allen on 2009-07-05
I've looked around trying to find a similar post, but in all of the other posts there's at least some sound (popping, sound at log-in but nowhere else, etc.) But I have no sound whatsoever.

I'm running Jaunty, 9.04 on a HP tx2000 and any assistance would be very much appreciated.

---

### Post by ivanvajar on 2009-07-05
Open Terminal and> sudo gedit /etc/modprobe.d/alsa-base.conf

At the end of file add> options snd-hda-intel model=hprestart and see if it helps

---

### Post by lhb1142 on 2009-07-05
First, I would right-click on the Volume Control in the upper right hand corner of the top panel; then click on Open Volume Control.

Click on the Preferences box found here and make sure that you have everything checked. Make sure that the Device is HDA Intel (Alsa mixer).

Then, under the Playback tab, make sure that everything is functional (there should be no red indicators showing something is disabled). Then make sure that all of the sliders are set to maximum.

You can also go into System > Preferences > Sound to make sure that everything looks okay; there are Test buttons there which you can try.

Finally I should attach a set of earphones (or an external loudspeaker system) to the headphone jack on your computer and listen through those.

Should all of the above fail, there is yet another option: go here < [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) > and CAREFULLY follow all instructions for the version of Ubuntu you are using.

I hope these suggestions are of some help to you. ):P

---

### Post by Essar Allen on 2009-07-05
Good thought, but no, that didn't fix it.

---

### Post by ivanvajar on 2009-07-05
Open up the Sound Preferences (System>Preferences>Sound) and change all the options to ALSA. For default mixer tracks, you want HDA NVidia (Alsa Mixer). Highlight the master track.
Next, a little bit of tweaking to ensure that all of our volume controls are on the same page.
Right click the volume control icon in the status tray and select preferences. Make sure it says HDA NVidia (Alsa Mixer) and that master is highlighted. Close that dialogue box and double click on the volume control icon to open up the channel mixer. &#8220;Headphone,&#8221; &#8220;PCM,&#8221; and &#8220;Front&#8221; should all be at max. The &#8220;Master&#8221; channel is the variable, that is when you want your audio soft you turn it down and when you want your audio loud you turn it up. The volume control icon in your status tray controls the master channel. After that restart.

---

### Post by Essar Allen on 2009-07-05
Gosh...that didn't work either. This is really starting to irk me.

No sound drivers showed up in Hardware Drivers...could that have anything to do with it?

---

### Post by ivanvajar on 2009-07-05
No, that's for proprietary drivers.

---

### Post by ivanvajar on 2009-07-05
> sudo gedit /etc/modprobe.d/alsa-base.conf is as we changed it?

Does > sudo gedit /etc/modprobe.d/alsa-base give you an empty file?

---

### Post by ivanvajar on 2009-07-05
Could you check if there is sound when you plug some speakers in?

---

### Post by Essar Allen on 2009-07-05
```
sudo gedit /etc/modprobe.d/alsa-base 
``` DOES give me an empty file, and do headphones count? Headphones don't give me any sound either.

---

### Post by ivanvajar on 2009-07-05
Open System>Preferences>Sound and see what happens when you change sound server (PulseAudio, OSS, ALSA). Yes, headphones count :-)

---

### Post by ivanvajar on 2009-07-05
This thing should work when for **default mixer tracks**, you select **HDA NVidia (Alsa Mixer)**.

---

### Post by sweetfishremix on 2009-07-05
> **ivanvajar said:**
> is as we changed it?

Does  give you an empty file?

Yea, I'm getting a empty file as well.

---

### Post by Essar Allen on 2009-07-05
> **ivanvajar said:**
> This thing should work when for **default mixer tracks**, you select **HDA NVidia (Alsa Mixer)**.

HDA ATI SB (Alsa Mixer) is all I've got...i've been using it instead doubting that it made a difference.  I'm just letting you know in case it does.

---

### Post by sweetfishremix on 2009-07-05
> **ivanvajar said:**
> This thing should work when for **default mixer tracks**, you select **HDA NVidia (Alsa Mixer)**.

Mine says " HDA ATI SB (Alsa Mixer) and when I activate it, still nothing happens. :[

---

### Post by Essar Allen on 2009-07-05
For HDA ATI SD ALC268 Analog (Alsa), when I tested it I got this error message: 

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

---

### Post by ivanvajar on 2009-07-05
This is X-file... Post a thread at laptop and hardware section and mention that we did > sudo gedit /etc/modprobe.d/alsa-base.conf and added > options snd-hda-intel model=hp at the end of file. I just don't get it. This thing worked for me.

---

### Post by sweetfishremix on 2009-07-05
> **ivanvajar said:**
> This is X-file... Post a thread at laptop and hardware section and mention that we did  and added  at the end of file. I just don't get it. This thing worked for me.

It's not working for us for some reason. ;[

---


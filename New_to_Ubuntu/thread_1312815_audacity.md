---
title: "audacity"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-03
I was looking for the rhythmbox record plugin but couldn't find one so tried audacity to record streamed audio.Unfortunately I don't have the stereo mix option so a no go.Does anyone know another program with which I can record stream audio?

---

### Post by Darce on 2009-11-03
Try the DownloadHelper plugin for Firefox.
Might be what your after.

---

### Post by dzon65 on 2009-11-04
I've got the firefox downloadhelper installed but there's no option for streaming audio.I'll check into that again.

---

### Post by lrcaballero on 2009-11-04
Try softonic.com search for Linux programs-multimedia and see what are your options!!! also try audacity.com and download the version for Linux from there (try it see what happens!).

Luis

---

### Post by dzon65 on 2009-11-04
Installed audacity from their site,it's the same one.As for the other site,the only one available is shareware.Too bad I can't find that rhythmbox plugin.The site where it used to be no longer exists.

---

### Post by dzon65 on 2009-11-04
I have soundrecorder installed but I can only record as ogg.

---

### Post by valvegrid on 2009-11-12
There's a couple of things that you might want to try, go to System>Preferences>Sound and in the Hardware tab make sure Audio Stereo Output is selected and not Audio Stereo Duplex, by switching these mine started working as it should and the mixer burst into life and Audacity started recording.

If you want to export to MP3 you have to have Lame installed, in Synaptic search for Lame and install libmp3lame0 then Audacity will find the library and export in MP3 for you.

---

### Post by Arup on 2009-11-12
One of the best for capturing streaming audio or video is vlc, its in the repos, give it a spin.

---

### Post by dzon65 on 2009-11-12
Arup.Looks good.Only,this is the latest vlc player and can't figure out how to set it.All video
instructions are on the older model.Do you happen to know a (video) tutorial on this latest vlc?Thanks in advance.

---

### Post by Arup on 2009-11-12
> **dzon65 said:**
> Arup.Looks good.Only,this is the latest vlc player and can't figure out how to set it.All video
instructions are on the older model.Do you happen to know a (video) tutorial on this latest vlc?Thanks in advance.

[http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html](http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html)


[http://wiki.videolan.org/Documentation:Play_HowTo/Basic_Use](http://wiki.videolan.org/Documentation:Play_HowTo/Basic_Use)

[http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

Some to start with.

Also suggest adding C. Korn ppa at [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc) to keep it latest.

---

### Post by dzon65 on 2009-11-12
> **valvegrid said:**
> There's a couple of things that you might want to try, go to System>Preferences>Sound and in the Hardware tab make sure Audio Stereo Output is selected and not Audio Stereo Duplex, by switching these mine started working as it should and the mixer burst into life and Audacity started recording.

If you want to export to MP3 you have to have Lame installed, in Synaptic search for Lame and install libmp3lame0 then Audacity will find the library and export in MP3 for you.

This depends on your soundcard,as for a lot off things it's kinda related to your system.I don't have the Audio Stereo Output option.But I'm glad it workd for you and thanks for the reply and tip.

---


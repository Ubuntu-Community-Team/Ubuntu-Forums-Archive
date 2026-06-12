---
title: "I broke VLC =("
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-02-24
I've been messing with customizing my desktop appearance, so I installed docky and compizconfig-settings-manager. I then decided to remove docky and try awn, then removed it and put cairo-dock. After all this, VLC stopped working (When I open it on it's own, it works fine, if I try to play a video, it crashes). I've tried removing cairo-dock, setting visual effects to none, purging both vlc and ubuntu-restricted-extras and reinstalling. None of this has helped, does anyone have any other ideas?

---

### Post by Sir Jasper on 2010-02-24
Hi Ozymandias_117,

I have no clue at all; however, your helping other Forum members has not gone unnoticed - so here is a bump.

My regards

---

### Post by bruno9779 on 2010-02-24
What graphic card do you have? and which driver do you have installed?

You could always try and compile VLC yourself.

here is the source : [http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

and here the compile instructions : [http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile)

and here you have a link to build from git: [http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html](http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html)

---

### Post by durand on 2010-02-24
Have you tried opening it in the terminal? Open Applications > Accessories > Terminal, type vlc and press enter. Then open your video as usual. What errors do you get?

---

### Post by Ozymandias_117 on 2010-02-24
@bruno9779 ATI Radeon HD 4770 I downloaded their drivers from their site and installed them. I haven't tried compiling, but since it worked beforehand, wouldn't the problem be elsewhere?

@durand vlc will open just fine, only problem is, it won't play anything. It doesn't give any error messages, just closes whenever I try to start a video

---

### Post by durand on 2010-02-24
Try vlc --verbose 2 maybe?

---

### Post by theozzlives on 2010-02-24
I  think durand is right, try to run it from terminal. Your choice of the dock you use shouldn't break VLC.

---

### Post by Ozymandias_117 on 2010-02-24
Could this be anything? 

```
[0x31946d8] main audio output warning: PTS is out of range (-30251), dropping buffer
[0x31946d8] pulse audio output debug: Pulse stream started
[0x31946d8] main audio output warning: output date isn't PTS date, requesting resampling (121093)
[0x31946d8] main audio output warning: audio drift is too big (121092), dropping buffer
[0x31946d8] main audio output warning: buffer is 97872 late, triggering upsampling
[0x31946d8] main audio output warning: output date isn't PTS date, requesting resampling (41025)
[0x31946d8] main audio output warning: audio drift is too big (138556), dropping buffer

```

---

### Post by Ozymandias_117 on 2010-02-24
Er... Nevermind... I still don't know what had caused the problem but apparently all I had to do to fix it was reboot... lol. Somehow I forgot that simple trick to fix 90% of computer problems... Sorry for wasting your time =\

---

### Post by terabyte1 on 2010-02-24
I suggest that you go into your system> administration> Synaptic Package Manager and type 'VLC' (without the quote marks) into the seach bar which is near the top of the Synaptic Package Manager(SPM) Box on the extreme right. (It is vertically oblong and has a 'V' in it), click on this box and type in VLC and click on search. When you find the VLC program, if the box next to it has a tick in it already, remove it and hit apply. Then when the SPM completes, do the search again as above, and put a tick in the box next to it, then hit apply at the top of the SPM.


What you have affectively done is unloaded VLC. Then re-loaded VLC in a fresh space. You should find that it will now work.


Cheers!

terabyte1 :guitar:

---

### Post by Ozymandias_117 on 2010-02-24
Apparently this is more than an isolated case, I just found someone who had the same thing in multimedia & video... Kinda curious what has caused it...

---


---
title: "Help! VLC won't play .wmv anymore!"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-02
For some reason VLC doesn't want to play anything anymore. It used to work on my old Ubuntu 9.04 install, but now for some reason after I did a fresh install it doesn't want to.

When I try to play them I get this message:

```

No suitable decoder module:
VLC does not support the audio or video format "wma2". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "MP4S". Unfortunately there is no way for you to fix this.

```

I get this error message for any video I try to play, for .avi it is either "XVID" or "DIVX" in place of "wma2" etc

I have the following codecs installed:

All the gstreamer codec packs (from Add/Remove programs)
w64codecs
ubuntu-restricted-extras
vlc-nox
vlc-data
vlc


VLC version: 0.9.9a Grishenko

---

### Post by humphreybc on 2009-10-02
Okay what the hell is going on here!

I decided the best course of action was to remove the VLC PPA and downgrade to the one available in the repositories. So I did this, as well as removing all the relevent packages... ie gstreamer plugins, w64codecs etc etc etc

Now my Synaptic Package Manager is all screwed up, it has a whole heap of files marked "local or obsolete" that depend upon things like "ubuntu-desktop" and "virtualbox-3.0" that if I remove them, it'll remove all that!! There's one there that seems to depend on every program I have installed, and it wants to remove all my programs to remove it!! But it lists it as obsolete!

I think it might have something to do with me adding third party PPA's for the following:

VLC
VirtualBox
Google
Openshot movie editor
Medibuntu

I would assume that when I installed Openshot, it installed a whole heap of dependencies that are beyond Jaunty, and when I disabled the openshot PPA, it said that these upgraded packages are obsolete?

VLC doesn't play anything, even with all the codecs installed, and uninstalling them is a nightmare. What on earth should I do!?

---

### Post by ninjapirate89 on 2009-10-02
My VLC did that to me just about an hour ago. I ripped a movie from dvd with Handbrake to .mp4 and I tried to play in VLC and it gave me a similar message. I played the video just fine in the default Movie Player and in Banshee. I don't know what is wrong with it. 
Edit -> See if Movie Player or something other alternative will work for you like it did for me.

---

### Post by humphreybc on 2009-10-02
Hmm. I've just finished removing all these packages and sorting out my Synaptic so it is clean and makes sense.

I've disabled my extra PPAs, and i'm going to install VLC + codecs from Add/Remove programs and see what happens...

---

### Post by humphreybc on 2009-10-02
Well, that was weird.

It works fine now. I just uninstalled everything "audio/video" I could think of... all plugins, codecs, programs, packages, you name it... including the restricted extras... then I made sure I removed all the old configuration files, and all the dependencies, then I cleaned apt-get, restarted, and then installed what I needed using Add/Remove programs and now everything is hunky-dory.

What the hell!

---

### Post by ninjapirate89 on 2009-10-02
> **humphreybc said:**
> Well, that was weird.

It works fine now. I just uninstalled everything "audio/video" I could think of... all plugins, codecs, programs, packages, you name it... including the restricted extras... then I made sure I removed all the old configuration files, and all the dependencies, then I cleaned apt-get, restarted, and then installed what I needed using Add/Remove programs and now everything is hunky-dory.

What the hell!

Thats too much work for me. I'll just use Movie Player. I don't really need VLC. Glad it worked for you.

---

### Post by mc4man on 2009-10-02
> Okay what the hell is going on here!

Your problem was that openshot ppa. It has updated ffmpeg libs that will prevent playback of  formats you previously were able to play (and now that you removed it and gotten the ubuntu repo ffmpeg libs are able to again 

I'd stay away from it

(( tested on a karmic install with a wma2 and a avc file that played in vlc before adding ppa and didn't after updating to the ppa's libavcodec, libavformat, ect.

---

### Post by Redsunz on 2009-11-06
I suspect Openshot.  Everything worked well for me except for some sound problems on 9.10. I should have gotten a clue after installing Openshot it uninstalled Blender.  Now I can't play any videos in VLC.  Looks like I will be reinstalling 9.10 tomorrow. :mad:
No more Openshot for me it looked promising but not if it hoses my computer.

---

### Post by humphreybc on 2009-11-06
Yeah it was Openshot that did it.

---

### Post by emeraldgirl08 on 2009-11-06
My VLC has started to act strangely. It worked fine yesterday and then today it will not play an AVI or FLV file I click on. Then after a minute after closing the GUI and reopening VLC it'll play. Oh...and the GUI seems to hang. I try to close VLC and it takes a minute to finally close or if I force it to close.

I wish there was a clear and easy way to decide what codecs to install w/o creating all kind of dependencies problems. I tried to keep my install of programs and codecs to a minimum this Ubuntu version round. 

Other than that my Ubuntu is ....Ubuntu. It's got some bugs to be worked out that I can live with. How do you know if you have Openshot installed???

**Edit:**

Nevermind I see that Openshot is a program. One that I did not install.

---

### Post by cadeirn on 2010-05-18
Change the video output from default, that solved the problem for me.

---


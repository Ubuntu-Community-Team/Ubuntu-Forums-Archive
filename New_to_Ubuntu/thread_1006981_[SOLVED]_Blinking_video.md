---
title: "[SOLVED] Blinking video"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by nefigah on 2008-12-09
Not sure what gives here, I hope someone can help me out ](*,)

I'm running 8.10 with an ATI 4850 using the evil drivers. (I imagine my problem has to do with that).

Any video I watch is unwatchably blinky. In VLC, I was able to fix this by following a suggestion on this forum and switching one of its properties to X11 I believe, making it mostly okay. But now I have the same problem when trying to watch, for example, .mov in Firefox. Unlike in VLC, there doesn't seem to be any options I can set, so I'm at a loss.

Thanks!

---

### Post by MasterShihoChief on 2008-12-09
As an anime watcher, I always used vlc when I was on windows, but found the new vlc on linux to be exactly as you say. I built and installed mplayer, after I used a different x264 package in the build. I then installed smplayer from add/remove programs, switched the renderer to gl2 and all my videos play flawlessly. I was extremely happy with it, I'm sure you will be too

If you want to try mplayer out, i recommend reading and following the following guide. It looks like a bit much, but once you get it working, you will never have to touch it again.

1. [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538) <<<follow this to install mplayer and all the codecs you require including the latest x264 build.

2. Install smplayer from add/remove programs

3. when u first start smplayer go to options>Preferences. Then click the video tab and change the output driver to gl2.

4. Kick back grab some popcorn and watch your video :popcorn:

---

### Post by MarblePanther on 2008-12-09
Compiz is usually the culprit with buggy video drivers

That is why i disable it (waste of resources and causes problems)

You can set the X11 video option in the firefox-mplayer also if that helps

---

### Post by nefigah on 2008-12-10
Thanks for the tips... I couldn't get totem to go away, however, even following those steps. If I disable the totem plugins, then Firefox just refuses to handle those MIME types, instead of using the mplayer plugin. It's ridiculous. So frustrating. :evil:

---

### Post by MarblePanther on 2008-12-10
Just uninstall totem from synaptic (and all its browser plugins, etc...)

Install mozilla-mplayer (or whatever the firefox-mplayer plugin is called)
Install mplayer and a a frontend for it like smplayer or gnome-mplayer

---

### Post by notoriousmic24 on 2009-02-09
I installed smplayer and mplayer and i still have blinking video. Flash videos like on browsers, firefox, work fine. Any ideas?

---


---
title: "[SOLVED] VLC slow to start"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by shankhs on 2008-12-09
I upgraded my ubuntu PC to 8.10 as a result vlc also got upgraded.The new vlc has cool features and I like it but it takes a whole lot of time to start the video though audio starts immediately.....:confused:
What should I do?
Is there any replacement for vlc???

---

### Post by MasterShihoChief on 2008-12-09
As an anime watcher, I always used vlc when I was on windows, but found the new vlc on linux to be exactly as you say. I built and installed mplayer, after I used a different x264 package in the build. I then installed smplayer from add/remove programs, switched the renderer to opengl and all my videos play flawlessly. Maybe you can just try installing mplayer, then smplayer, then changing the renderer to opengl, and try it out. I was extremely happy with it, I'm sure you will be too

---

### Post by shankhs on 2008-12-09
Can you please tell me from where did you get the binary of mplayer having different x264 packages in the build?

---

### Post by stevoo on 2008-12-09
vlc can plays everything .... try getting the newest vlc and build it from source if you have to.

Sometimes it is a little laggy, i have notices it too 

But you can try kafeine as well ...

---

### Post by MasterShihoChief on 2008-12-09
If you want to try mplayer out, i recommend reading and following the following guide. It looks like a bit much, but once you get it working, you will never have to touch it again. 

1. [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)   <<<follow this to install mplayer and all the codecs you require including the latest x264 build.

2. Install smplayer from add/remove programs

3. when u first start smplayer go to options>Preferences. Then click the video tab and change the output driver to gl2.

4. Kick back grab some popcorn and watch your video :)

---

### Post by mapes12 on 2008-12-09
For all things multimedia and video related have a look here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by shankhs on 2008-12-09
Thanks everybody...
I installed smplayer and watched the movie.
Thanx once again.

---

### Post by krychek on 2008-12-10
I don't understand why is this thread marked as "solved". The solution is to use another media player? I have the same issue with VLC. It's annoying to wait minutes until VLC finally starts. I couldn't find this bug reported on Launchpad.

---

### Post by Dr Small on 2008-12-10
> **krychek said:**
> I couldn't find this bug reported on Launchpad.

File one then ;)

---

### Post by krychek on 2008-12-10
> **Dr Small said:**
> File one then ;)
There is a new version of VLC, I should try that one first. I just haven't found a place to download a deb file for it.

---

### Post by philinux on 2008-12-10
> **krychek said:**
> I don't understand why is this thread marked as "solved". The solution is to use another media player? I have the same issue with VLC. It's annoying to wait minutes until VLC finally starts. I couldn't find this bug reported on Launchpad.

vlc starts for me in 1 second. To find out whats going on run it from the terminal. the command is just vlc.

---

### Post by krychek on 2008-12-10
> **philinux said:**
> vlc starts for me in 1 second. To find out whats going on run it from the terminal. the command is just vlc.
I can't test it right now but I guess it starts fast if I start it without any movie. How do I run from the command line with some movie? vlc /pathtomovies/movie.avi ? Probably I will find out how to do this, so you don't need to answer.

---

### Post by krychek on 2008-12-11
Ok, I tested it. VLC tries to connect to images.google.com. I don't have internet connection for my ubuntu box cuz I'm staying in a hotel this week. I don't think VLC should behave like this, it should start the video and then download whatever it wants to download.

---

### Post by smazain on 2010-07-12
yeah changing isnt the right solution... ws driving me nuts the whole day... noticed if u disable the media player startup speed returns bak to normal, tools>preferences>advanced>playlist> uncheck mediaplayer

now someone else may elaborate on how to make it usable with the mediaplayer

tried smplayer but hv to play files at increased speeds and vlc da one which keeps the pitch intact

---


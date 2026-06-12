---
title: "Blue tint on videos"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by expatCM on 2010-03-03
When I play back a video (avi / video_ts / mp4) I am seeing a strong blue tint.  Flesh tone appears as a turquoise.  This is with all media players whether it be smplayer / vlc / ....

All other programs appear to be working with the correct colors.  Photographs display without any tint at all.  It appears to be only video media that is affected.

Nvidia driver 185.18.36.  GeForce 9400 GT

Any ideas of what could be causing this.

---

### Post by jmszr on 2010-03-03
expatCM,

Here is a bug report and possible workaround for your problem: [https://bugs.launchpad.net/totem/+bug/395476](https://bugs.launchpad.net/totem/+bug/395476) .

---

### Post by expatCM on 2010-03-03
you really know your stuff ......  that is not only exactly the problem but the fix there also worked.

Thank you.

---

### Post by 3rdalbum on 2010-03-03
Oh, I never knew that's what caused it. Nvidia has never fixed that bug - they've only ever pushed it around from one card to another.

An easier workaround is to use the X11 video output, rather than Xv.

---

### Post by delectate on 2010-03-03
try latest driver

or reinstall ffmpeg

it seems,neither mplayer nor vlc,both of them use ffmpeg

---

### Post by mcduck on 2010-03-03
> **3rdalbum said:**
> Oh, I never knew that's what caused it. Nvidia has never fixed that bug - they've only ever pushed it around from one card to another.

An easier workaround is to use the X11 video output, rather than Xv.

..or, if your video player has option to swap U and V channels, that would also fix the colors.

---

### Post by dubref on 2010-04-30
As jmszr correctly noted, the fix is in [https://bugs.launchpad.net/totem/+bug/395476](https://bugs.launchpad.net/totem/+bug/395476) .

I had a very similar problem with my Nvidia G86 [GeForce 8500 GT] card in Ubuntu 9.10, somehow hue was set to maximum negative value(probably by Mplayer). 

Once I adjusted it to default(0) in Mplayer->Edit->Preferences->Display, all other video players(VLC,etc) started working perfectly.

Presumably, hue adjustment is somewhat global in nature for video.

---

### Post by fleamour on 2012-03-30
I have everyone looking like a smurf in YouTube videos.  11.10 latest kernel.

---

### Post by llamabr on 2012-03-30
This thread is two years old.  Please, if you have a problem, start a new thread, rather than resurrecting old closed threads.

---

### Post by souravc83 on 2012-03-30
Just FYI,
Seems to be due to a flash update.
There's already a thread here, in case you need to refer to.
[http://ubuntuforums.org/showthread.php?t=1948626&page=2](http://ubuntuforums.org/showthread.php?t=1948626&page=2)

---

### Post by fleamour on 2012-03-31
Yeah, thanks, sorry about that, did not check date...


:oops: :rolleyes: :oops:

---

### Post by Perfect Storm on 2012-03-31
Thread closed.

---


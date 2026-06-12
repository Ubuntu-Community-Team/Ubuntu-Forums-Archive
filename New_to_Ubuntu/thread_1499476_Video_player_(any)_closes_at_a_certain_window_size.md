---
title: "Video player (any) closes at a certain window size"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by mark01 on 2010-06-01
Hey guys,
I have a issue with video playback, doesn't matter what format (mp4, wmv or avi) when I resize the window any bigger it simply disappears, no warnings or dialogs of any sort. Full screen has the same effect, happens in all the players I have installed.
I am running 10.4, was Kubuntu till I removed KDE. Now running Gnome.
1.7GHZ Intel mobile 768MB of RAM.
Nvidia Ge Force 4200 Go at 1920*1200 (compositing runs flawlessly)
On a Dell Latitude D800
I'm not too sure what else to post but if you need to know more, just ask :)
Cheerio, Mark

---

### Post by Ozymandias_117 on 2010-06-01
Open a media player via the command line and play your video, resize and see if it throws any errors.

---

### Post by mark01 on 2010-06-02
> **Ozymandias_117 said:**
> Open a media player via the command line and play your video, resize and see if it throws any errors.

Same reaction.
```

[????????] x11 video output error: X11 request 133.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  815
  Current serial number in output stream:  816
Segmentation fault
```

---

### Post by Ozymandias_117 on 2010-06-02
I'm going to give you commands for VLC since your title says any video player does this, and I know it's settings/GUI the best.

Open VLC, go to Tools -> Preferences then on the left side select Video about 1/3 of the way down the page it says "Output" select X11 video output


Now open a terminal and type ```
gstreamer-properties
``` click on the Video tab and change the Default Output Plugin to X Window System (No XV)

---

### Post by mark01 on 2010-06-02
> **Ozymandias_117 said:**
> I'm going to give you commands for VLC since your title says any video player does this, and I know it's settings/GUI the best.

Open VLC, go to Tools -> Preferences then on the left side select Video about 1/3 of the way down the page it says "Output" select X11 video output


Now open a terminal and type ```
gstreamer-properties
``` click on the Video tab and change the Default Output Plugin to X Window System (No XV)

Thanks :) that has worked, but it is really choppy, I never had any issues with KDE, and I think I might still be using some of the backend of KDE, could this be an issue?

---

### Post by Ozymandias_117 on 2010-06-02
I wouldn't think so... vlc needs X11, but it doesn't really care what X11 is running... then the only other thing is your plugins... Which I don't see how those could be affected by what desktop environment you're using...

---


---
title: "TvTime how to edit x86config file"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by jettapup on 2010-09-19
Trying to get an older ATI all in wonder TV Tuner card working under TVTime starting TVTIME a window appears for a split second, and disappears, TVTIME Common problem tells me that the etc/x11/xf86config-4 file needs to edited to Video Overlay.

In Ubuntu 10.04 where is the x86 config file? I found x86 wrapper in the x11/directory, but no fx86config-4 file. Where would the overlay setting reside??

Probably a noob question but ya gotta start somewhere...
Thanks,
Jettapup

---

### Post by lkjoel on 2010-09-19
> **jettapup said:**
> Trying to get an older ATI all in wonder TV Tuner card working under TVTime starting TVTIME a window appears for a split second, and disappears, TVTIME Common problem tells me that the etc/x11/xf86config-4 file needs to edited to Video Overlay.

In Ubuntu 10.04 where is the x86 config file? I found x86 wrapper in the x11/directory, but no fx86config-4 file. Where would the overlay setting reside??

Probably a noob question but ya gotta start somewhere...
Thanks,
Jettapup
Is it up to date?
They might be referring to /etc/X11/xorg.conf.

---

### Post by jettapup on 2010-09-21
Is the advice in the TVTime common problem up to date? Don't know but the bug was reported  Submitted:

Nobody/Anonymous ( nobody ) - 2003-08-12 03:46:38 UTC
[http://preview.tinyurl.com/364yqwm](http://preview.tinyurl.com/364yqwm)
so I doubt it..  I'll look in  /etc/X11/xorg.conf.

---

### Post by Black_Tanto on 2010-09-21
I have been having sound problems on certain channels with TVtime. I start off having sound and then it goes silent, only on certain channels. I dont know if the problem is TVtime, PulseAudio or both.

---

### Post by jettapup on 2010-09-22
etc\x11\does not have a x11.org folder opr any config file

---

### Post by jettapup on 2010-09-26
Ok lets start over,
How does one find / and change the  option to select VideoOverlay??

Quoting common problem from TVTIME page @
[http://tvtime.sourceforge.net/problems.html#fgloverlay](http://tvtime.sourceforge.net/problems.html#fgloverlay)

With the Radeon FireGL drivers, the user has the option of having OpenGL use an overlay surface, giving 3D graphics without tearing, or video overlay surfaces for multimedia players. This can be set in the Device section for the fglrx of your /etc/X11/XF86Config-4 using:

    Option  "VideoOverlay"       

or

    Option  "OpenGLOverlay"      

To use tvtime, you MUST select VideoOverlay instead of OpenGLOverlay.
As before, I can not find any config file, As I suppose 10.04 has it burried somewhere.

Thanks for your time.
Jettapup

---

### Post by jettapup on 2010-11-29
Ok this is an old problem that I have never gotten a grip 0n...
I installed 10.10 and Tvtime stopped working... when the program was started, I'd get a black window, for half a second & then the window shut down... its the old over lay issue.. 
UNTIL.. the last update & I tried TvTime as i had not booted into Ubuntu for a while, and TV Time came up & stayed up.
I have NO Idea why it now works now.. I am assuming its in a recent up date,It started to work Friday after Thanksgiving.
I'd like a little insight if possible just for general info...

---


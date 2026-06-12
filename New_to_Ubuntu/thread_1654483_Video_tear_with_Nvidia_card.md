---
title: "Video tear with Nvidia card"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by blcpl on 2010-12-28
I've recently installed 10.10 on an old laptop (2.0ghz C2D, 2gb ram, Nvidia 7400go) and I'm experiencing issues with video playback. Any video I play, no matter the resolution, displays tearing, and a whole lot of it. A quick search trough the forums seems to show that the video driver is the culprit (and disabling all visual effects seems to solve the issue), but is it possible in some way to force vsync and keep the fancy-schmancy shadowing and window-dragging? The driver control panel has a "sync to vblank" option, but it doesn't seem to do anything...

Another video-related question: this video card doesn't support hardware accelerated video decoding, but I still played 1080p videos fine with win7, whereas in ubuntu they're unwatchable. I've tried the default video player (Totem), and both Gnome Mplayer and VLC without success. Is it possible to play hi-def video with these specs or should I give up?

Thanks in advance :)

---

### Post by ajgreeny on 2010-12-28
For the 1080 video, try mplayer in terminal ```
mplayer path/to/file
```.

If that works you can set those video file types to always use mplayer from a double click of the files, or from a right click in the mplayer video window.

I have a panasonic camera which takes MTS videos and the only app that plays them on my old machine, similar to yours, is straight mplayer.  Gnome-mplayer, totem, vlc etc are not of any use for those, thought all video players seem to work well on the very same files on my wife's much newer and faster machine.

---

### Post by yetiman64 on 2010-12-28
This [[COLOR=Blue]--link--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=8722686&postcount=1") helped me get rid of screen tearing with an nvidia gt240 vid card while using compiz, and playing back videos. *_For the final command to restartX_*, I used a slightly different command than listed,
```
sudo service gdm restart
```The problem made watching video painful, but using this fix in 10.04 has the playback now flawless.

The fix enables "sync to vblank" both in the driver settings and compiz settings and creates a startup entry for "NVIDIA settings" which has nvidia-settings load from a config file (I suspect this change is what allows nvidia-settings to keep the changes in place).

Edit: like the OP in the thread linked, I also used the optional changes as well (I set compiz refresh rate to 120 - ie double my video card refresh rate - and disabled "Detect Refresh Rate"), though these changes may not be necessary for you they are probably worth checking out.

---

### Post by blcpl on 2010-12-28
Thanks a lot for the advice :)

Tried running mplayer from the terminal, and while it plays 1080p files a lot better, it stills chugs here and there... and it doesn't have a timeline, so no scrubbing/fast forwarding (don't know if there are keyboard shortcuts tho), so I'll just use a more powerful machine for that.

The tearing seems to be gone, and that what the issue I was most interested in fixing, so thanks a lot!

---

### Post by yetiman64 on 2010-12-28
> **blcpl said:**
> Thanks a lot for the advice :)

Tried running mplayer from the terminal, and while it plays 1080p files a lot better, it stills chugs here and there... and it doesn't have a timeline, so no scrubbing/fast forwarding (don't know if there are keyboard shortcuts tho), so I'll just use a more powerful machine for that.

The tearing seems to be gone, and that what the issue I was most interested in fixing, so thanks a lot!

You can use the keyboard to control mplayer (my main player as well). 

For skipping forwards/backwards use the up and down arrows (for larger jumps) and the right and left arrows (for shorter jumps). The spacebar will pause/restart video playback and the "f" key toggles fullscreen/windowed. This is just a few of the options, for more lookup ```
man mplayer
``` in a terminal. The fourth section down "Interactive control" lists all the keyboard options.

---


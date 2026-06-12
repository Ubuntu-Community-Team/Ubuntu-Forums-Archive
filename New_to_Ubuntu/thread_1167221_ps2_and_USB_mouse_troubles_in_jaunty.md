---
title: "ps/2 and USB mouse troubles in jaunty"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by amor0fati on 2009-05-22
I have two separate internal boot drives with Jaunty installed on both of them.  My main drive is a sata drive, and my secondary is an IDE drive.  My mouse is a USB mouse with a ps/2 adapter.  Ever since installing Jaunty on my IDE, the mouse hasn't worked on it.  I once got it working with USB on that drive, but even that stopped working after the next reboot.

My mouse worked fine on my sata drive when I still had intrepid, but upon upgrading to jaunty, it would only work in USB.  I managed to fix it by:
```
sudo gedit /etc/rc.local
```
and then typing:
```
modprobe -r psmouse
modprobe psmouse proto=imps
```
before the exit 0 line.

However, after mistakenly following this:
> **psyke83 said:**
> 
I have a possible solution.

Make sure Rhythmbox is closed, then open a terminal. Then, pkill the "pulseaudio" process and launch Rhythmbox again, and see if the skipping stops. So:

```
$ pkill pulseaudio
$ rhythmbox
```

If the above worked, then this next part will allow you to use PulseAudio without annoying skips:

Make a backup and then edit /etc/pulse/daemon.conf, and replace the lines at the end of your config with the following in red:

```
; default-sample-format = s16le
[COLOR="Red"]default-sample-rate = 48000[/COLOR]
; default-sample-channels = 2

[COLOR="Red"]default-fragments = 8[/COLOR]
[COLOR="Red"]default-fragment-size-msec = 10[/COLOR]
```

Now, log out and log back in, then run Rhythmbox normally. If this works, please let me know the name of your sound card, i.e. the output of:

```
lspci | grep audio
```

Thanks!
in order to fix my skipping rhythmbox problems (which it didn't), before realizing it said that it was obsolete, my mouse once again ceased working in ps/2 and would only work in USB.

Apart from that, my mouse is extremely jumpy in USB, and the pointer sticks to the side of the screen whenever it moves between my dualscreens or sometimes it just jumps to the opposite side instead; both behaviors are extremely disruptive to functionality.  All of these problems have been unique to Jaunty for me.

---

### Post by amor0fati on 2009-05-28
I should also say that my keyboard is ps/2 and works fine, and that the usb-ps/2 adapter is the one that came with the mouse (logitech mx laser).

I've looked at many threads, and none seem to have any real solutions.  I tried editting my xorg.conf, but that put me in low-graphics mode.

I really need some help here.

---

### Post by LowSky on 2009-05-28
pulseaudio has nothing to do with your mouse, running those commands shouldn't do anything to your mouse.

what kind of mouse is it? do you have an old LiveCD, does the same thing happen while running that?

Last but not least mice go bad,  replacements cost as little as $5

---

### Post by amor0fati on 2009-05-28
> **LowSky said:**
> pulseaudio has nothing to do with your mouse, running those commands shouldn't do anything to your mouse.

Tell me about it!  I certainly can't explain it, but that's the only change I remember making between bootups.

> **LowSky said:**
> what kind of mouse is it? do you have an old LiveCD, does the same thing happen while running that?

It's a Logitech Mx Laser.  I can't seem to find my old live cd, but I'll make one and get back to you on this.

> **LowSky said:**
> Last but not least mice go bad,  replacements cost as little as $5

Doesn't seem likely.  The mouse stopped working in ps/2 exactly after upgrades or other changes and rebooting.  I managed to fix it the first time through a script, and it does work in USB, just not very well.  I'm not very keen on spending $5 that I barely have on a crappy mouse that I won't like using when it seems quite likely that my mouse, itself, is just fine.  Not to mention that a new mouse may not even work in the ps/2 slot.  Every indication tells me this is a software issue, but I guess I could be wrong.

---

### Post by amor0fati on 2009-05-28
Hmm, didn't seem to work on the live disks either, but I vaguely recall having to use USB when I first installed Intrepid and then magically finding it to work in ps/2 after a few updates.

HOWEVER, I managed to get it working by:
```
sudo gedit /etc/rc.local
```
and then typing:
```
rmmod psmouse
modprobe psmouse proto=imps
```
before the exit 0 line.
Workaround found here: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/335297]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/335297")

I am still getting that annoying pointer sticking thing when I move between screens, though, but my pointer is no longer jumpy.  Occassionally when I right click in a browser, it seems to assume random options within the right-click menu without a second click, but that's always happened for me with Ubuntu--not sure why.  

These issues are along the same sort of lines as windows randomly opening on my second screen, rather than the main screen (very annoying).  I still haven't been able to find solutions for rhythmbox, so I've switched to banshee, which runs quite slow but doesn't skip.  Ubuntu's got some really strange quirks, and if I could just find the solutions for those few, it would work perfectly.

---

### Post by amor0fati on 2009-05-28
I tried using the same fix on my secondary harddrive in CLI using nano, but it didn't work.  The mouse won't work in either USB or PS/2 on that drive.  I'm also still stuck in low-graphics mode on that particualr drive.  I think I can fix that in CLI using envy, but I doubt it will have an impact on my mouse issue.

---

### Post by amor0fati on 2009-05-28
Envyng didn't work.  I don't have the right kernel headers, apparently, and I can't figure out how to install them without use of a mouse.  I tried:
```
sudo apt-get install linux-headers-`uname -r`
```
but it couldn't find it.

---


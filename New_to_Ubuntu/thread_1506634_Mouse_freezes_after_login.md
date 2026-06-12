---
title: "Mouse freezes after login"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by sleepee on 2010-06-10
Ok...  this has been an annoying problem for me before, but now, it's serious.
ok, so i startup my laptop, and Ubuntu loads fine. i can move the mouse and click anywhere on the screen... until i enter my username and password and login.
as soon as i do that, for some reason, my mouse freezes.  i can't move it, or click on anything...
i've done hard reboots, soft reboots, rebooting into an old kernel, plugged in a usb optical mouse....nothing.  this has happened to me a few times before randomly, though not frequently, and i'd just reboot and be fine.  idk what's going on this time.. i don't even know where to begin to fix this..
right now, i'm using windows (which i hate using now) and the mousepad and pointer works fine, so im guessing it's not a hardware problem.


another thing... this actually started happening when my computer stopped detecting my keyboard strokes.  i was just browsing the internet, not doing anything unusual.  luckily, a reboot fixed that... unfortunately, after that reboot, i started getting my mouse problem..

any help would be appreciated.. thanx

---

### Post by nhasian on 2010-06-10
3rd one today.  here you go:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503)

---

### Post by sleepee on 2010-06-10
> **nhasian said:**
> 3rd one today.  here you go:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503)

wow, that was fast reply..

so i read that bug report.. i do have an hp dv7 laptop, so that seems to be exactly the same bug i have..
anyway, so any idea what can be done about it?  i'm still not sure what i'm supposed to do with the gnome-settings-daemon to make it work properly..
or do i just have to wait for an update for the bug to get fixed??

---

### Post by nhasian on 2010-06-10
as far as i can tell from launchpad, no one is working on fixing this bug yet.  another user mentioned pressing alt-o (letter o) would re-enable the mouse and keyboard but i haven't tried that.  personally i never use my touchpad (it sucks on the HP dv9500) so i use a wireless usb mouse.  as a result i'm not affected by the bug since i dont use the touchpad.

---

### Post by sleepee on 2010-06-11
> **nhasian said:**
> as far as i can tell from launchpad, no one is working on fixing this bug yet.  another user mentioned pressing alt-o (letter o) would re-enable the mouse and keyboard but i haven't tried that.  personally i never use my touchpad (it sucks on the HP dv9500) so i use a wireless usb mouse.  as a result i'm not affected by the bug since i dont use the touchpad.

that sux... :(
i did try that alt-o thing too...  didn't work for me.  neither did my usb mouse for some reason.
i rebooted like 50 times and nothing happened, but i pressed control-alt-f2 once, restarted x, and then the mouse worked...
i guess i just have to make sure not to turn off the mousepad while i wait for the fix.. if it ever comes..
thanx for the info though..

---

### Post by nhasian on 2010-06-11
actually you want to keep it disabled, and you will avoid the problem.  

> **sleepee said:**
> i guess i just have to make sure not to turn off the mousepad while i wait for the fix..

---

### Post by Rytron on 2010-06-13
> **sleepee said:**
> that sux... :(
i did try that alt-o thing too...  didn't work for me.  neither did my usb mouse for some reason.
i rebooted like 50 times and nothing happened, but i pressed control-alt-f2 once, restarted x, and then the mouse worked...
i guess i just have to make sure not to turn off the mousepad while i wait for the fix.. if it ever comes..
thanx for the info though..

Hi sleepee. How did restart x after you hit Alt + F2?

---


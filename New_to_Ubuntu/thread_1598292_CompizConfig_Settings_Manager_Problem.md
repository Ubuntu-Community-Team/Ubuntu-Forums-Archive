---
title: "CompizConfig Settings Manager Problem"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by burg1n on 2010-10-16
I just installed Ubuntu 10.10 on my dell Inspiron 1520. I installed CompizConfig Settings Manager (CCSM) and was messing around with it a little bit. I always thought the "wobbly windows" setting was funny and wanted to try it out again but I noticed that any effect I turned on wasn't actually working. Turning on ANY setting or effect in CCSM has no effect at all. The settings stay turned on, even through a reboot. I have tried rebooting many times, reinstalling CCSM, and a few other suggestions I've seen on other threads. I really don't care about wobbly windows but there are some settings I'd really like to have in there. Also, I have been having a problem with my mouse that I haven't been able to figure out but a lot of the threads with similar mouse problems say it's a video driver. I have an Nvidia Geforce 8400 m GS

When I go to System > Administration > Additional Drivers it lists 2 drivers. One of them is "recommended". When I go to the Nvidia website, go to linux drivers, enter my video card information, it gives me 1 driver, which is the same as the recommended one. I have tried CCSM with both drivers, after reboots and everything. The drivers don't seem to be different at all besides the non-recommended one makes my docky program lag a lot. 

Also, when I go to System > Preference > Appearance my Visual Effects is set to none. When I choose either of the other 2 settings it says searching for drivers, then says they were applied. But when I open Appearance again (even RIGHT away) the setting is changed back to none. One person told me this is normal when you have CCSM installed but I have not seen any information about it anywhere else so I'm just making sure.

Thanks :popcorn:

---

### Post by Quackers on 2010-10-16
If you haven't seen it already take a look at this thread and see if anything jumps out at you :-)
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by burg1n on 2010-10-16
> **Quackers said:**
> If you haven't seen it already take a look at this thread and see if anything jumps out at you :-)
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Thanks for the link, I downloaded and ran the compiz-check script and got the following:


```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) y

```

Why did it skip those? And when I installed ubuntu It wouldn't let me enable any kind of transparency with anything and my docky also didn't run because of a compositing error. SO I enabled metacity. I just disabled it when it asked me too and CCSM still isn't doing anything, and I dont have any transparency or shadows or anything but I'm going to reboot to make sure.

I ran this compiz-check again right after I disabled it and I got this:

```
 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [SKIP]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: glxinfo not installed 
```

Then it tells me to install glxinfo mesa-utils I did this and it's OK's all the way across!! Going to try to restart and hopefully everything is working but it's not right now.

---

### Post by burg1n on 2010-10-16
OK so..I rebooted my computer. After I log in I can't see my cursor!! It was pretty annoying but I made it to my appearance settings, the settings stayed at extra :)

and also the effects I am enabling in CCSM are fixed!!
I also believe my previous mouse problems are fixed (mouse moving kind of weird and by itself) 

BUT I have a worse mouse problem now :/ I can not see the cursor at all unless I change my appearance settings to none. The mouse still works, I just have to watch for stuff to highlight or whatever when I move my mouse all over the screen to find something.

What could be wrong now? Thanks for all of the help :)

---

### Post by Quackers on 2010-10-16
I'm glad Compiz seems to set ok now. Sadly I have no idea about the cursor problem :-( Maybe somebody will come along that has seen this before. I hope you get things fully sorted out soon :-)

Edit Actually I have had similar problems but that was some time ago and in a Mac OSX86 installation. That was caused (I think) By the framebuffer part of the graphics driver. BTW a new Nvidia driver appeared for me last night, version 260.19.12. but that was through a backport (X Updates ([http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) maverick)

---

### Post by burg1n on 2010-10-16
Alright!

Previously I had mentioned that I was having a weird problem with my mouse. I opened a separate thread for that problem and someone had suggested that I set "HWcursor "off"" in my xorg.conf. I did this and it had no effect but I never took that line out.

I just took that whole line out of the file and my cursor is back :)

Which is weird, because googling this problem with the cursor completely disappearing I saw someone suggest that you ADD that line. :P

w00t for wobbly windows!

---

### Post by Quackers on 2010-10-16
:):):) wobbly wobbly wobbly :lolflag:=D>=D>=D>

---

### Post by burg1n on 2010-10-16
Actually just forgot about something else, When I finally got CCSM to run, the title bars on almost all of my programs have disappeared. any ideas?

---

### Post by Quackers on 2010-10-16
It's possible that you need to reload the window manager. There are a couple of threads about the forum with various fixes. The one that works every time for me is to click on the Compiz icon in the Cairo dock and select Reload WM (but that's not much good to you I'm afraid).

---

### Post by burg1n on 2010-10-16
someone on a different forum mentioned the code:

gtk-window-decorator

I typed it in and of course, something wasn't installed, it installed it and I have title bars :D


Officially [Solved]...until I notice something else :P

---


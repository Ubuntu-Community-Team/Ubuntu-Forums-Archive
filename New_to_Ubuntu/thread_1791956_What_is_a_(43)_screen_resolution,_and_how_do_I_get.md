---
title: "What is a (4:3) screen resolution, and how do I get rid off it?"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by tekiy on 2011-06-27
My screen resolution is (4:3) . How do I get rid of the four by three ?
(I am referring to System/Preferences/Monitors)

---

### Post by oldfred on 2011-06-27
What video card & what monitor? Video card should detect monitor correctly, but if using an older one it may be settings in xorg.conf, but newer versions do not really use the old xorg files.

Mine is 4:3 but it is shown by nVidia as 1280x1024. My monitor is an early LCD and I like the vertical format rather than all the new one's that are wide screen.

Wide screen seems good for movies and TVs, but I rarely watch movies on the computer and most everything else vertical works better.

---

### Post by JRV on 2011-06-27
(4:3) means the screen is a multiple 4x3 pixels.
Like 800x600, 640x480, 1024x768 Etc.

What do you mean by "How do I get rid of it?"?

Do you want to have a wide screen format?

If you have an old computer you might be stuck with 4x3.

Look under System=>Administration=>Hardware Drivers to see if a different graphics driver is recommended.

---

### Post by tekiy on 2011-06-27
My computer is Amilo Li 2727 and is only 1 year old. 

So question remain, how do I get rid of this terrible (4:3) resolution,
or in other words, how do I get a wide screen ?

My graphics card is as follows

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)

---

### Post by uRock on 2011-06-27
Open your menu and go to System> Preferences> Monitors then you should be able to change the resolution there.

---

### Post by tekiy on 2011-06-27
My options are 800x600 (4:3)

---

### Post by uRock on 2011-06-27
Have you run the Additional Drivers application to see if there are any drivers offered?

---

### Post by tekiy on 2011-06-27
Yes I did. The problem remains

---

### Post by doas777 on 2011-06-27
> **tekiy said:**
> Yes I did. The problem remains
what driver did you install?

---

### Post by tekiy on 2011-06-27
I didn't install any driver, and also
  
it works fine on Ubuntu 8.10, so maybe it's possible
to deduct the problem this way.

---

### Post by doas777 on 2011-06-27
> **tekiy said:**
> I didn't install any driver.
that would be why you have a 4:3 res.
what kind of video card do you have?
```
sudo lshw -C Display
```

---

### Post by tekiy on 2011-06-28
See #4

---

### Post by Swagman on 2011-06-28
Try adding uni/multiverse to your software sources

You may find it'll then detect that your video has additional drivers available..

Which'll most likely cure your standard res issue

---

### Post by tekiy on 2011-06-28
Well, it worked on previous Ubuntu without any special drivers,
so why is it not working now?

It is strange but on Ubuntu 8.10 the resolutions are also mentioned
with (4:3), but when I select them they turn out to be widescreen
(except for high resolution which is fine always, but flash
proggies are to small then so I don't use it.)

"Universe" and "multiverse" sources are active.

---

### Post by oldfred on 2011-06-28
I think it was with 10.04 they moved some video stuff into the kernel. With 9.10 I did a clean install on my desktop and had absolutely no issues. With 10.04 and ever since I have had to add nomodeset to boot installer and on first boot. Once my nVidia driver is installed then everything is fine.

I booted my 3 year old laptop the see how it is configured. It has always just worked with Ubuntu. It currently has 10.10 installed but shows no custom video drivers and just shows the screen under monitor as 1280x800 (16x10), but it is a combo box that gives other options, all lower quality like 800x600. My display controller is Mobile 945GM/GMS/GME.

---

### Post by mcduck on 2011-06-28
> **tekiy said:**
> Well, it worked on previous Ubuntu without any special drivers,
so why is it not working now?

It is strange but on Ubuntu 8.10 the resolutions are also mentioned
with (4:3), but when I select them they turn out to be widescreen
(except for high resolution which is fine always, but flash
proggies are to small then so I don't use it.)

No, my "universe" and "multiverse" sources are always active.

Because the driver versions included in other versions would be different from the ones included in 8.10. :)

Anyway, the (4:3) is simply the aspect ratio of the resolution you are using, so your problem isn't the (4:3) part but not getting the correct resolution for your display.

And a resolution with aspect ratio of 4:3 will always be standard, not wide-screen. If you use such resolution and it fills your whole widescreen display, then it's your computer's display that's scaling the image (which will always result in blurry image).

Anyway, getting the correct reoslution for your display is simply a question of getting a workng driver for your graphics card. if the one included with Ubuntu isn't working for you, then I'd recommend trying a more up-to-date version form some PPA repository. For example you could check if [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") or [Ubuntu-X team]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") has more recent driver available for your graphics card.

---

### Post by uRock on 2011-06-28
It may just be me, but it looks like that model has a 4:3 monitor. 
[IMG]http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/lifebook/AMILO/Amilo-L/images/Li2727%20open.jpg[/IMG]

Installing drivers should give you more options to customize the output.

---

### Post by mcduck on 2011-06-28
> **uRock said:**
> It may just be me, but it looks like that model has a 4:3 monitor. 
[IMG]http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/lifebook/AMILO/Amilo-L/images/Li2727%20open.jpg[/IMG]

Installing drivers should give you more options to customize the output.

It's just you. ;)

Based on the specs, the machine has a 1280x800 WXGA display (which would make it's aspect ratio 16:10)

I suppose 16:9/16:10 is such a common aspect ratio that it doesn't really look that wide any more. Waiting for the manufacturers to jump into 2,35:1 or something so we could finally view movies full-screen without letter boxing...

---

### Post by jocko on 2011-06-28
> **uRock said:**
> It may just be me, but it looks like that model has a 4:3 monitor. 
[IMG]http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/lifebook/AMILO/Amilo-L/images/Li2727%20open.jpg[/IMG]

Installing drivers should give you more options to customize the output.

That screen is very clearly 16:10. Why are people so stuck up with telling tekiy about drivers? He has already stated what video card he has (Intel GM965/GL960). There are no proprietary drivers for intel cards. Intel makes open source drivers. As they are open source they are already included in ubuntu, and they are in use by default on supported hardware. So he already has the correct driver for his card.

@tekiy:
Sometimes the monitor is not detected properly and you end up with some safe standard resolution.
You should be able to add the correct resolution with xrandr or by making a custom xorg.conf. [This page]("https://wiki.ubuntu.com/X/Config/Resolution") explains it.

---

### Post by mcduck on 2011-06-28
> **jocko said:**
> Why are people so stuck up with telling tekiy about drivers? He has already stated what video card he has (Intel GM965/GL960). There are no proprietary drivers for intel cards. Intel makes open source drivers. As they are open source they are already included in ubuntu, and they are in use by default on supported hardware. So he already has the correct driver for his card.
A *certain* version of the drivers is indeed already included, but that doesn't mean that installing the *latest version* isn't a solution worth considering. Especially if the resolution was correct with another version of the driver that was used on some previous Ubuntu release.

---

### Post by jocko on 2011-06-28
> **mcduck said:**
> A *certain* version of the drivers is indeed already included, but that doesn't mean that installing the *latest version* isn't a solution worth considering. Especially if the resolution was correct with another version of the driver that was used on some previous Ubuntu release.
That's true, I meant the people who keep telling him to use the Hardware Drivers manager...

---

### Post by uRock on 2011-06-28
> **jocko said:**
> That's true, I meant the people who keep telling him to use the Hardware Drivers manager...

Why not offer help your way instead of trolling other peoples' methods? It is quite obvious that the built in driver isn't working and, therefore, another driver may be more suitable.

---

### Post by jocko on 2011-06-28
> **uRock said:**
> Why not offer help your way instead of trolling  other peoples' methods? It is quite obvious that the built in driver  isn't working and, therefore, another driver may be more  suitable.
I did offer my help:
> **jocko said:**
> @tekiy:
Sometimes the monitor is not detected properly and you end up with some safe standard resolution.
You should be able to add the correct resolution with xrandr or by making a custom xorg.conf. [This page]("https://wiki.ubuntu.com/X/Config/Resolution")[]("https://wiki.ubuntu.com/X/Config/Resolution") explains it.

It's just that I find it silly not to point out that some other people's advice will not help, both to help tekiy to filter among the advice and to tell people why their advice will not help.
I have never said that installing a *newer* driver won't help, just that there is no proprietary driver to be installed from the Hardware Drivers manager.
I apologize if you found that offensive. I did not mean to offend anyone, just trying to help.

Tekiy:
There is a newer intel driver in the [xorg-edgers ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") that you could try, but if that does not improve things I think the only solution is to  to [set up the correct mode for the monitor]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by tekiy on 2011-06-28
> **mcduck said:**
> And a resolution with aspect ratio of 4:3 will always be standard, not wide-screen. If you use such resolution and it fills your whole widescreen display, then it's your computer's display that's scaling the image (which will always result in blurry image).


I am using (4:3) because there is nothing else to choose, what is standard is not
something that I am asking.

800x600 is more blurry than the high resolution, but it is not blurred further by widescreen 
(as Ubuntu 8.10 proves), and even if it does I don't notice it, so I really need 
  a wide screen version of 800x600

---

### Post by uRock on 2011-06-28
jocko's info may be most helpful for you. I am guilty of not having much experience with Intel chipsets.

---


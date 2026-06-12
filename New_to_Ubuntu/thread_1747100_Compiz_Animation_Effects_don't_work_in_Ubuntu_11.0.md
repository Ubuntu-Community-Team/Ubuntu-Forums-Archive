---
title: "Compiz Animation Effects don't work in Ubuntu 11.04 Natty"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by angelziru on 2011-05-02
Hi everyone!
I had recently upgraded my OS to Ubuntu 11.04.
My CCSM effects work fine when using the 10.10 version but for some effects in 11.04, they no longer work.

I want to configure my animations (i.e. open, close and minimize) to effects like BURN, dream and the like, but they don't work.

I really want the burn effect.

Btw, paint fire on screen, wobbly windows, and water effects WORK in my laptop. It's just that the animations esp. BURN don't. :( 

Your help is highly appreciated! Thank you in advance.

---

### Post by ububopp on 2011-05-03
Hi,

I'm also experiencing a problem with the animations on compiz. My windows no longer roll up when I roll my mouse wheel like they used to in 10.10. I have enabled the shade and disabled options in animation section but nothing happens.
Was this feature disabled or is it a bug?
By the way I'm using 64 bit 11.04 and the radeon driver for my ati graphics card.

---

### Post by sikander3786 on 2011-05-03
Just installed compiz-fusion-plugins-extra package and tested all the animations like explode, burn, airplane, beam etc and all of those worked without even a glitch. I am using ATI Radeon X200 (an older card) with the open source Radeon drivers.

So which graphics card is there and which version of drivers is installed? What happens when you enable those effects? Unity crashes, compiz crashes or nothing?

---

### Post by alphacrucis2 on 2011-05-04
> **sikander3786 said:**
> Just installed compiz-fusion-plugins-extra package and tested all the animations like explode, burn, airplane, beam etc and all of those worked without even a glitch. I am using ATI Radeon X200 (an older card) with the open source Radeon drivers.

So which graphics card is there and which version of drivers is installed? What happens when you enable those effects? Unity crashes, compiz crashes or nothing?

The animations aren't working for me with Natty with unity desktop. Using fglrx with hd3400.

Edit. Now working. Not sure what was wrong

---

### Post by ububopp on 2011-05-04
My animations work but I was having a problem with the roll up option for shading not working with the mouse scroll. I got it fixed using ubuntu tweak. really cool app. Just to clarify I'm using the radeon driver on a hd4200 on a G61-511wm hp laptop.
Finally 11.04 is working the way I want it to.

---

### Post by EGamerHDK on 2011-05-05
From all the problems I personally had with Compiz and Unity I simply stayed away from it. It might have been updated so, I'll go play around with it when I get back onto my Ubuntu machine. If it doesn't work I'll download the compiz-fusion-plugins-extra package.

---

### Post by jonesints on 2011-05-05
I have an integrated graphics card on my laptop Intel GM965/GL960. That never stopped me from having the 3d graphics enabled and having the "wobbly window" and other compiz effects under 10.10.

Now under Unity I've tried enabling them but it seems you *require* to enable some graphic drivers in the proprietary drivers menu. The funny thing is none are detected and therefore  I just can't run compiz?!

Surely Unity is aiming to be idiot proof, but honestly, it seems to complicate things more!

ps, I also tried the Ubuntu Classic session with gnome shell but I still can't run the 3d effects. Makes me wonder this is 11.04 and not necessarily Unity?

---

### Post by EGamerHDK on 2011-05-06
> **jonesints said:**
> I have an integrated graphics card on my laptop Intel GM965/GL960. That never stopped me from having the 3d graphics enabled and having the "wobbly window" and other compiz effects under 10.10.

Now under Unity I've tried enabling them but it seems you *require* to enable some graphic drivers in the proprietary drivers menu. The funny thing is none are detected and therefore  I just can't run compiz?!

Surely Unity is aiming to be idiot proof, but honestly, it seems to complicate things more!

ps, I also tried the Ubuntu Classic session with gnome shell but I still can't run the 3d effects. Makes me wonder this is 11.04 and not necessarily Unity?

Yeah, I tried the cube again to no avail. Seems futile. Oh well. I like the basic-"ness" of it for now.

---

### Post by jonesints on 2011-05-06
Success! 

OK, I just had to do everything manually but it worked.

I made sure compiz was installed and running. the compiz --replace command can replace the window manager otherwise the Compiz Fusion Icon application can replace metacity.

Then installed missing packages, including CompizConfig Settings Manager

sudo apt-get install compizconfig-settings-manager 

and whatever extra plugins the same way.

Then just went to System Settings and had to enable the different effects manually. It may ask you to disable certain ones due to conflict. 

Note: the cube still didn't work it just messed things up big time. Bug?? 
Managed to fix things by going to Preferences in CompizConfig Settings and reset compiz settings to default.

---

### Post by sikander3786 on 2011-05-06
> **jonesints said:**
> Note: the cube still didn't work it just messed things up big time. Bug?? 
Managed to fix things by going to Preferences in CompizConfig Settings and reset compiz settings to default.

I hope this would help.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by EGamerHDK on 2011-05-07
> **sikander3786 said:**
> I hope this would help.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Ugh! Finally! A detailed way on how to do it. I'll have to try it when I get some time.

---

### Post by wildmanne39 on 2011-05-16
> **EGamerHDK said:**
> Ugh! Finally! A detailed way on how to do it. I'll have to try it when I get some time.

Hi, the easiest way to get compiz to work is to log out and then log in as ubuntu classic and you can install compiz without breaking unity. :P

---

### Post by pritam_par on 2011-08-10
Check out the link the issue has been solved here

[http://ubuntuforums.org/showthread.php?t=1747045](http://ubuntuforums.org/showthread.php?t=1747045)

---

### Post by beew on 2011-08-10
> **wildmanne39 said:**
> Hi, the easiest way to get compiz to work is to log out and then log in as ubuntu classic and you can install compiz without breaking unity. :P

No, that doesn't work. If you enable the cube in Classic it wouldn't carry over to Unity, you have to enable it in Unity. Someone suggested to install awn or the cairo dock first and make sure you have the menu available, that way, in case Unity crashes you have a way to logout, login etc. After that you can uninstall awn or Cairo.

---

### Post by haemphyst on 2011-10-30
OK...  I have tried everything suggested here, as well as nearly everyplace I have found any SORT of answer for this damn thing...  :P

I cannot make the burn plug in to work...  I have three PCs (two laptops and one desktop) and I can make nearly every OTHER desired feature work, and still no "burn".

ANY help?  Please?

It HAS to be something I am doing wrong, because they're all pretty much the same, as far as hardware is concerned, all 4GB RAM, and dual-core Intel CPUs at least...  All running 32-bit Lucid.

---


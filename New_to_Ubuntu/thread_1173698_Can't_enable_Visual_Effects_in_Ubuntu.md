---
title: "Can't enable Visual Effects in Ubuntu"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Twittery on 2009-05-30
Hello there ,

Quite some days ago I downloaded Ubuntu (Jaunty Jackalope) and everything went well .  I tried to change the visual effects from none to Normal ; soon my screen went blank and a dialogue box appeared which said **can't enable Visual Effects** . :( Any help is appreciated !!

---

### Post by Twittery on 2009-05-30
edit : I am totally new to Linux !!! :roll:

---

### Post by Elfy on 2009-05-30
open Hardware drivers - enable any drivers that it says are available.

If there are none available - open a terminal from the Apps - Accessories menu. Run this command and paste the output please

```
lspci |grep VGA
```

---

### Post by Twittery on 2009-05-30
> open Hardware drivers - enable any drivers that it says are available.Result : No proprietary drivers are in use on this system .

> **forestpixie said:**
> 

If there are none available - open a terminal from the Apps - Accessories menu. Run this command and paste the output please

```
lspci |grep VGA
```

[CENTER][U][SIZE=3]**lspci |grep VGA**

[/SIZE][/U][SIZE=3][SIZE=1][SIZE=2]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)[/SIZE]
[/SIZE]
[/SIZE][LEFT]Note:  Mine is an old PC .
[/LEFT]
[/CENTER]

---

### Post by QIII on 2009-05-30
Some older Intel graphics chipsets are not supported in 9.04.

Look here:

[https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes)


Look for the sections
"Performance regressions on Intel graphics cards" and "Display freezes with Intel graphics cards"


Then you may want to use the Search box above and investigate further.

---

### Post by Twittery on 2009-05-30
So you mean I can't enable them !! 
Awww

---

### Post by shaoxiao on 2009-05-30
The default graphic driver may can't support visual effect ! you may need to install the right driver by yourself . Then it will be fine !

---

### Post by lakersforce on 2009-05-30
> **shaoxiao said:**
> The default graphic driver may can't support visual effect ! you may need to install the right driver by yourself . Then it will be fine !

But this is a pain in the *** to do, especially since you are new (I've been using gnu/linux a couple of years and I think it's a pain...which means I havn't bothered). Your best solution at the present time is to go back to 8.10 or wait for 9.10. Unless ofc you can live without the funky desktop effects (which is the only part affected...3d acceleration still works reasonibly well.)

---

### Post by bobin on 2009-05-30
i had the same problem . by default (i think) proprietery drivers are not installed. u will have to do it manually. i couldnt installit from the appearances tab.  i had to download it from the nvidia (my case) site.

---

### Post by QIII on 2009-05-30
If you do install drivers yourself, be aware that you may get funky behavior if you try to use System -> Preferences -> Display.

Sometimes you have to make changes directly in xorg.conf.

---

### Post by shaoxiao on 2009-05-30
> **lakersforce said:**
> But this is a pain in the *** to do, especially since you are new (I've been using gnu/linux a couple of years and I think it's a pain...which means I havn't bothered). Your best solution at the present time is to go back to 8.10 or wait for 9.10. Unless ofc you can live without the funky desktop effects (which is the only part affected...3d acceleration still works reasonibly well.)
Sorry ,yes, enable visual effect(after install correct driver) may cause other problems (at least i came across)

---

### Post by Twittery on 2009-05-30
Thanks for the quick replies . I think I'd be better off  without any visual effects for the time being (after seeing all those posts ; hmm : no) . But I'd still stick around with Jaunty
[CENTER][SIZE=3]**                                       (Ubuntu Rocks)**[/SIZE][/CENTER]

---

### Post by b@sh_n3rd on 2009-05-30
Hi, I've got the 82845GV Integrated video adapter. I had to make a few changes to get some stuff working, like my screensavers. Now I've even got cairo-dock ([http://www.facebook.com/photo.php?pid=30396352&l=96820cf5bc&id=1421833186](http://www.facebook.com/photo.php?pid=30396352&l=96820cf5bc&id=1421833186)) :D.. ([COLOR=Red]WARNING: AWN WILL FREEZE YOUR SYSTEM WITH THE UPCOMING FIX[/COLOR]). Sadly, even though I've got it working to a certain extent, even *I* couldn't enable desktop effects, :'(. We'll just have to learn to live without it until the Ubuntu team takes pitty on us Intel users. Here's the fix. You should use "Optimal" as that will give you the best performance. Any questions, pls ask here. I'll be happy to help you :D.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

(All you had to do was put a peep in the **Multimedia and Video** section. This HOWTO is there, large as life :D)

**EDIT:** Before you try this fix, type: ```
# glxinfo | grep render
``` and post the output here

---

### Post by Twittery on 2009-05-30
[CENTER][SIZE=3][U][B]Output

[/B][/U][/SIZE]```
[SIZE=2]get fences failed: -1
param: 6, val: 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20090326 2009Q1 RC2 x86/MMX/SSE2[/SIZE]

```[/CENTER]

---

### Post by b@sh_n3rd on 2009-05-30
well..you definitely don't need the fix. queer though...at the time I was trying to fix my video prob, I got: ```
direct rendering: No
OpenGL renderer string: Software Rasterizer
```

You're plain lucky :D (I have no idea about the two lines above that, but it disappeared whenever I run that command after installing the newer kernels. It *does* however, appear with a different command)
---------------------------------------------------------------------------------------------------------------------
Since it was mentioned I thought I'd ask this.
If it's possible to manually build the driver for the 845, how would I do it? and where do I get the source from?

---

### Post by entr3p on 2009-06-04
I think this article might help you out. If you want you can bypass the blacklist and use the visual effects.

[URL="http://www.learningubuntu.com/articles/fix-intel-graphics-ubuntu-904-enabling-visual-effects"]
Fix Intel graphics on Ubuntu 9.04 - Enabling visual effects[/URL]

---


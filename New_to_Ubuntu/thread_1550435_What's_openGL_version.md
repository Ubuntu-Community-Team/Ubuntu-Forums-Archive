---
title: "What's openGL version?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by liva on 2010-08-11
Hey 

I am trying to install a software (Evaluation version of  Foundry Mari "www.thefoundry.co.uk") on my Linux (Ubuntu) and it once I run the app it tells  me:




Mari currently requires OpenGL version 2.0. OpenGL is reporting version 1.4




I am not any good in this kind of the thing, what does it mean, and most importantly what's the solution, if there's any!

Thanks

---

### Post by cybuss on 2010-08-11
> **liva said:**
> Hey 

I am trying to install a software (Evaluation version of  Foundry Mari "www.thefoundry.co.uk") on my Linux (Ubuntu) and it once I run the app it tells  me:




Mari currently requires OpenGL version 2.0. OpenGL is reporting version 1.4




I am not any good in this kind of the thing, what does it mean, and most importantly what's the solution, if there's any!

Thanks

OpenGL is ubuntu's version of directx i think it means you need a update on your opengl
im not sure if its updated with regular updates

---

### Post by Perfect Storm on 2010-08-11
I'm guessing you have an intel video card?

---

### Post by Macskeeball on 2010-08-11
OpenGL has to do with graphics. Programmers use it to make games, screensavers, etc.

[quote="Wikipedia"]OpenGL is a programming interface for 3D graphics which helps computer programmers make their 3D graphics perform better and faster by running parts of their programs on a video card (GPU) rather than just the central processor (CPU). Programming interfaces like OpenGL are usually called an "API," which stands for "Application Programming Interface".

OpenGL is often compared to Direct3D, an API for 3D graphics on Windows. Programming for Direct3D is different in some ways because the APIs use different naming schemes for talking to a computer's graphics driver, which means that programmers need to write different code for OpenGL and Direct3D to do the same things.
OpenGL is owned by the Khronos Group, and is an example of open source software. This means that all of OpenGL's programming, and the explanations for how the programming all works, can be viewed, copied, revised, and re-released by anyone.[/quote]

---

### Post by liva on 2010-08-11
> **Artificial Intelligence said:**
> I'm guessing you have an intel video card?


no, not actually, I happen to run a GEForce 7300!

---

### Post by liva on 2010-08-11
> **Macskeeball said:**
> OpenGL has to do with graphics. Programmers use it to make games, screensavers, etc.


Yeah, I kind of understand that, I am just wondering how should I upgrade mine. Is it something that is entirely dependent on the hardware or is it possible to upgrade it?

Thx

---

### Post by Zorgoth on 2010-08-11
I believe that card *should* support OpenGL 2.0.  There are two recommendations I would have:

1) Install the proprietary nVidia drivers using System > Administration > Hardware Drivers

2) See if that works, and if it doesn't, type in a terminal "glxinfo | grep direct" to see if you have direct rendering.  If it says something like "No.  LIBGL_ALWAYS_INDIRECT set," see if you can get "glxinfo | grep direct" to work right by first typing "unset LIBGL_ALWAYS_INDIRECT."  In most situations only applications launched by compiz (through keyboard shortcuts etc) will have this variable set, but I have seen it in other places.

To check your OpenGL version, type "glxinfo | grep -i opengl"
That should tell you both the OpenGL version you are using and what your card can support.

---

### Post by muteXe on 2010-08-11
> **cybuss said:**
> OpenGL is ubuntu's version of directx 

Eh?

---

### Post by Jmih on 2010-08-11
pranay@pranay-desktop:~$ glxinfo | grep direct
direct rendering: Yes
pranay@pranay-desktop:~$ glxinfo | grep -i opengl
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.7.1
OpenGL extensions:

btw how do update mine?

---

### Post by Zorgoth on 2010-08-11
> 
OpenGL vendor string: VIA Technology


Get a new graphics card, or if you have a laptop, a new computer.  If you want good OpenGL, you need an nVidia (#1), ATI (#2), or Intel HD/Intel X4500+ (#3) - Intel X3100 or Intel GMA 965/960/950/945/etc is in any real sense too old for anything but basic desktop use - they only support up to OpenGL 1.4 (compiz capable though).

---

### Post by Perfect Storm on 2010-08-11
> **Jmih said:**
> pranay@pranay-desktop:~$ glxinfo | grep direct
direct rendering: Yes
pranay@pranay-desktop:~$ glxinfo | grep -i opengl
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.7.1
OpenGL extensions:

btw how do update mine?

Lets see which card you have:
```
lspci |grep VGA
```

---

### Post by Jmih on 2010-08-22
> **Artificial Intelligence said:**
> Lets see which card you have:
```
lspci |grep VGA
```

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

### Post by Perfect Storm on 2010-08-22
> **Jmih said:**
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

See Zorgoth posts. You need another video card that supports OpenGL v2 or higher.

---


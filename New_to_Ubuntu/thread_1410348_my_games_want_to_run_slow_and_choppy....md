---
title: "my games want to run slow and choppy..."
date: 2010-02-18
forum: New to Ubuntu
---

### Post by one_nz on 2010-02-18
My games run slow and choppy on Ubuntu.

please note the following:
-windows vista ultimate 32-bit/ubuntu x86 jaunty (9.04) dual boot
-ATI radeon HD 4850, 512 mb, 256-bit memory interface
-AMD Athlon 64 X2 dual core 5000+ (about 2.6 GHz?)
-2 GB 240-pin DDR2 RAM
-Linux kernel 2.6.28-11 Generic
-WINE version 1.1.38

I have no problem running any game on vista genreally for most games i can turn the setting on high and it will still run fine.
However for ubuntu they run really slow and choppy.

quick answers:
-did you download and install the drivers for the video card?
=yes

-did you download and install the drivers for the CPU?
=i have no idea where to get them (HINT HINT)

I assume my problem is i don't have my CPU drivers...
-Do i need them?
-if yes, where do i get them?
-if no, then what is my problem?

---

### Post by DrMelon on 2010-02-18
> **one_nz said:**
> 
I assume my problem is i don't have my CPU drivers...
-Do i need them?
-if yes, where do i get them?
-if no, then what is my problem?

You don't need CPU drivers - if you did, you wouldn't be able to boot because your motherboard wouldn't have the drivers anyway.

What we need to know is this: what are you trying to play? Also, turn off Desktop Effects/Compiz, because they use your Graphics Card quite a lot.

Also, please note that games will not run perfectly under a completely different operating system.

---

### Post by one_nz on 2010-02-18
> **DrMelon said:**
> 
.........Also, please note that games will not run perfectly under a completely different operating system.

The only reason I'm TRYING to get help is because my games run slower that my old dead grandmother, and is EXTREMELY CHOPPY.
The game I'm trying to play is rainbow 6 Vegas 2
I turned off my desktop effects and it did nothing to help....

> **DrMelon said:**
>  You don't need CPU drivers - if you did, you wouldn't be able to boot because your motherboard wouldn't have the drivers anyway...........

Do i even need to say anything?... yes i know CPU does already has drivers... BUT they do sometimes need UPDATES. Which will improve performance sometimes.

---

### Post by holastickboy on 2010-02-18
ATI cards are notoriously horrible at Wine/Cedega.  Also, Rainbow Six Vegas 2 is quite a hefty game, even under the nicest instances, you will get some performance hit using Wine/Cedega.

---

### Post by marshmallow1304 on 2010-02-18
> **one_nz said:**
> The game I'm trying to play is rainbow 6 Vegas 2

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11643&iTestingId=50154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11643&iTestingId=50154)

One "bronze" rating and four "garbage" ratings.  The report for the bronze rating mentions "significant slowdown".


Run this one in Windows.

---

### Post by one_nz on 2010-02-18
awwww....
oh well
Anyone know how to get beyond good and evil working?
every time i try to start it, it keeps saying it's not properly installed

---

### Post by RJARRRPCGP on 2010-02-18
Do other 3D games run majorly slow?  

If they do, then I'm afraid that your ATI drivers aren't installed or the driver installer failed to install the ATI drivers properly.

ATI support is probably NOT included, because ATI support likely requires PROPRIETARY driver blobs! 


You're less likely to have problems with Intel graphics. Intel graphics is supported out-of-the-box!

You need to run ```
glxinfo
```and it MUST say "direct rendering: Yes" !

---

### Post by one_nz on 2010-02-18
this is the only game out of 3 that will actually start and yes i installed those drivers.

it says
```
jacob@jacob-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_NV_swap_group, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_ARB_fbconfig_float
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_NV_swap_group, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, 
    GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 3.2.9252 Compatibility Profile Context
OpenGL shading language version string: 1.50

```

---

### Post by skymera on 2010-02-18
Using WINE for games isn't such a good idea.
If they work, you'll generally get degraded performance compared to running the game nativwely.

I dabbled with WINE years back to run Half Life2 and Team Fortress 2, both of which run ok.

WINE is generally a last resort. I have Windows7 for my games :)

---

### Post by Gene393 on 2010-06-20
My Games such as Secret Mayro Chronicles, Teeworlds, and I have no tomatoes (all downloaded from the ubuntu software centre) all run painfully slow and choppy as soon a you start them up, whats up:confused:....................Must Resist...........................AAARRRGGGHHHH!!!!!, I cant....:lolflag::guitar::lolflag::guitar:...........That felt good

---


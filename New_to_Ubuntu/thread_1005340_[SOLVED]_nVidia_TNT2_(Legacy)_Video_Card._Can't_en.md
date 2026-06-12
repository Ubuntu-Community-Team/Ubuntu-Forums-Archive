---
title: "[SOLVED] nVidia TNT2 (Legacy) Video Card. Can't enable Compiz/Desktop Effects"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by DaveyG on 2008-12-08
Well hey all. I did a fresh install of Ubuntu 8.04, as i had a disappointing effort of trying to install the Legacy nVidia Drivers on Ubuntu 8.10. After the install i enabled/downloaded the Acceleration Driver listed under System -> Administration -> Hardware Drivers, i also reconfigured XServer, so that i could set the correct resolution..

Now, the problem is that cannot enable Compiz/Desktop Effects, even though my Grpahics Card is up and running..

It's a 32MB Card, i'm pretty sure that's enough MB's to enable Effects, but maybe i'm wrong.

Heres the output of lspci if that helps:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:04.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```

Any help or advice would be much appreciated :)

---

### Post by Mze on 2008-12-08
[http://albertomilone.com/wordpress/?p=212](http://albertomilone.com/wordpress/?p=212)

You will be needing the Legacy driver for Hardy: nvidia-glx-legacy

---

### Post by DaveyG on 2008-12-08
nvidia-glx-legacy seems to already be installed.
I re-installed, to see it that would help, but sadly it didn't

/me fail

Can you reccomend any other possible solutions?

---

### Post by anewguy on 2008-12-08
You can't run compiz desktop effects with that video card.  I used to have one, and it wouldn't work because the card doesn't support everything needed.

Try this in a terminal, and you'll see what's missing:

glxinfo


EDIT:  while in terminal, do compiz --replace  and you will see the error from compiz as well.


Dave

---

### Post by DaveyG on 2008-12-09
> **anewguy said:**
> You can't run compiz desktop effects with that video card.  I used to have one, and it wouldn't work because the card doesn't support everything needed.

Try this in a terminal, and you'll see what's missing:

glxinfo


EDIT:  while in terminal, do compiz --replace  and you will see the error from compiz as well.


Dave

Thanks for the Reply Dave,

Results from glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE
OpenGL version string: 1.5.3 NVIDIA 71.86.04
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_compiled_vertex_array, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_SGIS_multitexture, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Results from compiz --replace:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:002d (rev 15) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

After i installed xserver-xgl, the results from compiz --replace where:
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

I'm a little stuck.. As the desktop now looks a little messed up =/

---

### Post by DaveyG on 2008-12-09
Bump; Guys, i still have this problem...

---

### Post by Tatty on 2008-12-09
In what way does the desktop look messed up?

---

### Post by DaveyG on 2008-12-09
> **Tatty said:**
> In what way does the desktop look messed up?

It's kind of patchy here and their. Example: if i right-click then left-click in Firefox so it closes the menu, it would show parts of the Desktop, which is behind it.. Also when i select from text from the Address Bar it would highlight white instead of Brown..

It's kind of hard to explain, as it's sort of weird.

---

### Post by Tatty on 2008-12-09
> **DaveyG said:**
> It's kind of patchy here and their. Example: if i right-click then left-click in Firefox so it closes the menu, it would show parts of the Desktop, which is behind it.. Also when i select from text from the Address Bar it would highlight white instead of Brown..

It's kind of hard to explain, as it's sort of weird.

Because your card is so old, you "may" find it runs better on the open source drivers.  Try uninstalling the legacy drivers and see if that helps.

---

### Post by DaveyG on 2008-12-10
> **Tatty said:**
> Because your card is so old, you "may" find it runs better on the open source drivers.  Try uninstalling the legacy drivers and see if that helps.

Cheers for the tips, I'm using just the restricted drivers for now, which seem to be ok.
It's not a big deal as I'm hopefully buying a new GPU soon. One last question though, which Graphics Card would you recommend to use with Ubuntu? I'm looking for something that would be fully supported and wouldn't require too much configuration/setup.

My Motherboard has a PCI Express x16 Slot :)

---


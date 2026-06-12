---
title: "Compiz problems -"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Rich.. on 2010-03-21
HEY, 
   
wondering if anybody can help me, I am new to ubuntu i have 9.10 Karmic.
I want to use compiz it looks great but when i downloaded it i cant get it to work when i go SYSTEM---->PREFERENCES----->APPEARANCE    then to VISUAL EFFECTS------>EXTRA(or normal) i get logged off, i have been searching around nothing seems to work i have deleted Compiz now until i can find a solution..... has this happened to anyone else???
BTW this may be important ...

--------------------------------------
Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] (rev 03)
 Driver in use:         openchrome
 Rendering method:      AIGLX
--------------------------------------

i have been told my 'openchrome' driver should support this software
Any help or advice is appreciated! THANKS FOR READING

---

### Post by blazemore on 2010-03-22
Please run the command ```
glxinfo
``` and post the result here. Thanks!

---

### Post by Rich.. on 2010-03-23
rich@rich-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 7.6
OpenGL extensions:
    GL_ARB_draw_buffers, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_texture_compression, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

24 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x55 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x56 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x57 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x58 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x5a 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x5b 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x5c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5d 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x63 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x66 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x3c 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 Ncon

24 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3d  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x3f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x40  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x41  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x42  0 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x44  0 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x45  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x49  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x4a  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x4c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x4d  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x51  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x54  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

-----------------------------------------------------------------------------------
Thanks for the reply! i do not have compiz installed at the moment if i need to re install it i will and post another result if it makes a difference. I have no idea what this means lol. Hope you can make sense of it. once again thanks for replying.

---

### Post by halitech on 2010-03-23
According to [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) 3D doesn't normally work very well. There is a proprietary driver linked to on that page with instructions on how to install it. You may have better luck with it although unless you have a laptop, I'd suggest you get a real video card and be much happier.

---

### Post by Rich.. on 2010-03-23
Halitech, Thanks for the link it does say on it that it is for 8.10 I am running 9.10 do you know if this will make much of a difference. and yes i am using a laptop (webbook) i didnt think to mention this in my first post..sorry. 
thanks for replying.

---

### Post by halitech on 2010-03-23
I'm not sure if it will make any difference or not but worth trying and seeing if it gives an option for 9.10. Since you are using a laptop, then changing the video card isn't really an option.

---

### Post by anewguy on 2010-03-23
Halitech is correct - I had a laptop (Gateway) with a S3 UniChrome graphics processor, and Compiz was a no-go with it.  I can't remember exactly where I found it (maybe as a result of doing compiz --replace on the command line) but there is something that compiz wants that the S3 couldn't deliver.  This has been about 3 years now, so it's possible something has changed.  I tried both the 2D and the 3D Openchrome drivers (those were the only ones available at the time to try) but still no luck.  At that point in time, the 3D driver did have a tendancy to make strange things happen - like locking the PC or my session going down.

Some of this may have changed in the ensuing 3 years, but I don't put much hope in the S3Unichrome being able to do what you want.

Dave ;)

---

### Post by Rich.. on 2010-03-25
thanks for the help guys, i have been a little busy but im gonna look to see if there is one for 9.10 an ill let you know what happens. if this dont work i can accept it that its not gonna happen on this computer. i do want to upgrade my laptop though so i may look for one thats able to support the software.

---

### Post by halitech on 2010-03-25
if you feel you need compiz, look at a laptop that has a good Nvidia video card. Nvidia seems to be more on top of providing proprietary drivers then ATI without dropping support for "older" cards.

---

### Post by Rich.. on 2010-03-31
ok. sorry for not replying sooner. I give up its not working lol, i will keep it in mind when looking for the new laptop , they dont do a driver for 9.10 just 9.04 so i tried it anyway just incase but no luck..

---

### Post by Contra75 on 2010-03-31
Have you read this how-to:

[http://ubuntuforums.org/showthread.php?t=1414548&highlight=configure+compiz+fusion](http://ubuntuforums.org/showthread.php?t=1414548&highlight=configure+compiz+fusion)

I had similar problem simply because I did not install Compiz Setting Manager in addition to Compiz :lolflag:

---


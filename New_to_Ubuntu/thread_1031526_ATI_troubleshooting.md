---
title: "ATI troubleshooting"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by tacmend on 2009-01-05
ok. so i have an ati graphics card. and it is in use. obviosly since i have a picture. but it fails to run in anything but low graphics mode. is this a error in a install of the driver or in ubuntu itself? or am i looking at this all wrong?

---

### Post by Michael.Godawski on 2009-01-05
hello,

when you say it is in use do you mean you have installed the drivers for it?
Did you check System > Administration > Hardware Drivers?

If this does not work perhaps you can try to install the drivers via the applications [envy ng]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by tacmend on 2009-01-05
i mean i see the desktop. so its being used. but not to its full.

---

### Post by Michael.Godawski on 2009-01-05
You can run this command in terminal to see if direct rendering is enabled:

```
glxinfo | grep rendering
```

---

### Post by tacmend on 2009-01-05
what will that do? sorry. i dont know to much.

---

### Post by Michael.Godawski on 2009-01-05
oh pretty nothing. It will only show us if the direct rendering is enabled. Just displays some info in terminal.

The output should be:
```

direct rendering: Yes
```

---

### Post by tacmend on 2009-01-05
also, do you know anything about getiing the start up usb to work? i installed it, but when i  started my computer and told it to boot from removable devices, it just went to a black screen then booted windows. and yes this means i am dual booting.

---

### Post by tacmend on 2009-01-05
what is the signifigance of rendering?

---

### Post by DWBC on 2009-01-05
If the issue is that you are not offered a higher screen resolution than 800X600, have a look at the thread 'Display adapter and screen resolution' which I just went through and marked 'solved' last night.  To save yourself a lot of reading, you can start at the end.  :)

---

### Post by tacmend on 2009-01-05
i cant do anything. its stuck at 800x 600 and i cant do any visual effects either. and when i click on anything that opens into a window, after i close t it leaves a green drag. then slowly fades. its wierd.

---

### Post by Michael.Godawski on 2009-01-05
> **tacmend said:**
> what is the signifigance of rendering?


[LIST]
[*][http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)
[/LIST]
In Linux, [Direct Rendering Infrastructure]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure") (DRI) facilitates faster graphics rendering.
If this line says "No",from the command posted above, it means that graphics data will not be passed directly to the graphics hardware, thus significantly reducing speed.

---

### Post by zika on 2009-01-05
> **Michael.Godawski said:**
> oh pretty nothing. It will only show us if the direct rendering is enabled. Just displays some info in terminal.

The output should be:
```

direct rendering: Yes
```

I do not want to hijack this thread (I've been warned once) but I have ATI HD 3650 with the latest official (from the ati.amd.com) drivers with Catalyst 8.12 and I get from [I]glxinfo:

[/I]```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3600 Series
OpenGL version string: 1.4 (2.1.8304 Release)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

```is this wrong? I do not have any problems but You made me think ...

since this is about ATI troubleshooting I hope I'm not making a mistake by asking this ...

---

### Post by Michael.Godawski on 2009-01-05
> **zika said:**
> I do not want to hijack this thread (I've been warned once) but I have ATI HD 3650 with the latest official (from the ati.amd.com) drivers with Catalyst 8.12 and I get from [I]glxinfo:

[/I]```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3600 Series
OpenGL version string: 1.4 (2.1.8304 Release)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

```is this wrong? I do not have any problems but You made me think ...

since this is about ATI troubleshooting I hope I'm not making a mistake by asking this ...

Are you having trouble when playing 3D games? If not: do not change a working system.
:D

---

### Post by zika on 2009-01-05
> **Michael.Godawski said:**
> Are you having trouble when playing 3D games? If not: do not change a working system.
:D
no, I do not play games, let alone 3D ... ;)

I've just tried ```
aticonfig --overlay-type=Xv
``` and it changed xorg.conf but I do not see any difference (even in videos where I have to use X11 (no xv)). did I make a mistake? should I revert to previous xorg.conf (it made a backup) or should I keep it?

the only difference is:```
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
```in Section "Device".

but it works better if I reverse, ```
    Option        "VideoOverlay" "off"
    Option        "OpenGLOverlay" "on"
```in Section "Device".

am I making any sense?

---


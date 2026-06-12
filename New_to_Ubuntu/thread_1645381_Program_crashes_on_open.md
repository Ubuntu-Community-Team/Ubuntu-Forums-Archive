---
title: "Program crashes on open?"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by MatthewWilliams on 2010-12-14
I just got the install for Braid working, but now there's a new problem.

Whenever I try to open Braid, my screen goes black for a second (as if it were trying to change the resolution), it flashes to a black screen with my cursor on it, my screen goes black again, it shows me the screen I was on before I tried to open it except the bar at the bottom goes to about a fifth of the way up, until finally it goes back to normal. Braid never opens.

I tried recording it, but my desktop recorder crashes when I try to run it at the same time.

Help?

---

### Post by TeoBigusGeekus on 2010-12-14
Run it from a terminal and post any error messages.

---

### Post by MatthewWilliams on 2010-12-14
> **TeoBigusGeekus said:**
> Run it from a terminal and post any error messages.

I'll do that in a second, but I just noticed that all the icons on my desktop are missing. So there's that, too.

**EDIT:** How do I run it from Terminal? *facepalm*

---

### Post by Ligerzero_942 on 2010-12-14
Type
> ./<Name of Executable>

---

### Post by MatthewWilliams on 2010-12-14
Thanks!

```
Game Startup Error: Unable to set up graphics.
Reason: Missing required OpenGL extension.

To help fix this problem make sure you are running the newest version of your video drivers.
Lastly, you could try running this game with the -windowed command-line option.
```

---

### Post by brandotron on 2010-12-14
> **MatthewWilliams said:**
> Thanks!

```
Game Startup Error: Unable to set up graphics.
Reason: Missing required OpenGL extension.

To help fix this problem make sure you are running the newest version of your video drivers.
Lastly, you could try running this game with the -windowed command-line option.
```

I am having the exact same problem. Bought the Humble Bundle, installed Braid, got all excited about wasting the entire workday, and then, this. Same error message, I'm on a Gateway C140x on 10.04, using the open source drivers because my card is long unsupported by the proprietary drivers. 

I tried -windowed, but it doesn't seem to make a difference, I get the same error message again.

I ran LIBGL_DEBUG=verbose glxinfo, nothing looked out of order to me, but maybe this will help someone who knows more about this than I do (which wouldn't take much):

```
brandon@ubuntu:/$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, GL_ARB_copy_buffer, 
    GL_ARB_depth_texture, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_seamless_cube_map, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_cull_vertex, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_texture_env_combine3, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_texture_signed_rgba, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_depth_clamp, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

72 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xca 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcb 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xcc 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xd0 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd1 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd2 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd3 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd4 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xd5 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xd6 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd7 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd8 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd9 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xda 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xdb 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xdc 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xde 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xdf 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xe0 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xe1 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xe2 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe3 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe4 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe5 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xe7 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xe8 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xe9 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xea 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xeb 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xec 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xed 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xee 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xf1 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xf2 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf3 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf4 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf5 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf6 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xf7 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xf8 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xf9 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xfa 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xfb 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xfc 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xfd 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xfe 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xff 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x100 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x101 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x102 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x103 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x104 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x105 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x106 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x107 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x108 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x109 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x10a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x10b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x10c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x10d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x10e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

96 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6a  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x6b  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x6c  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x6d  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x6e  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x6f  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x70  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x71  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x72  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x73  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x74  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x75  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x76  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x77  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x78  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x79  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7a  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x7b  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x7c  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7d  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x7e  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x7f  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x80  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x81  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x82  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x83  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x84  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x85  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x86  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x87  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x88  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x8d  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x8e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x8f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x90  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x91  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x92  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x93  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x94  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x95  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x96  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x97  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x98  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x99  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9a  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9b  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9c  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9d  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x9f  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0xa0  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa1  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa2  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa3  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa4  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0xa5  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0xa6  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa7  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa8  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa9  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xaa  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xab  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xac  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xad  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xae  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xaf  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xb1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xb2  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb3  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb4  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb5  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb6  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb7  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb9  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xba  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xbb  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xbd  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xbe  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbf  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc1  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc2  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xc3  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xc4  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc5  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc6  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc7  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc8  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc9  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by kakarotoks on 2010-12-14
The solution was found by Scott Mansell on the icculus bugzilla : 
[http://bugzilla.icculus.org/show_bug.cgi?id=4825](http://bugzilla.icculus.org/show_bug.cgi?id=4825)
install 'driconf' then run it and enable the S3TC extension in the "Image quality" tab of driconf.
Enjoy one of the best indie games! :)

---

### Post by jacksonpollack on 2010-12-14
That solution allows me to start Braid, but all I get is a black screen and everything freezes. I started it in windowed mode, and this is the error I got: 
```
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max ALU instructions (83 out of 64)
Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (DRI2)
  Minor opcode of failed request:  8 ()
  Resource id in failed request:  0x460000f
  Serial number of failed request:  150
  Current serial number in output stream:  150
```

---

### Post by firefly2442 on 2010-12-14
Anyone know what the system requirements are for running Braid?  I have an Asus eeePC 1000 with integrated graphics.  Not sure that will cut it since I'm getting the same OpenGL errors even after installing the driconf package.

---

### Post by jacksonpollack on 2010-12-15
Not sure about the requirements for Braid, but I can play the Windows version of Braid on my computer just fine using WinXP via Virtual Box. Kinda silly I can get it to work that way but not using the native Linux version. My point just being that those errors don't necessarily mean your don't meet the hardware requirements.

---

### Post by laus_deo on 2010-12-15
This has appeared on some other parts of the forum

>  Braid:
After installing Braid in Ubuntu 10.10 64 bit(first you right click the braid-linux.run.bin file, go to permits give execution rights then you put the braid-linux.run.bin in your folder or in the Terminal get to the actual position of the file using cd. Finally just write ./braid-linux.run.bin and install the game), I just did what Comment 13 on the Braid bug report and it's working now.
And that was installing driconf is on the Software Center or sudo apt-get driconf then you go to System>Preferences>Dri 3D Acceleration under the Image Quality tab change No to Yes when it say S3TC.
That works for me.

---

### Post by brandotron on 2010-12-15
> **kakarotoks said:**
> The solution was found by Scott Mansell on the icculus bugzilla : 
[http://bugzilla.icculus.org/show_bug.cgi?id=4825](http://bugzilla.icculus.org/show_bug.cgi?id=4825)
install 'driconf' then run it and enable the S3TC extension in the "Image quality" tab of driconf.
Enjoy one of the best indie games! :)

This worked! Thank you!

---

### Post by mrrix32 on 2010-12-15
Tried the above suggestion, the screen goes black, a cursor appears (can be moved) but nothing else happens and I can't close it. I then ran it windowed from the Terminal and got this:

```
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max ALU instructions (83 out of 64)
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (DRI2)
  Minor opcode of failed request:  8 ()
  Resource id in failed request:  0x3e0000f
  Serial number of failed request:  342
  Current serial number in output stream:  342

```

Any suggestions? Or are my Graphics too poor?

---

### Post by Dax0r on 2010-12-15
> **mrrix32 said:**
> Tried the above suggestion, the screen goes black, a cursor appears (can be moved) but nothing else happens and I can't close it. I then ran it windowed from the Terminal and got this:

```
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max nr indirect texture lookups (8 out of 4)
i915_program_error: Exceeded max ALU instructions (83 out of 64)
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (DRI2)
  Minor opcode of failed request:  8 ()
  Resource id in failed request:  0x3e0000f
  Serial number of failed request:  342
  Current serial number in output stream:  342

```

Any suggestions? Or are my Graphics too poor?

Same error here.
A workaround is to run it on root.

---

### Post by Arlanthir on 2010-12-15
> **kakarotoks said:**
> The solution was found by Scott Mansell on the icculus bugzilla : 
[http://bugzilla.icculus.org/show_bug.cgi?id=4825](http://bugzilla.icculus.org/show_bug.cgi?id=4825)
install 'driconf' then run it and enable the S3TC extension in the "Image quality" tab of driconf.
Enjoy one of the best indie games! :)

Fixed it here :)

---

### Post by kakarotoks on 2010-12-15
> **firefly2442 said:**
> Anyone know what the system requirements are for running Braid?  I have an Asus eeePC 1000 with integrated graphics.  Not sure that will cut it since I'm getting the same OpenGL errors even after installing the driconf package.

I don't think it would run in a netbook. The game requires ridiculous graphics power even though it's a simple game. There are some command line options that can make it run smoother (-no_post -novsync or something.. see the README file in the windows version (I don't know why they didn't put the game's readme in the linux version too).

---

### Post by jacksonpollack on 2010-12-15
The relevant bug report is here:

[http://bugzilla.icculus.org/show_bug.cgi?id=4829](http://bugzilla.icculus.org/show_bug.cgi?id=4829)

---


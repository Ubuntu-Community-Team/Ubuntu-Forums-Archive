---
title: "ATI Radeon 4800 Resolution Problem"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by navinrai on 2009-03-08
Hello All,

So I've become fed up with Windows, after having paid for a copy of it, getting a virus and loosing everything on my computer, and then not being able to use my serial to reinstall. So, Ubuntu for me. I am having a few problems though. The main one is this:

I have an ATI Radeon 4800 Video Card. I have the Propriety drivers installed. I also have ATI Catalyst installed. I have two monitors which both work. The only problem is that my resolution is set incorrectly. Each monitor has a resolution of 1680x1050, which would give me an overall resolution of 3360x1050 for both. What I am getting, however is 2048x768. 

I would love to find a way to make my resolution correct!

This is my first time using Linux, and I have been trying to figure out how to work the program by reading the forums. One thing I read a lot about is the xorg.conf file. Some threads seem to say that it should be edited, however I am hesitant to do so because I'm not sure exactly what I should do with the information in there. Here is what it says now:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"fglrx"
EndSection
```


Any advice anyone can lend me I would appreciate! I have found that the people on this board are extremely helpful to newbs like me, so thanks in advance. 

:D

---

### Post by navinrai on 2009-03-08
sorry to double post, I just want to provide as much info as possible. This is my results from 

```
glxinfo
```

Results

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMDX_vertex_shader_tessellator, GL_AMD_performance_monitor, 
    GL_AMD_texture_texture4, GL_ARB_color_buffer_float, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_instanced, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_buffer_float, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

81 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x49 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x71 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x72 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x89 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon

83 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x48  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x49  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  8 1 None
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x72  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  8 1 None
0x89  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon
0x89  0 tc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0x89  0 tc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon


Thanks again!

---

### Post by navinrai on 2009-03-09
after much playing around here, I've got a different looking xorg.conf file. Still no solution, however. Here's what it looks like now:


> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	Option	    "metamodes" "1680x1050 +0+0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "metamodes" "1680x1050 +0+0"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "metamodes" "1680x1050 +0+0"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
	Option	    "Mode2" "1680x1050" #Resolution for second monitor
	Option	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Mode2" "1680x1050"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


And here's what I've tried:

1. Reinstalling the ATI Drivers automatically following the ATI website manual. 
2. Running the ATI config file, and adding my monitor size for both the first and second monitors
3. Just typing into the xorg.conf file in each monitor section:

> 	Option	    "metamodes" "1680x1050 +0+0"

and from here I'm at a bit of a loss. Someone please help!

---

### Post by Svensk023 on 2009-03-09
I looked through all your posts and I too am at a loss ;(
so I'm posting to bump your thread
Someone please help out!

although I do have one question, are you using two graphics cards with crossfire? because if so, you need to enable crossfire via aticonfig

---

### Post by navinrai on 2009-03-09
Hey Svensk023, Thanks for the reply

No I'm not using crossfire, just the one card with two outputs on it, one digital and the other analogue sent to my monitors. 

I believe I may have found the problem, however, after searching though ATI's website. One [this page]("http://support.amd.com/us/kbarticles/Pages/1105-HowCanIConfigureMultip.aspx") it says:

> Some of these configurations allow for extremely large desktop resolutions. Please note the maximum resolutions for OpenGL operation are as follows:
Resolution 	Family 	Boards
2560x2560
2048x2048 	R300
R200 	Radeon 9500-9800, FireGL Z1/X1/X2
Radeon 8500-9200, FireGL 8700/8800/E1

I am starting to think that this means the largest I can possibly have my resolution set to is something with 2048 as the width, and seeing as I am trying to get 3360x1050, maybe it just doesn't work at all. Hopefully there's some other solution!

---

### Post by Svensk023 on 2009-03-09
im not highly experienced with configuring two monitors under linux, but im sure there is a way arounf it. I dont see your car listed in that list, but most of the dual monitors I have seen were connected to computers with 2 graphics cards. I'm not entirely using a single card may have somehting to do with it?
But what I know to be true is that ATI cards and linux have been clashing heads for some time.
what window manager are you using?

---

### Post by markbuntu on 2009-03-09
I am running a 3850x1200 big desktop with my HD3650 on Hardy and Intrepid so you should have no problem with a 4800. You should do this in the catalyst control center display manager. First make sure it detects the displays properly and set the resolutions and then set the big desktop.

---

### Post by navinrai on 2009-03-09
> **markbuntu said:**
>  First make sure it detects the displays properly and set the resolutions and then set the big desktop.

Hmm. . . maybe this is my problem? What should I do? I'll tell you what has happened so far:

[LIST=1]
[*]I got Ubuntu up and running. At this point, it was configured correctly on one of my monitors, at the correct resolution (1680x1050) with the second monitor cloning the first. 
[*]I installed the driver automatically through System>Administration>Hardware Drivers to the ATI driver that was there. This gave me two monitors under big desktop set up and working perfectly except one thing - the resolution was off
[*]I uninstalled the driver and reinstalled it, and tried various things with the xorg.conf that other threads made me think might work - and I have had no result. So I still have my resolution off. 
[/LIST]

You know, I think you may be right in it not detecting my monitors correctly. This is because when I go to System>Preferences>Screen Resolution, it does not say a name for my monitor, rather it just says unknown. I don't know if that sheds any further light on the situation, but any questions you can ask me please do, and I appreciate any help I can get!!

---

### Post by markbuntu on 2009-03-10
You really need to use the Catalyst Control Center to configure the driver. If you do not have it it is amdcccle in the repos.

What you need to do is set the monitor resolutions for each screen while still in clone mode and then change to big desktop. If you want to force the resolution of one screen youu should use the aticonfig command line utility

aticonfig --help

for options and explanations

xorg.conf will be going away soon so the sooner people stop fooling around with it the better off they will be, Xorg has already deprecated it. All configuration options are moved to drivers and their utility programs.

---

### Post by navinrai on 2009-03-11
Ok, so I guess then I should stop messing around with the xorg.conf and start messing around with the aticonfig file. 

So here's my dilemma. I try to set the screen resolution and get nowheres. My command is this:

```
sudo aticonfig --resolution=Screen0,1680x1050
```

and it gives me this return:

> Error: Section # expected
aticonfig: parsing the command-line failed.

I am at a loss about this. It still will not accept that my displays are 1680x1050 each.

Help me configure this file please, and I'll love you forever!

---

### Post by markbuntu on 2009-03-11
This is the example from 
aticonfig --help

 3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768

---

### Post by Canezila on 2009-03-23
Hi everyone here.

I have been a Nvidia card user for many years.  BUT, I am looking into getting a ATI RadeonHD48xx type card.  The price looks good and the main reason is:
1.  Folding@Homne
2.  Rendering video with the GPU

These cards have up to 800 processing cores, compared to my Nvidia 9600 GT 512 that has only 64.  

Question:  Would a knowledgeable Ubuntu and ATI user recommend making this switch?  The only game I play is UrbanTerror and I only do that during the summer when I have time.  Otherwise my computer is a music computer with video editing.  

Thank you.
Brian

---


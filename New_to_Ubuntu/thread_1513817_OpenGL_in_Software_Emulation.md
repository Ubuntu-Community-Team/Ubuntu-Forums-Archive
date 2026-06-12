---
title: "OpenGL in Software Emulation"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-06-20
Question: I have problems getting OpenGL to work with my graphics card. It used to work without problems on all Ubuntus < 10.04

> 
~# lspci | grep "VGA"
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)


> 
glxinfo | grep "render"
direct rendering: Yes
OpenGL renderer string: Mesa X11



I had problems with OpenArena, so I downloaded GoogleEarth to check whether the system really runs on OpenGL. As suspected, then answer was no...

Google Earth
> 
You are currently running google earth in OpenGL with Software Emulation. In this mode, google earth will work, but it will run very slowly...



glxinfo:
```

~# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.7.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.7.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, GL_ARB_copy_buffer, 
    GL_ARB_depth_texture, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
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
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_fog_coord, GL_EXT_gpu_program_parameters, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_resize_buffers, GL_MESA_texture_array, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_depth_clamp, GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, GL_NV_point_sprite, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

72 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcb 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcc 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xce 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcf 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd0 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd1 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd2 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd3 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd4 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd5 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd6 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd7 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd8 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd9 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xda 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdb 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdc 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdd 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xde 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdf 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe0 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe1 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe2 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe3 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe4 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe5 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe6 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe7 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe8 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe9 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xea 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xeb 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xec 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xed 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xee 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf0 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf1 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf2 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf3 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf4 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf5 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf6 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf7 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf8 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf9 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfa 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfb 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfc 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfd 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfe 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xff 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x100 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x101 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x102 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x103 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x104 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x105 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x106 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x107 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x108 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x109 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None

72 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcb  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcc  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcd  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xce  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xcf  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd0  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd1  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd2  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd3  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd4  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd5  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd6  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd7  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd8  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xd9  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xda  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdb  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdc  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdd  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xde  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xdf  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe0  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe1  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe2  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe3  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe4  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe5  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe6  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe7  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe8  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xe9  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xea  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xeb  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xec  0 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xed  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xee  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xef  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf0  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf1  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf2  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf3  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf4  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf5  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf6  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf7  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf8  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xf9  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfa  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfb  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfc  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfd  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xfe  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0xff  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x100  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x101  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x102  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x103  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x104  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x105  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x106  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x107  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x108  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x109  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10a  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10b  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10c  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10d  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10e  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x10f  0 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a  0 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None

```

What's the matter ? Am I missing firmware ?

---

### Post by WitchCraft on 2010-06-20
bump.

---

### Post by shawnansasio on 2010-06-20
Well, your graphics card stinks! (no offense) tell us what display driver you are using. (probablaby VESA)

---

### Post by WitchCraft on 2010-06-24
xserver-xorg-video-intel - X.Org X server -- Intel i8xx, i9xx display driver

My graphics card doesn't stink it works fine,
and it definitely works on Linux, since I had it running correctly before 10.04 came along.

---

### Post by WitchCraft on 2010-06-24
It looked like mesa wasn't properly installed

apt-get install xlibmesa-dri xlibmesa-gl xlibmesa-glu mesa-utils libgl1-mesa-dri libgl1-mesa-glx

> 
apt-get install xlibmesa-gl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgl1-mesa-glx
The following packages will be REMOVED:
  libgl1-mesa-swx11 libgl1-mesa-swx11-i686
The following NEW packages will be installed:
  libgl1-mesa-glx xlibmesa-gl


Now google earth works on GL, but OpenArena still has problems: when I move left or right and move the mouse, the mouse doesn't move until I let the key go or vice-versa...

---

### Post by WitchCraft on 2010-06-26
bump

---

### Post by WitchCraft on 2010-06-29
bump.

---


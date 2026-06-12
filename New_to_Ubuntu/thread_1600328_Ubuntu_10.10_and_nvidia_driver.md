---
title: "Ubuntu 10.10 and nvidia driver"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2010-10-18
So I've tried both an upgrade and a fresh install of ubuntu 10.10 and gotten this irritating problem.

With any nvidia drivers enabled, the desktop slows to a crawl for certain things.  I've tried both the 173 and the "current version" drivers supplied in the additional drivers menu option.  I've also downloaded the 260 drivers directly from Nvidia with the same results every time.

Basically this is what happens.  With no nvidia drivers installed, ubuntu boots up nicely with a smooth purple boot splash.  After that, I can log in and my themes are all fine with no compiz support.

If I use any of the nvidia drivers, upon reboot, I get an odd ubuntu boot splash that's bigger and says ubuntu 10.10 instead of just the regular ubuntu logo.  The GUI also takes significantly longer to boot up and the theme for the windows doesn't apply.  Instead of a dark gray theme, I get a crappy generic looking light grey interface instead.  I've also noticed that many time windows are slow to respond to resizing or just form change elements.  Holding in backspace randomly yields slow or nonexistent backspacing.  

The odd thing is that after installing the nvidia drivers and rebooting, everything appears to be fine.  But then I reboot for a second time and I'm back to the slow response time and everything.  Does this have anything to do with the Xorg problems, or does it seem unrelated?


I'm using 64-bit ubuntu with a core i7 processor and a 9800Gt video card.

Thanks.

---

### Post by sandyd on 2010-10-18
> **CryptiniteDemon said:**
> So I've tried both an upgrade and a fresh install of ubuntu 10.10 and gotten this irritating problem.

With any nvidia drivers enabled, the desktop slows to a crawl for certain things.  I've tried both the 173 and the "current version" drivers supplied in the additional drivers menu option.  I've also downloaded the 260 drivers directly from Nvidia with the same results every time.

Basically this is what happens.  With no nvidia drivers installed, ubuntu boots up nicely with a smooth purple boot splash.  After that, I can log in and my themes are all fine with no compiz support.

If I use any of the nvidia drivers, upon reboot, I get an odd ubuntu boot splash that's bigger and says ubuntu 10.10 instead of just the regular ubuntu logo.  The GUI also takes significantly longer to boot up and the theme for the windows doesn't apply.  Instead of a dark gray theme, I get a crappy generic looking light grey interface instead.  I've also noticed that many time windows are slow to respond to resizing or just form change elements.  Holding in backspace randomly yields slow or nonexistent backspacing.  

The odd thing is that after installing the nvidia drivers and rebooting, everything appears to be fine.  But then I reboot for a second time and I'm back to the slow response time and everything.  Does this have anything to do with the Xorg problems, or does it seem unrelated?


I'm using 64-bit ubuntu with a core i7 processor and a 9800Gt video card.

Thanks.
attach a copy of /var/log/Xorg.0.log the next time you have problems.
also post output of
```

glxinfo
```

---

### Post by CryptiniteDemon on 2010-10-18
glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 260.19.12
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vdpau_interop, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x041 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x042 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x044 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x045 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x046 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x048 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x049 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x04a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x054 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x056 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x05f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x060 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x063 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x064 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x065 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x067 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x068 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x069 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06a 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x070 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x071 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x072 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon

164 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ca  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cc  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cd  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0ce  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0cf  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0d0  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0d1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d2  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d4  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d5  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d6  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d7  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d8  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d9  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0da  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0db  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dc  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0de  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0df  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e0  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e2  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e4  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e5  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e6  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e7  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e8  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e9  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ea  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0eb  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ec  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ed  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ee  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ef  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f0  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f1  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f2  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f3  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f4  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f5  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f6  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f7  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f8  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f9  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fa  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fb  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fc  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0fe  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0ff  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x100  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x102  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x103  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x104  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10a  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10b  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10c  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10e  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10f  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x110  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x112  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x113  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x118  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None

```


Xorg log
```
[    30.782] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    30.782] X Protocol Version 11, Revision 0
[    30.782] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    30.782] Current Operating System: Linux corei7 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64
[    30.782] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=4d5c4f06-c95c-45ab-a94f-f1cbcf61a487 ro quiet splash
[    30.782] Build Date: 16 September 2010  06:18:41PM
[    30.782] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    30.782] Current version of pixman: 0.18.4
[    30.782] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    30.782] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.782] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 18 22:02:28 2010
[    30.782] (==) Using config file: "/etc/X11/xorg.conf"
[    30.782] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.782] (==) ServerLayout "Layout0"
[    30.782] (**) |-->Screen "Screen0" (0)
[    30.782] (**) |   |-->Monitor "Monitor0"
[    30.782] (**) |   |-->Device "Device0"
[    30.782] (**) |-->Input Device "Keyboard0"
[    30.782] (**) |-->Input Device "Mouse0"
[    30.782] (==) Automatically adding devices
[    30.782] (==) Automatically enabling devices
[    30.782] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.782] 	Entry deleted from font path.
[    30.782] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    30.782] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.782] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.782] (WW) Disabling Keyboard0
[    30.782] (WW) Disabling Mouse0
[    30.782] (II) Loader magic: 0x7d0200
[    30.782] (II) Module ABI versions:
[    30.782] 	X.Org ANSI C Emulation: 0.4
[    30.782] 	X.Org Video Driver: 8.0
[    30.782] 	X.Org XInput driver : 11.0
[    30.782] 	X.Org Server Extension : 4.0
[    30.783] (--) PCI:*(0:2:0:0) 10de:0605:3842:c977 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072
[    30.783] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    30.783] (II) "extmod" will be loaded by default.
[    30.783] (II) "dbe" will be loaded by default.
[    30.783] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    30.783] (II) "record" will be loaded by default.
[    30.783] (II) "dri" will be loaded by default.
[    30.783] (II) "dri2" will be loaded by default.
[    30.783] (II) LoadModule: "glx"
[    30.805] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.810] (II) Module glx: vendor="NVIDIA Corporation"
[    30.810] 	compiled for 4.0.2, module version = 1.0.0
[    30.810] 	Module class: X.Org Server Extension
[    30.810] (II) NVIDIA GLX Module  260.19.12  Fri Oct  8 11:41:55 PDT 2010
[    30.811] (II) Loading extension GLX
[    30.811] (II) LoadModule: "extmod"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.811] (II) Module extmod: vendor="X.Org Foundation"
[    30.811] 	compiled for 1.9.0, module version = 1.0.0
[    30.811] 	Module class: X.Org Server Extension
[    30.811] 	ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension MIT-SCREEN-SAVER
[    30.811] (II) Loading extension XFree86-VidModeExtension
[    30.811] (II) Loading extension XFree86-DGA
[    30.811] (II) Loading extension DPMS
[    30.811] (II) Loading extension XVideo
[    30.811] (II) Loading extension XVideo-MotionCompensation
[    30.811] (II) Loading extension X-Resource
[    30.811] (II) LoadModule: "dbe"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.811] (II) Module dbe: vendor="X.Org Foundation"
[    30.811] 	compiled for 1.9.0, module version = 1.0.0
[    30.811] 	Module class: X.Org Server Extension
[    30.811] 	ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension DOUBLE-BUFFER
[    30.811] (II) LoadModule: "record"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.811] (II) Module record: vendor="X.Org Foundation"
[    30.811] 	compiled for 1.9.0, module version = 1.13.0
[    30.811] 	Module class: X.Org Server Extension
[    30.811] 	ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension RECORD
[    30.811] (II) LoadModule: "dri"
[    30.812] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.812] (II) Module dri: vendor="X.Org Foundation"
[    30.812] 	compiled for 1.9.0, module version = 1.0.0
[    30.812] 	ABI class: X.Org Server Extension, version 4.0
[    30.812] (II) Loading extension XFree86-DRI
[    30.812] (II) LoadModule: "dri2"
[    30.812] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.812] (II) Module dri2: vendor="X.Org Foundation"
[    30.812] 	compiled for 1.9.0, module version = 1.2.0
[    30.812] 	ABI class: X.Org Server Extension, version 4.0
[    30.812] (II) Loading extension DRI2
[    30.812] (II) LoadModule: "nvidia"
[    30.812] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    30.812] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.812] 	compiled for 4.0.2, module version = 1.0.0
[    30.812] 	Module class: X.Org Video Driver
[    30.812] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[    30.812] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.812] (++) using VT number 7

[    30.813] (II) Loading sub module "fb"
[    30.813] (II) LoadModule: "fb"
[    30.814] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.814] (II) Module fb: vendor="X.Org Foundation"
[    30.814] 	compiled for 1.9.0, module version = 1.0.0
[    30.814] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.814] (II) Loading sub module "wfb"
[    30.814] (II) LoadModule: "wfb"
[    30.814] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.814] (II) Module wfb: vendor="X.Org Foundation"
[    30.814] 	compiled for 1.9.0, module version = 1.0.0
[    30.814] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.814] (II) Loading sub module "ramdac"
[    30.814] (II) LoadModule: "ramdac"
[    30.814] (II) Module "ramdac" already built-in
[    30.814] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.814] (==) NVIDIA(0): RGB weight 888
[    30.814] (==) NVIDIA(0): Default visual is TrueColor
[    30.814] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.814] (**) NVIDIA(0): Option "NoLogo" "True"
[    30.814] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.814] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.814] (II) NVIDIA(0):     enabled.
[    37.751] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[    37.751] (--) NVIDIA(0): Memory: 524288 kBytes
[    37.751] (--) NVIDIA(0): VideoBIOS: 62.92.69.00.70
[    37.751] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    37.751] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    37.751] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[    37.751] (--) NVIDIA(0):     Toshiba TSB-TV (DFP-0)
[    37.751] (--) NVIDIA(0): Toshiba TSB-TV (DFP-0): 330.0 MHz maximum pixel clock
[    37.751] (--) NVIDIA(0): Toshiba TSB-TV (DFP-0): Internal Dual Link TMDS
[    37.862] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    37.862] (==) NVIDIA(0): 
[    37.862] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    37.862] (==) NVIDIA(0):     will be used as the requested mode.
[    37.862] (==) NVIDIA(0): 
[    37.862] (II) NVIDIA(0): Validated modes:
[    37.862] (II) NVIDIA(0):     "nvidia-auto-select"
[    37.862] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    37.905] (--) NVIDIA(0): DPI set to (46, 46); computed from "UseEdidDpi" X config
[    37.905] (--) NVIDIA(0):     option
[    37.905] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    37.905] (--) Depth 24 pixmap format is 32 bpp
[    37.905] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    37.907] (II) NVIDIA(0): Initialized GPU GART.
[    37.922] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    37.945] (II) Loading extension NV-GLX
[    37.975] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    37.997] (==) NVIDIA(0): Disabling shared memory pixmaps
[    37.997] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    37.997] (==) NVIDIA(0): Backing store disabled
[    37.997] (==) NVIDIA(0): Silken mouse enabled
[    38.009] (**) NVIDIA(0): DPMS enabled
[    38.009] (II) Loading extension NV-CONTROL
[    38.010] (II) Loading extension XINERAMA
[    38.010] (II) Loading sub module "dri2"
[    38.010] (II) LoadModule: "dri2"
[    38.010] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    38.010] (II) NVIDIA(0): [DRI2] Setup complete
[    38.010] (==) RandR enabled
[    38.010] (II) Initializing built-in extension Generic Event Extension
[    38.010] (II) Initializing built-in extension SHAPE
[    38.010] (II) Initializing built-in extension MIT-SHM
[    38.010] (II) Initializing built-in extension XInputExtension
[    38.010] (II) Initializing built-in extension XTEST
[    38.010] (II) Initializing built-in extension BIG-REQUESTS
[    38.010] (II) Initializing built-in extension SYNC
[    38.010] (II) Initializing built-in extension XKEYBOARD
[    38.010] (II) Initializing built-in extension XC-MISC
[    38.010] (II) Initializing built-in extension SECURITY
[    38.010] (II) Initializing built-in extension XINERAMA
[    38.010] (II) Initializing built-in extension XFIXES
[    38.010] (II) Initializing built-in extension RENDER
[    38.010] (II) Initializing built-in extension RANDR
[    38.010] (II) Initializing built-in extension COMPOSITE
[    38.010] (II) Initializing built-in extension DAMAGE
[    38.010] (II) Initializing built-in extension GESTURE
[    38.010] (II) Initializing extension GLX
[    38.030] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    38.035] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    38.035] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.035] (II) LoadModule: "evdev"
[    38.035] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    38.035] (II) Module evdev: vendor="X.Org Foundation"
[    38.035] 	compiled for 1.9.0, module version = 2.3.2
[    38.035] 	Module class: X.Org XInput Driver
[    38.035] 	ABI class: X.Org XInput driver, version 11.0
[    38.035] (**) Power Button: always reports core events
[    38.035] (**) Power Button: Device: "/dev/input/event1"
[    42.580] (II) Power Button: Found keys
[    42.580] (II) Power Button: Configuring as keyboard
[    42.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    42.580] (**) Option "xkb_rules" "evdev"
[    42.580] (**) Option "xkb_model" "pc105"
[    42.580] (**) Option "xkb_layout" "us"
[    42.581] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    42.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.581] (**) Power Button: always reports core events
[    42.581] (**) Power Button: Device: "/dev/input/event0"
[    54.205] (II) Power Button: Found keys
[    54.205] (II) Power Button: Configuring as keyboard
[    54.205] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    54.205] (**) Option "xkb_rules" "evdev"
[    54.205] (**) Option "xkb_model" "pc105"
[    54.205] (**) Option "xkb_layout" "us"
[    54.206] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    54.206] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    54.206] (**) Logitech USB Receiver: always reports core events
[    54.206] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    58.574] (II) Logitech USB Receiver: Found keys
[    58.574] (II) Logitech USB Receiver: Configuring as keyboard
[    58.574] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    58.574] (**) Option "xkb_rules" "evdev"
[    58.574] (**) Option "xkb_model" "pc105"
[    58.574] (**) Option "xkb_layout" "us"
[    58.574] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    58.574] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    58.574] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    58.574] (**) Logitech USB Receiver: always reports core events
[    58.574] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    64.571] (II) Logitech USB Receiver: Found 12 mouse buttons
[    64.571] (II) Logitech USB Receiver: Found scroll wheel(s)
[    64.571] (II) Logitech USB Receiver: Found relative axes
[    64.571] (II) Logitech USB Receiver: Found x and y relative axes
[    64.571] (II) Logitech USB Receiver: Found absolute axes
[    64.571] (II) evdev-grail: failed to open grail, no gesture support
[    64.571] (II) Logitech USB Receiver: Found keys
[    64.571] (II) Logitech USB Receiver: Configuring as mouse
[    64.571] (II) Logitech USB Receiver: Configuring as keyboard
[    64.571] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    64.571] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    64.571] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    64.571] (**) Option "xkb_rules" "evdev"
[    64.571] (**) Option "xkb_model" "pc105"
[    64.571] (**) Option "xkb_layout" "us"
[    64.571] (II) Logitech USB Receiver: initialized for relative axes.
[    64.571] (WW) Logitech USB Receiver: ignoring absolute axes.
[    64.572] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    64.572] (II) No input driver/identifier specified (ignoring)

```

---

### Post by sandyd on 2010-10-18
> **CryptiniteDemon said:**
> glxinfo:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 260.19.12
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_sync, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_multisample, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vdpau_interop, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x041 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x042 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x044 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x045 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x046 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x048 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x049 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x04a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x054 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x056 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x05f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x060 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x063 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x064 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x065 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x067 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x068 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x069 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06a 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x070 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x071 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x072 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon

164 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0ca  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cc  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cd  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0ce  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0cf  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0d0  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0d1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d2  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d4  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d5  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d6  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d7  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d8  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d9  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0da  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0db  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dc  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0de  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0df  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e0  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e1  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e2  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e3  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e4  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e5  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e6  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e7  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e8  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e9  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ea  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0eb  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ec  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ed  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ee  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ef  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f0  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f1  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f2  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f3  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f4  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f5  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f6  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f7  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f8  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f9  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fa  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fb  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fc  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fd  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0fe  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x0ff  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x100  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x102  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x103  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x104  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10a  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10b  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10c  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10e  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x10f  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x110  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x112  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x113  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x114  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x116  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x117  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x118  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None

```
Xorg log
```
[    30.782] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    30.782] X Protocol Version 11, Revision 0
[    30.782] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    30.782] Current Operating System: Linux corei7 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64
[    30.782] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=4d5c4f06-c95c-45ab-a94f-f1cbcf61a487 ro quiet splash
[    30.782] Build Date: 16 September 2010  06:18:41PM
[    30.782] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    30.782] Current version of pixman: 0.18.4
[    30.782]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    30.782] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.782] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 18 22:02:28 2010
[    30.782] (==) Using config file: "/etc/X11/xorg.conf"
[    30.782] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.782] (==) ServerLayout "Layout0"
[    30.782] (**) |-->Screen "Screen0" (0)
[    30.782] (**) |   |-->Monitor "Monitor0"
[    30.782] (**) |   |-->Device "Device0"
[    30.782] (**) |-->Input Device "Keyboard0"
[    30.782] (**) |-->Input Device "Mouse0"
[    30.782] (==) Automatically adding devices
[    30.782] (==) Automatically enabling devices
[    30.782] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.782]     Entry deleted from font path.
[    30.782] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    30.782] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.782] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.782] (WW) Disabling Keyboard0
[    30.782] (WW) Disabling Mouse0
[    30.782] (II) Loader magic: 0x7d0200
[    30.782] (II) Module ABI versions:
[    30.782]     X.Org ANSI C Emulation: 0.4
[    30.782]     X.Org Video Driver: 8.0
[    30.782]     X.Org XInput driver : 11.0
[    30.782]     X.Org Server Extension : 4.0
[    30.783] (--) PCI:*(0:2:0:0) 10de:0605:3842:c977 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072
[    30.783] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    30.783] (II) "extmod" will be loaded by default.
[    30.783] (II) "dbe" will be loaded by default.
[    30.783] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    30.783] (II) "record" will be loaded by default.
[    30.783] (II) "dri" will be loaded by default.
[    30.783] (II) "dri2" will be loaded by default.
[    30.783] (II) LoadModule: "glx"
[    30.805] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.810] (II) Module glx: vendor="NVIDIA Corporation"
[    30.810]     compiled for 4.0.2, module version = 1.0.0
[    30.810]     Module class: X.Org Server Extension
[    30.810] (II) NVIDIA GLX Module  260.19.12  Fri Oct  8 11:41:55 PDT 2010
[    30.811] (II) Loading extension GLX
[    30.811] (II) LoadModule: "extmod"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.811] (II) Module extmod: vendor="X.Org Foundation"
[    30.811]     compiled for 1.9.0, module version = 1.0.0
[    30.811]     Module class: X.Org Server Extension
[    30.811]     ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension MIT-SCREEN-SAVER
[    30.811] (II) Loading extension XFree86-VidModeExtension
[    30.811] (II) Loading extension XFree86-DGA
[    30.811] (II) Loading extension DPMS
[    30.811] (II) Loading extension XVideo
[    30.811] (II) Loading extension XVideo-MotionCompensation
[    30.811] (II) Loading extension X-Resource
[    30.811] (II) LoadModule: "dbe"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.811] (II) Module dbe: vendor="X.Org Foundation"
[    30.811]     compiled for 1.9.0, module version = 1.0.0
[    30.811]     Module class: X.Org Server Extension
[    30.811]     ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension DOUBLE-BUFFER
[    30.811] (II) LoadModule: "record"
[    30.811] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.811] (II) Module record: vendor="X.Org Foundation"
[    30.811]     compiled for 1.9.0, module version = 1.13.0
[    30.811]     Module class: X.Org Server Extension
[    30.811]     ABI class: X.Org Server Extension, version 4.0
[    30.811] (II) Loading extension RECORD
[    30.811] (II) LoadModule: "dri"
[    30.812] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.812] (II) Module dri: vendor="X.Org Foundation"
[    30.812]     compiled for 1.9.0, module version = 1.0.0
[    30.812]     ABI class: X.Org Server Extension, version 4.0
[    30.812] (II) Loading extension XFree86-DRI
[    30.812] (II) LoadModule: "dri2"
[    30.812] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.812] (II) Module dri2: vendor="X.Org Foundation"
[    30.812]     compiled for 1.9.0, module version = 1.2.0
[    30.812]     ABI class: X.Org Server Extension, version 4.0
[    30.812] (II) Loading extension DRI2
[    30.812] (II) LoadModule: "nvidia"
[    30.812] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    30.812] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.812]     compiled for 4.0.2, module version = 1.0.0
[    30.812]     Module class: X.Org Video Driver
[    30.812] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[    30.812] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.812] (++) using VT number 7

[    30.813] (II) Loading sub module "fb"
[    30.813] (II) LoadModule: "fb"
[    30.814] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.814] (II) Module fb: vendor="X.Org Foundation"
[    30.814]     compiled for 1.9.0, module version = 1.0.0
[    30.814]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.814] (II) Loading sub module "wfb"
[    30.814] (II) LoadModule: "wfb"
[    30.814] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.814] (II) Module wfb: vendor="X.Org Foundation"
[    30.814]     compiled for 1.9.0, module version = 1.0.0
[    30.814]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.814] (II) Loading sub module "ramdac"
[    30.814] (II) LoadModule: "ramdac"
[    30.814] (II) Module "ramdac" already built-in
[    30.814] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.814] (==) NVIDIA(0): RGB weight 888
[    30.814] (==) NVIDIA(0): Default visual is TrueColor
[    30.814] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.814] (**) NVIDIA(0): Option "NoLogo" "True"
[    30.814] (**) NVIDIA(0): Enabling RENDER acceleration
[    30.814] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    30.814] (II) NVIDIA(0):     enabled.
[    37.751] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:2:0:0 (GPU-0)
[    37.751] (--) NVIDIA(0): Memory: 524288 kBytes
[    37.751] (--) NVIDIA(0): VideoBIOS: 62.92.69.00.70
[    37.751] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    37.751] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    37.751] (--) NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:2:0:0
[    37.751] (--) NVIDIA(0):     Toshiba TSB-TV (DFP-0)
[    37.751] (--) NVIDIA(0): Toshiba TSB-TV (DFP-0): 330.0 MHz maximum pixel clock
[    37.751] (--) NVIDIA(0): Toshiba TSB-TV (DFP-0): Internal Dual Link TMDS
[    37.862] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    37.862] (==) NVIDIA(0): 
[    37.862] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    37.862] (==) NVIDIA(0):     will be used as the requested mode.
[    37.862] (==) NVIDIA(0): 
[    37.862] (II) NVIDIA(0): Validated modes:
[    37.862] (II) NVIDIA(0):     "nvidia-auto-select"
[    37.862] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    37.905] (--) NVIDIA(0): DPI set to (46, 46); computed from "UseEdidDpi" X config
[    37.905] (--) NVIDIA(0):     option
[    37.905] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    37.905] (--) Depth 24 pixmap format is 32 bpp
[    37.905] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    37.907] (II) NVIDIA(0): Initialized GPU GART.
[    37.922] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    37.945] (II) Loading extension NV-GLX
[    37.975] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    37.997] (==) NVIDIA(0): Disabling shared memory pixmaps
[    37.997] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    37.997] (==) NVIDIA(0): Backing store disabled
[    37.997] (==) NVIDIA(0): Silken mouse enabled
[    38.009] (**) NVIDIA(0): DPMS enabled
[    38.009] (II) Loading extension NV-CONTROL
[    38.010] (II) Loading extension XINERAMA
[    38.010] (II) Loading sub module "dri2"
[    38.010] (II) LoadModule: "dri2"
[    38.010] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    38.010] (II) NVIDIA(0): [DRI2] Setup complete
[    38.010] (==) RandR enabled
[    38.010] (II) Initializing built-in extension Generic Event Extension
[    38.010] (II) Initializing built-in extension SHAPE
[    38.010] (II) Initializing built-in extension MIT-SHM
[    38.010] (II) Initializing built-in extension XInputExtension
[    38.010] (II) Initializing built-in extension XTEST
[    38.010] (II) Initializing built-in extension BIG-REQUESTS
[    38.010] (II) Initializing built-in extension SYNC
[    38.010] (II) Initializing built-in extension XKEYBOARD
[    38.010] (II) Initializing built-in extension XC-MISC
[    38.010] (II) Initializing built-in extension SECURITY
[    38.010] (II) Initializing built-in extension XINERAMA
[    38.010] (II) Initializing built-in extension XFIXES
[    38.010] (II) Initializing built-in extension RENDER
[    38.010] (II) Initializing built-in extension RANDR
[    38.010] (II) Initializing built-in extension COMPOSITE
[    38.010] (II) Initializing built-in extension DAMAGE
[    38.010] (II) Initializing built-in extension GESTURE
[    38.010] (II) Initializing extension GLX
[    38.030] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    38.035] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    38.035] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.035] (II) LoadModule: "evdev"
[    38.035] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    38.035] (II) Module evdev: vendor="X.Org Foundation"
[    38.035]     compiled for 1.9.0, module version = 2.3.2
[    38.035]     Module class: X.Org XInput Driver
[    38.035]     ABI class: X.Org XInput driver, version 11.0
[    38.035] (**) Power Button: always reports core events
[    38.035] (**) Power Button: Device: "/dev/input/event1"
[    42.580] (II) Power Button: Found keys
[    42.580] (II) Power Button: Configuring as keyboard
[    42.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    42.580] (**) Option "xkb_rules" "evdev"
[    42.580] (**) Option "xkb_model" "pc105"
[    42.580] (**) Option "xkb_layout" "us"
[    42.581] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    42.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.581] (**) Power Button: always reports core events
[    42.581] (**) Power Button: Device: "/dev/input/event0"
[    54.205] (II) Power Button: Found keys
[    54.205] (II) Power Button: Configuring as keyboard
[    54.205] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    54.205] (**) Option "xkb_rules" "evdev"
[    54.205] (**) Option "xkb_model" "pc105"
[    54.205] (**) Option "xkb_layout" "us"
[    54.206] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    54.206] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    54.206] (**) Logitech USB Receiver: always reports core events
[    54.206] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    58.574] (II) Logitech USB Receiver: Found keys
[    58.574] (II) Logitech USB Receiver: Configuring as keyboard
[    58.574] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    58.574] (**) Option "xkb_rules" "evdev"
[    58.574] (**) Option "xkb_model" "pc105"
[    58.574] (**) Option "xkb_layout" "us"
[    58.574] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    58.574] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    58.574] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    58.574] (**) Logitech USB Receiver: always reports core events
[    58.574] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    64.571] (II) Logitech USB Receiver: Found 12 mouse buttons
[    64.571] (II) Logitech USB Receiver: Found scroll wheel(s)
[    64.571] (II) Logitech USB Receiver: Found relative axes
[    64.571] (II) Logitech USB Receiver: Found x and y relative axes
[    64.571] (II) Logitech USB Receiver: Found absolute axes
[    64.571] (II) evdev-grail: failed to open grail, no gesture support
[    64.571] (II) Logitech USB Receiver: Found keys
[    64.571] (II) Logitech USB Receiver: Configuring as mouse
[    64.571] (II) Logitech USB Receiver: Configuring as keyboard
[    64.571] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    64.571] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    64.571] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    64.571] (**) Option "xkb_rules" "evdev"
[    64.571] (**) Option "xkb_model" "pc105"
[    64.571] (**) Option "xkb_layout" "us"
[    64.571] (II) Logitech USB Receiver: initialized for relative axes.
[    64.571] (WW) Logitech USB Receiver: ignoring absolute axes.
[    64.572] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    64.572] (II) No input driver/identifier specified (ignoring)

```
[http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/](http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/)
use the more extreme one.

looks like the new version of xorg broke something

---

### Post by birkopf on 2010-11-02
> **sandyd said:**
> [http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/](http://www.omgubuntu.co.uk/2010/09/nvidia-graphics-laggy-ubuntu-fix/)
use the more extreme one.

looks like the new version of xorg broke something

Try to uninstall any previous versions of nvidia drivers (I can write you command if you'd want, but basically sudo apt-get remove --purge nvidia* will do rock n' roll :guitar: )

try this guide:

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

it contains official stable release of nvidia drivers. it that wouldn't help, you could try installing envy.


I actually had problem with driver myself. Solution for me: Don't Touch restricted drivers. I just installed driver 173 from ubuntu software centre and it works fine. There seems to be difference, but I cannot explain. 

let us know how it went on!

---


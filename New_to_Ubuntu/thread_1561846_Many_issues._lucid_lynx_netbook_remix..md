---
title: "Many issues. lucid lynx netbook remix."
date: 2010-08-26
forum: New to Ubuntu
---

### Post by slyJ on 2010-08-26
recently installed lucid lynx. netbook remix and came up with problems after installing the updates and everything.

I have a Samsung NC10.

Problems include.
1. Startup = Ubuntu is running in low graphics mode.
2. No proprietary drivers are in use. (intel gma 950)
3. Cannot find where I installed ubuntu into. No idea how to remove it. (i was thinking of going back to hardy heron, because i've used it before on another laptop, i also read that NC10 has no issues with it)

---

### Post by jtarin on 2010-08-26
For your graphics lets look at what we might do. I will need you to run a few commands in the terminal and post the results so we can help. First one ```
lspci -v -t
```

---

### Post by slyJ on 2010-08-26
-[0000:00]-+-00.0  Intel Corporation Mobile 945GME Express Memory Controller Hub
           +-02.0  Intel Corporation Mobile 945GME Express Integrated Graphics Controller
           +-02.1  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
           +-1b.0  Intel Corporation N10/ICH 7 Family High Definition Audio Controller
           +-1c.0-[0000:02]----00.0  Atheros Communications Inc. AR5001 Wireless Network Adapter
           +-1c.2-[0000:03]----00.0  Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
           +-1d.0  Intel Corporation N10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation N10/ICH 7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation N10/ICH 7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation N10/ICH 7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
           +-1e.0-[0000:04]--
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller
           \-1f.3  Intel Corporation N10/ICH 7 Family SMBus Controller

---

### Post by jtarin on 2010-08-26
OK...good. Now ```
lsmod
```

---

### Post by slyJ on 2010-08-26
[PHP]Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_hda_codec_realtek   203310  1 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          21941  2 
joydev                  8708  0 
arc4                    1153  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121792  0 
uvcvideo               56990  0 
i915                  285076  3 
mac80211              205146  1 ath5k
drm_kms_helper         29297  1 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
usbhid                 36110  0 
lp                      7028  0 
ath                     7611  1 ath5k
intel_agp              24119  2 i915
drm                   162409  2 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  1 i915
soundcore               6620  1 snd
hid                    67032  1 usbhid
psmouse                63245  0 
cfg80211              126517  3 ath5k,mac80211,ath
serio_raw               3978  0 
output                  1871  1 video
led_class               2864  1 ath5k
agpgart                31724  2 intel_agp,drm
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
sky2                   40775  0 

[/PHP]

---

### Post by jtarin on 2010-08-26
Now ```
glxinfo
```

---

### Post by slyJ on 2010-08-26
[PHP]name of display: :1.0
display: :1  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
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
    GL_EXT_texture_swizzle, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_envmap_bumpmap, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, 
    GL_ATI_separate_stencil, GL_IBM_multimode_draw_arrays, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_resize_buffers, 
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_point_sprite, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc2 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc3 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc4 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xc5 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc6 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc7 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xc8 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc9 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xca 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xcb 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xcc 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xcd 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xce 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xcf 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd0 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xd1 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xd2 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd3 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd4 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xd5 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd6 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd7 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xd8 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd9 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xda 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xdb 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdc 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xdd 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xde 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xdf 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xe0 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe1 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe2 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xe3 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xe4 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xe5 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe6 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xe7 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe8 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe9 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xea 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xeb 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xec 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xed 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xee 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xef 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xf0 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf1 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf2 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xf3 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xf4 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xf5 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf6 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xf7 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf8 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf9 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfa 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xfb 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xfc 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xfd 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xfe 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xff 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x41 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x42  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x43  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x44  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x45  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x46  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x47  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x48  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x49  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x4a  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x4b  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x4c  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x4d  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x4e  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x4f  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x50  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x51  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x52  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x53  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x54  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x55  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x56  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x57  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x58  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x59  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x5a  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x5b  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x5c  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x5d  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x5e  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x5f  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x60  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x61  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x62  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x63  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x64  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x65  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x66  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x67  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x68  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x69  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x6a  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x6b  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x6c  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x6d  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x6e  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x6f  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x70  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x72  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x7a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x7e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x80  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x81  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x82  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x83  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x84  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x85  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x86  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x87  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x88  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x89  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x8a  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x8b  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x8c  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x8d  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x8e  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x8f  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x90  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x91  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x92  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x93  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x94  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x95  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x96  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x97  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x98  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x99  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x9a  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9b  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9c  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x9d  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x9f  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xa0  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0xa1  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0xa2  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa3  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa4  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xa5  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa6  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xa7  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xa8  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xa9  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xaa  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xab  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xac  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xad  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xae  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xaf  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb0  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xb1  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xb2  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb3  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb4  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xb5  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb6  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xb7  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xb8  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xb9  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xba  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbb  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbc  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xbd  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xbe  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbf  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xc0  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xc1  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

[/PHP]

---

### Post by jtarin on 2010-08-26
Ok everything appears good. Some people also have problems with the nVidia drivers competing with the intel ones after the upgrade; remove them with:
```
sudo apt-get --purge remove nvidia*
```

Just be careful to read what it wants to remove first.Then reboot.

You could have had a bad upgrade. Any error messages or other oddities?

---

### Post by slyJ on 2010-08-26
Ubuntu is running in low-graphics mode

Your screen,graphics card,and input device settings could not e detected correctly. You will need to configure these yourself.

^that's the full startup message.

Trying to figure out what was wrong I've also noticed that my xorg.conf is blank. <not sure what that means.

I've tried the removal of the nvidia & rebooted, no such luck of removing the startup message

---

### Post by jtarin on 2010-08-26
Lets try this then ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by slyJ on 2010-08-26
infinitej@infinitej:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for infinitej: 
infinitej@infinitej:~$ 


is this whats supposed to happen?

---

### Post by jtarin on 2010-08-26
> **slyJ said:**
> Ubuntu is running in low-graphics mode

 I've also noticed that my xorg.conf is blank. <not sure what that means.

In 10.04 there is no configuration upon install it is done on the fly with good-excellent result in most cases. Sometimes reverting back to using xorg is a better bet for some.

---

### Post by jtarin on 2010-08-26
> **slyJ said:**
> infinitej@infinitej:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for infinitej: 
infinitej@infinitej:~$ 


is this whats supposed to happen?you entered your password then nothing?

---

### Post by jtarin on 2010-08-26
> **jtarin said:**
> you entered your password then nothing?
If that is thecase then xorg is likely not installed...which is common in 10.04. Remove existing xorg using the following command. ```
sudo apt-get remove --purge xserver-xorg
```Install xorg using the following command```
sudo apt-get install xserver-xorg
```Reconfigure xorg using the following command```
sudo dpkg-reconfigure xserver-xorg
```I hope that helps. You might have to edit xorg to fine tune it after reboot.

---

### Post by jtarin on 2010-08-26
I must add this chipset you have is less than optimal for running on Ubuntu 10.04 at present, but you can get it working....somewhat. maybe not to your liking but we'll try to do what we can. What kernel are you using and are you using Grub2 to boot or Legacy Grub?

---

### Post by slyJ on 2010-08-27
i think it was something like 2.6.34 something, but now i cannot be sure. 

after i set that up, i cannot boot into lucid. nothing in recovery mode works. i think its because reconfigure did nothing when i did it in terminal before i reboot. now im looking into removing lucid and placing hardy 8.04 which i have a boot usb for.

startup leads to terminal, cannot boot into ubuntu.

---

### Post by jtarin on 2010-08-27
Do you get any messages? If you don't want to try and configure xorg you can remove it with sudo ```
apt-get remove --purge xserver-xorg
```To find your kernel version from the terminal ```
uname -v
```

---


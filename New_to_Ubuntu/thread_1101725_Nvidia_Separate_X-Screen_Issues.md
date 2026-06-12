---
title: "Nvidia Separate X-Screen Issues"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by yogiman.uk on 2009-03-20
Hi

I have an NVidia 6600 AGP twin outputs.  I have setup dual monitors and I have set it so that I have 2 separate x screens.

Can anyone advise me on the following problems:-

1. I can not drag windows between the two x-screens is this possible without using Twin View?

2. I can not choose to run applications on one or the other screen, i.e if I attempt launch OpenOffice on the 2nd screen it always appears on the left, is there a way to allow a choice of which screen.

3. I can launch Firefox on screen 1 no problem, I can launch multiple firefox occurrences on screen 1 no problem, but if I have a copy on screen 1 and attempt to open a copy on screen 2 it crashes and I have to restart x.  Am I doing something wrong or is this a known bug?

Any help would be appreciated, thanks in advance.

Regards


Yogiman

---

### Post by NT4usB on 2009-03-22
> **yogiman.uk said:**
> Hi

I have an NVidia 6600 AGP twin outputs.  I have setup dual monitors and I have set it so that I have 2 separate x screens.

Can anyone advise me on the following problems:-

1. I can not drag windows between the two x-screens is this possible without using Twin View?

Don't think windows will drag (they don't for me) but files do. Also, copy/paste.> 

2. I can not choose to run applications on one or the other screen, i.e if I attempt launch OpenOffice on the 2nd screen it always appears on the left, is there a way to allow a choice of which screen.
Not sure why yours acts that way. My apps launch in the screen I click them in.
You can force things by using the command line```
DISPLAY=":0.1" *some application*
```> 

3. I can launch Firefox on screen 1 no problem, I can launch multiple firefox occurrences on screen 1 no problem, but if I have a copy on screen 1 and attempt to open a copy on screen 2 it crashes and I have to restart x.  Am I doing something wrong or is this a known bug?Mine won't open on both windows at the same time either. *It's not a bug, it's a feature *g**

Post your xorg.conf and lets see if we can spot a problem.

---

### Post by yogiman.uk on 2009-03-23
Hi NT4Usb thank for the reply you're a :KS

Regards

yogiman!

---

### Post by bigbudz on 2009-05-08
I have the same problem with firefox and dual screens. Does anyone know of a fix for this?

---

### Post by eorisis on 2009-05-11
Hello, it looks like we have the same video card. I have worse problem just because I know less I think. My problem is that I cannot use it at 1280x1024 resolution even. everything looks big on the screen and I have no idea what to add in the xorg.conf file. I have this problem for more than a year now. today I installed the new ubuntu 9.04 desktop i386 hoping it would see the card but no luck. even browsing with firefox is slow. of course I have activated the restricted drivers (v180), and it looks like it works well with 3d like compiz and 3d screensavers (never run games here)..

on my laptop ubuntu works great.

here is some info about the card taken from a windows software, pc wizard 2008.
I don't know what to do to make even the resolution work, so it would be just great if someone tells me what to look for, I wanna make it work. thanks and congrats for the great new release of ubuntu.




[FONT=FreeSans, sans-serif][SIZE=2][COLOR=#800000]**VIDEO CARD: **[/COLOR][COLOR=#800000]**NVIDIA GeForce 6600 **[/COLOR][/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]**General Information :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Manufacturer :    Nvidia Corp [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Model :    NVIDIA GeForce 6600 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Bus Type :    AGP [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Total Memory :    256 MB [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Texture Memory :    362 MB [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Processor :    GeForce 6600 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Converter :    Integrated RAMDAC [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Refresh Rate (min/max) :    60/75 Hz [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Codename :    NV43 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Revision :    A4 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Bus :    128-bit [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Memory Type :    DDR [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GPU Frequency :    300.86 MHz - [initial : 300 MHz] [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Memory Frequency GPU :    501.19 MHz - [initial : 500 MHz] [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Pixel Pipelines :    8 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Vertex Pipelines :    3 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Texels :    4000 MTexels/s [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]DirectX Support :    9.0c [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Pixel Shader Version :    3.0 [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**nForceware Configuration :**     [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Standard 2D :    GPU: 300 MHz - Memory: 500 MHz [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]3D Performance :    GPU: 300 MHz - Memory: 500 MHz [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]ForceWare Version :    6.14.11.7813 [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**GPU Configuration :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Technology SLi :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]AA Mode :    OFF [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Frame Buffered :    3 [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Video Bios Information :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Date :    06/01/05 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Version :    Version 5.43.02.71.00  [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]ID :    Version 5.43.02.71.00 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Bios SignOn :    GeForce 6600 VGA BIOS IDN1 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Forceware :    6.14.11.7813 [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**i2C Bus Information :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Number of Bus :    3 [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**General Features :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Width :    300 mm [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Height :    240 mm [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Pixel per inch :    96x96 dpi [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]bits per pixel :    32 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Colour Bits/Planes :    1 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Brushes :    4294967295 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Pens :    4294967295 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Markers :    0 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Device Fonts :    0 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Device Colours :    4294967295 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Clip Output to Rectangle :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Hardware Acceleration :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Blend and Shade Capabilities :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GradientFill Rectangle :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GradientFill Traingle :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Per Pixel AlphaBlend :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Premultiplied Alpha :    No [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Raster Capabilities :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Banding :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Transfer Bitmaps :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Bitmap >64 KB :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Fonts larger than 64 K :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]DIBs :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]DIBTODEV :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Flood Fills :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Scaling :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]StretchBlt :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]StretchDIB :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Curves Capabilities :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Chord Arcs :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Circles :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Elipses :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Interiors :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Pie Wedges :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Rounded Rectangles :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Styled Borders :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide Borders :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide, Styled Borders :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Lines Capabilities :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Interiors :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Markers :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Polylines :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Polymarkers :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Styled :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide, Styled :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Polygonal Capabilities :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Interiors :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Alternate Fill Polygons :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Winding Fill Polygons :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Rectangles :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Scan Lines :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Styled Borders :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide Borders :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Wide, Styled Borders :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Text Capabilities :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Stroke Precision :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Stroke Clip Precision :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]90° Character Rotation :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Any Angle Character Rotation :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Independent X-Y Scaling :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Double Weighted Characters :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Italic :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Underline :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Strikeout :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Raster Fonts :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Vector Fonts :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Color Management Capabilities :     **[/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]CMYK :    No [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Gamma Ramp :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]ICM Device :    No[/SIZE][/FONT]
 




                                 [COLOR=#800000][FONT=FreeSans, sans-serif][SIZE=2]**OPEN GL**[/SIZE][/FONT][/COLOR]
 [FONT=FreeSans, sans-serif][SIZE=2]**General Information :**     [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Manufacturer :    NVIDIA Corporation [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Version :    2.1.2 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Renderer :    GeForce 6600/AGP/SSE2 [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Acceleration :    Yes, Hardware [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Extensions :    ** [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_color_buffer_float :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_depth_texture :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_draw_buffers :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_fragment_program :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_fragment_program_sha...    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_fragment_shader :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_half_float_pixel :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_imaging :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_multisample :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_multitexture :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_occlusion_query :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_pixel_buffer_object :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_point_parameters :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_point_sprite :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_shadow :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_shader_objects :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_shading_language_100 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_border_clamp :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_compression :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_cube_map :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_env_add :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_env_combine :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_env_dot3 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_float :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_mirrored_repeat :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_non_power_of_...    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_texture_rectangle :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_transpose_matrix :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_vertex_buffer_object :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_vertex_program :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_vertex_shader :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ARB_window_pos :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ATI_draw_buffers :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ATI_texture_float :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_ATI_texture_mirror_once :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_S3_s3tc :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_env_add :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_abgr :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_bgra :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_blend_color :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_blend_equation_separate :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_blend_func_separate :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_blend_minmax :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_blend_subtract :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_compiled_vertex_array :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_Cg_shader :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_depth_bounds_test :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_draw_range_elements :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_fog_coord :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_framebuffer_blit :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_framebuffer_multisample :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_framebuffer_object :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_gpu_program_parameters :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_multi_draw_arrays :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_packed_depth_stencil :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_packed_pixels :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_pixel_buffer_object :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_point_parameters :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_rescale_normal :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_secondary_color :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_separate_specular_color :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_shadow_funcs :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_stencil_two_side :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_stencil_wrap :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture3D :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_compression_s3...    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_cube_map :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_edge_clamp :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_env_combine :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_env_dot3 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_filter_anisotropic :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_lod :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_lod_bias :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_mirror_clamp :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_object :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_texture_sRGB :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_timer_query :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_EXT_vertex_array :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_IBM_rasterpos_clip :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_IBM_texture_mirrored_repeat :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_KTX_buffer_region :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_blend_square :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_copy_depth_to_color :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_depth_clamp :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_fence :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_float_buffer :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_fog_distance :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_fragment_program :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_fragment_program_option :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_fragment_program2 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_framebuffer_multisample_...    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_half_float :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_light_max_exponent :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_multisample_filter_hint :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_occlusion_query :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_packed_depth_stencil :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_pixel_data_range :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_point_sprite :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_primitive_restart :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_register_combiners :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_register_combiners2 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texgen_reflection :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_compression_vtc :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_env_combine4 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_expand_normal :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_rectangle :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_shader :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_shader2 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_texture_shader3 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_array_range :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_array_range2 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_program :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_program1_1 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_program2 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_program2_option :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NV_vertex_program3 :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_NVX_conditional_render :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_SGIS_generate_mipmap :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_SGIS_texture_lod :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_SGIX_depth_texture :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_SGIX_shadow :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_SUN_slice_accum :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]GL_WIN_swap_hint :    Yes [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]WGL_EXT_swap_control :    Yes [/SIZE][/FONT] 
 

 [FONT=FreeSans, sans-serif][SIZE=2]**Texture Information :**     [/SIZE][/FONT] 
 [FONT=FreeSans, sans-serif][SIZE=2]Maximum Texture Size :    4096 x 4096 [/SIZE][/FONT]

---


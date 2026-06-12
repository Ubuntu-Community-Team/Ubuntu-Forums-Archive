---
title: "CPU scaling?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by techunit on 2010-05-01
Hi can anybody help me set up CPU scaling on my laptop before it over heats?

I have a 2GHz core2duo

I have some control but it is still getting hot... Thanks for any help..

 Update & Notice: 
This thread was posted on the inaccurate assumption that my system was not scaling the CPU accurately. This was inaccurate and had more to do with bad Graphics Drivers as I am finding out from a different thread.

---

### Post by clhsharky on 2010-05-01
HI 

Whats your video chip,may be part of solution?

Sharky

---

### Post by techunit on 2010-05-01
I have a ATI Radion  HD3650

---

### Post by clhsharky on 2010-05-01
techunit

Have you install fglrx? The proprietary ATI video driver.

---

### Post by techunit on 2010-05-01
no becuase it was causing problems

---

### Post by clhsharky on 2010-05-01
OK what problems with fglrx? and there a little help with OSS drivers.

Sharky

Are you still on Karmic?

---

### Post by techunit on 2010-05-01
Alright... You understand we are talking about CPU scaling right not GPU scaling.

Problems: Boot splash was wrong resolution and I couldn't recover from suspend...

---

### Post by techunit on 2010-05-01
NO I'm on Lucid

---

### Post by clhsharky on 2010-05-01
OK whats your idle?

---

### Post by techunit on 2010-05-01
I installed cpufrequtils and sysfsutils and that helped a little bit I think. It cooled down some.

---

### Post by techunit on 2010-05-01
800MHZ is my idle according to CPU scaling applet

---

### Post by techunit on 2010-05-01
I know I have some cpu scaling but my computer is still getting pretty hot..

---

### Post by clhsharky on 2010-05-01
Good glad to hear that.

There is some Power Management for OSS but not on stock Lucid if your interested.

Sharky

Is fan still loud?

---

### Post by techunit on 2010-05-01
What is OSS and sure I'm plenty experience but I don't know everything...

---

### Post by techunit on 2010-05-01
The fan isn't loud until I restart Then I get loud.

---

### Post by techunit on 2010-05-01
Look I can be more descriptive if need be but I don't know what you need to know. I am not new to linux but this is an area where I don't have much knowledge on it.

---

### Post by techunit on 2010-05-01
Generally I just set p4_clockmod to run at start-up and everything starts working but it hasn't worked since jaunty

---

### Post by clhsharky on 2010-05-01
The OSS drivers "Open Source Stack" default Lucid includes

DDX 'radeon driver '
drm  lib
DRM2  lib
mesa
kernel
xserver

all that is used in OSS drivers
Theres more but it depends on what chip.
And with Lucid we have KMS 'kernel mode setting' Karmic had UMS 'user mode space'

That the open sconce drivers, you don't need to know all that, but you asked.

The rest is easy , are you running KMS now?

Sharky

---

### Post by techunit on 2010-05-01
How would I know Which I am using.

---

### Post by techunit on 2010-05-01
I am on lucid so I must have KMS correct

---

### Post by techunit on 2010-05-01
All right lets try OSS

---

### Post by clhsharky on 2010-05-01
Lucid is KMS unless you changed it "nomodeset" at boot string.

```
glxinfo
```

Might need to install  " mesa-utils "

---

### Post by techunit on 2010-05-01
Should I install them?

---

### Post by clhsharky on 2010-05-01
Yes

Its going to tell info thats needed

---

### Post by techunit on 2010-05-01
I have to post a large log yes? If so how do I make a code box for that (I am used to HTML)

---

### Post by clhsharky on 2010-05-01
Just the first half

move your pointer across the icons at top where your posting an you will see code
past in between code boxes it will fill out.

---

### Post by techunit on 2010-05-01
```
tobias@tobias-laptop:~$ glxinfo
name of display: :0.0
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
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV635 9591) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
    GL_EXT_compiled_vertex_array, GL_EXT_texture_env_add, 
    GL_ARB_depth_texture, GL_ARB_depth_clamp, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_provoking_vertex, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_MESAX_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
```

Here it is

---

### Post by clhsharky on 2010-05-01
OK  you got KMS

> OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV635 9591) 20090101  TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1


DRI2 is KMS 

Power Management for OSS is in kernel.
Have you installed a kernel image before?

---

### Post by techunit on 2010-05-01
I believe I have on a netbook

---

### Post by techunit on 2010-05-01
Is there a comand to tell me how hot my system is running (temp)

---

### Post by clhsharky on 2010-05-01
OK its not hard

were installing kernel 2.6.34.rc6

you will need these 3 deb downloaded
installed 1 at a time 
in this order
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb	
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb

from here
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc6-lucid/)


then restart

You may need radeon.dynpm=1 in the boot string to enable dynamic PM with a 2.6.34 kernel.
While installing debs if it asks you about config choose the one you have

the .34 kernel is also more stable than U.32

I'm waiting right here

Sharky


temp there is but I'll have to find it .If you want to wait Ill search

> cat /proc/acpi/thermal_zone/THRM/temperature

---

### Post by techunit on 2010-05-01
Im not sure about installing a different linux kernel. Generally there is an easier way to get around the problem.

---

### Post by techunit on 2010-05-01
I would like to know what temperature my system is at right know so I can tell if installing cpufrequtils and sysfsutils helped any...

---

### Post by techunit on 2010-05-01
Its not that I don't trust you but I do understand that installing a different kernel can solve your problem but also create more problems

---

### Post by clhsharky on 2010-05-01
Ok

---

### Post by techunit on 2010-05-01
I also understand that if you feel that you can't help me because I am too cautious, but let me know don't leave me hanging ok! :)

---

### Post by clhsharky on 2010-05-01
I wouldn't do that,  but I understand your hesitance. and i see you understand what your doing to, good.

Your old kernel will still be there to fallback on in grub so you wont get totally s*****.

Would you like to do more reading on this I can point you to?

Sharky

Be right back take a break

---

### Post by techunit on 2010-05-01
Yes of course...

---

### Post by techunit on 2010-05-01
Information like lowering the clock speed and increasing the number of Mhz steps would be nice if you can help with that. I know that you have already helped me a lot. Thanks alot :)

---

### Post by mc4man on 2010-05-01
Sorry - curiousity has gotten the best of me - haven't seen you post your temps yet
(run numerous times to get better idea

```
cat /proc/acpi/thermal_zone/THM/temperature

```

---

### Post by clhsharky on 2010-05-01
techunit

You will see some UMS PM thas done in xorg.conf it stays the same no power up always the same but helpful for some people.
And dynamic PM thats in kernel, KMS.The first thread there talking about  whats in the kernel .The last thread is what there working on now.

2.6.34 and power management
[http://www.phoronix.com/forums/showthread.php?t=23201](http://www.phoronix.com/forums/showthread.php?t=23201)
[http://www.phoronix.com/forums/showthread.php?t=23227](http://www.phoronix.com/forums/showthread.php?t=23227)
[http://www.phoronix.com/forums/showthread.php?t=23447](http://www.phoronix.com/forums/showthread.php?t=23447)

 You will find several dev here. Have fun I'll check back in a while ,
send me a message or something.

Sharky

---

### Post by techunit on 2010-05-01
Thanks Sharky

---

### Post by techunit on 2010-05-01
> **mc4man said:**
> Sorry - curiousity has gotten the best of me - haven't seen you post your temps yet
(run numerous times to get better idea

```
cat /proc/acpi/thermal_zone/THM/temperature

```

Doesn't work in lucid

---

### Post by clhsharky on 2010-05-01
Ill search
I've seen others just don't remember where I saw it
Doesn't work on mine ether, learn something new every day.

The kernel dynamic PM is about half or better than fglrx is at the moment, but is expected to come in at less than 7-8 watts difference on entry level gaming card "4770-5750" with next patch. Already tested.

---

### Post by mc4man on 2010-05-01
> Doesn't work in lucid 
Guess setups can be different
lucid - core2duo
> doug@doug-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature 
temperature:             40 C


(I'd go to /proc/acpi/... and see what's there, load and reload the file if it exists somewhere...

---

### Post by techunit on 2010-05-01
I get 0 degree Celsius so obviously something isn't right

---

### Post by techunit on 2010-05-01
I think it may have more to do with fan speed. I don't think the fan was moving...

---

### Post by techunit on 2010-05-02
It looks like I had CPU scaling all along but what happened was the GPU drivers FGLRX was causing my system to get hot. Also when I was using it my systems fans were not very responsive. After removing them and doing a switch to battery power and then back to AC (NOT SURE HOW THIS HELPED BUT IT DID) The fans started up and the system started running much cooler.

---

### Post by techunit on 2010-05-02
Still not sure why my sensors are still not recognized... It may help if I change the thread name.

---

### Post by techunit on 2010-05-02
I am marking this thread solved now seeing that the thread title is not accurate to the true issue.

---

### Post by clhsharky on 2010-05-02
Good to hear your progressing.

Sharky

---


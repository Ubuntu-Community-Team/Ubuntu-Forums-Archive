---
title: "Problems with ubuntu 8.10 on laptop"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by teranex on 2008-12-04
Hi,

Two days ago a installed ubuntu on a Acer Travelmate 4001, and i have some problems, which i can't seem to fix. Obviously i already searched this forum and google and tried some things, but none of them seemed to fix the problem and as i'm a new linux user i don't really know what i'm doing, so maybe i even made things worse while trying to fix them...

* Whenever i shutdown the laptop, i see a black screen with "acpid exiting..." (and a blinking cursor), and the laptop is not turned off (i can turn it off by pressing and holding the power button for a few seconds). I guess this has something to do with ACPI, but i have no idea how to fix this

* Just after installation my x-server would freeze: i could move the mousepointer, but it didn't move smoothly, i could not type and i could not click (although somethimes i could manage to login). After googling and browsing this forum, i modified my xorg.conf file to use the VESA driver, and now i can login and use my laptop, but the screenresolution is completely wrong (it is 1024x768, while it should be 1200x800) and i can't change it, and i'm also not able to enable Compiz. I already tried to install the ATI drivers and modify the xorg.conf file, but when whenever i choose another driver in the config-file the x-server wont start anymore...

A friend of mine has the exact same laptop as i do, on which he also installed Ubuntu 8.10 just a week ago. He had problems with ACPI, which he had to disable using a kernel param before he could install (with ACPI enabled his laptop would crash). But his graphics card works without any problems and his xorg.conf-file is allmost empty.

any help is very much appreciated as i have no idea how to fix these issues....

---

### Post by roger_1960 on 2008-12-04
Hi

Can you open a terminal applications-accessories-terminal

and then post the output of

xrandr -q

This should let you know what is possible.

This command 'xrandr' is the way to configure graphics in 8.10.  xorg should not really be used now.  Have a look also at 

man xrandr

for an explanation of the command.  Also see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

The absense of a GUI to edit screen resolution in 8.10 is, I believe, a registered bug which is being looked at.......

---

### Post by teranex on 2008-12-04
```
jeroen@thunderbox:~$ xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
```

I guess this list is not very complete, because my screen is a widescreen and those resolutions are all for normal screens...

My xorg.conf currently looks like
```

Section "Device"
	Identifier	"Configured Video Device"
	Option "UseFBDev" "true"
	Driver "vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option "DPMS"
	HorizSync 28-51
	VertRefresh 43-60
	#ModeLine "1024x768" 113.31 1024 1096 1208 1392 768 769 772 814 -HSync
	ModeLine "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        Subsection "Display"
            Depth 24
            Modes "1280x800"
        EndSubsection
EndSection

```

When i replace it with an allmost empty xorg.conf file my x-server doesn't start anymore (i just get a gui-less screen with a login-prompt)...

thx for any help!

---

### Post by Wickd on 2008-12-04
What graphics device are you using? Is it Nvidia, what? Also it would appear that your screen was not detected, could you post that model as well?

Also see if you can run the following command without error:

sudo /etc/init.d/acpid restart

Cherio :)

---

### Post by MeURi on 2008-12-04
Googling, I found that your laptop has an Ati video card. Is that correct? If so, you may want to use the Ati fglrx driver for your adapter; look in Synaptic for it, or check the restricted driver manager.

The resolution you get is completely wrong because you're using a general vesa driver, which does not support wide resolutions, nor resolutions higher than 1024x768 (I could be wrong about the latter, anyway).

Look [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

For the shutdown problem, if you see something different from the startup splash screen (going backwards, this time), you have one more problem :-P (regarding Usplash misconfigured). Anyway I can't help. Let me google a bit :-) (and I advise you to do the same, maybe the solution is real simple and already covered by others ;-))

---

### Post by teranex on 2008-12-04
It is indeed an ATI Radeon 9600 card.

I had already installed the drivers from the ati.com site without any luck. Now I followed the instructions from [BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). during installation of the first deb-package (fglrx-kernel-source_<version>.deb) i received some errors telling me that it was already installed (probably because i already tried to install the drivers). And when i executed the command `sudo aticonfig --initial' i got a Segmentation Fault. So i replaced my xorg.conf with just an 'allmost-empty' one (just the Device Monitor and Screen sections with Identifiers and a monitor and device reference in the Screen section). After rebooting i now have 1200x800 !! :) :)
However i still can not enable Compiz (Visual Effects in appearance settings is set to None). Although i could live with it it would be nice to have. When i run `fglrxinfo' i also get an error (which i guess is why i can't enable compiz):

```

jeroen@thunderbox:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault

```

I tried to remove the fglrx module as explained in [BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and rebooten again but this did not help.


About the acpid. This is the output of the command:
```

jeroen@thunderbox:~$ sudo /etc/init.d/acpid restart
[sudo] password for jeroen: 
 * Stopping ACPI services...                                             [ OK ] 
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                             [ OK ] 

```
i guess that looks OK

> **MeURi said:**
> For the shutdown problem, if you see something different from the startup splash screen (going backwards, this time), you have one more problem :-P (regarding Usplash misconfigured).

yep, i guess that's it. When i shutdown my laptop i can see the splash screen with the 'backwards' progressbar. When that is completely black, i get the black screen with just 'acpid exiting'... i'll try googling some more for that.

thx for the help!

---

### Post by teranex on 2008-12-04
It seems that i solved the shutdown issue by adding 
```

ifconfig eth0 down
ifconfig eth1 down

```
to /etc/init.d/alsa-utils as described here [https://answers.launchpad.net/ubuntu/+question/49799](https://answers.launchpad.net/ubuntu/+question/49799).

So now i'm only left with the problem that the GLX module can't be loaded and that i (prolly because of that) can't enable compiz, as i described in the previous post in this thread :). If somebody could help me with this last problem i would be a very happy man :)

---

### Post by teranex on 2008-12-05
Hmm apparently modifying /etc/init.d/alsa-utils didn't really fix the issue, because now sometimes it shuts down completely and other times it keeps displaying the message 'acpid exiting'. I also tried booting with the acpi=force kernel param but this didn't help either.

So i'm back at two problems left...

---

### Post by MeURi on 2008-12-06
I got no notification for your recent posts... anyway.

Glad you solved some of your problems. For the GLX issue, I think it should be loaded by default when starting X, but you can force it by having a section like this in your Xorg.conf:
```

Section "Module"
	Load	"glx"
EndSection

```
 If it exists already, simply add the *Load "glx"* option.

For the segmentation fault while running fglrxinfo, maybe it gets solved by loading the GLX module. Anyway, take a look at the Xorg.0.log placed into /var/log/ and see if it shows anything suspicious

---

### Post by teranex on 2008-12-07
Ok, I just got glxinfo and Compiz (! :) ) working. How i did it is a mystery to me :)
I was trying some more installs and uninstalls so as one of the steps in a how-to in did `sudo apt-get install xorg-driver-fglrx'. After rebooting my x-server didn't start anymore. So from the text-only login shell i did `sudo apt-get remove xorg-driver-fglrx' and rebooted again. My x-server started again and guess what, i can enable compiz :D

---

### Post by MeURi on 2008-12-08
Ehm... great! :-D I don't know how is this possible, though...

Check if something has been left over by previous installations, especially if you installed the drivers by hand, because if you have Xorg configured to load the fglrx driver, it should not start after you removed the driver ;-)

Also, if you are not interested in full 3D acceleration support, you may try the open source ati driver, as described [here](https://help.ubuntu.com/community/RadeonDriver).

---

### Post by teranex on 2008-12-08
> **MeURi said:**
> Ehm... great! :-D I don't know how is this possible, though...

Check if something has been left over by previous installations, especially if you installed the drivers by hand, because if you have Xorg configured to load the fglrx driver, it should not start after you removed the driver ;-)

Also, if you are not interested in full 3D acceleration support, you may try the open source ati driver, as described [here](https://help.ubuntu.com/community/RadeonDriver).

I guess it must have been some mix up of the closed source ATI drivers and the open source versions. In my x-org log i found a warning/error telling me that a module was not compatible with the version of another module (before i 'fixed' it). So i guess reinstalling and removing it again, just removed the incompatible versions somehow. I used [that page](https://help.ubuntu.com/community/RadeonDriver) indeed :). When i go to System > Administration > Hardware Drivers i get an empty list, so i guess i'm using the open source drivers. My xorg.conf, is allmost empty (i didn't specify a driver there).

This is the ouput from glxinfo now
```

jeroen@thunderbox ~
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
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
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x56  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x58  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x5a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5b  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x60  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

I'm really happy this is fixed :) now i'm only left with the acpid exiting problem... :)
thx for your help!

---

### Post by MeURi on 2008-12-08
You're welcome :-)

---

### Post by thepenguinonthetelly on 2008-12-16
I'm also having issues getting Compiz to work, apparently (also probably the same reason I'm having issues installing Google Earth).  It seems to be installed (already tried a reinstall via Synaptic), but it's missing from the System/Preference menu.  I'm on a laptop with onboard Intel graphics (I can't remember the command to find my card specs right now).

---

### Post by MeURi on 2008-12-18
For the command, issue a ```
lspci | grep VGA
```

Then, are you looking for Compiz in the menu, or for Google Earth?

The second can be enabled (if missing after installation) by right-clicking on the menu in the panel and choosing "_E_dit Menus"; then you have to find the entry and enable it, if it's disabled.

Compiz, instead, is not placed there. You can enable it via System->Appearance preferences, under the section "Visual Effects": if you have those settings to "None", Compiz is disabled. Every other setting enables it.

---

### Post by halovivek on 2008-12-18
> **teranex said:**
> Hi,

Two days ago a installed ubuntu on a Acer Travelmate 4001, and i have some problems, which i can't seem to fix. Obviously i already searched this forum and google and tried some things, but none of them seemed to fix the problem and as i'm a new linux user i don't really know what i'm doing, so maybe i even made things worse while trying to fix them...

* Whenever i shutdown the laptop, i see a black screen with "acpid exiting..." (and a blinking cursor), and the laptop is not turned off (i can turn it off by pressing and holding the power button for a few seconds). I guess this has something to do with ACPI, but i have no idea how to fix this

* Just after installation my x-server would freeze: i could move the mousepointer, but it didn't move smoothly, i could not type and i could not click (although somethimes i could manage to login). After googling and browsing this forum, i modified my xorg.conf file to use the VESA driver, and now i can login and use my laptop, but the screenresolution is completely wrong (it is 1024x768, while it should be 1200x800) and i can't change it, and i'm also not able to enable Compiz. I already tried to install the ATI drivers and modify the xorg.conf file, but when whenever i choose another driver in the config-file the x-server wont start anymore...

A friend of mine has the exact same laptop as i do, on which he also installed Ubuntu 8.10 just a week ago. He had problems with ACPI, which he had to disable using a kernel param before he could install (with ACPI enabled his laptop would crash). But his graphics card works without any problems and his xorg.conf-file is allmost empty.

any help is very much appreciated as i have no idea how to fix these issues....

Acer laptop always gives problem for linux and it is not supporting. i am using acer 5530 with no sound properly configured. really bad about Acer

---

### Post by thepenguinonthetelly on 2008-12-18
> **MeURi said:**
> For the command, issue a ```
lspci | grep VGA
```

Then, are you looking for Compiz in the menu, or for Google Earth?

The second can be enabled (if missing after installation) by right-clicking on the menu in the panel and choosing "_E_dit Menus"; then you have to find the entry and enable it, if it's disabled.

Compiz, instead, is not placed there. You can enable it via System->Appearance preferences, under the section "Visual Effects": if you have those settings to "None", Compiz is disabled. Every other setting enables it.

I couldn't find Google Earth, but a reinstall of that fixed the problem.  I have the visual effects enabled now, too.

However, I have a new problem.  Google Earth loads and then crashes like crazy.  Is the Intel 82852/855GM not strong enough to run it?

---

### Post by MeURi on 2008-12-18
I actually don't know, but I don't think so...

If you have Windows, you can try Google Earth under Windows and see how it works, IF it works :-P

Anyway, I found some complaints about GE under Linux and integrated Intel cards (see [here](http://bbs.keyhole.com/ubb/showflat.php/Cat/0/Number/456558/page/0/fpart/1/vc/1) for example).

Maybe there's something related in these forums, search for that.

I personally use GE very rarely, and on Windows (but I have an nVIDIA card).

---


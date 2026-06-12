---
title: "X Server fail, no GUI after installing NVidia Driver in 9.04"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by andy_blah on 2009-04-27
I have installed the NVidia video card driver, after that restarted , it booted, after that, I don't see the gui, I type in the username and password and I try to start the X Server (by the startx command and got this:

```
exec: 5: /use/bin/X11/X not found
xinit: Server error
```

Any way to fix this annoying issue?

---

### Post by abhiroopb on 2009-04-27
can you try 
```

sudo nvidia-xconfig

```
and restart

---

### Post by andy_blah on 2009-04-27
Typed that command, but only got a new blank command line, nothing else, after restarting, I still have the same problem, unfortunately :(

---

### Post by abhiroopb on 2009-04-27
ok try:

sudo rm /etc/X11/xorg.conf

This will force it to use a backup which should work. Then try re-installing the nvidia graphics card.

---

### Post by andy_blah on 2009-04-27
Tried that, now this shows up (when again, I have to use the startx command becuse the GUI doesn't show up...):

```
xauth: error in locking authority file /home/andyblah/.Xauthority
xauth: error in locking authority file /home/andyblah/.Xauthority
xauth: error in locking authority file /home/andyblah/.Xauthority
xauth: error in locking authority file /home/andyblah/.Xauthority
exec: 5: /use/bin/X11/X not found
xinit: Server error

xauth: error in locking authority file /home/andyblah/.Xauthority
```

---

### Post by abhiroopb on 2009-04-27
restart the computer and try the command
if that fails, then try...

sudo rm /home/andyblah/.Xauthority and then try the command

---

### Post by andy_blah on 2009-04-27
By "the command" you mean startx or 
rm /etc/X11/xorg.conf ?

If the anwser is startx, then I've tried, and it still displays the same error messages as in the first post of this thread, with 2 new messages confirming that a new authority file has been created.

---

### Post by abhiroopb on 2009-04-27
sorry.. by "command" I meant:

sudo rm /etc/X11/xorg.conf

---

### Post by andy_blah on 2009-04-27
It shows this error: "No such file or directory"

It probably means that the back-up of xorg.conf isn't used

---

### Post by abhiroopb on 2009-04-27
what happens if you do startx now?

otherwise try this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by andy_blah on 2009-04-27
startx displays the same error I have posted on the first post of this thread

When I try the command you suggested, it returns me this error: ```
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.
```

---

### Post by abhiroopb on 2009-04-27
If xserver-xorg is broken you might want to try sudo apt-get -install --reinstall xserver-xorg

---

### Post by andy_blah on 2009-04-27
I triple checked how I typed in the command, and tired multiple times, but I only get this command line error:

```
E: Command line 'i' [from -install] is not known.
```

---

### Post by abhiroopb on 2009-04-27
my bad....

sudo apt-get install --reinstall xserver-xorg

---

### Post by ibuclaw on 2009-04-27
Erm.... :|


```
file /usr/bin/X11/X
```
Does that file exist? From the error you are getting, this tells me that it isn't there ...

The fix would be:
```
sudo apt-get install --reinstall x11-common xserver-xorg
```

Also, @abhiroopb and your rm command ... that is not a very smart thing to do.

Also, in Ubuntu, to reconfigure xserver-xorg, you must supply the -phigh option, else it just does nothing.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Regards
Iain

---

### Post by abhiroopb on 2009-04-27
> **tinivole said:**
> Erm.... :|


```
file /usr/bin/X11
```
Does that file exist? From the error you are getting, this tells me that it isn't ...

The fix would be:
```
cd /usr/bin
sudo ln -s . X11
```

Also, @abhiroopb and your rm command ... that is not a very smart thing to do.

Also, in Ubuntu, to reconfigure xserver-xorg, you must supply the -phigh option, else it just does nothing.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Regards
Iain


Really? I didn't really know better. I've done the rm command since Dapper whenever I'd do something to mess up the xorg, seemed like the quickest way to reset the xorg file (after which you could run the reconfigure command).

---

### Post by ibuclaw on 2009-04-27
> **abhiroopb said:**
> Really? I didn't really know better. I've done the rm command since Dapper whenever I'd do something to mess up the xorg, seemed like the quickest way to reset the xorg file (after which you could run the reconfigure command).
```
dpkg-reconfigure -phigh xserver-xorg
```
Makes a backup of the current config and restores the failsafe default configuration. Of course, you can do what you want on your system, just that, IMO, that way is safe, and non-destructive.

---

### Post by abhiroopb on 2009-04-27
> **tinivole said:**
> ```
dpkg-reconfigure -phigh xserver-xorg
```
Makes a backup of the current config and restores the failsafe default configuration. Of course, you can do what you want on your system, just that, IMO, that way is safe, and non-destructive.

Fair enough.

---

### Post by andy_blah on 2009-04-28
Thank you both for the answers, tried to reinstall xserver-xorg (by tinivole's command) and managed to finish with it, after that I restarted, and yet again the GUI isn't showing up...

I typed in again sudo startx, but I've got those errors:

```
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
no screens found
giving up

xinit: No such file or directory (errno2): unable to connect to X Server
xinit: No such process(errno3): server error
xauth: error in locking authority file /home/andyblah/.Xauthority
```

---

### Post by durand on 2009-04-28
Then try running:
```
sudo nvidia-xconfig
```

---

### Post by andy_blah on 2009-04-28
Did that and it gave me a new blank command line, afer that I ran the startx command and gues what? Some more errors ^_^;

```
WARNING: All config files need .conf: /etc/modprobe.d/dkms it will be ignored in a future release

FATAL: Module nvidia not found
(EE)NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA(0): ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

xinit: No such file or directory (errno2): unable to connect to X Server
xinit: No such process(errno3): server error
xauth: error in locking authority file /home/andyblah/.Xauthority
```

---

### Post by durand on 2009-04-28
Reboot, go into recovery mode and load a failsafe xorg. Then go to Hardware Drivers and reinstall nvidia. If it's installed, remove it and try again. It looks like they have been removed or not installed correctly in the first place.

---

### Post by andy_blah on 2009-04-28
I don't know exactly how to load a failsafe xorg. While I was in the Recovery menu, I tried the xfix option, and got into normal mode - nothing fixed

---

### Post by Kareeser on 2009-04-28
Sounds like your drivers weren't properly installed in the first place...

Go to nvidia.com and download the proper drivers for your card. It should come in a .sh file.

The easiest way, if you have a hardwire connection is to type "wget", and the URL after it.

```

cd /tmp
wget http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run
sudo sh NVIDIA-Linux-x86-180.51-pkg1.run

```

This, of course, is assuming you have a card supported by the driver.

---

### Post by andy_blah on 2009-04-28
My card is NVidia 5500FX. I have installed the driver by enabling those desktop effects (I always install the video card driver by that), and didn't check if it went well. Please confirm if the driver supports my card, at the moment I have a slow PC from which I check those forums, and I can barely do this v.v;

---

### Post by fornix on 2009-04-28
> **andy_blah said:**
> I have installed the NVidia video card driver, after that restarted , it booted, after that, I don't see the gui, I type in the username and password and I try to start the X Server (by the startx command and got this:

```
exec: 5: /use/bin/X11/X not found
xinit: Server error
```

Any way to fix this annoying issue?

Just noticed that the path was /use ??
does such a directory exist by default? I thought it was /usr/bin

---

### Post by andy_blah on 2009-04-28
Yes, it was /usr/bin/X11/X, it seems that I have mistyped that (I have to write down the lines, and then type them here.

---

### Post by durand on 2009-04-28
Try what Kareeser said, it should hopefully work though I'm not sure how futureproof it is. It's a quick fix though.

---

### Post by andy_blah on 2009-04-28
Okay, since nobody confirmed me if the driver works for my card, I have gone to NVidia's  site and tried to figure out what driver matches my card, so I know that it is 173.14.18, x86 version, but my only problem is that I can't get wget to work, it says that it fails to resolve with the NVidia's site. I have checked and everything is in place at connection-wise, and instead of trying to figure out what's wrong, I could transfer the driver from another computer with a and drive, the only problem is that it is formatted as FAT32, and I don't know how to use the mount command to mount a FAT32 partition. Can somebody help?

---

### Post by durand on 2009-04-28
Hang on, I'll get you a link to the driver. BTW, you can use www-browser in the terminal to get a text mode browser. Kinda ugly but it's very handy sometimes.

---

### Post by durand on 2009-04-28
Here you go:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.18/NVIDIA-Linux-x86-173.14.18-pkg1.run
```

---

### Post by andy_blah on 2009-04-28
Nothing seems to work, cannot connect to anything from the command prompt, and I did check and typed in correctly the link. ^_^

What I need now is the correct command for mounting a FAT32 partition (/dev/sdc/) so I could copy the driver from my USB pendrive to the /tmp folder.

---

### Post by durand on 2009-04-28
It's:
```
sudo mount /dev/sd{some_letter}{some_number} folder_to_mount_to
```
The letter is usually b unless you have more than one harddrive in which case it becomes c, etc. The number starts at 0, it probably is 0 but it depends on how many partitions your usb stick has. If you run:
```
dmesg | tail
``` you might get some clue as to what it is but you can just try anything and if it doesn't work, then it will tell you. Remember to create the folder_to_mount_to.
```
mkdir folder_to_mount_to
```

---

### Post by andy_blah on 2009-04-28
Managed to fix the problem finally! I thought that I have to specify the file system too in the command, that's why I couldn't mount the pen drive's partition ^_^; Thank you for giving me those commands, and thank you everybody for helping me fix this issue.

Now, for a strange reason, the CPU load stays at 79 - 100% with only Firefox running. This didn't happen before this problem appeared, what should I do to fix this?

---

### Post by durand on 2009-04-28
Go to System > Administration > System Monitor and check what program is using the CPU.

---

### Post by andy_blah on 2009-04-28
Did that before, but I forgot to mention. Gnome System Monitor uses 30% and Firefox 5%. I can see that the CPU is at 100% with the System Monitor panel item, so I don't think that the Gnome System Monitor is the cause here :?.

---

### Post by durand on 2009-04-28
Well, gnome system monitor isn't the cause but it tells us what the high load program is. You can also try running "top" in a terminal. The program at the top is your culprit.

---

### Post by andy_blah on 2009-04-28
```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND     
 2886 root      20   0 72876  19m 7856 R 64.0  5.1  62:04.31 Xorg   
```

It seems that Xorg is the culprit, I will try to restart to see if this issue is fixed and will edit this post with the answer

---

### Post by durand on 2009-04-28
Hmm yeah :S I've seen that happen before but it usually dissipates pretty quickly.

---

### Post by andy_blah on 2009-04-28
Seems that restarting didn't fix the problem. I don't know how much you mean by "quickly", but this computer has been running for about an hour (after I got over the xorg problem)

---

### Post by durand on 2009-04-28
Yeah, thats not quite right. You are using the nvidia driver right? And does it stop using 100% cpu if you close firefox?

---

### Post by andy_blah on 2009-04-28
I suppose that I am running it, how could I check that? And closing Firefox doesn't seem to fix it :?

---

### Post by durand on 2009-04-28
Ugh, this is getting quite messy. Try running glxgears and see if it runs at an acceptible rate. Or check the output of glxinfo. It should say direct rendering: yes. So does it start fully using the cpu as soon as you start ubuntu or do you need to do something else? Check /var/log/Xorg.log if there are any errors showing up. You can use System > Administration > System Log Viewer for this.

---

### Post by andy_blah on 2009-04-28
Thank you for your further assistance

glxgears output:
```
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/200553 the monitor refresh rate.
737 frames in 5.0 seconds = 147.397 FPS
808 frames in 5.0 seconds = 161.484 FPS
850 frames in 5.0 seconds = 168.575 FPS
825 frames in 5.0 seconds = 164.973 FPS
786 frames in 5.0 seconds = 157.194 FPS
785 frames in 5.0 seconds = 156.716 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.

```

glxinfo output:
```
name of display: :0.0
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.18
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

```

The problem appears as soon as Ubuntu is started I suppose, when I log in, the System Monitor panel item indicates immediately 100%

It seems that there is no System Log Viewer option in the Administration Menu, I suppose that there are differences between the Jaunty beta and stable. There isn't any Xorg.log in the folder, only Xorg.0.log and Xorg.failsafe.log, and couldn't find any errors (took a quick look)

---

### Post by andy_blah on 2009-04-28
Noticed that everything I do in the terminal, this error always pops up five or six times at once:

```
Xlib:  extension "Generic Event Extension" missing on display ":0.0".

```

---

### Post by durand on 2009-04-28
Yeah, it does seem to be an important error...Maybe you could do a google search or something. I have to go to sleep now but I'll help you tomorrow. Oh and it's called Log File Viewer, I was just guessing it's name.

---

### Post by andy_blah on 2009-04-28
I did a google search, but didn't found any answer yet, and will have to continue searching tommorow, since I have to go to bed too ^_^;

---

### Post by NiGHTSChao on 2009-04-28
- .-; I know you guys are still sorting this out but I have the same issue, I installed the new drivers, or activated them anyway and rebooted and my system has no GUI now, its stuck at a blank black screen with the ubuntu post/system check stuff

I dont even know how to access the command line and when I do type in the commands (from the root-recovery console) nothing seems to work

Should I just go with ubuntu 8.10???

---

### Post by iansane on 2009-04-28
I'm also getting a blank screen, after the first loading screen with the progress bar. It never makes it to the log in screen. All I can do to get a screen at all is go into recovery mode and do the last option (xfix auto fix). It just changes me back to the default driver. I've tried all the different glx drivers and the driver from nvidia web site. Actually I posted in a different post because I didn't see this one.

---

### Post by NiGHTSChao on 2009-04-28
> **iansane said:**
> I'm also getting a blank screen, after the first loading screen with the progress bar. It never makes it to the log in screen. All I can do to get a screen at all is go into recovery mode and do the last option (xfix auto fix). It just changes me back to the default driver. I've tried all the different glx drivers and the driver from nvidia web site. Actually I posted in a different post because I didn't see this one.

I can't even get THAT to ******* work..
Xfix doesn't do anything..

---

### Post by iansane on 2009-04-28
well I hope someone with some knowlege can help out. No one has answered my other post yet. Since I do have a screen at least, after xfix I guess I can get used to scrolling back and forth to see a giant web page untill I find out why none of the nvidia drivers are working. I'll deal with it as long as I can because I don't want to go back to intrepid or hardy. My netgear wireless usb is finally working natively on a 64 bit OS and I'm so happy about that. :-)

---

### Post by andy_blah on 2009-04-29
For those that are stuck only with the command line, try to follow what the others have suggested in this thread. And for those who can revert back to the generic video driver, go to [this]("http://nvidia.com/Download/index.aspx?lang=en-us") page, and select your card model and OS Type (for here, either Linux 32 or 64bit), and get to the appropriate driver's page. You should now get a .run file from there, after downloading, move the file in your /tmp folder, start the terminal, and use those commands:

```
cd /tmp
sudo sh *the name of the file*.run
```

After this, it will start the driver, and all you need to do is to confirm some actions, after that, you're done.

About my problem now, it seems that it fixed itself, the error doesn't appear anymore (at least it didn't by now) and the processor isn't stressed that much (now Xorg uses ~8% CPU, is that normal?)

EDIT: Just noticed that the NVidia control panel(or what it was called like...) has dissapeared and I can't modify the resolution and refresh rate anymore. What should I do to fix this?

---

### Post by andy_blah on 2009-04-29
I have stumbled across another error:

```
Error: API mismatch: the NVIDIA kernel module has version 173.14.16,
but this NVIDIA driver component has version 173.14.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
```

---

### Post by iansane on 2009-04-29
> **andy_blah said:**
> For those that are stuck only with the command line, try to follow what the others have suggested in this thread. And for those who can revert back to the generic video driver, go to [this]("http://nvidia.com/Download/index.aspx?lang=en-us") page, and select your card model and OS Type (for here, either Linux 32 or 64bit), and get to the appropriate driver's page. You should now get a .run file from there, after downloading, move the file in your /tmp folder, start the terminal, and use those commands:

```
cd /tmp
sudo sh *the name of the file*.run
```

After this, it will start the driver, and all you need to do is to confirm some actions, after that, you're done.

About my problem now, it seems that it fixed itself, the error doesn't appear anymore (at least it didn't by now) and the processor isn't stressed that much (now Xorg uses ~8% CPU, is that normal?)

EDIT: Just noticed that the NVidia control panel(or what it was called like...) has dissapeared and I can't modify the resolution and refresh rate anymore. What should I do to fix this?

Well I think it's a related problem I'm having but not exactly the same one. I have the correct driver from nvidia and installed it with no problem. Well, minor trouble but I've done it several times. I have to boot in recovery mode and do "telinit 3" and then when it reboots go back into terminal and still have to stop gdm. Otherwize the .run installer gives me errors about wrong run level and x still running. Either way, once it's installed and I reboot I get the black screen and have to revert back to the ubuntu driver. This is the case with all of the glx drivers from synaptic too.

Should I blacklist other video drivers so there's not a conflict? If so, how do I do that and if it doesn't work, how do I un-blacklist them?

---

### Post by modmadmike on 2009-04-29
I am having the same problem as all of you (SEEMS JAUNTY + NVIDIA = USR F**KED!) I had it so bad that I could not even CTRL+F* so thankfully I installed the server edition with ssh which worked (My entire drive is aes encrypted so no livecd usage). I got it to use the framebuffer driver but i cant stand no nvidia driver so im going to ```
apt-get remove x11-common
apt-get install ubuntu-desktop
``` then try to install the driver using jockey instead of by going to appearance prefs and then enabling desktop effects [or using the nvidia installer]. I know the nvidia driver works in 9.04, for i got it to work on my friends laptop which has an nvidia 8400m and I happen to have a 8400 desktop card... [trying to fix it lol]   

+1hour-fixed jockey, it was not fixed by reinstalling [it said there were no available drivers] so I manually reinstalled  it, still not fixed, I ran jockey-gtk --help and then executed a few of the commands and changed the mode to any which worked! Installed the nvidia driver and rebooted.


+1.5hours- got scared ****less because the encrypted drive was not mounting in grub. rebooted and it worked lol. NVIDIA DRIVER RUNS LIKE IT DID IN 8.10!!! so if you need to get it working DO NOT use the appearince prefs or the NVIDIA retail driver!

---

### Post by modmadmike on 2009-04-29
> **modmadmike said:**
> I am having the same problem as all of you (SEEMS JAUNTY + NVIDIA = USR F**KED!) I had it so bad that I could not even CTRL+F* so thankfully I installed the server edition with ssh which worked (My entire drive is aes encrypted so no livecd usage). I got it to use the framebuffer driver but i cant stand no nvidia driver so im going to ```
apt-get remove x11-common
apt-get install ubuntu-desktop
``` then try to install the driver using jockey instead of by going to appearance prefs and then enabling desktop effects [or using the nvidia installer]. I know the nvidia driver works in 9.04, for i got it to work on my friends laptop which has an nvidia 8400m and I happen to have a 8400 desktop card... [trying to fix it lol]   

+1hour-fixed jockey, it was not fixed by reinstalling [it said there were no available drivers] so I manually reinstalled  it, still not fixed, I ran jockey-gtk --help and then executed a few of the commands and changed the mode to any which worked! Installed the nvidia driver and rebooted.

+1.5hours- got scared ****less because the encrypted drive was not mounting in grub. rebooted and it worked lol. NVIDIA DRIVER RUNS LIKE IT DID IN 8.10!!! so if you need to get it working DO NOT use the appearance prefs or the NVIDIA retail driver!
d

---

### Post by modmadmike on 2009-04-29
> **modmadmike said:**
> d

opps ment to edit the first one not qoute it lol

---

### Post by iansane on 2009-04-29
Not sure I understand what you said about jockey but my jockey works and shows drivers. 3 different ones. I tried all three, one at a time, and none of them worked. Just to see, I installed 8.10 and have the same problems with it. What happened to glx-new? It worked for me when I was using 8.04 but it's not in synaptic now. Oh and I also had to use an older version of dpkg-reconfigure to be able to have video options. I almost forgot that. nvidia-xconfig never worked for me even with 8.04 So what should I do now that Ubuntu is getting rid of everything that works for my system? Is there any other way to get more than 800x600 res? That's all I am trying to get is a higher resolution. I don't use extra affects.

---

### Post by modmadmike on 2009-04-29
> **iansane said:**
> Not sure I understand what you said about jockey but my jockey works and shows drivers. 3 different ones. I tried all three, one at a time, and none of them worked. Just to see, I installed 8.10 and have the same problems with it. What happened to glx-new? It worked for me when I was using 8.04 but it's not in synaptic now. Oh and I also had to use an older version of dpkg-reconfigure to be able to have video options. I almost forgot that. nvidia-xconfig never worked for me even with 8.04 So what should I do now that Ubuntu is getting rid of everything that works for my system? Is there any other way to get more than 800x600 res? That's all I am trying to get is a higher resolution. I don't use extra affects.

what GPU are you using. If you don't use extra effects then you should use the default aka: xserver-xorg-video-nv, it cant handle 3D but it can handle video

---

### Post by iansane on 2009-04-30
OK I see the nv is installed but how do I tell the system to use it? And will it give me higher resolutions than 800x600? I remember my system used it by default when I was running hardy and older and when I could change video settings with dpkg-reconfigure xserver-xorg it would always be on nv before I changed it to nvidia. Where can I edit the xorg.conf file to make it work? If it helps, this is all that is in the current default xorg.conf.

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


```

I remember before it would say "nvidia" and "FPD1960" for my LCD and other such things when it was configured with dpkg-reconfigure. 

Thanks

---

### Post by apjone on 2009-04-30
Hey just a quick FYI that envy is my trusted way to do Nvidia/ATI drivers

envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - dummy package to envyng-core
envyng-qt - install the ATI or the NVIDIA driver

apt-get install and run it envyng -t and that may help

---

### Post by iansane on 2009-04-30
Thanks apjone but tried it that way too. It installs the same drivers that jockey does. Tried them all with Jockey, envy, from nvidia site, and manually through synaptic. I just tried the glx-180 manually again and installed everything with 180 in the title. I'm about to restart gdm and see what happens but here's the new xorg.conf file after running nvidia-xconfig.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Wed Nov 26 11:21:13 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Now I have a better idea of what gets edited in the file.

Hope it works this time

---

### Post by iansane on 2009-04-30
No luck for me. I got the black screen again. Had to go into recovery and let xfix reset me to the default driver again.

I'll leave it alone for a while. If anyone knows how to resolve my problem, thanks.

---

### Post by iansane on 2009-04-30
OK I thought I'd leave it alone but I just installed virtual box to get my vm's up again and the video is all messed up. My windows vm only has 4 for color and the resolution is low too. I'm assuming this has to do with low graphics on the host.

Can anyone tell me how to configure xserver to use the nv driver since nvidia isn't working?

---

### Post by iansane on 2009-05-01
Yay it's working!! Very strange. . . 

As I was installing Intrepid for the hundreth time because I keep trying random stuff to make nvidia work and messing the system up, I was doing updates and what do ya know? A 2 nvidia updates were there even before I tried installing nvidia on the clean system. I also installed every package I could think of in synaptic that I've installed for other things that has to do with building, kernels, source code, headers. You know, all the stuff that eventually gets installed because it's required for some package to build or install. Well then I went into Jockey and activated the 180 driver, rebooted and it works. My vm graphics are good now too. 

I wish I knew what was causing the problem. It will take a while and a lot of reinstalls to narrow it down to exactly what it was.

Now I'm afraid to upgrade to Jaunty for fear of loosing it again but I'll probably do that next weekend.

Thanks for all the responses to the OP and to my problem even though they didn't work for me.

---

### Post by andy_blah on 2009-05-02
> **andy_blah said:**
> I have stumbled across another error:

```
Error: API mismatch: the NVIDIA kernel module has version 173.14.16,
but this NVIDIA driver component has version 173.14.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
```

Can somebody help me with this? Seems that direct rendering doesn't work T.T

---

### Post by modmadmike on 2009-05-06
> **andy_blah said:**
> Can somebody help me with this? Seems that direct rendering doesn't work T.T
Two fixes:

1. install the nvidia driver version 173.14.16 instead
2. run the nvidia uninstaller (look for it in the /bin or /usr/bin dir with the ls command) and then re-install. :popcorn:

---

### Post by andy_blah on 2009-05-06
Thank you, will try those and will report back afterwards ^_^

---

### Post by modmadmike on 2009-06-10
For any who still has this problem run:
```
Kern=$(uname -r)
sudo apt-get install build-essential linux-headers-$Kern
```
and then reinstall the nvidia drivers with jockey. :D

---

### Post by iansane on 2009-06-10
Had the exact same problem using an ATI card too. Only no compatible drivers in jockey. Got the driver from ATI and installed it and same black screen. What is it with Ubuntu and video drivers? Or is it Nvidia and ATI not releasing what ever the Ubuntu developers need to develope drivers?

I'm wondering if that line in terminal will also fix the ATI problem.

BTW only using ATI because my last computer got fried and my new one actually lets me disable the onboard nvidia and I had a ATI card laying around. But same issue as before if I try using the onboard nvidia in the new machine.

---

### Post by iansane on 2009-06-10
modmadmike,

I just got home and realised you just said install build-essentials and the headers for my kernel. Don't understand to complication of running it in terminal like that but oh well. Guess it makes sure people install the right header file version. 

That didn't work for me on my old machine and doesn't work on my new one. For Nvidia and ATI the drivers just don't work.

At least I'm getting good res and faster video processing from the ATI and Ubuntu's default driver than I did with Nvidia and vesa driver.

---

### Post by YfoMp5QBh2 on 2010-09-01
> **abhiroopb said:**
> what happens if you do startx now?
 
otherwise try this:
 
sudo dpkg-reconfigure xserver-xorg
 
 
Hi All,
 
I'm having this exact same problem, I used "sudo rm /etc/X11/xorg.conf" and I tried "startx" straight after and now it just gives me a blank screen, my monitor says "no input".
 
Can anyone help?

---

### Post by babygenius55 on 2011-07-12
Why are sooo many people having this problem?  including myself.  i'm going back to 10.04  When the errors made sense.

---

### Post by Fitch on 2011-10-16
Did all of that and still no GUI.
So, I hit the escape key and went into GRUB.
I pressed enter on the 2nd line from the top (the one that says "Recovery Mode) and edited the video settings by going down to "FailsafeX" (Failsafe gRaphics mode)
then "Run Ubunto in Low Graphics Mode" which goes to VESA, and install another NVidia driver from the normal "Hardware" "Additional Drivers" icon

---


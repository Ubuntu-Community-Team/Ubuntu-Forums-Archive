---
title: "can't open login shell"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-17
It's been a day's worth of headaches trying to install 10.04 on a brand new HP Pavillion dv6. I seem to have it going now, but it's still acting very funny ...

When I hit ctrl+alt+f2, instead of opening up a login shell, the graphics wig out and the computer locks up, so I'm forced to restart it. Actually, it happens when I hit ctrl+alt+fn+f2 because the function keys are set to mulimedia controls by default, but either way, I can't open any other tty's.

On what seems to be a related note, I tried to edit my /etc/default/grub file so the computer would boot into a bash shell instead of into GUI. Works fine on my Dell laptop but on the HP, again, the computer freezes up before I get a login prompt.

Help, please!

Edit: I should add that the same things happened when I tried installing Mint 9 as well.

---

### Post by ubudog on 2010-08-17
What kind of graphics card do you have?  Find out using:
```
glxinfo
```

You need mesa-utils installed in order to run glxinfo.  Install it using:
```
sudo apt-get install mesa-utils
```

---

### Post by Chris1274 on 2010-08-17
Here's what glxinfo yields:
```
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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4 x86/MMX/SSE2
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

```

---

### Post by sandyd on 2010-08-17
> **Chris1274 said:**
> It's been a day's worth of headaches trying to install 10.04 on a brand new HP Pavillion dv6. I seem to have it going now, but it's still acting very funny ...

When I hit ctrl+alt+f2, instead of opening up a login shell, the graphics wig out and the computer locks up, so I'm forced to restart it. Actually, it happens when I hit ctrl+alt+fn+f2 because the function keys are set to mulimedia controls by default, but either way, I can't open any other tty's.

On what seems to be a related note, I tried to edit my /etc/default/grub file so the computer would boot into a bash shell instead of into GUI. Works fine on my Dell laptop but on the HP, again, the computer freezes up before I get a login prompt.

Help, please!

Edit: I should add that the same things happened when I tried installing Mint 9 as well.
what about opening a terminal via Applications -> Accessories -> Terminal?

and post the output of
```

cat ~/.bashrc
cat ~/.bash_profile
```

---

### Post by Chris1274 on 2010-08-17
The GUI terminal opens fine, it's the tty's that I can't access. Here's the output:

```
cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

There's no ~/.bash_profile.

---

### Post by ubudog on 2010-08-17
> **Chris1274 said:**
> Here's what glxinfo yields:
```
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
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4 x86/MMX/SSE2
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

```
Thanks, let me look at it.

---

### Post by sandyd on 2010-08-17
```

nano ~/.bash_profile

```
enter this in for the contents
```

# /etc/skel/.bash_profile

# This file is sourced by bash for login shells.  The following line
# runs your .bashrc and is recommended by the bash info pages.
[[ -f ~/.bashrc ]] && . ~/.bashrc

```

---

### Post by Chris1274 on 2010-08-17
Alas, that didn't solve the problem. It still seizes up when I hit ctrl+alt+f2. The graphics get all splotchy on the left side of the screen and the GUI freezes, forcing me to restart.

---

### Post by ubudog on 2010-08-17
Could be your graphics card, Intel cards aren't friendly with Linux.  What driver are you using?

---

### Post by Chris1274 on 2010-08-17
I'm not sure which one I am using, but I'm *not* using the ATI/AMD FGLRX driver, even though the driver manager says I should. After my first few attempted installs I finally realized that that one crashed everything, so I'm sticking with whatever the default driver is.

I guess it's no big deal, I have complete functionality in the GUI. I just hate it when things that should work don't :mad:

---

### Post by ercferret18 on 2010-08-17
try booting with the "nomodeset" kernel option.

---

### Post by Chris1274 on 2010-08-18
How do I do that? Should I edit the /etc/default/grub file?

---

### Post by Chris1274 on 2010-08-18
Nope, that caused some real ugliness, total seizure at startup. I had to boot into recovery mode to re-edit the grub file.

---

### Post by ercferret18 on 2010-08-18
have you tried booting with the "text" kernel option? this should bypass gdm and give you a console prompt.

---

### Post by Chris1274 on 2010-08-18
I have, that derails things too. You would think that booting straight into text mode would avoid any graphics issues, but nope, it won't let me. It's frustrating too because that's my preferred startup method.

---

### Post by ercferret18 on 2010-08-18
hmm... do you get any message before your system crashes? make sure that you don't have the "splash" option so that you can see the messages.

---

### Post by Chris1274 on 2010-08-18
On my previous attempt, I had this setup in the grub file:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"
```

Should I try this instead?
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="nomodeset"
```

When I tried the text option earlier on (which failed) I hadn't added nomodeset.

---

### Post by ercferret18 on 2010-08-18
yeah... try both text and nomodeset and see how it goes

---

### Post by Chris1274 on 2010-08-18
Well, that got me into text mode at the startup, and I was able to switch across tty's, but when I entered "startx" to get the GUI going we crapped out. Some blotchy pixels and then a blank frozen screen. I guess there's something seriously funky going on with my graphics card.

---

### Post by Chris1274 on 2010-08-18
Just wondering if the problem might be that I'm running the 32-bit version of Lucid on a 64-bit processor with integrated graphics???

---

### Post by Chris1274 on 2010-08-21
Success! Installing the 2.6.34 kernel seems to have solved the problem. I can switch back and forth between X and tty without any issues.

---

### Post by ubudog on 2010-08-21
> **Chris1274 said:**
> Success! Installing the 2.6.34 kernel seems to have solved the problem. I can switch back and forth between X and tty without any issues.

Nice!  Always good to have the latest updates, lol.

---

### Post by militition on 2010-10-19
> ** said:**
> 
[COLOR="Black"]_**re: **[[COLOR="Black"]**internet marketing arizona[/COLOR]**](http://www.*********************/)_[/COLOR]You know the last time I bought a house I lost over 100K just like everyone else in the nation, I doubt Ill do it again.

---

### Post by ubudog on 2010-10-19
Ummm?  WTF?  Why are you advertising on this forum?

---


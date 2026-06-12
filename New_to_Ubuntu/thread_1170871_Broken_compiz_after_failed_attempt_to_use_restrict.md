---
title: "Broken compiz after failed attempt to use restricted ATI driver"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by po-ko on 2009-05-26
Hi guys, 

Hopefully I'll be able to provide enough background info on my problem. Let me know if there's any other info I can provide.

I'm running Jaunty on a 64 bit Lenovo w500.

So, last week I had everything up an running perfectly - compiz effects worked out of the box, great. Then, I stumbled upon the restricted drivers dialog, and though: "hey, this should make everything run better, great!" and enable I go (ATI/AMD proprietary FGLRX graphics driver). Didn't reboot, figured I'd get to it eventually. Anyway, come this week, start up my machine for the new work week, and BAM! black screen upon startup (actually, first it was a weird frozen tv-snow screen). 

So after an hour of rooting around on the internets, I realized that I'd updated that driver, and uninstalled it. (sudo apt-get remove xorg-driver-fglrx and dpkg-reconfigure -phigh xserver-xorg) Wee! Problem fixed, I can see my screen!

But wait! Now I get a popup from avant saying that compiz isn't working. So I go to the Appearance prefs dialog and attempt to enable, and get the following sad popup:
Desktop effects could not be enabled. 

So now I'm trying to fix this. Except, since I'm kind of a noob, I can't figure out which driver my machine is actually using, and what graphics card I actually have in this thing.

Here are some relevant outputs:

poko@polinux:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

(which is the actual card??)

poko@polinux:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


poko@polinux:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20


and my xorg.conf looks like this:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection


Unfortunately, I couldn't revert to a backup of the conf, since I'd installed that crappy fglrx driver, and the backup had that referenced. 

Any ideas for a solution to this? I really like Avant Window Navigator, and would like to have it back. I know it's possible .. somehow :)

Thanks ahead of time!! And let me know if there's any other info I can provide.

---

### Post by Michael Dooley on 2009-05-26
[[COLOR="Red"]This thread[/COLOR]]("http://swiss.ubuntuforums.org/showthread.php?t=764633") may be just the ticket for you.

---

### Post by po-ko on 2009-05-27
Hey Micheal, thanks, that did help. Compiz and my beloved Avant are back :D

For those that don't want to click the link, I ran 

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

and already had the compizconfig-settings-manager package installed. Selecting "Extra" effects in the Appearance prefs no longer gave me the sad "Destop effects could not be enabled" dialog.

Thanks again :)

---


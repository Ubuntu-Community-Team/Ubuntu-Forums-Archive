---
title: "how do i check my graphic driver"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by gackt on 2009-02-17
So i read that fglrx is much better than mesa, now how do i know which one i'm using? Thanks

---

### Post by sandyd on 2009-02-17
```

sudo gedit /etc/X11/xorg.conf

```

look around for mesa.
if it isn't there, put this under "configured video device"

```

Driver "fgrlx"

```

---

### Post by fooman on 2009-02-17
try this in a terminal:

```
glxinfo
```

does that help?

---

### Post by gackt on 2009-02-18
this is my xorg.conf:


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

there is no mesa or fglrx. Well currently i'm running warcraft3 (dota) quite smooth.

this is the result from glxinfo:
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

is this mean that i'm using glx already?? thanks gus

---


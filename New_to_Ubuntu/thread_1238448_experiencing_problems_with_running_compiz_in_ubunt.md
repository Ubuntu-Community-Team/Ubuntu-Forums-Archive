---
title: "experiencing problems with running compiz in ubuntu 9.04"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by hisunnyvashistha on 2009-08-12
This is what is displayed on Terminal.......

sunny@sunny-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


kindly help me out ....thanking you in advance.....

---

### Post by rajeev1204 on 2009-08-12
Whats the output of glxinfo | grep render ?

---

### Post by Kaymeerah on 2009-08-12
do u have a graphics card driver installed?

---

### Post by hisunnyvashistha on 2009-08-14
sunny@sunny-laptop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---

### Post by hisunnyvashistha on 2009-08-14
yes i have graphics card driver installed....


sunny@sunny-laptop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---

### Post by hisunnyvashistha on 2009-08-14
> **Kaymeerah said:**
> do u have a graphics card driver installed?

[IMG]http:///home/sunny/Desktop/Screenshot-1.png[/IMG]

yes i have graphics card driver installed ....
NVIDIA accelerated graphics driver (version 180)

---

### Post by hisunnyvashistha on 2009-08-14
> **rajeev1204 said:**
> Whats the output of glxinfo | grep render ?

   this is the output of it...


sunny@sunny-laptop:~$ glxinfo | grep render direct rendering: Yes OpenGL renderer string: GeForce Go 7400/PCI/SSE2     GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---


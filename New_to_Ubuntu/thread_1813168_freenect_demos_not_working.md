---
title: "freenect demos not working"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by fargalaxy1 on 2011-07-27
[FONT=Courier New]Dear all,

I'm trying to make kinect work on Ubuntu 10.04. I followed carefully the instructions found at [/FONT] [FONT=Courier New][[COLOR=Blue]this page[/COLOR]]("http://openkinect.org/wiki/Getting_Started#Ubuntu") and i guess i successfully installed *freenec*t. 
The problem rises when i start the demo applications:[/FONT]

------ **glview demo** --------

```
 freenect-glview 
```[FONT=Courier New]I get a white window, and, as far as i read on the web, it is a quite common problem.[/FONT]

------ ** glpclview** **demo** --------

```
freenect-glpclview
```[FONT=Courier New]the freenect window closes immediately and i get:[/FONT]
```
 [Stream 70] Expected 1748 data bytes, but got 1908. Dropping...
*********************************WARN_ONCE*********************************
File r300_draw.c function r300TryDrawPrims line 671
Rendering was 27 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

```----- **cppview demo** -------

```
freenect-cppview
```[FONT=Courier New]white window again... the terminal outputs[/FONT]
```

RGB callback
RGB callback
RGB callback
RGB callback
GL thread
RGB callback
Depth callback
......... etc

```[FONT=Courier New]I do have installed *freeglut3* and libusb-1.0-0-dev.
I have an  ATI Radeon X300 which does not support non-power-of-two textures.

What do you think?[/FONT][FONT=Courier New]

Thank you so much for the help,[/FONT] [FONT=Courier New]

Martina[/FONT]

---


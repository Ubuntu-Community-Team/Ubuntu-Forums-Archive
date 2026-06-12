---
title: "OpenGL 2.0?"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by someoney3000 on 2010-12-07
I am interested in setting up an emulator for opengl 2.0 (I'm assuming my built-in video card does not support opengl 2.0) so I may code and compile some shader programs.  Is that possible?

Thank you for any help you may provide.

---

### Post by khelben1979 on 2010-12-07
Try typing **lspci** from a terminal. Then we know what graphics you got in there and if it supports [OpenGL]("http://en.wikipedia.org/wiki/Opengl") 2.0 or not. OpenGL 4.1 is the latest version.

---

### Post by someoney3000 on 2010-12-07
> **khelben1979 said:**
> Try typing **lspci** from a terminal. Then we know what graphics you got in there and if it supports [OpenGL]("http://en.wikipedia.org/wiki/Opengl") 2.0 or not. OpenGL 4.1 is the latest version.

Thank you for your quick response.  I didn't realize that OpenGL has gone all the way up to 4.1.

The line that you requested is:

Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by khelben1979 on 2010-12-07
Looks like you have Integrated GMA 950 graphics. Checked [here]("http://en.wikipedia.org/wiki/945_chipsets"). And if that is correct, you have support for max [OpenGL 1.4]("http://en.wikipedia.org/wiki/OpenGL#OpenGL_1.4") according to the PDF document which I attached.

---

### Post by someoney3000 on 2010-12-08
> **khelben1979 said:**
> Looks like you have Integrated GMA 950 graphics. Checked [here]("http://en.wikipedia.org/wiki/945_chipsets"). And if that is correct, you have support for max [OpenGL 1.4]("http://en.wikipedia.org/wiki/OpenGL#OpenGL_1.4") according to the PDF document which I attached.

I sort of assumed that was the case.  Is there no way to emulate higher versions of OpenGL?  Mesa started as a software emulation didn't it?

---

### Post by khelben1979 on 2010-12-08
> History: Initially, Mesa 3D started off by rendering all 3D computer graphics on the CPU, but the architecture of Mesa 3D was open to implement graphics processor-accelerated 3D rendering in Mesa 3D. Once 3D graphics cards became mainstream on PC hardware, companies began working on adding support for hardware-accelerated 3D rendering to Mesa 3D. The library was one of the first drivers to support hardware-acceleration via the 3dfx Glide API driver for the very popular Voodoo I/II graphics cards and others as well. All rendering was done indirectly in the X server, leaving some overhead and speed lagging behind the theoretical maximum. The Direct Rendering Infrastructure (DRI) finally succeeded in providing an interface for direct 3D rendering by the OpenGL applications and was officially added to Mesa 3D. - [wikipedia]("http://en.wikipedia.org/wiki/Mesa_3D_%28OpenGL%29")

I don't think so. From what I can see, the MESA 3D was created to give the open source graphic drivers 3D support. Latest stable version is 7.8.2.

---

### Post by mcduck on 2010-12-08
> **khelben1979 said:**
> - [wikipedia]("http://en.wikipedia.org/wiki/Mesa_3D_%28OpenGL%29")

I don't think so. From what I can see, the MESA 3D was created to give the open source graphic drivers 3D support. Latest stable version is 7.8.2.

Actually, from the very same article:

> Whilst Mesa 3D supports several hardware graphics accelerators, it may also be compiled as a software-only renderer. Since it is also free/open source software, it is possible to use it to study the internal workings of an OpenGL-compatible renderer.

It's going to be seriously slow, though. :D

---

### Post by khelben1979 on 2010-12-08
> **mcduck said:**
> It's going to be seriously slow, though. :D

Very slow, yes. :)

---

### Post by someoney3000 on 2010-12-08
> **mcduck said:**
> Actually, from the very same article:



It's going to be seriously slow, though. :D

Urk.  Alright thanks.  I'll stick to my desktop then.

---


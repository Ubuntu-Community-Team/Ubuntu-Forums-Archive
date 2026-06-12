---
title: "GLX missing on display error"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by dagarshali on 2009-10-15
Hi,
I upgraded to the 9.10 yesterday and initially had problems with it restarting..Then I found that it doesn't have nvidia driver and I renamed the xorg.conf to xorg.conf.old and it rebooted fine..

I then installed envy and downloaded nvidia driver.

When i run an application called paraview..I now get this error..

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: In /home/dagarshali/OpenFOAM/ThirdParty-1.6.x/paraview-3.6.1/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, line 405
vtkXOpenGLRenderWindow (0x9be0a58): Could not find a decent visual



Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: In /home/dagarshali/OpenFOAM/ThirdParty-1.6.x/paraview-3.6.1/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, line 405
vtkXOpenGLRenderWindow (0x9be0a58): Could not find a decent visual



Xlib:  extension "GLX" missing on display ":0.0".
ERROR: In /home/dagarshali/OpenFOAM/ThirdParty-1.6.x/paraview-3.6.1/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, line 612
vtkXOpenGLRenderWindow (0x9be0a58): GLX not found.  Aborting.


Aborted (core dumped)

Any help to rectify this problem..

Best regards,
vishwa

---


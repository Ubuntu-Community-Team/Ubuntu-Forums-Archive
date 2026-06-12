---
title: "Nvida driver will not load correctly"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by duck4128 on 2011-08-10
I have downloaded the proprietary driver 280.13 from NVIDIA for my Quadro 4000 graphics card, however after I run the installer I get the following error

"Aug  9 17:14:33 amax kernel: [   21.000297] NVRM: API mismatch: the client has the version 280.13, but
Aug  9 17:14:33 amax kernel: [   21.000298] NVRM: this kernel module has the version 270.41.06.  Please
Aug  9 17:14:33 amax kernel: [   21.000299] NVRM: make sure that this kernel module and all NVIDIA driver
Aug  9 17:14:33 amax kernel: [   21.000300] NVRM: components have the same version.
"
The gui will not start and I can only access the command line in fail safe.  
Is there something that I need to update manually outside of the installer that I am unaware of? I am running the installer manually from the command line. any help would be greatly appreciated. Thanks!

---

### Post by Daveth on 2011-08-10
Welcome to the Ubuntu Forums. 
Which version of Ubuntu are you using there? Are the drivers in the software centre not good enough/ fast enough?

---

### Post by papibe on 2011-08-10
How did you installed the Nvidia driver?
Did you reboot after the install?
Have you upgrade your system recently and receive a new kernel update?


Regards.

---

### Post by duck4128 on 2011-08-10
thanks for the quick reply, I am using ubuntu 11.04. The repositories have the driver 270.41.06 which I am currently using. It works great locally, however, I really want to be able to generate 3D graphics remotely with NX nomachine. When I try to do that with Comsol I get the following error:

Xlib:  extension "NV-GLX" missing on display ":2000.0".
Xlib:  extension "NV-GLX" missing on display ":2000.0".
FL3D: error at line 423 in file fl3dglcontext_x11common.c:
   Failed to find GLXFBConfigSGIX.
FL3D: error at line 423 in file fl3dglcontext_x11common.c:
   Failed to find GLXFBConfigSGIX.
FL3D: error at line 423 in file fl3dglcontext_x11common.c:
   Failed to find GLXFBConfigSGIX.

I am under the impression this is an error associated with this driver. which is why I am trying to find a way to run NVIDIA's recommended driver.  If this error is being caused by something else I will gladly be redirected. Thanks!

---

### Post by Daveth on 2011-08-11
I'm uncertain if this is not entirely a red herring but this post sort of replicates your error chain, and suggests opengl versions are critical to COMSOL versions. Might be rubbish, but worth checking out
[HTML]http://www.comsol.com/community/forums/general/thread/4154/[/HTML]

---

### Post by realzippy on 2011-08-11
*If* you want 280.13,simply add xswat ppa to your sources:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
and reinstall nvidia-current.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
sudo apt-get update
```

---

### Post by duck4128 on 2011-08-11
I now have 280.13 installed correctly, however this error persists when I try to run the graphics remotely:

Xlib:  extension "NV-GLX" missing on display ":2000.0".
Xlib:  extension "NV-GLX" missing on display ":2000.0".
FL3D: error at line 423 in file fl3dglcontext_x11common.c:
   Failed to find GLXFBConfigSGIX."

Daveth thank you SO much for pointing me to that Comsol post I believe I am having the same issue.  It seems like an OpenGL issue conflicting with nx nomachine.  I will also start pursuing this with COMSOL and NVIDIA forums. I will update if I find a workable solution. If anyone has anything else to add, PLEASE DO.

THANKS!

---

### Post by duck4128 on 2011-08-12
Just to update and conclude the error:
"
Xlib:  extension "NV-GLX" missing on display ":2000.0".
 Xlib:  extension "NV-GLX" missing on display ":2000.0".
 FL3D: error at line 423 in file fl3dglcontext_x11common.c:
    Failed to find GLXFBConfigSGIX."

is due to the fact that  that NX nomachine does not support versions of OpenGL >=1.5 necessary for programs like Comsol.
 The original error in installing the driver:
"[SIZE=1]Aug  9 17:14:33 amax kernel: [   21.000297] NVRM: API mismatch: the client has the 
                                                                          version 280.13, but
Aug  9 17:14:33 amax kernel: [   21.000298] NVRM: this kernel module has the 
                                                                         version 270.41.06.  Please
Aug  9 17:14:33 amax kernel: [   21.000299] NVRM: make sure that this kernel module
                                                                        and all NVIDIA driver
Aug  9 17:14:33 amax kernel: [   21.000300] NVRM: components have the same version.[/SIZE]"
 

was due to not correctly removing the previous drivers these commands resolved this issue:

[FONT=Times New Roman,serif][FONT=Calibri,sans-serif][COLOR=black][FONT=Georgia](1) remove the current nvidia packages you might have installed[/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black][FONT=Courier New]sudo[/FONT][/COLOR][COLOR=black][FONT=Courier New] apt[/FONT][/COLOR][COLOR=#666600][FONT=Courier New]-[/FONT][/COLOR][COLOR=#000088][FONT=Courier New]get[/FONT][/COLOR][COLOR=black][FONT=Courier New]  remove nvidia[/FONT][/COLOR][COLOR=#666600][FONT=Courier New]-[/FONT][/COLOR][COLOR=black][FONT=Courier New]common nvidia[/FONT][/COLOR][COLOR=#666600][FONT=Courier New]-[/FONT][/COLOR][COLOR=black][FONT=Courier New]current[/FONT][/COLOR]
 
 [COLOR=black][/COLOR] 
 [COLOR=black][FONT=Georgia](2) go to the text window via ctrl+alt+F2. [/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
 [COLOR=black][FONT=Georgia](3) stop X[/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black][FONT=Courier New]sudo[/FONT][/COLOR][COLOR=black][FONT=Courier New] service gdm stop[/FONT][/COLOR]
 
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
 [COLOR=black][FONT=Georgia](4) remove the nouveau module[/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black]sudo[/COLOR][COLOR=black] apt-get --purge remove xserver-xorg-video-nouveau[/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR]
 
 [COLOR=black][/COLOR] 
 [COLOR=black][FONT=Georgia](5) stop gdm and restart X[/FONT][/COLOR][COLOR=black][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black]sudo[/COLOR][COLOR=black] service gdm start[/COLOR][COLOR=black][/COLOR]
 
 [COLOR=black][/COLOR] 
 [COLOR=black][FONT=Georgia][/FONT][/COLOR][COLOR=black][FONT=Georgia][/FONT][/COLOR]
 [COLOR=black][FONT=Georgia]Restart the system[/FONT][/COLOR][COLOR=black][FONT=Georgia][/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
 [COLOR=black][FONT=Georgia](6) stop X[/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black][FONT=Courier New]sudo[/FONT][/COLOR][COLOR=black][FONT=Courier New] service gdm stop[/FONT][/COLOR]
 
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
 [COLOR=black][FONT=Georgia](7) install driver[/FONT][/COLOR]
 [COLOR=black][FONT=Georgia][/FONT][/COLOR] 
   [COLOR=black]sudo[/COLOR][COLOR=black] sh NVIDIA-Linux-x86_64-280.13.run[/COLOR]

[/FONT][/FONT]
Thanks for the support!
[FONT=Calibri][FONT=Times New Roman,serif][FONT=Calibri,sans-serif][/FONT][/FONT][/FONT]

---


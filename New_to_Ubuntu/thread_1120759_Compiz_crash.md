---
title: "Compiz crash"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by psychomichael on 2009-04-09
I just tried to set the computer up for dual monitors and failed miserably. After resetting everything back to the way it was with just one monitor and getting the resolution reset to the proper settings, Compiz no longer works. When I start it in the terminal, I get this error:

```
michael@darkmage:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d1 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

```

Any ideas, anyone?

---

### Post by Hospadar on 2009-04-09
What happens when you run these two things in a terminal
```
glxinfo | grep direct
```
You should see something like "direct rendering: Yes"
and
```
glxgears
```
You should see some 3d gears

Do you know what video hardware you are using?

You might also want to try
sudo dpkg-reconfigure xserver-xorg
this should return your xorg.conf to it's original settings, then you can go to the hardware driver manager and re-activate your restricted driver (if you use one)

---

### Post by psychomichael on 2009-04-09
Thanks, both codes did what you said they would. Here's the terminal output from the glxgears command:

```
michael@darkmage:~$ glxgears
4835 frames in 5.0 seconds = 966.917 FPS
5123 frames in 5.0 seconds = 1024.566 FPS
5124 frames in 5.0 seconds = 1024.672 FPS
5123 frames in 5.0 seconds = 1024.587 FPS
5123 frames in 5.0 seconds = 1024.571 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.

```

I'm actually cleaning up my drives to reformat with a different version of linux...been having trouble with my soundcard not working right for several months with no solutions.

---


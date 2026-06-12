---
title: "Desktop effects and nvidia-glx-177"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by festlig-faetter on 2008-12-09
Hi everybody.
I'm having a bit of trouble with my graphics driver.

A couple a weeks ago, i was running desktop effects fine. But one day, they were nowhere to be found.
So i tried [System] -> [Preferences] -> [Appearance] -> [Visual Effects] and tried turning it back on. But after blinking a couple of times, it just gave me a message saying "Desktop effects could not be enabled"

Then i tried to open a terminal:
```

$glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

I found a thread on this forum describing the problem, but it stops just before giving the answer in a simplified form:
[Desktop effects could not be enabled]("http://ubuntuforums.org/showthread.php?t=877724")

In short:
Anyone know how to install nvidia-glx-177 to another kernel? :confused:

I am using a GeForce 8400M graphics card, and i am running kernel 2.6.27-10

---

### Post by w4ett on 2008-12-09
One of the easiest methods to try and fix your problem is by the use of Envy:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

You can also manually remove and reinstall the driver, but I have found Envy to be pretty valuable for times like these. :)

---

### Post by phidia on 2008-12-09
Have you tried using synaptic (the package manager) to install that package?
In my experiance some M (mobile) cards are not recognized as well-is this a laptop?
If you can't install your driver using the package manager try installing envyng it's in the repos and use that to install the driver.

Added: Use envyng not envy.

---

### Post by festlig-faetter on 2008-12-09
Allright, here's what i've done so far:

Deleted all other linux kernels, then the one i am presently using, just in case the driver was installed to a different kernel
Installed EnvyNG, and try to have it install first the nvidia-glx-173 and after that the nvidia-glx-177

Tried to run the glxinfo again, with the identical results.

I haven't installed libgl1-mesa-dev, but when i try, it says that i should uninstall nvidia-glx-117-new, does that give anybody a clue?
It is a laptop, but i've never had a problem with linux not recognizing the graphics card before...

I'm thinking that maybe some driver (or whatever) isn't started during booting the system. :confused:

[INDENT][EDIT]
I just looked through /var/log/syslog to see if that said anything clever, and i find these lines, which hopefully gives a clue about what is going on:

```

[   52.399067] glxinfo[6460]: segfault at 0 ip 000000000040313a sp 00007ffff3ed9480 error 4 in glxinfo[400000+5000]
[   52.419506] glxinfo[6467]: segfault at 0 ip 000000000040313a sp 00007fff1ae8d550 error 4 in glxinfo[400000+5000]
[   52.761079] CE: hpet increasing min_delta_ns to 15000 nsec
x-session-manager[6069]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
pulseaudio[6201]: module-x11-xsmp.c: X11 session manager not running.
pulseaudio[6201]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```
[/INDENT]
[INDENT][INDENT][EDIT #2]
Okay, i tried:

```
sudo lshw
```
Which gives this for graphics:
```

*-display
  description: VGA compatible controller
  product: GeForce 8400M G
  vendor: nVidia Corporation
  physical id: 0
  bus info: pci@0000:01:00.0
  version: a1
  width: 64 bits
  clock: 33MHz
  capabilities: bus_master cap_list
  configuration: driver=nvidia latency=0 module=nvidia

```
Shouldn't it have a physical id ?
[/INDENT][/INDENT]
Jesper

---


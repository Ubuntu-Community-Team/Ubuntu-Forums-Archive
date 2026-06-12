---
title: "Unity will not run"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-06-10
Just loaded this computer with Ubuntu 11.04.      Got a message right off as follows:
It seems that you do not have the hardware required to run Unity.   Please choose Ubuntu classic at the login screen and you will be using the traditional environment.  Also got a message about additional drivers.  

I had been using Unity on a different computer and had grown to like it.      After searchinjg these forums, I saw that my video adapter driver may be the issue.   Undated the Nvida driver as said was required for 3D video.      No change and I do not see any message about selecting classic desktop when I log into the system.  This box is about 6 years old but does have a graphic accelerator adapter with a fan on it.      

Processor is 3.06 GHZ with hyper threading   (natty sees as 2 processors)
mem= 1.2 gig
disk= 60 gig Sata 

Short of pulling the video adapter, how can I tell which one?    
What else could cause me not to be able to run Unity?

All help is appreciated?

---

### Post by sikander3786 on 2011-06-10
Please let us see the outputs of these commands:

```

/usr/lib/nux/unity_support_test -p
lshw -c video
```

If your card is black-listed, you might try to force start Unity.

[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

---

### Post by dFlyer on 2011-06-10
Run this command to see what is preventing unity:

/usr/lib/nux/unity_support_test -p

---

### Post by comput99 on 2011-06-10
is tht a good change?

---

### Post by ghostborg on 2011-06-10
Take that as things to come, try login as Gnome Classic.

---

### Post by rbowen1 on 2011-06-10
[QUOTE=sikander3786;10924785]Please let us see the outputs of these commands:

```

/usr/lib/nux/unity_support_test -p
lshw -c video
```Terminal shows:  
  OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv28 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no


Can I try a different driver or am out of luck for Unity on this box??

---

### Post by rbowen1 on 2011-06-11
Update:
Graphic adapter:  NVIDIA GeForce4 Ti 4200 with AGP8x
Bus:  AGP 4X 
Memory:  128 MB

Web link to adapter:  [http://www.nvidia.com/page/geforce4ti.html](http://www.nvidia.com/page/geforce4ti.html)

Tried sudo: nvidia-settings  and got "  command not found  "

Installed nvidia-settings

Now getting:  You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

sudo nvidia-xconfig"  returns:  "sudo: nvidia-xconfig: command not found"


Any help is appreciated!!

---

### Post by LowSky on 2011-06-11
> **rbowen1 said:**
> Update:
Graphic adapter:  NVIDIA GeForce4 Ti 4200 with AGP8x
Bus:  AGP 4X 
Memory:  128 MB

Web link to adapter:  [http://www.nvidia.com/page/geforce4ti.html](http://www.nvidia.com/page/geforce4ti.html)

Tried sudo: nvidia-settings  and got "  command not found  "

Installed nvidia-settings

Now getting:  You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

sudo nvidia-xconfig"  returns:  "sudo: nvidia-xconfig: command not found"


Any help is appreciated!!

you need to install the driver first
System > Administration > Additional drivers

enable the recommended driver.

if nothing come up on the list lets us know.

---

### Post by rbowen1 on 2011-06-11
> **LowSky said:**
> you need to install the driver first
System > Administration > Additional drivers

enable the recommended driver.

if nothing come up on the list lets us know.

Shows:

No proprietary drivers are in use on this system

Experimental 3D support for NVIDIA cards
Tested by the Ubuntu developers

This driver provides a highly experimental 3D acceleration for NVIDIA graphics cards, as a free alternative to the proprietary driver.

This driver is activated and is currently in use.

---

### Post by rbowen1 on 2011-06-19
Looks like I am stuck with Gnome Classic.      No problem!  Unity is more like a windows environment.   Gnome Classic  just takes some getting used to.      I have not used a windows OS for some time now. Ubuntu rocks!     Closing this thread.

---


---
title: "Please convert commands fro ubuntu"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-11-03
I have intel video driver. I got this error 
```
checking for PCIACCESS... yes
[COLOR="Red"]checking for DRM... configure: error: Package requirements (libdrm >= 2.4.11) were not met:[/COLOR]

No package 'libdrm' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DRM_CFLAGS
and DRM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```[SIZE="1"]a fragment of the process[/SIZE]

The solution and following steps are given at this [web page]("http://intellinuxgraphics.org/install.html")

but i am not able understand these commands. What will be the corresponding procedure for Ubuntu 9.04 distro. Please someone make my way easier.

Thanks...

---

### Post by lykwydchykyn on 2009-11-03
Can I ask why you're trying to compile the intel driver yourself?  Not that you can't, but why?  Is it to fix a specific issue?

---

### Post by Old *ix Geek on 2009-11-03
> **lykwydchykyn said:**
> Can I ask why you're trying to compile the intel driver yourself?  Not that you can't, but why?  Is it to fix a specific issue?This is purely a guess on my part, but given the fact that the post is in the **Absolute Beginners** board, I'd imagine the OP has no idea that that's what the instructions are telling her/him to do, or that it's unnecessary to solve the problem.

> **eshant_engineer said:**
> I have intel video driver. I got this error 
```
checking for PCIACCESS... yes
[COLOR="Red"]checking for DRM... configure: error: Package requirements (libdrm >= 2.4.11) were not met:[/COLOR]
```
**[color="red"]No package 'libdrm' found[/color]**It's telling you that you're missing one of the package's requirements, **libdrm**. Go to Synaptic and put **libdrm** in its search box.  From the list of matches that appears, look for items with **libdrm** in their names; make sure their version numbers are greater than or equal to 2.4.11; if they're not installed, install them.

Now you're ready to try again.  If it still doesn't work, post again and tell us what happened.

---

### Post by anagor on 2009-11-03
Those packages should be installed already, but in case they aren't for some reason, what you need is, 
GUI way: in synaptic find and install the following:
libdrm2
libdrm-intel1

they are both version 2.4.14 in ubuntu 9.04

or if you prefer command line then:
sudo apt-get install libdrm2 libdrm-intel1

then restart the computer and all should work ok.
There is no need to recompile or install packages from other sources then the default Ubuntu repositories, for the Intel graphic drivers to function on Ubuntu 9.04

---


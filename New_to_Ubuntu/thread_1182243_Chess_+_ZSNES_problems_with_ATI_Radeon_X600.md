---
title: "Chess + ZSNES problems with ATI Radeon X600"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by mtheultimate on 2009-06-08
I dont know if these 2 problems are related but here they are:

I installed the 2 python packages needed for Gnome Chess 3D mode and
now it crashes and wont startup if I activate 3D mode.
I have to run "gconftool-2 --toggle /apps/glchess/show_3d" to revert to 2D mode.

ZSNES works great but if the display settings is in a windowed "O" (for OpenGL) 
mode (like "ODR-W") when I move the window the screen fills up with dirty repaint
regions (its not repainting the background and just "smearing" all over the screen).
If im not in an OpenGL mode everything is fine.

Since these are both OpenGL related problems, is it a problem with my ATI Radeon X600
card? Ive only been using Ubuntu for 2 days (Im using Jaunty) so im a total "noob".
Was I supposed to install a display driver on my own?

---

### Post by mtheultimate on 2009-06-08
I guess im going to try to proceed by downloading the ATI driver from:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.19&lang=English)

When I run:
sh ./ati-driver-installer-9-3-x86.x86_64.run

I get the error:
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Anyone have any help? Should I even be doing this?

---

### Post by windy81 on 2009-07-13
i have the same ati mobility radeon x600 card in my laptop, and it doesn't seem to have any options in Ubuntu to modify it's settings like in windows.

shame really

unless im being noob, and there is  ? 
i am very new to ubuntu

---


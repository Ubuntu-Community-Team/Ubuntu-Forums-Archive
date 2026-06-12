---
title: "Remote desktop with tightvnc and OpenGL"
date: 2018-02-03
forum: Networking &amp; Wireless
---

### Post by eazydatamining on 2018-02-03
Hi,

I am connecting from a windows machine using vnc viewer to an Ubuntu running tightvnc with XFCE option and tried to run an application (Cura 3) that needs OpenGL. Although the application runs to any user locally. When I tried to connect remotely with vnc viewer I got the message "Failed to probe OpenGL" "Could not probe OpenGL. This program requires OpenGL 2.0 or higher. Please check your video cards drivers.

Any ideas?

Thank you in advance.
Manolis

---

### Post by slickymaster on 2018-02-03
Thread moved to **Networking & Wireless** for a better fit

---

### Post by TheFu on 2018-02-03
OpenGL normally requires direct access to a GPU **ON THE SAME MACHINE**.  There might be remote desktop solutions which have gotten openGL to work over a wire - I vaguely remember reading about it and attempting to get turboVNC working, but never did.

Sorry I don't have an proven answer.  I'd start research by looking for "opengl remote desktop". [https://unix.stackexchange.com/questions/233571/enabling-graphics-acceleration-for-opengl-over-remotely-via-vpn-from-ubuntu-clie](https://unix.stackexchange.com/questions/233571/enabling-graphics-acceleration-for-opengl-over-remotely-via-vpn-from-ubuntu-clie) has a few ideas which might be useful.

---


---
title: "Blank/Black screen with cursor after logon"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Xzinum on 2009-04-27
Hi there,

I recently upgraded to Jaunty. I was having the same exact errors when i upgraded from Intrepid. Today, i made a fresh install and i'm still getting suck at the same spot. 

Since the upgrade I haven't been able to get past the log in screen.

I get to the login screen, i can hear the little sound, enter my credentials, and then nothing. I get a cursor and a black screen and that's it.

I've run the recovery to fix possible graphics problems, no solution found.
I've set my xorg.conf to load the vesa driver (i'm using an old graphics card, GeForce 5200FX) and lowered my screen resolution to 1024x768 as the highest resolution possible and still get nothing.

Looking at the syslog, i get the two folling gdm warnings:

gdm[3225]: Warning: using default salt value (undefined in ~/.ecryptsrc)
and
console-kit-daemon[2909]: WARNING: Couldn't read /proc/2908/environ: Failed to open file '/proc/2908/environ': No such file or directory

Can anybody help?

---


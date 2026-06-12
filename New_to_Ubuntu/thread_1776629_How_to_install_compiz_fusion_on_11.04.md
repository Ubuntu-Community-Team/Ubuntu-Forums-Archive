---
title: "How to install compiz fusion on 11.04 ?"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-06
How to install compiz fusion on 11.04 ?

whats the best and safest way ?

ps

im not sure if im running unity or gnome. how do i find out ?

---

### Post by philinux on 2011-06-06
> **kalimojo said:**
> How to install compiz fusion on 11.04 ?

whats the best and safest way ?

It's installed by default.

All you are missing is this package.
```
sudo apt-get install compizconfig-settings-manager
```

If you dont like cli use the Software centre to install it.

The menu entry is then in System>preferences. ;)

---

### Post by jaacko on 2011-06-06
> **kalimojo said:**
> 
im not sure if im running unity or gnome. how do i find out ?

You're running unity if you have a vertical bar on the left side of your screen showing some icons.

Also, if you're running the default gnome desktop (the 'classic' mode in 11.04), you'll see gnome panels on the bottom and on the top of your screen.

---

### Post by kalimojo on 2011-06-06
> **jaacko said:**
> You're running unity if you have a vertical bar on the left side of your screen showing some icons.

Also, if you're running the default gnome desktop (the 'classic' mode in 11.04), you'll see gnome panels on the bottom and on the top of your screen.

im running gnome then as i dont have hte vertical bar on the lhs. do i need to be running unity to use compiz fusion ?

---

### Post by jaacko on 2011-06-06
Nope, compiz should run fine with gnome also.

---

### Post by dFlyer on 2011-06-06
If you defaulted to gnome without choosing it at startup can you please list your computer specs. Your system should have defaulted to Unity on 11.04 unless it couldn't support it, which would than question your ability to run unity with compiz.

---

### Post by kalimojo on 2011-06-06
> **dFlyer said:**
> If you defaulted to gnome without choosing it at startup can you please list your computer specs. Your system should have defaulted to Unity on 11.04 unless it couldn't support it, which would than question your ability to run unity with compiz.
ibm thinkpad t41 pentium m 1600 mhz
40 gb hd
512 mb of ram

anything else you need to know ?

---

### Post by dFlyer on 2011-06-06
Please run this in a terminal and post your results:

 /usr/lib/nux/unity_support_test -p

---

### Post by kalimojo on 2011-06-06
> **dFlyer said:**
> Please run this in a terminal and post your results:

 /usr/lib/nux/unity_support_test -p

OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R100 (RV200 4C57) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

---

### Post by dFlyer on 2011-06-06
Looks like unity is not supported. Maybe someone else can help you from here to maybe get it working if possible.

---

### Post by kalimojo on 2011-06-06
> **dFlyer said:**
> Looks like unity is not supported. Maybe someone else can help you from here to maybe get it working if possible.

thanks, when i run knoppix i can use the wobbly windows

---


---
title: "rotate cube messed up"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by libihero on 2009-08-09
whenever i try to rotate the cube, all of the graphics become messed up, and the cube and the windows become to randomly discolor

---

### Post by laurielegit on 2009-08-09
What compiz plugins have you got active? TBH, is your graphics card good enough for it? Are you running any video intensive apps? Try just fiddling with the settings. What's your graphics card?

---

### Post by libihero on 2009-08-09
how do i check what graphics card i have?
i just had ubuntu reinstalled because i wanted a fresh start with it, and the cube used to work perfectly fine before.

---

### Post by libihero on 2009-08-09
how do i check what graphics card i have?
i just had ubuntu reinstalled because i wanted a fresh start with it, and the cube used to work perfectly fine before.

---

### Post by fooman on 2009-08-09
> **libihero said:**
> how do i check what graphics card i have?
...

open a terminal and type or copy/paste the following:

```
lspci | grep VGA
```

---

### Post by libihero on 2009-08-09
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

im running 8.10 btw and using the proprietary driver fglrx

---

### Post by Kaymeerah on 2009-08-09
try installing the opensource xorg drivers, i think the x1200 driver doesnt work on 8.10 and over due to xserver version, maybe that was just 9.04 tho

---

### Post by libihero on 2009-08-10
ya that was just 9.04
i mean it used to work before....

---

### Post by libihero on 2009-08-11
bump...
could there be a difference since this time i'm running 64 bit instead of 32 bit?
in 32 bit it worked perfect...

---

### Post by Buuntu on 2009-08-11
Did you active your driver in System > Administration > Hardware Drivers?
 
If you have maybe try an older version of the driver.

---

### Post by libihero on 2009-08-11
ya it is active
what i dont understand is why it used to work before and it doesnt work now?
the only difference of the two is i reinstalled ubuntu and used a 64 bit version instead

---

### Post by Buuntu on 2009-08-11
Well then the answer is to use the 32 bit version I guess.  I know it isn't the answer you were looking for but maybe that is the only solution?

You're sure you have a 64-bit processor right?  Maybe your hardware doesn't work with 64bit Linux.

I'm not an expert though, so you might want to talk to someone else about it.

---

### Post by libihero on 2009-08-12
bump...
help please :(

---

### Post by libihero on 2009-08-13
bump...

---

### Post by libihero on 2009-08-14
bump...

---

### Post by nhasian on 2009-08-16
the graphics clipping looks like its just the video driver.  I wouldnt abandon the 64 bit OS for that.  You can enable the backports repository to see if it offers a newer version of the display driver.

System->Administration->Software Sources, click on the *updates* tab, then tick the boxes for pre-release updates and unsupported updates.

---

### Post by libihero on 2009-08-16
it didnt work :(

---

### Post by nhasian on 2009-08-16
libihero,

I know that the upcoming version of Ubuntu Karmic Koala has some updated video drivers for ATI graphics adaptors.  Its only about two months away.  If you're feeling courageous and want to upgrade to the development version Karmic Koala Alpha 4 you can do so with the command:

```
update-manager -d
```

Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by libihero on 2009-08-16
i have 8.10 now, and i didnt upgrade since the proprietary driver for my comp for 9.04 didnt exist.  the open source driver caused flickering of the screen also... so im guessin the same will prolly happen if i do 9.10
do you think the reason is because im using 64 bit instead of 32 bit?  when i had 32 bit it worked perfectly fine.  or should i reinstall compiz maybe...?

---

### Post by nhasian on 2009-08-17
no it has nothing to do with 32 bit or 64 bit.  its just a graphics driver problem.  updating to a newer version of the graphics driver should resolve your issue.

---

### Post by earthpigg on 2009-08-17
9.04 broke/crippled video for a lot of people.

many are sticking with 8.10 until 9.10 for that reason.

not a solution, but food for thought.

---

### Post by libihero on 2009-08-17
i updated the graphics driver but it still didnt fix the problem :(
could it just be compiz, not the driver?

---

### Post by libihero on 2009-08-18
bmp...

---

### Post by Buuntu on 2009-08-18
Umm, it COULD be but probably isn't.  You could always try just removing and reinstalling Compiz though.

---

### Post by libihero on 2009-08-19
i typed in compiz replace and i got this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


does this help at all?

---

### Post by libihero on 2009-08-19
btw this it only happens when i have windows open
when i try the rotate cube without any windows open it works just fine

---

### Post by libihero on 2009-08-20
bump...

---

### Post by earthpigg on 2009-08-20
> **libihero said:**
> btw this it only happens when i have windows open
when i try the rotate cube without any windows open it works just fine

turn off 3d windows, see if that does it ;)

---

### Post by libihero on 2009-08-20
that actually worked!  but the thing is it still does that "broken glass" thing when i do expo also...
is there a common demoninator there?

---

### Post by earthpigg on 2009-08-20
the common denominator is that, however fun all those plugins are, many are beta-quality (my humble opinion) and simply do not work well in certain combinations with certain display resolutions, etc.

3d cube is probably top of that list. use it on dual monitors with 3d windows if you want to see some _*real*_ funkiness.

its fine though -- you are not at risk of causing any real damage to your system by playing around with compiz. just understand that certain combinations will simply not work well together with certain hardware, etc.

---

### Post by libihero on 2009-08-21
is there a way i can reset all of the configs for compiz to see if it works normally?

---

### Post by fooman on 2009-08-22
> **libihero said:**
> is there a way i can reset all of the configs for compiz to see if it works normally?

open ccsm,  click the preferences button (bottom left)...then click the "reset to defaults" button.

---


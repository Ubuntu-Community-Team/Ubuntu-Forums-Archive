---
title: "Intel Graphics Drivers?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-14
I ran glxgears and I got this:

1712 frames in 5.0 seconds
1770 frames in 5.0 seconds
1790 frames in 5.0 seconds
1768 frames in 5.0 seconds
1676 frames in 5.0 seconds
1768 frames in 5.0 seconds
1723 frames in 5.0 seconds

This seems pretty low, even for my crappy graphics.  I have a Intel GMA X4500HD integrated video card.  Is there anything I can do or install to make it work better in Ubuntu?

---

### Post by maddog39 on 2010-01-14
To my knowledge, the GMA graphics drivers have been sub-par on newer chipset models for some time now. I think your probably out of luck for the time being.

---

### Post by Dreakon on 2010-01-14
Are there any better drivers out there than the default 9.10 ones?  Even if only slightly? :P

---

### Post by halitech on 2010-01-14
minimize the gears window while its running, should double the output ;)

---

### Post by Dreakon on 2010-01-14
> **halitech said:**
> minimize the gears window while its running, should double the output ;)
Genius!  Why didn't I think of that! ;)

Oh well, guess I'm stuck for now.  Fortunately I don't plan on doing much gaming or 3D apps outside of Google Earth every now and then.  Thanks for the info! :P

---

### Post by halitech on 2010-01-14
As far as I know there are no other drivers available for the intel cards. There may be some tweaks you can make to increase the performance but I'm not sure what at the moment. Maybe a search on here or Launchpad will yeild some info.

---

### Post by tom.swartz07 on 2010-01-14
> **Dreakon said:**
> I ran glxgears and I got this:

1712 frames in 5.0 seconds
1770 frames in 5.0 seconds
1790 frames in 5.0 seconds
1768 frames in 5.0 seconds
1676 frames in 5.0 seconds
1768 frames in 5.0 seconds
1723 frames in 5.0 seconds

This seems pretty low, even for my crappy graphics.  I have a Intel GMA X4500HD integrated video card.  Is there anything I can do or install to make it work better in Ubuntu?

Thats way better than mine. 
```
tom@ubuntu-karmic:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
580 frames in 5.0 seconds
620 frames in 5.2 seconds
420 frames in 5.3 seconds
440 frames in 5.1 seconds
500 frames in 5.2 seconds
460 frames in 5.2 seconds
360 frames in 5.5 seconds

```

:(

Ive come to terms that my ATI card is no longer supported.

---

### Post by halitech on 2010-01-14
> **tom.swartz07 said:**
> Thats way better than mine. 
```
tom@ubuntu-karmic:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
580 frames in 5.0 seconds
620 frames in 5.2 seconds
420 frames in 5.3 seconds
440 frames in 5.1 seconds
500 frames in 5.2 seconds
460 frames in 5.2 seconds
360 frames in 5.5 seconds

```

:(

Ive come to terms that my ATI card is no longer supported.

What card do you have? I have an HD4350 and here's mine

```
daryl@debian:~$ glxgears
5650 frames in 5.0 seconds = 1129.455 FPS
6273 frames in 5.0 seconds = 1254.466 FPS
6238 frames in 5.0 seconds = 1247.563 FPS
6077 frames in 5.0 seconds = 1215.361 FPS

```

---

### Post by tom.swartz07 on 2010-01-14
> **halitech said:**
> What card do you have? I have an HD4350 and here's mine

```
daryl@debian:~$ glxgears
5650 frames in 5.0 seconds = 1129.455 FPS
6273 frames in 5.0 seconds = 1254.466 FPS
6238 frames in 5.0 seconds = 1247.563 FPS
6077 frames in 5.0 seconds = 1215.361 FPS

```

i have an ati radeon x1270. last time it was supported was 8.04...

i was looking into it around jaunty era, and it bricked my xorg 3 times. i just gave up. haha

---

### Post by halitech on 2010-01-14
ok, yeah ati dropped support after 8.10. best option would be to swap out for an HD series card or drop back to 8.04 which still have support for awhile yet if you want better support.

---

### Post by nwadams on 2010-01-14
hi guys. Ok first of all glxgears IS NOT a good benchmark tool. As for the OP's question. The default drivers installed are about as good as they will get unless intel releases better drivers.

---


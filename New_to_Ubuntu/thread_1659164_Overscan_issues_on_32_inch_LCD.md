---
title: "Overscan issues on 32 inch LCD"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Famicommander on 2011-01-03
I recently installed Ubuntu 10.10 32 bit on a media box that I built for my grandmother for her Christmas present.

I installed the OS and everything worked fine on my computer monitor at home. However, on her 32 inch LCD (native resolution 1280*720), we're getting some overscan on all four sides of the screen. 

I have not installed any graphics drivers because everything worked fine out of the box, but now obviously it doesn't.

The video card is an ATI Radeon X1550, PCI Express. She doesn't plan on running any 3D content. Just playing video, playing audio, running a few 2D games, and browsing the internet.

Would anyone be able to help me correct the overscan issue?

Thanks in advance.

---

### Post by Famicommander on 2011-01-03
Still haven't been able to figure this one out.

---

### Post by sandyd on 2011-01-03
> **Famicommander said:**
> I recently installed Ubuntu 10.10 32 bit on a media box that I built for my grandmother for her Christmas present.

I installed the OS and everything worked fine on my computer monitor at home. However, on her 32 inch LCD (native resolution 1280*720), we're getting some overscan on all four sides of the screen. 

I have not installed any graphics drivers because everything worked fine out of the box, but now obviously it doesn't.

The video card is an ATI Radeon X1550, PCI Express. She doesn't plan on running any 3D content. Just playing video, playing audio, running a few 2D games, and browsing the internet.

Would anyone be able to help me correct the overscan issue?

Thanks in advance.
might be the default underscan thingy they enabled in the kernel
post output of
```

xrandr
```

the command is
```

xrandr --output [SCREEN] --set underscan off 

```

---


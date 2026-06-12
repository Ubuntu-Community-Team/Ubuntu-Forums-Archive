---
title: "Weirdly Related Packages"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-02-27
So I have been messing with DVD authoring and video converting and I noticed that for a lot of the packages installed with gstreamer0.10-ffmpeg have two versions: regular and extra. For example, libavutil49 has an alternate package libavutil-extra-49. In each case both are listed in the dependencies, yet when I originally installed, it installed libavutil49 and not the other one. It seems to replace the other but what is the point. Winff then uninstalled some of these and installed the extra versions. All of my files still work like they used to, and all dependencies are still satisified. What is the point of having sets of packages like this?

---

### Post by skymera on 2010-02-27
This is from Libavutil49 description:
```
 This package contains a Debian-specific version of the libavutil shared
object that should only be used by Debian packages. 
```

this is from libautil49 extra description:
```
 This package contains a unrestricted version of the libavutil shared
object that should only be used by Debian packages. 
```
The reason for this? Not sure.

I guess "Debian-specific" means totally free.

---

### Post by Martin Marshalek on 2010-02-27
That makes sense. It's no real issue but I would be curious to see why the extra packages aren't installed by default though. Just having some of these plugins are against Debian's philosophy so what is included in the extra packages that is so proprietary or non-free?

---


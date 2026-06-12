---
title: "Ubuntu Software Center disappear!"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by LightThunder on 2009-12-01
Ok I'm new at Ubuntu but:
If I click on Ubuntu Software Center, it opens, but I don't have time to look at it, and it closes itself.

---

### Post by cariboo on 2009-12-03
For diagnostic purposes open an Applications-->Accessories-->Terminal and type:

```
software-center
```

Paste the error message in your next post.

---

### Post by Alenki on 2009-12-21
Hello,

im new here, am also new on Linux, I don't know too much about handle problems here, i found this thread looking on google a solution for this problem. My Ubuntu version is 9.10. I made what cariboo907 said, this is my result:

ab@Ab:~$ software-center

(software-center:2005): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:2005): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:2005): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:2005): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:2005): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:2005): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:2005): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:2005): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:2005): GStreamer-WARNING **: adding type gint multiple times

(software-center:2005): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:2005): GStreamer-WARNING **: adding type glong multiple times

(software-center:2005): GStreamer-WARNING **: adding type guint multiple times

(software-center:2005): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:2005): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: Error al volver a escanear el registro , child terminated by signal
ab@Ab:~$

---

### Post by stewarb on 2009-12-30
Same thing happened to me, and I got all the same Gstreamer messages. It all started to go wrong after installing "ubuntu-restricted-extras" in order to try to get DVD's to play. 
I've re-installed several times and can confirm that "ubuntu-restricted-extras" definately causes this problem for me. 
I am very new to Ubuntu and this happened a few weeks ago but I managed to get software center working again by removing "gstreamer0.10-plugins" (either bad or ugly can't remember exactly which) from "synaptic package manager" under System - Administration.
I don't know if this breaks anything else but it all seemed OK for me back then (have re-installed since). I still have not been able to play DVD's - even my own created home movies - so not encrypted - but that's another thread I'm trying to find.

Please note, I'm not suggesting the fix, just what caused the problem for me in the hope that it gives someone a clue to this. Did you install "ubuntu-restricted-extras" by any chance?

---


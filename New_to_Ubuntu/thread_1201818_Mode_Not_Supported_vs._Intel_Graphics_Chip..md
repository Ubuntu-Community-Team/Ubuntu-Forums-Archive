---
title: "Mode Not Supported vs. Intel Graphics Chip."
date: 2009-07-01
forum: New to Ubuntu
---

### Post by beardlace on 2009-07-01
Ok, so I'm using an old desktop and running Ubuntu Hardy Heron 8.04.1 LTS.  

It has
00:02.0 VGA compatible conwoozlerer:  
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) 

I have a SAMSUNG LNT-3242HX/XAA 40" LCD TV.
 
I have to boot in recovery mode to autodetect hardware and get anything to appear on screen. Otherwise the screen reads "mode not supported."

I'm lurked the forum and searched all the threads. I have tried to edit xorg until my eyes bled. What do I do here?

---

### Post by gn2 on 2009-07-01
Try using a different type of connector.
I had exactly the same problem in 8.04 with a Samsung 32" LCD TV connecting with HDMI, so switched to VGA and it works, albeit not at the desired resolution.
Think the resolution issue is more to do with the TV than the laptop though.

---

### Post by LowSky on 2009-07-01
boot into recovery mode and choose xfix, also what is the recommended screen size for the samsung? we could always add that to you xorg file

---


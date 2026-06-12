---
title: "Installing nvidia 180.11 drivers in Intrepid"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by gwyndyn on 2009-03-31
I've searched around a bit and have seen varying reports on how to install this via the terminal or via synaptic, and I figured I'd check here for any helpful information before I subject my husband to listening to me swear again because I broke my computer while messing with it. ;)

So...can anyone give me advice as to the best way to move from the Nvidia 177 driver to the 180 beta driver?  I'm able to see the nvidia-glx-180 in Synaptic, but do I need to do something to uninstall the 177 driver first?  Can I just use the Synaptic package manager to install the new driver, or do I need to download it from the Nvidia website and do some finagling in the terminal in order to get it working?  Thanks so much for any help/advice y'all can give me!

---

### Post by rybaxs on 2009-03-31
its good to use synaptic package drivers like my NVidia, it was a general/standard driver for Nvidia..because before, when I downloaded drivers at NVidia site, my video card didn't work.. :(

---

### Post by 3rdalbum on 2009-04-01
Just install the nvidia-glx-180 package. It's listed in Synaptic as "Replaces: nvidia-glx-177" among other things, so it will automatically remove the old driver before installing the new one.

---

### Post by gwyndyn on 2009-04-01
Thanks so much. I'll give that a try after work today.

---

### Post by gwyndyn on 2009-04-02
Worked like a charm. Thanks!

---


---
title: "How to roll back Nvidia 195 driver to version 185 ?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by videodrone on 2010-06-19
Hello all.
Today I allowed Update Manager on Ubuntu 10.04 to download and install all of its recommendations. One of the things it did was update my Nvidia driver to version 195 which seems to have killed my audio over HDMI. How do I roll back to the previous version of my Nvidia driver ?

regards
videodrone

---

### Post by Autodave on 2010-06-19
> **videodrone said:**
> Hello all.
Today I allowed Update Manager on Ubuntu 10.04 to download and install all of its recommendations. One of the things it did was update my Nvidia driver to version 195 which seems to have killed my audio over HDMI. How do I roll back to the previous version of my Nvidia driver ?

regards
videodrone

Go into Synaptic Package manager and search for NVIDIA.  Then, pick the one you want.

---

### Post by bumanie on 2010-06-19
Nvidia 185 is not compatible with the version of xorg - xorg version 7.5 - that is in 10.04; do not roll back to 185 if you still want a computer with a GUI.

---


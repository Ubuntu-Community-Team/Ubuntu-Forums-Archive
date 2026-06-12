---
title: "Generic msgs"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by geomarsh on 2011-05-25
Can somone tell me where these come from and how to get rid of them. 
"Ubuntu, with Linux, 2.6.32-31-generic"   I see a list of them when I log into Ubuntu.
Thank you for the advice to use Synaptic.   What is Synaptic?

---

### Post by avtolle on 2011-05-25
These are various kernels installed on your system. You may remove them through Synaptic (be sure you do not remove the one to which you are booted). To find out which one this is, run ```
uname -r
```from the command line. I recommend keeping one "older" kernel version besides the current one which boots, "just in case".

---


---
title: "Two kernels with different configs"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by metalac on 2007-07-23
Hey guys,

So installed the nvidia drivers and when i restarted I found out that my wireless card isn't working.  It's an rtl8187 based card.  It worked fine prior to nvidia driver install with native drivers (no ndiswrapper).  What i did notice is that now i have 2 kernels 2.6.22.8 that doesn't have the rtl8187 module but works fine with nvidia module, and another called 2.6.22.8-generic that has the rtl8187 module, but doesn't work with nvidia module.  Does anyone knows why this happened in the first place, and how I could fix it?

I figured I'd just recompile the kernel, but I can't find rtl8187 in the kernel config.  Also the kernel that works the wireless driver is in /lib/module/kernel/2.6.22.8-generic/ubuntu/wireless, which is strange, does this mean that there is the ubuntu package for rtl8187?

thanks.

---

### Post by metalac on 2007-07-23
bump.

---


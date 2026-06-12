---
title: "new kernel/sound card failure ?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by stevek123 on 2010-03-01
fwiw I'm still running Hardy... I suspect this doesnt matter as I see lots of folks have this issue. Every time I update the kernel, it fails to recognize the sound card and I need to to rebuild the driver. I just follow this thread...= Comprehensive Sound Problem Solutions
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
After this latest kernel, the module assistant didnt work and I had to make it manually. Not TERRIBLE but this is getting to be a pain. I've even gotten to the point where i dont want the darned new kernels and I delay installing them for a long time...so...
HOW/WHERE can I modify my settings so that new kernel installation doesnt wipe the sound drivers??? I would suspect that I can edit some(???) file where the sound settings are not overwritten and dumped.

---

### Post by sandyd on 2010-03-01
> **stevek123 said:**
> fwiw I'm still running Hardy... I suspect this doesnt matter as I see lots of folks have this issue. Every time I update the kernel, it fails to recognize the sound card and I need to to rebuild the driver. I just follow this thread...= Comprehensive Sound Problem Solutions
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
After this latest kernel, the module assistant didnt work and I had to make it manually. Not TERRIBLE but this is getting to be a pain. I've even gotten to the point where i dont want the darned new kernels and I delay installing them for a long time...so...
HOW/WHERE can I modify my settings so that new kernel installation doesnt wipe the sound drivers??? I would suspect that I can edit some(???) file where the sound settings are not overwritten and dumped.

When drivers are manually compiled for the kernel, they are compiled _for_that_kernel_only. That is, unless you add it to dkms, but that is out of the scope of my knowledge.
They are compiled as modules, which are in /lib/modules if your curious.

The modules are not being replaced, since each kernel has its own modules directory.

You can **try** moving the modules from one kernel to another, but it is **highly** not reccomended.

---

### Post by stevek123 on 2010-03-01
GGGRRRRR
Thanks Carlee. Good to know but pain to follow thru with. and with that in mind... Let me HIGHLY RECOMMEND to all who search and hit this thread  to bookmark the link I first posted! YOU WILL NEED IT.
;)
steve

---


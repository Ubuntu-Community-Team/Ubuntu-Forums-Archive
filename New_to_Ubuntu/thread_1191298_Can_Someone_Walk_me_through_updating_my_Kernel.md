---
title: "Can Someone Walk me through updating my Kernel?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by kendoori on 2009-06-18
Am nervous about doing this, and would like to go to 2.6.30 and potentially have the option to fail back to my current 2.6.28-11

---

### Post by renkinjutsu on 2009-06-18
You might want to take a look at this doc
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")
It's relatively easy to compile your own kernel, the method described in the Ubuntu document above guides you through packaging your own deb file which you can use to install your kernel.. your newly installed kernel is separate from and will not affect your older kernels. If needed, you can uninstall your new kernel through apt-get or through synaptic..

pay attention to any errors during the installation of your debs, it might be a good idea to keep a log handy.. post back if you have any problems! Good luck!

---

### Post by SOULRiDER on 2009-06-18
Always remember to keep an older version. The problem with compiling your own kernel is that you have to make usre all your hardware is selected or things will not work. Also, certain features int he kernel also have to be enabled.

Check this thread out:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---


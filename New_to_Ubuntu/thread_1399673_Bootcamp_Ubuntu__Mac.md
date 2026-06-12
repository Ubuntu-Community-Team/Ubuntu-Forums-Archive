---
title: "Bootcamp Ubuntu / Mac"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by noorez on 2010-02-06
Hi,

My parents bought be a macbook pro to replace my old laptop but I'm having a bit of trouble figuring out how to use boot camp to install ubuntu.

Since boot camp partitions the hard drive for you, what do I need to tell the ubuntu installer about how to partition my hard drive? What option do I choose when it asks me?

Also, I know that I cannot overwrite macs boot loader so should I be installing it to the ubuntu partition?

---

### Post by CJN on 2010-02-06
Since, as you  said, boot camp partitions the hard drive for you, you need to  tell the ubuntu installer to install to the last partition on the drive (the one created by bootcamp), you won't need to specify any further partitioning.

Also, to answer your second question you will want to check the advanced options near the end of the installation to tell the installer to put the boot loader in /

---


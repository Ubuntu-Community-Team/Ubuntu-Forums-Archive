---
title: "safely deleting old kernel files"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by frank002 on 2010-11-30
Hello:
 I am using Ubuntu 10.04 and have so far updated to the latest kernel 2.6.32-26. I like to keep at least the last two so I also have 2.6.32-25. I have already deleted 2.6.32-21 and 2.6.32-24 using Synaptic. When I go to
/boot, I see remnants of the kernels I have deleted. There are files such as abi-2.6.32-21-generic, config-2.6.32-24-generic, initrd.img-2.6.32-21-generic, vmlinuz-2.6.32-24-generic. I was wondering if I could safely delete all of these? 

 Thank You

---

### Post by JOHNNYG713 on 2010-11-30
In terminal,  sudo update-grub

---

### Post by nhasian on 2010-11-30
you can also get the latest linux kernel from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Liverbones on 2010-11-30
You certainly should be able to with no problems. I don't see how those could possibly affect the newer kernels, but to be perfectly honest, I'm no expert when it comes to Linux kernels. I just know from personally deleting such files that I've never experienced problems.

**Edit:** Also forgot to mention... by default, Synaptic tends to leave many configuration files behind for the packages that you remove, which may very well be why you still have those files from older kernels.

---

### Post by frank002 on 2010-11-30
Went ahead and deleted the files and everything is ok so far. Thanks four quick replies.

---

### Post by Liverbones on 2010-11-30
No problem. :) Some of us are bored at work, I'm sure. (That couldn't possibly be self-referential.) :P

---


---
title: "Procedure for getting the Intel 9465 wireless card workin using native drivers"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by ciphermonk on 2007-06-29
I just did a writeup on how to get that card working on fedoraforum. Because I'm not using any packages to do this, the same procedure should work with Ubuntu and other linux distros...


[http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550)

---

### Post by Scotty562 on 2007-07-03
I get a panic error on boot after the first 'make install.' Am I doing something wrong? When I run the first command that file you had me move into the folder only answered some of the options. I didn't know what to put for the rest of them so I just 'entered' through the list.  Could that be the problem?

I'm running feisty on a hp dv6500.

---

### Post by ciphermonk on 2007-07-05
Yes that's more that likely the issue. Did you download the 2.6.21.5 kernel from kernel.org? That's the kernel that the config file is made against

---

### Post by Scotty562 on 2007-07-05
I deffinately downloaded the 2.6.21.5 kernel. Another thing I noticed, the final command that was suppose to enter the information into the grub menu didn't insert the correct information. 'update-grub' entered the information but the actual menu.lst file was missing a piece that the other kernel had. So I'm not sure what was going on there.

---

### Post by ciphermonk on 2007-07-05
Hrm... it sounds like something went wrong with the kernel compile. part of what 'make install' does is add the newly compiled kernel to the bootloader as an option.

---

### Post by dracomordag on 2007-07-28
anyone willing to translate that into something i can understand? (the link in the OP)

---


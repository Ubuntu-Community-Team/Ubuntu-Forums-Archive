---
title: "new Ubuntu user"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by CB3 on 2009-10-04
When my daughter upgraded to a new laptop I inherited her old one, with which she had been experiencing all sorts of problems. Over the past few months I have re-installed Windows numerous times, but could never get the machine to work properly.
 
Finally in my frustration I loaded Ubuntu on the old Dell. Now, for the first time, I can use the laptop - I love it! I am not knowledge with Ubuntu or am I familiar with the Firefox browser, but I am trying to learn all I can.
 
Apparently I have a slight problem at boot-up. I have to hit ESC as the script begins, then I get 3 lines, the bottom one about the kernel. I hit enter on the top line and the system boots. If I just cut the machine on and let it run the boot on its own, it will run a moment, then make a thump sound and then cut off. Any suggestions?
 
Otherwise, I am pleased I discovered this system.
Thanks,
CB3

---

### Post by SuperSonic4 on 2009-10-04
Can you post the output of ```
cat /boot/grub/menu.lst
```. You can use the terminal or any text editor

---

### Post by LewRockwell on 2009-10-04
> **CB3 said:**
> When my daughter upgraded to a new laptop I inherited her old one, with which she had been experiencing all sorts of problems. Over the past few months I have re-installed Windows numerous times, but could never get the machine to work properly.
 
Finally in my frustration I loaded Ubuntu on the old Dell. Now, for the first time, I can use the laptop - I love it! I am not knowledge with Ubuntu or am I familiar with the Firefox browser, but I am trying to learn all I can.
 
Apparently I have a slight problem at boot-up. I have to hit ESC as the script begins, then I get 3 lines, the bottom one about the kernel. I hit enter on the top line and the system boots. If I just cut the machine on and let it run the boot on its own, it will run a moment, then make a thump sound and then cut off. Any suggestions?
 
Otherwise, I am pleased I discovered this system.
Thanks,
CB3

sounds like it might be a problem with ACPI

you can search for threads on it both here on the forum and across the interwebs with your preferred search engine

you might try searching with the model number of your laptop also

.

---

### Post by CB3 on 2009-10-04
I guess I was premature in assuming my laptop was not booting properly after installing Ubuntu.  I just noticed the "upgrade manger" at the lower left corner.  It listed 249 updates.  I downloaded and installed all of them and the computer then booted up perfectly.
 
Thanks for your suggestions.
CB3

---


---
title: "After Update, 2 versions of Ubuntu in Grub"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Nebelhom on 2010-01-15
Hi guys,

I just did a full install of Ubuntu 9.10 Karmic Koala. After the update was done, I had to restart and now I have two options for Linux to choose in the Grub thing at the beginning.

Ubuntu, Linux 2.6.31-17-generic

and

Ubuntu, Linux 2.6.31-14-generic

both work perfectly fine, but I'd like to remove the older one of the two (version 2.6.31-14). How would I best do that?

thanks for the help guys

...oh one other thing. If you know why it did that, that would be nice to know as well. thanks

---

### Post by drs305 on 2010-01-15
Many users leave one older working kernel on their machine so they have a working "backup" in case problems arise with the current kernel.

You can remove the older kernel(s) if you desire via Synaptic. I wrote a guide about StartUp-Manager a while back but recently updated the section on removing older kernels. I added a paragraph on Ubuntu Tweak, which is a great and simple GUI app which can remove these kernels.

Here is the link. Check the section on removing kernels:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Nebelhom on 2010-01-15
Thanks for the link. Do you know why it was left there automatically? Because the update manager never explicitly asked me if I wanted to keep it...

Would you advise me to leave it there?

---

### Post by drs305 on 2010-01-15
I would leave at least one old kernel, at least until you are sure the new one works. Even then, if you experience problems later having an older kernel to revert to allows you to easily determine if the problem is kernel-related or not.

Each time a new kernel is introduced, the older ones by default are retained. The new kernel goes to the top of the menu, and the older ones are moved down. Eventually you could have a lot of older kernels displayed on the menu. 

APT (the Ubuntu package manager) won't automatically remove these older kernels. So the user is left with the option to manually remove the kernels or hide them from the menu. For the moment, hiding them is easier it Grub legacy than Grub 2, but it can be done there as well by modifying scripts. Generally, my personal preference is just to keep two kernels, and then remove the oldest one via Synaptic or Ubuntu Tweak when a new kernel is introduced.

---

### Post by arubislander on 2010-01-15
As drs305 hinted at, it was left there in case the newer kernel did not work the way you wanted on your setup. I'd suggest you keep it for a while... maybe even till the next kernel update :)

---

### Post by Nebelhom on 2010-01-15
Awesome! Thanks a lot guys.

---


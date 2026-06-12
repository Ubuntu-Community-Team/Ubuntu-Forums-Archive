---
title: "Lucid Lynx after installation issues"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by jorgecarrillo150990 on 2010-04-30
I have two "problems" (nothing system breaking or anything) after installing Lucid.

First of all, in my GRUB it says "Ubuntu 9.10" instead of "Ubuntu 10.04".

After I click that it says the system didn't mount something but after 30 seconds it starts loading Lucid.

Now, the new splash is horrible in my laptop. It looks ancient. It is in a very small resolution. (Maybe this has to do with Plymouth not playing nice with nVidia cards...)

Could someone help me

---

### Post by c00lwaterz on 2010-04-30
high temp in my case. fan not working in my case. wifi not working in my case.

---

### Post by Sealbhach on 2010-04-30
Yeah, I had the low resolution in Plymouth, you can change it in your /etc/default/grub like so:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3)

And run sudo update-grub.

You need to know your proper screen resolution though.

I don't know why it still says Ubuntu 9.10....

.

---


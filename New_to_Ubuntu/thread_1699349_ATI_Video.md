---
title: "ATI Video"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Kyluke on 2011-03-03
Hey, as we all know the proprietary drivers for ATI have always lead to  screen tearing and/or other issues. A lot of people have suggested using  the open source drivers but for some of us that is not an option  because we need the full power of our graphics card.

This tearing  issue has been going on for as long as I can remember and yet it has  only been addressed by ATI recently. I read in a blog ([www.ubuntugamer.com/tag/screen-tearing/]("http://www.ubuntugamer.com/tag/screen-tearing/"))  that ATI has released a fix for this issue but I need to be running  kernel version 2.6.37. Now I don't know how to upgrade to kernel version  2.6.37 and then will the fix simply just be applied and work?

Please advise ASAP I need linux for university

---

### Post by Kirboosy on 2011-03-03
Have you run your Update Manger to update your computer lately? I'm not sure if the kernel is available yet or not but its worth a shot.

---

### Post by Kyluke on 2011-03-04
Yes I have and as far as I know it isn't

---

### Post by Kirboosy on 2011-03-04
Try reading this article [KernelCompile]("https://help.ubuntu.com/community/Kernel/Compile")

---

### Post by clhsharky on 2011-03-04
Kyluke

> I need to be running kernel version 2.6.37
Why?

The fix is in Catalyst 11.1 not in the kernel.
Support for 2.6.37 kernel was added to cat 11.1 but not necessary for the fix.

Catalyst 11.1 also supports .35 kernel in Maverick.
Kernel 2.6.37 has benefits like cgroups and can be installed, but is not supported by Maverick repositories.


Sharky

---


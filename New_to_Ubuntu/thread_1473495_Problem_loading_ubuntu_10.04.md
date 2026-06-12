---
title: "Problem loading ubuntu 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by bloodpuddin on 2010-05-05
I originally installed 9.10 on my machine, side-by-side with windows. After I upgraded to 10.04, I couldn't access windows vista. So, per instructions from a different thread, I repaired my loader, and now I can get to vista no problem- but when I choose Ubuntu from the loader, It acts like it's installing Ubuntu again, and eventually freezes up. Should I just wipe my Linux partition and start over? I am a noob to all of this, but I have no problem following explicit instructions....

---

### Post by Jon Monreal on 2010-05-05
> **bloodpuddin said:**
> It acts like it's installing Ubuntu again, and eventually freezes up.

Hello,

I'm wondering what you mean by this. Does a bunch of text scroll across your screen? Can you be more specific as to what happens?

Thanks.

---

### Post by bloodpuddin on 2010-05-05
I select "ubuntu" from the loader screen.  Instead of loading ubuntu, Text on the black screen reads "finishing installation, press f4 for more options" and a time.  Press f4, and I get the choice of normal, safe mode, or something else I cant remember.  No matter what I pick, I get a ubuntu loading screen with the logo, and it starts to pulse, and eventually freezes on a black screen.

---

### Post by Jon Monreal on 2010-05-05
I see.

Did you ever boot into Ubuntu after the upgrade (and it worked)?

If you think the upgrade may have failed, you can boot the Live CD, go to a terminal, mount your Ubuntu filesystem and then chroot to it. You can then type
```
dpkg --configure a
```
and press enter. If you need help with chroot, I can post instructions.

---

### Post by bloodpuddin on 2010-05-05
No, I have for sure rebooted with 10.04, and it worked fine until I fixed the loader for windows using the repair cd.

---

### Post by Jon Monreal on 2010-05-06
Are there any earlier kernel versions you can try in the Grub list?

---


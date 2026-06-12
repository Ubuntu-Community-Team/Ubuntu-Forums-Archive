---
title: "every update puts new version in boot window"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by bman-28 on 2010-10-03
I have dual boot with win7 and Ubuntu, every time I do an update it adds another boot line.
how do i stop this from happening and remove all the rest

---

### Post by drs305 on 2010-10-03
You are most likely talking about new kernel options. Each time a new kernel is added to your OS it is also added to the Grub menu. 

Most users keep at least one extra kernel on the menu as a backup (at least until assured the new one works properly).

I just wrote a new HOWTO on how to remove older kernels (and limit the number displayed in the Grub 2 menu):
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

If you also want to eliminate the memtest86+ entry and/or recovery modes (may not be a good idea) you can see the link in my signature line: G2-Tweaks. See the section "Built-In Settings and Non-Tweak Ways to Limit Menu Entries".

---

### Post by bman-28 on 2010-10-03
Thanks, I will try to do this and get back to the poat.

---

### Post by bman-28 on 2010-10-03
this dose not work, no left or right selections! must have done something wrong

---

### Post by drs305 on 2010-10-03
> **bman-28 said:**
> this dose not work, no left or right selections! must have done something wrong

It could be the way I explained it, but I don't understand what you mean by right/left selections. Would you explain what you weren't able to do?

If you are using Ubuntu Tweak and everything is grayed out, make sure you have pressed the "Unlock" button to the lower right and entered your password.

---


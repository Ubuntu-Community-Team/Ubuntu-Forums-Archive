---
title: "XFCE won't boot on startup"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Xerxes1 on 2009-02-10
Yeah X11 won't start when I boot up. I just get the CLI instead after I installed it. How do I get it to boot on startup?

---

### Post by Xerxes1 on 2009-02-10
Bumping, this can't be that hard surely?

---

### Post by Xerxes1 on 2009-02-11
sigh... bumping again

---

### Post by ibutho on 2009-02-11
What happens when you login to the terminal and run "startx".

---

### Post by Xerxes1 on 2009-02-11
> **ibutho said:**
> What happens when you login to the terminal and run "startx".

It starts, just as normal. Just not on bootup

---

### Post by ibutho on 2009-02-11
Do you have gdm installed? If so, try the following
```
sudo update-rc.d -f remove gdm
sudo update-rc.d gdm defaults
```
That will remove any current gdm startup and create new ones. 

If you don't have gdm installed, install it.

---

### Post by JKyleOKC on 2009-02-11
> **Xerxes1 said:**
> It starts, just as normal. Just not on bootup

From the applications menu, select the System entry. From that menu, select Services. When you get to Services, scroll down until you locate the Graphical Login Manager item. If it's NOT checked, you need to hit the Unlock button, enter your password into the unlock dialog, then check the item and close out the Services window. It will tell you that the X server is already running and ask if you want to use a different display. Tell it yes, number 1, and exit. Then restart your system and login should be working as expected.

If the box IS checked, however, then for some reason your "gdm" daemon isn't being launched. I'll have to leave diagnosis of that problem to someone more expert than myself. However the fact that "startx" works properly indicates that you don't have any of the most common display problems!

---

### Post by Xerxes1 on 2009-02-11
Yeah I was using xdm, I will try gdm now

---


---
title: "Computer boot wierd stuff"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by J697 on 2011-02-26
When I boot the computer up, instead of getting a Ubuntu screen with dots loading, I get a blinking cursor on a black screen. Then after 5-10 seconds, a big block of text appears and disappears in 0.25 second (I don't get to see what it says) and then it shows the login screen and then I log on etc everything is perfect beyond that point. I just want my computer to look "neat" when it turns on. I just want it to make the boot up screen the loading screen, like when you shut it off.

---

### Post by lkjoel on 2011-02-26
> **J697 said:**
> When I boot the computer up, instead of getting a Ubuntu screen with dots loading, I get a blinking cursor on a black screen. Then after 5-10 seconds, a big block of text appears and disappears in 0.25 second (I don't get to see what it says) and then it shows the login screen and then I log on etc everything is perfect beyond that point. I just want my computer to look "neat" when it turns on. I just want it to make the boot up screen the loading screen, like when you shut it off.
 When you get the blinking cursor, try pressing:
<CTRL>+<ALT>+<F7>
and if that doesn't work, try:
<CTRL>+<ALT>+<F1>

---

### Post by davidmohammed on 2011-02-26
sometimes you need to add the "framebuffer" to allow plymouth to work correctly.

try

```
sudo su

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

exit

```

---


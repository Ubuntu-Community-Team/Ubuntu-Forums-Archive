---
title: "Black Screen - tty1 flashing - 9.10 -"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by MehdizLinux on 2009-11-25
After Update, I restarted. After white Ubuntu logo, a small text is flashing (Computername tty1) and asking for username and password. Keyboard doesn't work fine to enter he UN and PW. Searched, No solution for similar cases!

Thanks.

---

### Post by cariboo on 2009-11-28
Try starting in recovery mode, hold down the shift key while booting. Then at the menu drop to a root prompt. Rename your /etc/X11/xorg.conf:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then at the prompt type:

```
exit
```

then choose Resume form the menu. This should get you back to your desktop.

---


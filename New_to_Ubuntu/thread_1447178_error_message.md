---
title: "error message"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by mrdusty on 2010-04-05
Hello,  complete newbie here.  I tried to download a couple  of games, and in the terminal I keep getting the following error: E: Directory '/var/log/apt/' missing
Could somebody please let me know  what I did wrong.
Acer Aspire One latest remix
Thanks,
  Richard

---

### Post by 3rdalbum on 2010-04-05
> **mrdusty said:**
> Hello,  complete newbie here.  I tried to download a couple  of games, and in the terminal I keep getting the following error: E: Directory '/var/log/apt/' missing
Could somebody please let me know  what I did wrong.
Acer Aspire One latest remix
Thanks,
  Richard

Did you delete /var/log/apt?

This command should, hopefully, fix the error:

```
sudo mkdir /var/log/apt
```

But I don't know why that directory was missing.

---

### Post by mizar001 on 2010-04-05
I suggest you to use 'add/remove programs' from Ubuntu menu (or 'ubuntu software center' if you have karmic).

In any case you can create the missing folder to solve your problem :
sudo mkdir /var/log/apt

---

### Post by mrdusty on 2010-04-05
3rdalbum and mizar01,
  Thanks for the quick reply. It seems to have taken  care of the problem, but...sometimes on booting  up, remix doesn't seem to remember my settings, I've adjusted my screen resolution the way it said in a previous thread, but when I boot,  either with my monitor on or off, I'll either lose the cursor, or it will boot into the 800x600 mode instead of 1024x600.
    Oh, I  downloaded clamav, and  it went fine,  but  I can't find it in any of my menus.
   Sorry for the problems,
    Richard

---


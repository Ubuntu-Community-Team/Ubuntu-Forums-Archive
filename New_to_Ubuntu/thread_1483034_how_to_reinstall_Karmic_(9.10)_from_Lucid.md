---
title: "how to reinstall Karmic (9.10) from Lucid"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-05-14
I have installed the Lucid version, and since then I haven't been able to make my soundcard work nor the xbmc.
If possible I would like to revert to the Karmic, could anybody give me some tips on how to do that...?

---

### Post by empty_spaces on 2010-05-14
You cannot roll back an upgrade, you need to do a fresh install of Karmic.
I would recommend trying to make the sound work before reinstalling Karmic
What is the output of **aplay -l** in the terminal?

---

### Post by northern lights on 2010-05-14
Please post the output of ```
sudo lshw -C multimedia && aplay -l
``` Thank you.

---


---
title: "hangs"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by jtmedin on 2009-06-30
I get hangs randomly with my notebook. Think it is hardware but in windows cntl+alt+del can get me out of it sometimes. Is there something like that in ubuntu? TIA

---

### Post by wpshooter on 2009-06-30
> **jtmedin said:**
> I get hangs randomly with my notebook. Think it is hardware but in windows cntl+alt+del can get me out of it sometimes. Is there something like that in ubuntu? TIA

Yes there is, it is call systems monitor.

But what you need to be concentrating on is discovering what the hardware problem is with you notebook, so that you do not have these hangs to start with !!!

---

### Post by beastrace91 on 2009-06-30
Not exactly, however you can just force an X restart (which would fix anything hanging that working in the graphical interface) do so with the following:

Press control+alt+f1 to drop down to a terminal loggin

Loggin and then run ```
sudo /etc/init.d/gdm restart
```

That will restart X and clear any running programs with out a full reboot.

~Jeff

---


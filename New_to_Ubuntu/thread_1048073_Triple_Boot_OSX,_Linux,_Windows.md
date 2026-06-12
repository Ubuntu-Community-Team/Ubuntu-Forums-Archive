---
title: "Triple Boot OSX, Linux, Windows"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by ankitguptag18 on 2009-01-23
i was able to boot to all three os using grub before.
then i formated my ubuntu, after a fresh installation grub shows only ubuntu and windows can any one say me how do i add osx in grub......

---

### Post by brsmits on 2009-01-23
```
sudo nano /boot/grub/menu.lst
```

It should be in there, you might have to uncomment it or something.  Similar thing happened to me after upgrading to Ibex with XP and Vista partitions.  If not, then talk to someone who really knows what they are doing.  ;)  [NOT me]

---

### Post by ankitguptag18 on 2009-01-23
i can only see ubuntu and windows in menu.lst
i cant see OSX

---

### Post by igknighted on 2009-01-23
Macs have funny bioses, I don't think grub works the same on them.  I used to run Ubuntu on an old ibook and had a lot of issues with the bootloader.  What are you using to boot windows, bootcamp?

---

### Post by ankitguptag18 on 2009-01-23
i am using grub to load windows.
i was using grub to boot OSX also. but after reinstalling ubuntu i can no longer do that.....

---

### Post by igknighted on 2009-01-23
> **ankitguptag18 said:**
> i have toshiba A10.
i am using grub to load windows.
i was using grub to boot OSX also. but after reinstalling ubuntu i can no longer do that.....

I don't think we can help with OSX on non-apple hardware issues here due to legal issues, sorry.

---


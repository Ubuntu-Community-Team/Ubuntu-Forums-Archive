---
title: "Probems with pendrives again, grrrr!!!!!"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Enkidux on 2009-07-27
:confused:

I have just re-installed xubuntu (I just don't know how many times already) everything seems to be working fine and when I plug a memory stick (both that I have) they don't mount, messages as follows pop up:

Failed to mount "7G volume"
the enclosing drive for the volume is locked.

What does this mean? what is locked? how do I change this, this is driving me NUTS!!! I used to be able to use the drives plug and play, but not anymore, Anyone knows why my computer doesn't like me anymore???

If it was our lovely Window$ i would think there might be a virus there, but with ubuntu would that be possible???

Help someone out there please!!!!!


thank you.

---

### Post by halitech on 2009-07-27
what format are the drives? I'm guessing NTFS and that they weren't cleanly unmounted before being removed from a computer

---

### Post by Enkidux on 2009-07-27
I have no clue, I used gparted to try to open them and not even that worked. 

i am trying to install UNR in my netbook using imagewriter, and while gparted and nautilus cannot open it, imagewriter seems to be able to write to it.... how come?

this is just super confusing. 

I really like ubuntu, but this mounting problems are a pain in the neck.

please any ideas anyone?

---

### Post by halitech on 2009-07-27
with the drive plugged in, open a terminal and post the results of
```
sudo fdisk -l
```and ```
lsusb
```

---


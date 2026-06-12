---
title: "Browse Network Files within Xubuntu"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Sugi on 2009-03-01
How do browse network files within Xubuntu?

Sugi


My Fix:
Installed nautilus and your ready to go.
$ sudo apt-get install nautilus

---

### Post by 73ckn797 on 2009-03-01
You have to install Samba from the repositories.

---

### Post by chrisod on 2009-03-01
Add Nautilus to Xbuntu. Xbuntu out of the box doesn't support browsing network files.

```
sudo apt-get install nautilus
```

Then select gnome on the login screen. Once you add links to network files on your gnome desktop they should be remembered and will still be there if you log back in under XFCE. At least it worked that way for my NAS drive.

---

### Post by Sugi on 2009-03-02
chrisod, the nautilus fix did it.  Thanks :D

73ckn797 and Chrisod I came from Ubuntu Hardy Heron using Gnome as my GUI and later installed XFCE.  So I was able to keep all my installed programs.

Thanks again,
Sugi

---


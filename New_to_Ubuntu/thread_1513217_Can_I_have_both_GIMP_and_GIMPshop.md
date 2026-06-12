---
title: "Can I have both GIMP and GIMPshop?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-19
So if I download GIMPshop, will it replace GIMP? I don't want to install it unless I'm sure.

---

### Post by Elfy on 2010-06-19
Appears that gimpshop installs to /usr/local/bin - gimp is in /usr/bin 
So it would seem that you could use either.

At least here - gimp in a terminal ran gimpshop, gimp in the menu ran gimp.

---

### Post by Legendary_Bibo on 2010-06-19
ah man, there doesn't seem to be an AMD64 version. :(

---

### Post by philinux on 2010-06-19
> **Legendary_Bibo said:**
> ah man, there doesn't seem to be an AMD64 version. :(

I would first install ia32libs from synaptic then to install gimpshop use this.

```
sudo dpkg -i --force-all package_name.deb
```

More info. Not sure if there's a newer version of getlibs out there.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---


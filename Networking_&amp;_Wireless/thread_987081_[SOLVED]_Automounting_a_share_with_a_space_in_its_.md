---
title: "[SOLVED] Automounting a share with a space in its name?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Prosis on 2008-11-19
I have to add a share in my fstab but it has a space in its name.  But given that it's at work and I can't ask them to remove the name because then it would force the whole company to change the configurations on their computers, I have to find a way.

I've tried:

```

//192.168.1.2/"Drop Box"    /media/share    smbfs     guest      0    0
//192.168.1.2/Drop\ Box    /media/share    smbfs     guest      0    0

```

to no avail.  I always get an error: [mntent]: line 18 in /etc/fstab is wrong

How to do it then?

Thank you!

---

### Post by sisco311 on 2008-11-19
```
//192.168.1.2/Drop**\040**Box    /media/share    smbfs     guest      0    0
```

**\040** = the ascii code of space (in octal)

---

### Post by Prosis on 2008-11-19
Oh dear can I kiss you, seriously ? :lolflag:

Thanks! :)

---


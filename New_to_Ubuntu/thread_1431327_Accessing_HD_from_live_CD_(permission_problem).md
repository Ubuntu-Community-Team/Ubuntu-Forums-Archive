---
title: "Accessing HD from live CD (permission problem)"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Yizi on 2010-03-16
My ubuntu is messed up and i need to reinstall but first i need to take my data out, i can mount the drive well but it gives me a ```
The folder contents could not be displayed, you do not have have the permissions
```

How do i give permission? i know the password.

---

### Post by undecim on 2010-03-16
If you mount the drive using the file browser, permissions shouldn't be an issue.

If you get permission errors anyways, you can press alt+f2 and type "gksu nautilus" to get a file browser as root. Just be careful in a root file browser because it makes it easy to break things.

---

### Post by Yizi on 2010-03-16
Worked! Thanks

---


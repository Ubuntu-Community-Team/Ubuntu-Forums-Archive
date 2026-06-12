---
title: "Is 64 Bit ubuntu compatible with 32 bit?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-25
Is 64 Bit ubuntu compatible with 32 bit software?

---

### Post by balaknair on 2009-03-25
If you're asking whether the packages you use for 32-bit Ubuntu can be installed on 64-bit, the answer in most cases is no. Most programmes/packages are available in both 32-bit and 64-bit versions, and the 32-bit version cannot be installed on the 64-bit Ubuntu, and vice versa. You will need to install the 64-bit version of the package on the 64-bit OS. Most packages will have a 64-bit version available, and some will have 'wrapper' packages that enable the 32-bit versions to run in the 64-bit OS(though this is not a perfect solution, in most cases it works).

---

### Post by jbrevik on 2009-03-25
If you want to force the 32bit program to install on amd64 arch:
```
sudo dpkg --force-architecture -i <filename>.deb

```

---

### Post by oldos2er on 2009-03-25
> **Gp. said:**
> Is 64 Bit ubuntu compatible with 32 bit software?

 You need the package 'ia32-libs'.

---

### Post by binbash on 2009-03-25
yes it does

---


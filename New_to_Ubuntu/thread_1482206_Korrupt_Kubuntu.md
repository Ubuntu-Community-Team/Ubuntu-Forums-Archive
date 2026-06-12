---
title: "Korrupt Kubuntu?"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-13
Did anyone notice this? or it's only me?

---

### Post by Zorael on 2010-05-17
Did you upgrade or install fresh? Make sure all packages are as they should.

```
$ sudo aptitude update
$ sudo aptitude install -f
$ sudo aptitude full-upgrade
```

Also try renaming your **~/.fonts.conf** file to something else, just incase it's messing with your fonts.

---

### Post by SKhan on 2010-05-19
> **Zorael said:**
> Did you upgrade or install fresh? Make sure all packages are as they should.

```
$ sudo aptitude update
$ sudo aptitude install -f
$ sudo aptitude full-upgrade
```

Also try renaming your **~/.fonts.conf** file to something else, just incase it's messing with your fonts.

fresh install with all the latest bug fixes. anyways i have solved this problem on my own.
problem in first image can be solved by clicking "i" button which in the right-most button of notification widget.
problem in the second image can be solved by right-clicking and clicking and choosing some appropriate option.

---


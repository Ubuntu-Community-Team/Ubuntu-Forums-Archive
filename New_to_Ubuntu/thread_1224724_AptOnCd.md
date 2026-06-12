---
title: "AptOnCd"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by MrWES on 2009-07-27
I want to use AptOnCd to make an iso of my installed packages, but unfortunately, I have issued an sudo apt-get clean and there for /var/cache/apt/archives is empty. Is there anyway to make apt redown the the packages so I can create the Apt cd?

Thanks,
Bill

---

### Post by credobyte on 2009-07-27
If you remember the list of applications:
```
sudo apt-get -d first_package second_package

```

---

### Post by unutbu on 2009-07-27
This howto ([http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)) shows you how to repack the packages that are installed on your system into .debs.

---

### Post by aesis05401 on 2009-07-27
*snip*

unutbu posted better advice above.

---

### Post by wojox on 2009-07-27
Simply drag-and-drop the package from Nautilus to APTonCD window.

edit: unutbus way would be easier.

---

### Post by MrWES on 2009-07-27
> **unutbu said:**
> This howto ([http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)) shows you how to repack the packages that are installed on your system into .debs.

Bingo! perfecto!

thanks

---


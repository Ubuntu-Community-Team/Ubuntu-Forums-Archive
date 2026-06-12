---
title: "Corrupted library file"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-23
I believe that one of my library files may be corrupted. I am not totally sure and that is why I am writing this question.

The compiler cannot access it during compile and linking and when I put the library file in the same directory as the source code (there is no way the compiler could not find it then) it still claims it cannot find it.

Hence, it must be corrupt. How can I test that?

Newport_j

---

### Post by anewguy on 2010-04-23
You may want to try posting this in the programming section as well, just in case there is something you are doing (or not doing) that they may be familiar with.

Dave ;)

---

### Post by Ravernomina on 2010-04-23
> **newport_j said:**
> I believe that one of my library files may be corrupted. I am not totally sure and that is why I am writing this question.

The compiler cannot access it during compile and linking and when I put the library file in the same directory as the source code (there is no way the compiler could not find it then) it still claims it cannot find it.

Hence, it must be corrupt. How can I test that?

Newport_j

It sounds corrupt... try reinstalling GCC, for C++ reinstall G++

---

### Post by newport_j on 2010-04-23
I think that this is a CUDA library, not a gcc library.

Newport_j

---


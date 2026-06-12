---
title: "configure can't find sed and sort"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by afhx on 2011-07-16
When running configure to install a program I repeatedly get the messages that sort and sed cannot be found. However, if I run a test  configure script   with macros to find sed and sort these macros succeeds  and yet these not found messages also appear.I has just followed a script to install gtk.php which appears in this forum and these two not found
messages appear. The installation succeeded. Any help would be appreciated

---

### Post by _0R10N on 2011-07-16
Did you try to install it as a superuser?

---

### Post by Bachstelze on 2011-07-16
What exactly are you trying to install? What exactly are the error messages?

---

### Post by afhx on 2011-07-17
An example. When trying to install pecl-cairo, following the instructions given by bastones in this forum, right at the end of the configure output its states:
can't find sed
can't find sort
Apparently, it installed alright.
However, as I stated by running my own test  configure script. using macros to find sed and sort these succeed, so autoconf can find these, yet right at the configure out put I still get the two messages above. I took some time to learn autoconfigure and at the end of writing numerous test programs I began to get these two messages. It happens nearly every time I run a confgure script. However, this did not happen when installing php-gtk. I have reinstalled autoconfigure to see if this would work but it didn't. I worried because sed is used a lot in configure scripts.

---


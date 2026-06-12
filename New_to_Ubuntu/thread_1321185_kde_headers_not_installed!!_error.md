---
title: "kde headers not installed!! error"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by wirelinux on 2009-11-09
I am using Karmic Kola, Intel Core Duo
 
i was trying to compile Kile, latex editor of KDE from source code.
when i ran the configure command
./configure --prefix=/usr --with-qt-dir=/usr/lib/qt4
The error obtained is

                          "checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!"

the path to KDE on my system was the  output of `kde-config --prefix` which was /usr.
So why i am getting this error even if i am specifying the correct prefix.

How to fix this error. Can somebody help me out in this regard???

Thanks in advance

---

### Post by ranch hand on 2009-11-09
Just a guess but do you have "KDE headers installed" in relation to your prefix?

---


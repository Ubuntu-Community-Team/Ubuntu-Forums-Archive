---
title: "symlink borken and how can i fix it"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by vinodhkumarvk on 2010-09-03
hie....

i have created a link

using vinodh@ubuntu : sudo ln -s /usr/local/korebot2-oetools-1.0/tmp/cross  ~/development/cross


but it is showing that the link is broken....

wen i checked the properties of the link file

in type : link (broken) (inode/symlink) ---------------its showing like this

and i have to do corss compilation from the development folder only !!!

so how can i fix the broken link

---

### Post by scorp123 on 2010-09-03
> **vinodhkumarvk said:**
>  using vinodh@ubuntu : sudo ln -s /usr/local/korebot2-oetools-1.0/tmp/cross  ~/development/cross  Anything you execute after ***sudo*** will be executed under the account of super-user _**root**_ ... and not your user ID. So guess where "*~/development/cross*" is pointing to? => to **root**'s folder, not your's. It would be better if you used absolute paths there, e.g. */home/whatever* (please replace with correct values) instead of ***~/*** 

How to fix: Simply delete the broken symlink and recreate it again.

---


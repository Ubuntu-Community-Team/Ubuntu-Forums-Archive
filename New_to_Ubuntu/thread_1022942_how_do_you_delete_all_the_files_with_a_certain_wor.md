---
title: "how do you delete all the files with a certain word in them"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Static_Flow on 2008-12-27
I was wondering how to delete all the files with the word wine in them i know how to find them all with locate wine but i want to delete them all in one swift line in stead of going to each and delete them individually.

---

### Post by iponeverything on 2008-12-27
wine in the name or wine somewhere in the content of the file?

There are easier ways to remove applications.. Try the --purge option with dpkg.

---

### Post by Static_Flow on 2008-12-27
wine in the name and how do you use purge

---

### Post by kaibob on 2008-12-27
I think this is really a bad idea because you will inevitably delete files that you do not want to delete and may end up with a computer that won't work. But...

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

> Another use of xargs is illustrated below.  This command will efficiently remove all files named core from your system (provided you run the command as root of course):

find / -name core | xargs /bin/rm -f
find / -name core -exec /bin/rm -f '{}' \; # same thing
find / -name core -delete                  # same if using Gnu find

---

### Post by Static_Flow on 2008-12-27
thank you if all goes worse then i cna just reinstall everything i don't have alot on here.

---

### Post by iponeverything on 2008-12-27
dpkg --purge <packagte>

---


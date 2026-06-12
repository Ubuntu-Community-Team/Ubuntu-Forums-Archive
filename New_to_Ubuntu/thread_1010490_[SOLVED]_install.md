---
title: "[SOLVED] install"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by allsys3 on 2008-12-13
how do i get and install software throught the terminal?

---

### Post by Epikuma24 on 2008-12-13
Code:

tar xzvf *.tar.gz

Will extract the file. Then 'cd' into the extracted directory. What you do next depends on what the file is. You might have to compile it, or it might be precompiled.

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Hospadar on 2008-12-13
Stuff in the repositories:

sudo apt-get install <name of package from repositories>


To search:
apt-cache search <search pattern>

---


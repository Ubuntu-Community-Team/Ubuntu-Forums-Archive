---
title: "$path"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by vipulkelkar on 2009-10-04
Hi guys
when we 
echo $PATH
what path does it display

---

### Post by ad_267 on 2009-10-04
It shows the contents of the PATH variable. This is a list of directories separated by colons where your shell will look for executable files when you run a command.

Eg when you run "echo", bash will look in /bin and find /bin/echo, so it runs that file.

For more info see [http://en.wikipedia.org/wiki/PATH_(variable](http://en.wikipedia.org/wiki/PATH_(variable))

---


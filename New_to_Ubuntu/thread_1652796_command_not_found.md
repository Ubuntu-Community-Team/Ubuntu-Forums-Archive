---
title: "command not found"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by Trandre on 2010-12-25
In a manual I read the following:
To determine which version of gcc you have on your system, run the following
command:
$ gcc --version


When I execute the command in terminal, I get the following response: 
XXX: ~$ $ gcc --version
$: command not found

What am I doing wrong?

---

### Post by lisati on 2010-12-25
In some tutorials, it is common to use the $ sign as a representation of the command prompt. The error message means that your system doesn't recognize the "$" command. Try the following instead:
```
gcc --version
```

---

### Post by Trandre on 2010-12-25
Thanx Lisati,that did the trick :-)

---


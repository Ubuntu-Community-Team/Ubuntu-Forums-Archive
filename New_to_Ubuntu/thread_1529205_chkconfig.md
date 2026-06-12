---
title: "chkconfig"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by chandrav23 on 2010-07-11
Greetings.

[SIZE=2]"chan@chan-desktop:~$ chkconfig --list bluetooth
bluetooth                 0 off  1 off  2 on   3 on   4 on   5 on   6 off[/SIZE]"

explain the below 
[SIZE=2]0 off  1 off  2 on   3 on   4 on   5 on   6 off

explain all these services 1 to 6???????

Thanks
[/SIZE]

---

### Post by Rubi1200 on 2010-07-11
What you see are runlevels (0-6)

Here is an explanation:

[http://www.skullbox.net/init.php](http://www.skullbox.net/init.php)

Also, in newer versions of Ubuntu, Upstart handles services:

[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

Use this code to see what is running:

```
 initctl list
```

---

### Post by chandrav23 on 2010-07-12
Hi Rubi,
 
Thanks for your info..

---


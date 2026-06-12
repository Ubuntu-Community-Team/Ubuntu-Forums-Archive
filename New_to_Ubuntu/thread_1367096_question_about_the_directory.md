---
title: "question about the directory"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by thungmail on 2009-12-29
Hi
I've just enrolled my finger and there is a message from terminal
```

ThinkFinger 0.3 (http://thinkfinger.sourceforge.net/)
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Please swipe your finger (successful swipes 3/3, failed swipes: 0)... done.
Storing data (/home/tuan/.thinkfinger.bir)... done.

```
I just check to see the directory name **(/home/tuan/.thinkfinger.bir)**,but I could not find it
Can any one tell me where it is 
Thanks
Tuan

---

### Post by waspbr on 2009-12-29
open a terminal window and type

```
locate .thinkfinger.bir
```

---

### Post by lotharmat on 2009-12-29
Are you trying to find it from nautilus (file manager) or from the terminal.

If it is the former; you will need to enable 'Show Hidden files' from the view menu.

if you are using the terminal; use:

```
ls -a
```

to show all files

---

### Post by Dayofswords on 2009-12-29
i think files/dir like ".blahware" are hidden by default.

---

### Post by lotharmat on 2009-12-29
Anything preceded by a dot *is* hidden by default if you follow the instructions in my previous post you will be able to see it.

---

### Post by thungmail on 2009-12-29
hi
Thanks for your all answers.
Tuan

---

### Post by glubbdrubb on 2009-12-29
If it works out then just mark this thread as solved please, using the "Thread Tools" at the top of the page.

---


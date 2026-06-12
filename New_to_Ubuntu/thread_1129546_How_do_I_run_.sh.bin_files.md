---
title: "How do I run .sh.bin files?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-18
I have a .sh.bin file. I changed the permissions to allow it to be executed, but I can still not run it. Any idea how to do this?

---

### Post by jbrown96 on 2009-04-18
Try to execute it from a terminal. Try ```
sh /PATH/FILE
``` or just ```
/PATH/FILE
```

---

### Post by xarquid on 2009-04-18
And just to confirm you changed the permissions to be executed you:

```
chmod +x file
```

Correct?

And the above should allow you to execute it.

Good luck!

---

### Post by alanfang on 2009-04-18
Yes, I did change the permissions as you said. When I try to execute from the terminal with

```
/home/user/file.sh.bin
```

it tells me

```
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 3011480458 is different from 1415825258

```

---


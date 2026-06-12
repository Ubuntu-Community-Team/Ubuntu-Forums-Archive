---
title: "Stop a terminal operation in progress?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by DigiTan on 2009-02-21
This is a real quick one: How do I interrupt a console command when it's taking too long.  So I don't have to totally close the console if I enter a command wrong or it hangs?

---

### Post by karlr42 on 2009-02-21
Simple answer- control-c on your keyboard. Sends a signal(SIGTERM?) to the program telling it to end. If that doesn't work, control-d is good too.

---

### Post by DigiTan on 2009-02-21
Thanks.  Looks like both of those work for me.

Are there any differences between the two I should know about?

---

### Post by snova on 2009-02-21
> **DigiTan said:**
> Thanks.  Looks like both of those work for me.

Are there any differences between the two I should know about?

Ctrl-C sends SIGTERM, which usually ends the process- but not if it specifically ignores it (which is uncommon).

Ctrl-D sends EOF, which closes its standard input- if the program was waiting for input, for example, this would tell the program to assume no further data will be available.

If you run out of ways to kill it, this will always work:

```
killall -KILL *<name of process>*
```

Such as 'firefox'. This sends SIGKILL, which cannot be blocked or ignored.

---

### Post by karlr42 on 2009-02-21
[This link](http://www.linuxforums.org/forum/linux-programming-scripting/119516-difference-bw-ctrl-c-ctrl-d-ctrl-z.html#post577886) seems to explain it all quite well. Just remember it's up to the programmer of the application to decide what(if anything) to do when the OS tells the app you pressed control-c.

---


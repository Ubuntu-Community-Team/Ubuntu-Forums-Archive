---
title: "quick question about terminal"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by tim1970 on 2009-03-12
I have noticed after using the terminal and I am ready to exit, sometimes when I type 'exit' the terminal window will close.  Other times instead of closing it will say 'There are stopped jobs'.  Then I have to type 'exit' again to close the window.

What is happening here? And I am using up CPU resources?


Tim

---

### Post by JPtux on 2009-03-12
I believe you were in the middle of running a program under the terminal. E.g. typing sudo nautilus then exiting

---

### Post by snova on 2009-03-12
> **tim1970 said:**
> I have noticed after using the terminal and I am ready to exit, sometimes when I type 'exit' the terminal window will close.  Other times instead of closing it will say 'There are stopped jobs'.  Then I have to type 'exit' again to close the window.

What is happening here? And I am using up CPU resources?

It means there are programs running in the background, or suspended. Since it may be potentially undesirable for these programs to suddenly exit, it asks first.

For example, this would run a command in the background:

```
command **&**
```

If you had done that for anything, it's probably still running, and it's reminding you of that.

---


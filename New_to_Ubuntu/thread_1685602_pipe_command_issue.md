---
title: "pipe command issue"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by thelebowski on 2011-02-10
Hello ubuntu forums,

I got a lay up for you here. Why does this command not work as I think it would:

cd Documents | ls

This will only list the content in my current directory. Why does it not change to the directory Documents and then list the content. I thought this was one of the simplest usages of piping. Any help would be appreciated, thanks.

Relevant info:
- running ubuntu 10.10
- bash shell

---

### Post by Old *ix Geek on 2011-02-10
That's kind of an unusual way to use piping. :confused:

If what you're after is changing to a different directory and then listing its contents, all with just one line of commands, try:
```
cd Documents ; ls
```

---

### Post by thelebowski on 2011-02-11
Alright that certainly works, thanks. I thought you could easily use the pipe this way though. Or maybe that is only true on the t-shell.

---

### Post by CharlesA on 2011-02-11
You use the pipe to send the output of a command to the command after the pipe. Since cd has no output there's nothing to do.

---

### Post by thelebowski on 2011-02-11
Alright cool. Thanks for the feedback

---


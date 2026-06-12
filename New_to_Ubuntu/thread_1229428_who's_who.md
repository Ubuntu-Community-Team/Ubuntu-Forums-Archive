---
title: "who's who"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by rumo59 on 2009-08-02
I've only been using Ubuntu 9.04 for a few days now and still experimenting so very sorry if this is normal.
Looking through this fantastic forum I've been trying out a few commands just to get the feel of the system and to see what the outcome is.
In the terminal I typed **who** to find who was on the system bearing in mind that I'm the only user, the result was:

myname  tty7  2009-07-28  08:06  (:0)

myname  pts/0  2009-07-28  08:43  (:0.0) 

Is this normal?

Thanks

---

### Post by hansdown on 2009-08-02
Hi rumo59.

My output is the same.

Welcome to the forum.

---

### Post by lotharmat on 2009-08-02
Is one the terminal and one Xorg?

---

### Post by rumo59 on 2009-08-02
I have no idea

---

### Post by Bodsda on 2009-08-02
> **rumo59 said:**
> I've only been using Ubuntu 9.04 for a few days now and still experimenting so very sorry if this is normal.
Looking through this fantastic forum I've been trying out a few commands just to get the feel of the system and to see what the outcome is.
In the terminal I typed **who** to find who was on the system bearing in mind that I'm the only user, the result was:

myname  tty7  2009-07-28  08:06  (:0)

myname  pts/0  2009-07-28  08:43  (:0.0) 

Is this normal?

Thanks

The first one is you, logged on in your gaphical display, the second is a pseudo terminal slave

---

### Post by rumo59 on 2009-08-02
Thanks Bodsda

Not sure what that means yet, but if its ok then thats fine

---

### Post by aesis05401 on 2009-08-02
Hello, 

You can open a terminal and do the following:
```

ps -e | less

```

The list of processes has three important columns.  The first is the PID, which means process id.  You can use this number to find out all sorts of info about a process in /proc/<pid>... but we don't need that extra info right now.. 

We want the second and fourth columns.  Any pty or tty being used within your scope is listed here and the process name is in the third column.

Use regular pgUp/pgDn keys to navigate the list and press shift+q to exit back to your prompt.

Does this help?

---

### Post by rumo59 on 2009-08-02
Thanks

I'm learning fast

---

### Post by aesis05401 on 2009-08-02
You are in the right place.

---


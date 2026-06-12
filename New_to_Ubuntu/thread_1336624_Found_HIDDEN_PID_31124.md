---
title: "Found HIDDEN PID: 31124"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by mlnease on 2009-11-24
Hello,

I've just run unhide and, for the first time, received a positive:  "Found HIDDEN PID: 31124".  I googled this a bit and checked the forums but didn't find anything particularly helpful.  Can anyone tell me if this is anything to worry about, or how to find out?

Thanks in advance.

mike

---

### Post by skatinjj on 2009-11-24
Would have to know the process name and/or where it is starting from.

Run:

```
ps aux | grep 31124
```

and post the results here.

PID is just the number given to the different processes that run on your machine, not very useful unless you know where it started from.

---

### Post by mlnease on 2009-11-24
> **skatinjj said:**
> Would have to know the process name and/or where it is starting from.

Run:

```
ps aux | grep 31124
```and post the results here.

PID is just the number given to the different processes that run on your machine, not very useful unless you know where it started from.

Thanks, Skatinjj,

Here's the output:

23993  0.0  0.1   3036   800 pts/0    R+   17:25   0:00 grep --color=auto 31124

Mean anything to you?  I'm afraid it doesn't to me.

mike

---

### Post by skatinjj on 2009-11-27
Sorry I have been away for a while.

No sure what tha all means.  I know my machine runs a few processes that look like that.

---


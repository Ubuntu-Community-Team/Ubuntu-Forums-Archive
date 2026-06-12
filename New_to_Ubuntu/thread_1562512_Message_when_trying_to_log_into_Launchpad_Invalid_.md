---
title: "Message when trying to log into Launchpad: Invalid OpenID transaction ???"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by mikodo on 2010-08-27
Hello everyone,

I have not been able to get into Launchpad today using Firefox. When I try to register, I get the following message:

```
Invalid OpenID transaction
```I cleared my cookies and cache in Firefox, thinking that might help, as I  read in another thread, when someone was getting this message with  Ubuntu One, clearing them fixed the problem.

I have to go, if anyone has any ideas, I'll try them later and report back in the thread.


Thanks.

---

### Post by jtarin on 2010-08-27
[Try this]("http://ubuntuforums.org/showthread.php?t=1444360")

---

### Post by mikodo on 2010-08-27
> **jtarin said:**
> [Try this]("http://ubuntuforums.org/showthread.php?t=1444360")
I think that solution is about Ubuntu One, is it not?

---

### Post by jtarin on 2010-08-27
That solution is about your problem with receiving that message. Both sites use launchpad...if I'm not mistaken.

---

### Post by mikodo on 2010-08-27
Thanks Jtarin,

I'll have to do more reading about it.

Mike

---

### Post by jtarin on 2010-08-27
Of course I don't know if it will work if your not using FF.

---

### Post by mikodo on 2010-08-27
> **jtarin said:**
> Of course I don't know if it will work if your not using FF.

Thanks again,

I'm using FF. I still can't see the solution from the thread. 

I'll leave it for now, maybe I am not seeing the forest for the trees.

Thank you.

---

### Post by jtarin on 2010-08-27
Trees removed...> Thanks for helping, but I fixed it with u1sync --authorize. Don't know why I had to do it that way.

For anyone else reading, login to Ubuntu One on the website, open a terminal and type
Code:

u1sync --authorize

Press enter and a window should open redirecting you to one.ubuntu.com, if you are already logged in. That should fix the problem.

Would it be a good idea to include the u1sync --authorize bit into the FAQ?

EDIT : Client works fine after updating and restarting.At the place you have difficulty just before.... execute.

---

### Post by mikodo on 2010-08-30
The solution to the question in this thread is found here: [http://ubuntuforums.org/showthread.php?t=1563205](http://ubuntuforums.org/showthread.php?t=1563205)

Thank you.

---


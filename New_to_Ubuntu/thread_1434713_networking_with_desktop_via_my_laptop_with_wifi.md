---
title: "networking with desktop via my laptop with wifi?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by PatrickMoore on 2010-03-20
I installed linux mint on my dad's computer for him and my brother. of course with me being the only one in the household that used linux before this i do all the updates and cleaning  etc. what i want to know is whether or not i can access my dad's computer via my wifi connection and perform all the maintainance needed  as opposed to having to drop what im doing and disrupt my brother or him while i do all the maintainance.  can this be done on a wireless connection?

---

### Post by cariboo on 2010-03-20
Probably the easiest way to do it is via ssh, install openssh-server on your dad's computer, then from your system issue the following command:

```
ssh <you>@server
```

Where <you> is your user name, and server is your dad's computer, this supposes that you can at least ping the other computer from your laptop. 

For more info, have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html").

---

### Post by 2hot6ft2 on 2010-03-20
Like cariboo907 said you can do it with SSH. Just make sure they don't shut down while you're in the middle of doing something like installing updates.

---


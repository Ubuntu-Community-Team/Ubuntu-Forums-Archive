---
title: "Ubuntu won't accept my password"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by stickman51 on 2008-12-12
Thanks to all the good people in this forum, I finally got Ubuntu installed. Looks like I have a new problem now; Ubuntu seems to be running find but it will not accept my password. I do not want a password and would prefer to be rid of it. But I cannot even get in if it won't accept my password. Any suggestions?

---

### Post by SuperSonic4 on 2008-12-12
What if you did ```
passwd <user>
``` and left it blank

---

### Post by halitech on 2008-12-12
what do you mean it won't accept your password? where are you trying to use it?

far as removing it, you may want to do some reading here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Iowan on 2008-12-12
Same website has info on [resetting password]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by Frogbarf on 2008-12-12
> **stickman51 said:**
>  . . . I do not want a password and would prefer to be rid of it. . . 

One of the big virtues of Linux is a Unix-like security system largely based on file permissions, which in turn depend on which user id you are logged in with.

My advice (free and unsolicited, admittedly, hence maybe unwelcome and not worth much anyway:twisted:) is to get into the habit of doing your routine day to day work using an ordinary unprivileged user id and save your privileged user id (the one you set up during install) for system maintenance tasks.

And always use a password when you log on. At the moment Linux is afflicted with few trojans and viruses and little malware, but that situation could change overnight, and then making sure you fully use the security features may make a big difference.

Already, if your machine is used by more than one person, proper setup and use of user ids and passwords is important.

In the long run, you'll be happier if you form good habits now.

---


---
title: "Running startup program as a different user"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by DevilWithin on 2009-11-13
Hi all,

So I know how to run a program as a different user; and I know how to creat a startup program (under the preference).  But is there a way to combine the two?  Basically I have my ubuntu set to auto login as one user.  However I want a specific program run at the startup as a different user. Perhaps there's a one line command I can put into the startup program option?  Thanks.

---

### Post by sisco311 on 2009-11-13
It's a CLI or a GUI app?

---

### Post by DevilWithin on 2009-11-13
> **sisco311 said:**
> It's a CLI or a GUI app?
It's a gui app.  Ktorrent actually.

---

### Post by falconindy on 2009-11-13
In order to run a program as a user that isn't logged in, you need elevated permissions. 'sudo -u <user> <program>' is the proper way to do it.

---

### Post by DevilWithin on 2009-11-13
Thanks.
But how can I put that command into the startup program option, along with the password?
AFAIK, there isn't a parameter in the SU command that allows me to include the password.

---

### Post by falconindy on 2009-11-13
> **DevilWithin said:**
> Thanks.
But how can I put that command into the startup program option, along with the password?
AFAIK, there isn't a parameter in the SU command that allows me to include the password.
That's just it. Assuming I understand what you're doing (run KTorrent nonstop regardless of who is logged in) it's going to be difficult to do cleanly. I don't want to use the word 'impossible', but it's close. Best bet would be to look into a torrent client that can be run as a daemon.

---


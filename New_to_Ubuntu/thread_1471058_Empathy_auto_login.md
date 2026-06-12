---
title: "Empathy auto login"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by pjones0404 on 2010-05-03
I select the option in empathy to auto login at startup but it is not working. I would like to keep it in the menu at the top but would like it to auto login. Do i need to manually add it to the start up application? 

By the way I am running 10.4.

---

### Post by RedRecidivist on 2010-05-20
I'd like to know the answer to this too...

---

### Post by tagbre on 2010-05-22
Same problem here....

---

### Post by -humanaut- on 2010-05-22
What chat service are you running I've only run into this problem with Yahoo

---

### Post by RedRecidivist on 2010-05-22
Only MSN (Windows Live) for me...

I'm not with that PC to check it right now, but I think the problem is that Empathy is not starting at all - despite being configured to - it's not just that it's failing to log-in.

---

### Post by hannaman on 2010-05-23
Somewhere in these forums, it is explained that the option in Empathy only auto-connects to the internet on startup and does not do auto log-in.  To do the auto log-in, I added the command "empathy -h" to Startup Applications.  The -h option starts Empathy in hidden mode, so no dialogs show up.

---

### Post by RedRecidivist on 2010-05-23
That works, of course, but it's a bit of a botch! :)

Thanks for taking the time to answer though.

---

### Post by bluepicaso on 2011-01-02
Doesn'w work for me at all. i have to open it and select available from the status. then it starts loging in all accounts
:mad:

---

### Post by LordNodens on 2011-05-06
> **hannaman said:**
> Somewhere in these forums, it is explained that the option in Empathy only auto-connects to the internet on startup and does not do auto log-in.  To do the auto log-in, I added the command "empathy -h" to Startup Applications.  The -h option starts Empathy in hidden mode, so no dialogs show up.

Thanks a lot! This works!

---


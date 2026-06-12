---
title: "How do i stay logged in as sudo for a session?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mech7 on 2009-01-14
I have to do setup and it is very tiring typing sudo everytime, is there anyway to have the shell session stayed logged in as sudo as long as i not close?

---

### Post by Samalama on 2009-01-14
I believe the command you're looking for is
```
Su
```

---

### Post by bullgr on 2009-01-14
type in the terminal:

su

and enter the root password as requested and you will still remain root as far you close the terminal window...

---

### Post by jowilkin on 2009-01-14
I think su will only work if you have a root password setup.  If you do ```
sudo -s
```, I think that will always work.

---

### Post by Joeb454 on 2009-01-14
> **jowilkin said:**
> I think su will only work if you have a root password setup.  If you do ```
sudo -s
```, I think that will always work.

I've had issues using sudo -s before, because it keeps your environment profiles, and if you're not careful, it can end up changing permissions to items in your home directory.

Use ```
sudo -i
``` instead, it'll take roots environment variables, but other than that, is essentially the same as sudo -s :)

---


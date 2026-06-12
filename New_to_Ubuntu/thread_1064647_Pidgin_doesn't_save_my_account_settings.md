---
title: "Pidgin doesn't save my account settings"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by rausuar on 2009-02-09
Hi all,

I recently reinstalled my Ubuntu 8.10, and now, I cant get Pidgin 2.5.4 or earlier to save my account settings, which means that everytime I open Pidgin it asks me to add an account.

Any idea to this? I am using the latest updates...

att... RAUL

---

### Post by konqueror7 on 2009-02-09
how do you reintsall pidgin? could you try purging all it configuration file, then reinstall it, see if it works....

```
sudo apt-get autoremove --purge pidgin
```

---

### Post by rausuar on 2009-02-09
> **deuphil.kaufmann said:**
> how do you reintsall pidgin? could you try purging all it configuration file, then reinstall it, see if it works....

```
sudo apt-get autoremove --purge pidgin
```

It seems your solution worked!!! thanks!!!! (to be sincere, I am not very familiar with Ubuntu commands)...!

---

### Post by konqueror7 on 2009-02-09
no problem, glad it worked...you could try reading the offered tutorial of this forum...[here]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Resources")

---

### Post by juanbretti on 2009-03-02
Where does Pidgin saves its preferences?

I mean, where is the file that contains all the saved preferences and settings?

Thanks!

---

### Post by flyfox81 on 2010-05-07
Well, I guess it's a bit late for a response, but I just had that problem, and I managed to fix it. In the home directory, find the .purple directory. Check the permissions. Cheers

---


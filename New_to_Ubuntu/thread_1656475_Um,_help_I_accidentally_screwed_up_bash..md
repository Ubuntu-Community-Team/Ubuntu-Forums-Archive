---
title: "Um, help? I accidentally screwed up bash."
date: 2010-12-30
forum: New to Ubuntu
---

### Post by skooterz on 2010-12-30
EDIT: Never mind, I think I've solved it myself. I used PATH=$PATH: to re-add /bin/ and /usr/bin.

What happened was, I apparently remembered the command for setting your bash path wrong - I think I used "export PATH=$PATH: ~/bin" and apparently that was the wrong thing to do, because at first it wasn't finding ANY commands - I'd try and use "man" and it would give me "bash: man: no such file or directory". Next I tried setting things back the way they were with PATH= $PATH:/bin/bash/, but now only some commands work. e.g: "ls" does not work, though it tells me where it is. Is there any way to fix this without reinstalling? Please respond quickly.

---

### Post by cariboo on 2011-01-01
I marked the thread solved for you.

---

### Post by skooterz on 2011-01-01
> **cariboo907 said:**
> I marked the thread solved for you.

Thank you.

---

### Post by QLee on 2011-01-01
And, just so you'll know, skooterz, ~/bin (the /bin that you can create in your user home folder) is by default in the user's path, if the directory exists, no need to change the path, it is added when you log in.

---

### Post by skooterz on 2011-01-02
> **QLee said:**
> And, just so you'll know, skooterz, ~/bin (the /bin that you can create in your user home folder) is by default in the user's path, if the directory exists, no need to change the path, it is added when you log in.

I see. I did not know that. I always assumed you would have to add it, given that it is not there initially.

---


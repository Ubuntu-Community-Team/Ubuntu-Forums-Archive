---
title: "/home in Windows"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Oxwivi on 2010-12-01
Someone suggested I use some sort of ls functionality if I want my /home directory of Ubuntu with the one in Windows in dual-boot.

What do you guys know?

---

### Post by v1ad on 2010-12-01
uh.. that is not possible.

ls stands for list directory. it is a command that you would use in a command prompt, it will show u whats in the directory. they run on different formats. i don't understand why would you want them in the same directory.. unless you are using wubi

---

### Post by Oxwivi on 2010-12-01
I would want them in the same directory, cause I want to access them from both Ubuntu and Windows without having to waste space having the copies of the same files.

---

### Post by philinux on 2010-12-01
> **Oxwivi said:**
> I would want them in the same directory, cause I want to access them from both Ubuntu and Windows without having to waste space having the copies of the same files.

Then I wold suggest a shared NTFS partition.

Thread moved to ABT forum.

---

### Post by HurricaneHarry on 2010-12-01
It's not good having the windows user directory mixing with /home/username.
The suggestion of having your /home/user on an NTFS partition is no good either since the permissions scheme differs a lot.

The best way would in my opionion be to have a shared partition between the both, possibly using ntfs where you would keep the shared files.

Another option would be using something like dropbox or other cloud-storage to sync files between the different OSes wich has the benefit of a backup at hand.

---

### Post by bcbc on 2010-12-01
I think you mean "ln" not "ls". You want to link e.g. your ~/Pictures with /host/users/..../My Pictures?

---

### Post by Oxwivi on 2010-12-02
> **HurricaneHarry said:**
> The best way would in my opionion be to have a shared partition between the both, possibly using ntfs where you would keep the shared files.
How can I do that?
> **bcbc said:**
> I think you mean "ln" not "ls". You want to link e.g. your ~/Pictures with /host/users/..../My Pictures?
Yep.
> **philinux said:**
> Then I wold suggest a shared NTFS partition.

Thread moved to ABT forum.
Please move it back, I'm neither a beginner, nor seeking support.

---

### Post by bcbc on 2010-12-02
[http://ubuntuforums.org/showthread.php?t=1527106](http://ubuntuforums.org/showthread.php?t=1527106)

---


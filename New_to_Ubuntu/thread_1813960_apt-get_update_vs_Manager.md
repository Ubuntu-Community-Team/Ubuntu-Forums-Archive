---
title: "apt-get update vs Manager"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Arcken on 2011-07-28
Hey guys i have one question... I am using ubuntu 10.10 right now , and tried to update using the terminal with **apt-get update** and** apt-get upgrade,  **and it showed less updates than **Update Manager**. Is this because the apt ignore obsolete or something like that?

---

### Post by lkjoel on 2011-07-28
> **Arcken said:**
> Hey guys i have one question... I am using ubuntu 10.10 right now , and tried to update using the terminal with **apt-get update** and** apt-get upgrade,  **and it showed less updates than **Update Manager**. Is this because the apt ignore obsolete or something like that?
Try this instead:
```
sudo apt-get update
sudo apt-get **dist-**upgrade
```
This will upgrade all packages.
You can also try:
```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by Arcken on 2011-07-28
> **lkjoel said:**
> Try this instead:
```
sudo apt-get update
sudo apt-get **dist-**upgrade
```This will upgrade all packages.
You can also try:
```
sudo aptitude update
sudo aptitude full-upgrade
```

Ok , but is this the equivalent to what Manager do? Sorry for the newbie question hehe :P

---

### Post by lkjoel on 2011-07-28
> **Arcken said:**
> Ok , but is this the equivalent to what Manager do? Sorry for the newbie question hehe :P
If you are talking about the Update Manager, then yes. The Update Manager is simply an interface for apt-get.

---

### Post by Arcken on 2011-07-28
Ty :D

---

### Post by lkjoel on 2011-07-28
No problem!
Could you mark this thread as solved? Thread tools->Mark this thread as solved

---


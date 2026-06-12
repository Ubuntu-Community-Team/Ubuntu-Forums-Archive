---
title: "Running a script from another directory?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by BassKozz on 2009-01-23
How can I run a script from another directory?

For example:
If I am in the directory that the script is in, I can run:
```
./scriptname
```
and that works fine, but if I am in another directory I can't run the script even if I type in the full path, like so:
```
./home/username/folder/scriptname
```
I get the following error when trying the above:
> -bash: ./home/username/folder/scriptname: No such file or directory

So how can I run that script when I am not in the directory where the script resides?

---

### Post by mjheagle8 on 2009-01-23
no '.' before './home/username/folder/scriptname'

---

### Post by dawynn on 2009-01-23
'./' indicates to use the current directory.  More periods would indicate stepping into the parent folders further and further.  So '../' would indicate the parent directory for the folder you're currently in.

Ex. if you're in your /home/username/folder directory, indicating a script with a prefix of ./ would indicate the /home/username/folder directory, but ../ would indicate the /home/username directory.  .../ would indicate the /home directory, etc.

Assuming you're in your /home/username/folder directory, and you try to run ./home/username/folder/scriptname, what you are really asking for is /home/username/folder/home/username/folder/scriptname.

Long story short: you want to specify the full path starting from the forward slash.  Leave off the period.

Instead of ./home/username/folder/scriptname
use /home/username/folder/scriptname

---

### Post by BassKozz on 2009-01-23
Awesome, Thanks Guys.

I would give "Thanks" and mark this thread as "Solved" if I could ;-P

---

### Post by Malalo on 2009-01-23
You could edit your first post and change the title, changing it to "[SOLVED] Running a script from another directory?"...

---

### Post by mjheagle8 on 2009-01-23
no problem, glad i could help you.

---

### Post by BassKozz on 2009-01-23
> **Malalo said:**
> You could edit your first post and change the title, changing it to "[SOLVED] Running a script from another directory?"...

Done :D

---


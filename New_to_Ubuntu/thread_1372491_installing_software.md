---
title: "installing software"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by hell_tsh on 2010-01-04
i ain't new to ubuntu... but 1 of my friends laptop is driving me crazy. i've installed 9.10 in his machine using _wubi_ and it just won't let install any software.... i tried using both software centre and terminal (sudo apt-get install <whatever>), while on my laptop, i installed ubuntu on a complete disk n the thing just rocks! any suggestions/solution??

---

### Post by audiomick on 2010-01-04
You have checked that the machine has an Internet connection?

---

### Post by howefield on 2010-01-04
What is the error, why can't you install software ?

Try a 

```
sudo apt-get update
```

from the terminal and try again.

---

### Post by doas777 on 2010-01-04
what error are you getting specifically, and when you run apt-get, are softwarecenter and synaptic closed and update manager all closed? you can only use one of the above at any given time. 

close them all, reboot, and run:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by lotharmat on 2010-01-04
> **howefield said:**
> What is the error, why can't you install software ?

Try a 

```
sudo apt-get update
```

from the terminal and try again.


Paste the results from this..

---


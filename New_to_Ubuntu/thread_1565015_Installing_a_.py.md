---
title: "Installing a .py"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by steck638 on 2010-08-31
I am not exactly new to Ubuntu, but I am new to installing programs with the command prompt. I found a cool looking system monitor called Manometer and figured I could use the practice installing stuff, but it has a .py file instead of the tarball I was expecting. Now (after a bit of looking around online) all I have found is its a python file and something about it just working (but it dosnt).

When (and if) you want me to use the terminal please realize I have very little experience with it so far.

---

### Post by LowSky on 2010-08-31
welcome to the forums

I just looked up the application. it runs using an application called Screenlets (its in the repos and very easy to install from the software center too)

---

### Post by steck638 on 2010-08-31
That was easier than I thought it would be, Thanks :D


So next time I run into a .py instillation file what should I do with it?

---

### Post by CharlesA on 2010-08-31
It's a python script, so you would have to run it with python.

```
python /path/to/script.py
```

---

### Post by limestone on 2010-08-31
> **CharlesA said:**
> It's a python script, so you would have to run it with python.

```
python /path/to/script.py
```

Or if the script contains #!/usr/bin/python, you could just run ./file.py
If the file won't run try change mode with, chmod +x file.py first.

---

### Post by CharlesA on 2010-08-31
> **pont.andersson said:**
> Or if the script contains #!/usr/bin/python, you could just run ./file.py
If the file won't run try change mode with, chmod +x file.py first.
Good point. I normally only run shell scripts with ./path/to/script.sh. For perl and python I use the program name.

Thanks.

---

### Post by da burger on 2010-08-31
> **steck638 said:**
> That was easier than I thought it would be, Thanks :D


So next time I run into a .py instillation file what should I do with it?

I don't think they're that common (I've never seen one before) but if you do run into one, look around on the source site for instructions. A .py script is just like a .sh script except in a different language so it could really be anything. However as a general rule I would say that if you have all the dependencies installed and then just run the script that will either launch the application or install it depending on what the script was designed to do.

Angus

---

### Post by steck638 on 2010-08-31
I tend to only run into the stuff thats rare and hard to deal with :P

So just read the page I download it from, install everything it needs and it should work fine, thanks :D

---


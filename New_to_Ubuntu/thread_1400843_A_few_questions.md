---
title: "A few questions"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by mshtet on 2010-02-07
I switched to Ubuntu a few days ago, and I have a few questions.

I use Chrome beta as a web browser, and I can't "do anything" with the stuff that uses Flash. For example, I can't click the pause/play buttons in Youtube Videos. I have the Adobe version. I also find the same problem using Firefox.

I can't play .mpg or .wmv videos using the movie player. Any help?

Thanks in advance.

---

### Post by mushwars on 2010-02-07
you need to uncomment your restriced repositories from /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```

then you need to 

```
sudo apt-get install w32codecs ubuntu-restricted-extras
```

---

### Post by Gone fishing on 2010-02-07
Add the restricted extras (this can be done in System> Administration > Software Sources.)

I'd then then go here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the instructions

---


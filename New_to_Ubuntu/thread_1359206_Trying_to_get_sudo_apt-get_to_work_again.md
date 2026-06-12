---
title: "Trying to get sudo apt-get to work again"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by soulpanda on 2009-12-19
Hi,
      I'm trying to use the magical 'sudo apt-get' feature of ubuntu and I'm getting this message 

E: Type 'sudo' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I don't know what I did, and I'd really like to be about to install things on my computer again. Thanks for your help.

---

### Post by Grenage on 2009-12-19
My guess is that you accidentally modified you sources file.

```
gksu gedit /etc/apt/sources.list
```

Check the line mentioned and fix it.  It shouldn't be mentioning sudo at all.

---

### Post by snowpine on 2009-12-19
You can edit your sources thus:

```
gksu gedit /etc/apt/sources.list
```

If you're not sure what the problem is with line 36 (usually it's pretty obvious), you can copy & paste here.

---

### Post by soulpanda on 2009-12-19
Ok, here's line 36

sudo apt-key add - && sudo apt-get update

If the problem is obvious, well, I'm sorry, I'm still
at the absolute beginner stage. If there's something
wrong here, then I wouldn't know.

---

### Post by snowpine on 2009-12-19
> **soulpanda said:**
> Ok, here's line 36

sudo apt-key add - && sudo apt-get update

If the problem is obvious, well, I'm sorry, I'm still
at the absolute beginner stage. If there's something
wrong here, then I wouldn't know.

You should delete that line. It has no place in an /etc/apt/sources.list file. :)

---

### Post by soulpanda on 2009-12-19
Thanks! 
That worked like a champ.

---

### Post by 3rdalbum on 2009-12-19
In future, add repositories using the Software Sources program rather than by manually editing the sources.list file.

It prevents any mistakes like this.

---


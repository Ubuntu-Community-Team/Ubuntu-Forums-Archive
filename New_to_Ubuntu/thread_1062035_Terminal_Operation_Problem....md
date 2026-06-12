---
title: "Terminal Operation Problem..."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-06
I am trying to install the highlighted file below and I have taken a picture of the commands I have tried. Please tell me what I am doing wrong...I can not seem to find the Python-3.0 folder...

---

### Post by pritamps on 2009-02-06
> **Leo Dragonheart said:**
> I am trying to install the highlighted file below and I have taken a picture of the commands I have tried. Please tell me what I am doing wrong...I can not seem to find the Python-3.0 folder...

Your home directory would be /home/leo and not just /home. Basically, each user (even if there is only one) has a directory with his chosen name in /home.

So you would access the Python-3.0 directory with 

```
cd /home/leo/Python-3.0
```

You could use tab completion (pressing tab when you write only part of the name) and the computer will try to figure out what directory you're trying to get to.

Another way to get your home from anywhere is the ~...i.e. typing

```
cd ~
```

would get you to the home directory of whoever is logged in now.

Hope that helps!

---

### Post by taurus on 2009-02-06
Remove the / in front of the name, Python-3.0 if you are in your $HOME or.

```
cd ~/Python-3.0
```

---

### Post by Leo Dragonheart on 2009-02-06
Thanx guys it worked perfectly....:-)

---


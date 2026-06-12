---
title: "apt-get vs aptitude?"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-02-20
What exactly is the difference between apt-get and aptitude?

---

### Post by falconindy on 2010-02-20
apt-get has super cow powers.

---

### Post by NightwishFan on 2010-02-20
Aptitude is a front end for apt-get. I believe aptitude is better at handling dependencies. It also has a ncurses interface for displaying graphics on a TTY or terminal emulator. Just type "sudo aptitude" in a terminal to see what I mean. Personally I recommend that you use aptitude.

[http://en.wikipedia.org/wiki/Aptitude_%28software%29](http://en.wikipedia.org/wiki/Aptitude_%28software%29)

The normal syntax for aptitude is similar to apt-get. Such as:
```
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude install *packagename*
```

---

### Post by Ozymandias_117 on 2010-02-20
@falconindy:
Personally, I prefer the snake eating the elephant. :p

@NightwishFan
Alrighty, I'll start trying it instead, thanks.

edit: If aptitude is better at dependencies and uses ncurses, why are new users still told to run commands like "sudo apt-get install "? If it's superior, wouldn't it make more sense to tell them "sudo aptitude install "?

---


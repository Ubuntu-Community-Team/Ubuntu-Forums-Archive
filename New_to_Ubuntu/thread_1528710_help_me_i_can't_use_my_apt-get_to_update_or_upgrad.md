---
title: "help me i can't use my apt-get to update or upgrade"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by jellay17 on 2010-07-11
when I use the terminal to update this keep showing up "type 'wget'
is not known on line 45 in source list /etc/apt/sources.list"

how can I stop that wget? I cant update my system.. please help me.. thank you in advance..

---

### Post by jellay17 on 2010-07-11
whenever I used apt-get that wget warning always shows up.. help me please.. :( I can't even install applications from ubuntu software center.. :((

---

### Post by overdrank on 2010-07-11
> **jellay17 said:**
> when I use the terminal to update this keep showing up "type 'wget'
is not known on line 45 in source list /etc/apt/sources.list"

how can I stop that wget? I cant update my system.. please help me.. thank you in advance..

Hi and welcome, your source list has been edited and thus the  error message. 
You will need to correct the source list and the [RepositoriesUbuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") should help. :)
You may use this command in the terminal to edit your source list.
```
gksu gedit /etc/apt/sources.list

```


Moved to  Absolute Beginner Talk

---

### Post by jellay17 on 2010-07-11
weeeeeeeeee a big thanks to you sir.. :D done fixing it.. thanks a lot..

---

### Post by Pizack on 2010-07-11
> **jellay17 said:**
> weeeeeeeeee a big thanks to you sir.. :D done fixing it.. thanks a lot..

please mark as solved.

---


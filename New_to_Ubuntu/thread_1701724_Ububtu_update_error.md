---
title: "Ububtu update error"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by go2xraj on 2011-03-06
I am getting following error on update, please help me

E: Type 'sudo' is not known on line 60 in source list /etc/apt/sources.list
E: Unable to lock the list directory

---

### Post by Iowan on 2011-03-06
Have you checked contents of */etc/apt/sources.list* (especially line 60)?

---

### Post by go2xraj on 2011-03-06
I am a beginner i dont know how to do it, please help me

---

### Post by JBAlaska on 2011-03-06
Open a terminal and do:
```
gksu gedit /etc/apt/sources.list
```
Look at line 60 and if it has sudo, comment the line with a # at the begining, save, close gedit, and do:
```
sudo apt-get update
```

---

### Post by go2xraj on 2011-03-06
its done. Thank you very much

---


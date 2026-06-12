---
title: "Help, cannot log in"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Remmpa on 2009-05-02
I changed my password as usual. Then I left my computer and the screensaver went on. When I got back the appearance had changed and it askes for my username. I have no idea what this could be, since I haven´t had the need to use it before. Log-in previously only asked and showed password.
 
Please, can someone help me. I have no idea how to get into my computer now.
 
For the swedish, om det finns någon som kan förklara det på svenska så skulle jag vara jättetacksam.

---

### Post by Remmpa on 2009-05-02
bump

---

### Post by Jazzy_Jeff on 2009-05-02
You should have created a username when you installed Ubuntu. I have to put mine in each time I log in.

---

### Post by cariboo on 2009-05-02
Your user name is the same as the name of your home directory. If you don't remember what the name of your home directory is you could start in rcovery mode, at the menu drop to a root prompt and type:

```
cd /home
```

then

```
ls -l home
```

you should get a listing that looks something like this:

```
ls -l
total 12
drwxrwxrwx  7 root root 4096 2009-04-24 09:37 internal
drwxr-xr-x 52 jimk jimk 4096 2009-05-02 13:52 jim
drwxr-xr-x  4 root root 4096 2009-04-27 14:37 storage
```

as you can see my home directory is called jim.

---

### Post by Remmpa on 2009-05-05
Thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:popcorn:

---


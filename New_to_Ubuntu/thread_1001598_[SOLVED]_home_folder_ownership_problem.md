---
title: "[SOLVED] home folder ownership problem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by kloyde on 2008-12-04
i recently re-installed Ubuntu Hardy due to cd problems. in order to back pu my data, i simply copied the home folder and saved it to an external hard drive. when i reinstalled Ubuntu, i replaced the default home folder with the one i saved, but now every time i log in i recive this message: "User's $HOME/. folder dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $HOME directory must be owned by user and not writable by other users."  and when i go into Permission on home, i cant set the permission because i don't own the file. how do i fix this?

---

### Post by Peter09 on 2008-12-04
You will need to do it with administrator privileges. Use sudo to do this. If you have a GUI the you could run in a terminal

```
sudo nautilus
```

this will run nautilus with admin rights.

---

### Post by Dedoimedo on 2008-12-04
Hello,

Do this:

```
sudo chown yourname:yourname /home/yourname/* -R
```

Dedoimedo

---

### Post by kloyde on 2008-12-06
> **Peter09 said:**
> You will need to do it with administrator privileges. Use sudo to do this. If you have a GUI the you could run in a terminal

```
sudo nautilus
```

this will run nautilus with admin rights.

well, that got rid of the message at startup. Thanks alot for your input!!

---


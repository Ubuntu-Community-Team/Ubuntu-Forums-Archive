---
title: "root terminal not working properly."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-04-25
as stated my root terminal won't load. If i go to it manually it won't load after i put in my password. If i do the alt+f2 and then type gksu and then something else that won't load either. So what is going on with ubuntu i dare ask?

---

### Post by Sidewinder1 on 2009-04-25
Try:
```
gksudo nautilus
```
instead of gksu...
Not sure exactly what you're trying to access, but usually gksudo opens graphical programs with root privileges.
HTH, Side

---

### Post by lovelyvik293 on 2009-04-25
root terminal????

---

### Post by Sidewinder1 on 2009-04-25
Shhhh...([SIZE=1]thin[/SIZE]k he means su...) Shhh... Didn't hear it from me...

---

### Post by 133794m3r on 2009-04-25
woops also i put in gobuntu instead of ubuntu. And what do you mean i mean su >.> there is an application called specifically "Root Terminal" under system tools. In Ubuntu.

---

### Post by adult swim on 2009-04-26
i dont think the root terminal works in ubuntu
you want one, run ```
sudo -i
```

---

### Post by llamabr on 2009-04-26
Ubuntu users, for whatever reason, are discouraged from running terminal applications as root.

What exactly are you trying to do, and what error do you get?

---

### Post by 133794m3r on 2009-04-26
before i was trying to delete an install of PlaneShift that i installed as root and later found out i could never use so i wanted to delete it and i'm done with it now. And I'd like to know why root terminal is not working currently.

---


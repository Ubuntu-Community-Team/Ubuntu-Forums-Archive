---
title: "problems saving in /etc"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by sbu on 2009-10-09
I am trying to save a *.conf* file in the */etc* directory using a text editor (running in ubuntu 9.04). But i keep on getting a message saying i cannot save in the folder */etc* because i do not have permission. 

I am the only user.can any 1 tell what must I do to save a .conf file in the /etc?

---

### Post by JoelOFH on 2009-10-09
you need to gain root access. try using the su command to do such.

---

### Post by kiridude on 2009-10-09
open /etc as root

---

### Post by bruce2000 on 2009-10-09
start your text editor with sudo permission

ie for gedit type this in a terminal: gksu gedit filename

or for nano: sudo nano -w filename

---

### Post by kiridude on 2009-10-09
simplest way for you:
```
gksudo nautilus
``` 

then just point and click

---

### Post by CatKiller on 2009-10-09
> **JoelOFH said:**
> you need to gain root access. try using the su command to do such.

*su* won't work; you cannot (by default) log in as root on Ubuntu.

*sudo* is what you'd use. More info [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by sbu on 2009-10-11
Thank you! I will try that...

---

### Post by ChildOfMana on 2009-10-11
[quote="kiridude"]simplest way for you:
Code:

gksudo nautilus

then just point and click[/quote]

If you're going to do it this way then be *very* careful what you're pointing and clicking on.

Safer to just do ```
sudo gedit /etc/filename.conf
```

That way if you mess up you only risk messing up the one file.

---


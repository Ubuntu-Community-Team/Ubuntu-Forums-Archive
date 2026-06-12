---
title: "permission to save change to file /etc/apt/sources.list file"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by oconnor on 2009-06-21
I'm using jaunty:
All I want to do is add a line to this file:
/etc/apt/sources.list 
But it complains about a permission.  I open the file with text editor.  I'm using jaunty.  I'm the only person using this machine.  It only has one username/password.  What is going on?  

I looked in the System->Administration->Authorizations but I've never touched anything in there before and I really don't know what I'm doing...

Thanks

---

### Post by spiderbatdad on 2009-06-21
open your editor with sudo command. For example:
```
gksudo gedit /etc/apt/sources.list

or

sudo nano /etc/apt/sources.list
```

---

### Post by CatKiller on 2009-06-21
For a description of why it is the way it is, read [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Paqman on 2009-06-21
You don't actually have to edit that file manually on Ubuntu, just go to System > Admin > Software sources > Third Party Software and add your new repo there.

---

### Post by oconnor on 2009-06-22
Thanks very much.  I know that was a simple question I appreciate the details!

---


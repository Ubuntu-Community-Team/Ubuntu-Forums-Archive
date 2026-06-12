---
title: "Canon ip3500 printer problem"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-15
Whenever i print images on this printer, they come out with a sort of distorted shadow, close to them, kind of like a negative. Can someone help me print normally?


Also, is there a way to change the username of a user
And, i accidently deleted my turn off switch, with my name next to it, the place where you can choose, turn off, restart, log out ect. I have seen similar ones by right clicking, and 'add to panel', but none are exactly the same as the one i deleted, how can i bring it back?

---

### Post by nhasian on 2008-12-15
You can get the User Switcher back by right clicking on the toolbar, choosing *add to panel*, then Add *User Switcher*

You cannot rename a user.  You can create a new user then delete the old username.

to add the user enter:

```
sudo useradd -d /home/username -m username
```

then set the password with:

```
sudo passwd username
```

---

### Post by Falc7 on 2008-12-15
ah yes, those worked thanks, anyone have any idea about the printer?

---


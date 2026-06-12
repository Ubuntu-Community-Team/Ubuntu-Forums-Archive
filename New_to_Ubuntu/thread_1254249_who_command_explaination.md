---
title: "who command explaination"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by colau on 2009-08-31
who
```

user1    tty7         2009-08-31 14:46 (:0)
user1    pts/0        2009-08-31 15:18 (:0.0)

```
Why [COLOR="Red"]tty7,pts/0 and (:0),(:0.0)[/COLOR]?

---

### Post by Liolikas on 2009-08-31
[http://en.wikipedia.org/wiki/Teletypewriter](http://en.wikipedia.org/wiki/Teletypewriter)
```

man pts
man who

```

"On fingers" it means that user uses X session on ctrl+alt+F7 and remote login.

---

### Post by chanakaudaya on 2009-08-31
Who command displays the users who are logged in to that machine and their details.

username  terminal   start time           running duration

user1      tty7       2009-08-31 14:46    (:0)

---

### Post by The Cog on 2009-08-31
tty1-7 are the virtual terminals. You can access them by pressing Ctrl-Alt-F1 to Ctrl-Alt-F7. tty1-6 give you standard console terminals. tty7 is the terminal that is (normally) used to display the GUI. 

pts/0 is a virtual terminal created by the GUI, probably running gnome-terminal, running bash, running who. 

You can see a little more detail with the command **w**. 

The :0 and :0.0 are the logical names of the X displays they are using. The details of the naming convention elude me.

---

### Post by colau on 2009-08-31
> **The Cog said:**
> tty1-7 are the virtual terminals. You can access them by pressing Ctrl-Alt-F1 to Ctrl-Alt-F7. tty1-6 give you standard console terminals. tty7 is the terminal that is (normally) used to display the GUI. 

pts/0 is a virtual terminal created by the GUI, probably running gnome-terminal, running bash, running who. 

You can see a little more detail with the command **w**. 

The :0 and :0.0 are the logical names of the X displays they are using. The details of the naming convention elude me.
Thank you.

---


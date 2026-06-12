---
title: "Any help !!!"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by ASH.AT on 2010-11-08
Hello all ):P

I got some papers to do in my college about Ubuntu, but still don't  know anything about it so i was wonderin if i can get some help...

Anyway my problem is: when i add a user using the terminal with USERADD  command ( as a root ofcourse ), i can't log into it, it always says "  Authentication failure "... i tried the -m flag and still nothing ...  also tried the man useradd ....
I also edited the followin files : Passwd, Shadow and group...

I'm using the followin commands... 
```
Ash@Ubuntu~# useradd user
Ash@Ubuntu~# passwd user
```Now when i log in user account the system says : Authentication failure
and my supervisor said it's just a matter of some flags before user  name... dunno what he's talkin about...

Plz any help !!!

Thank you so much anyway ....:rolleyes:

---

### Post by uRock on 2010-11-08
Hello and welcome to the forums. Running **man adduser** in a terminal should help you get a better idea of how to use the command.

---

### Post by yorkie on 2010-11-08
try this link
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by cariboo on 2010-11-08
Personally I use adduser, as it asks you to create the password as part of process, you can also add all the other important info, like full name, room #, etc. :)

Seeing as this is a school project, and you are doing this to learn, have a look at:

```
man useradd
```

it gives you all the command line switches.

---

### Post by ASH.AT on 2010-11-08
[SIZE=5]Thank you all for the help... I'll try it right now ...[/SIZE]

---


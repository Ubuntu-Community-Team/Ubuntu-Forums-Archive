---
title: "please help me ICEauthority problem"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by linux_spirit on 2010-03-09
hello everyone.
i'm using ubuntu 9.10 
when I make a new user using "useradd" command then when trying to login a problem occurs telling me that "couldn't update the file ICEauthority" 
which prevents me from getting to the desktop of the new user and this problem didn't happen before but now I can never 
login with the new usernames I make 
please help !!!

---

### Post by spiderbatdad on 2010-03-09
Hi and welcome to the forums.
Useradd is not used for creating new users; it has a different purpose. Adduser is the command used for creating new users and will generate the appropriate files. 
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by linux_spirit on 2010-03-09
> **spiderbatdad said:**
> Hi and welcome to the forums.
Useradd is not used for creating new users; it has a different purpose. Adduser is the command used for creating new users and will generate the appropriate files. 
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

thank you very much for this but may I ask about the difference between these two commands and why <useradd> doesn't work? can we do something so that a similar functionality will be applied to it?

best regards

---

### Post by spiderbatdad on 2010-03-10
adduser is an advancement of the useradd program. It creates a home directory and the skeleton files needed by new users. Useradd would require additional command line options to do the same. For example useradd would be more appropriate for adding a user to an existing directory tree. To get more information on these commands, you can find better info in the man pages than I can give. So fire up your terminal and enter:
```
man adduser

man useradd
```

---

### Post by linux_spirit on 2010-03-13
> **spiderbatdad said:**
> adduser is an advancement of the useradd program. It creates a home directory and the skeleton files needed by new users. Useradd would require additional command line options to do the same. For example useradd would be more appropriate for adding a user to an existing directory tree. To get more information on these commands, you can find better info in the man pages than I can give. So fire up your terminal and enter:
```
man adduser

man useradd
```

truly I've got it thank you very much I'll keep diving in linux until the end.god bless you

---


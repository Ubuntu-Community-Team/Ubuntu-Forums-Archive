---
title: "Root/ user question..."
date: 2011-01-05
forum: New to Ubuntu
---

### Post by j*tech on 2011-01-05
Hi, Im a beginner Ubuntu user and new forum member (1st post, although ive been reading postings for about a month now, learned a lot so far :biggrin:).....Made the switch from XP to 10.10 last month, and Im in love  lol.....Ubuntu is an awesome OS, wish I would have switched years ago.....


Now on to my question.....I am a bit confused about root & user accounts.....Currently there are 3 users on my PC, myself (Admin) and 2 desktop users.....Am I logging into root by being an Admin user?  Should i switch to a desktop user and enable a root password?...I really dont want to be logged in as root, as ive heard its not a smart move...

---

### Post by noorez on 2011-01-05
While you do have administrator privileges by logging in as yourself, they are not always active or put another way you are not logged in as root. When you want to perform an administrator action you will be explicitly asked to type in your password. If you tried to perform an administrator action by normal means you would be denied permission.

EDIT:

For a typical desktop user, you do not need to enable the root account unless you have a good reason for it. Logging in as root as you said is not such a smart move unless you know exactly what you are doing and even then it is dangerous as no mistakes (even typos) are forgiven!

---

### Post by nothingspecial on 2011-01-05
> **j*tech said:**
> 


Now on to my question.....I am a bit confused about root & user accounts.....Currently there are 3 users on my PC, myself (Admin) and 2 desktop users.....Am I logging into root by being an Admin user? 

No

> **j*tech said:**
>  Should i switch to a desktop user and enable a root password?

No

You`re doing just fine. Having an admin account means you don`t have to log in as root.

---

### Post by j*tech on 2011-01-05
ok, cool, thanks for the replies...

---

### Post by j*tech on 2011-01-05
should i add Admin to Root usergroup or no?...

---

### Post by cariboo on 2011-01-05
The first user you setup is already a member of the admin group. To find what groups your user is a member of, just open an Applications->Accessories->Terminal and type:

```
groups
``` 

the results should look similar to this:

```
groups
cariboo adm dialout fax cdrom floppy tape dip video plugdev fuse lpadmin admin sambashare
```

---


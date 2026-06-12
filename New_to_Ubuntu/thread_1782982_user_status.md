---
title: "user status"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by g_ramesh on 2011-06-15
Hi,

while installing Ubuntu 10.10 I created a user and the installation was smooth.
Please tell me what is the type of user that was created during installation, whether it is with administrator rights ? How to check ?

---

### Post by nomko on 2011-06-15
The first user is also the root.
Any other user created after the installation is a normal user without root priviliges.

---

### Post by dcsoldschool53 on 2011-06-15
**The first user is a normal user who can have temporally root privileges by using the commands sudo and gksu/gksudo ( the administrator). Any other user created after that, is a normal user without any temporally root privileges unless you had created that account as a part of the first normal user's group.  In short, you had added the account to the administrator group. Then, He can have temporally root privileges too. I think, I said that right.**

---

### Post by seawolf167 on 2011-06-15
For more information on how to become the root user to do things like install packages or edit configuration files, you can read about it here - [RootSudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by egalvan on 2011-06-15
> **nomko said:**
> The first user is also the root.


As *dcsoldschool53* stated, the first user **IS NOT ROOT**

the root account (the root user) is locked (NOT disabled).

Almost ERVERYthing a normal user does on Ubuntu can be done with sudo,
as the link *seawolf167* provided pointed out.

It IS possible to un-lock the root account, but this is HIGHLY DISCOURAGED, as it is quite a security risk.
 And if you have to ask HOW to un-lock the root account, the risk rises exponentially.

---

### Post by nomko on 2011-06-16
> **egalvan said:**
> As *dcsoldschool53* stated, the first user **IS NOT ROOT**
 
the root account (the root user) is locked (NOT disabled).
 
Almost ERVERYthing a normal user does on Ubuntu can be done with sudo,
as the link *seawolf167* provided pointed out.
 
It IS possible to un-lock the root account, but this is HIGHLY DISCOURAGED, as it is quite a security risk.
And if you have to ask HOW to un-lock the root account, the risk rises exponentially.
 
My mistake!

---

### Post by g_ramesh on 2011-06-16
Thanks to all of you for replies. How to check whether a user is normal or super user etc?

---

### Post by dcsoldschool53 on 2011-06-16
> **g_ramesh said:**
> Thanks to all of you for replies. How to check whether a user is normal or super user etc?
  Mark this thread as solved if we answered your question.

---

### Post by seawolf167 on 2011-06-16
> **g_ramesh said:**
> Thanks to all of you for replies. How to check whether a user is normal or super user etc?

No user would be a "super user", the command *sudo* stands for substitute user-do, so when you use it, you are substituting yourself for root for that command. All users by default will be "normal" users, you can add them to the Sudoers file, take a look at the [information here]("https://help.ubuntu.com/community/Sudoers").

---

### Post by grahammechanical on 2011-06-16
You need to find the Users and Groups utility. In 10.10 I think that you find it under System>Administration or System>Preferences. You may find, as I did, that this user is listed as Custom. There are three options, Custom, Administrator and Desktop User. The Custom setting gives some administrator rights but not all of them. I can do all that I want to do with the custom setting. Click on Advance Settings>User Privileges to see what each option allows you to do.

Regards.

Regards.

---

### Post by g_ramesh on 2011-06-17
> **grahammechanical said:**
> You need to find the Users and Groups utility. In 10.10 I think that you find it under System>Administration or System>Preferences. You may find, as I did, that this user is listed as Custom. There are three options, Custom, Administrator and Desktop User. The Custom setting gives some administrator rights but not all of them. I can do all that I want to do with the custom setting. Click on Advance Settings>User Privileges to see what each option allows you to do.

Regards.

Regards.

Thanks grahammechanical for an informative answer, will check up in my system.

---


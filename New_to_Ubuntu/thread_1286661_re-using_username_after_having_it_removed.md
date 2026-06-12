---
title: "re-using username after having it removed"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by perubu on 2009-10-09
Hi,

Being new to linux, I accidentally erased the launch panel.
Not knowing how to reinstall the panel, I removed the user and erased the /home/username directory and files.
Trying to recreate a new user with the same name, Ubuntu refuses, telling me that the username exists already.  I understand that the user name existed but it no longer exist and I would like to use it again.

What would be the right process to get a fresh user names list.

Thanks,

Père Ubu

---

### Post by tarps87 on 2009-10-09
How did you remove the user?
Try running this command and see if you can see the user listed
```
sudo cat /etc/passwd
```
Also this should remove the user
```
sudo deluser *username*
```

---

### Post by perubu on 2009-10-09
Hey tarps87,

Thank you much for you quick answer.

I still have the same issue though, here is what happened after I followed your suggestion:

> **tarps87 said:**
> How did you remove the user?
        In the graphic UI: System Administration / Users and Groups / remove user
        then in the terminal "rm -rf /home/username"

Try running this command and see if you can see the user listed
```
sudo cat /etc/passwd
```
 I did sudo cat /etc/passwd | grep username, and did not get anything


Also this should remove the user
```
sudo deluser *username*
```
  it tells me the user 'username' does not exist

if I go again in the GUI to create new user "username", it still replies User name "username" already exists.

all advices welcome, thanks,

Perubu

---

### Post by macabrem on 2009-10-09
When you delete a user (e.g. "Bob"), then you need to delete the group "Bob" before it will let you create  the same user.  

Also, you may have to delete the home directory for Bob if it is still there.
```

sudo rm -r /home/bob


```

---

### Post by wojox on 2009-10-09
Did you reboot?

---

### Post by macabrem on 2009-10-09
> **perubu said:**
> 

if I go again in the GUI to create new user "username", it still replies User name "username" already exists.

all advices welcome, thanks,

Perubu

This goes along with my post above about deleting groups.  You can delete groups with the GUI by clicking "manage groups" or something akin to that in the same window where you add users.  Then, just delete the group associated with the username (if username is "bob" then delete group "bob").

And then make sure bob's home folder is gone from /home/

---

### Post by tarps87 on 2009-10-09
Could you try
```
sudo adduser *username*
```
that will show if it is a problem with the GUI or the system

---

### Post by tarps87 on 2009-10-09
> **macabrem said:**
> When you delete a user (e.g. "Bob"), then you need to delete the group "Bob" before it will let you create  the same user.  

Also, you may have to delete the home directory for Bob if it is still there.
```

sudo rm -r /home/bob


```

Good point, it is worth checking this. Too use to Arch, all the users are added to the group users

---

### Post by perubu on 2009-10-09
This is now fixed,

I followed Macabrem'advice, without rebooting, removing the group -- that still existed -- allowed me to re-create the user.

Thank you very much all for your prompt and efficient input on this, best

Père Ubu

---


---
title: "Completely erase user from computer?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-06-14
Using Jaunty, I created a user (non-admin) and then deleted the account and ```
$ sudo userdel -r account_name
```

But when I try to create another account with the same login it tells me that it already exists. I ran the above command again but it tells me that it doesn't exist.

Is it normal and I can't create a new account with the same login as old deleted one? Or do I need to delete a specific file?

Thanks!

---

### Post by asmoore82 on 2009-06-14
check for a group of the same name as the deleted user.

---

### Post by k3lt01 on 2009-06-14
Go to Places>Home and then click on the Home tab. In the Home tab screen you will see what users are there because they will have their own user folder.

---

### Post by sylvainrb on 2009-06-14
> **asmoore82 said:**
> check for a group of the same name as the deleted user.

Found the group and deleted it. I haven't try to see if it works but it should be ok now if I want to create a new user with same name as the old deleted one right?

Thanks!

---

### Post by camper365 on 2009-06-14
If you delete the home folder (as root) using:
```
sudo rm -r *username*
```
it will delete. Be careful when using sudo and rm -r together. Only do this if you want the new user to have the default configuration. If you want the old user's configuration DO NOT DELETE!

If you edit the passwd file (/etc/passwd) and you find the name of the user and delete that line, it will remove the user. If you do the same for /etc/group. Then the user and group will be gone.

---


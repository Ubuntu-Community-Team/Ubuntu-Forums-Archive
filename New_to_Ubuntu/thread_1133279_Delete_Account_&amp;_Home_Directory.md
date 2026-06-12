---
title: "Delete Account &amp; Home Directory"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Rog3236 on 2009-04-22
I have been following examples in Rickford Grant's "Ubuntu for Non-Geeks" third edition. Along the way I created a couple of "Dummy" user accounts which automatically creates home directories for them. When I go back and attempt to delete these accounts I receive the message. "Disables access to system without deleting users home directory." 

Question? How do I do a clean removal of both the account and the home directories of these "dummy" accounts?

Thanks,

---

### Post by Paqman on 2009-04-22
Either you can remove the accounts then open Nautilus as root and delete the home folders, or you can do both steps at once from the command line:
```

sudo userdel --remove username

```

---

### Post by nandemonai on 2009-04-22
```
sudo userdel -r <username>
```

-r, --remove
           Files in the user´s home directory will be removed along with the home directory itself and the user´s mail spool. Files
           located in other file systems will have to be searched for and deleted manually.

Edit: Blast, beaten to it. :P

---

### Post by Iowan on 2009-04-22
I never remember if it's **userdel** or **deluser**. **man userdel** suggests **deluser** is preferred method. ```
userdel -r username
```>  -r, --remove
           Files in the user’s home directory will be removed along with the
           home directory itself and the user’s mail spool. Files located in
           other file systems will have to be searched for and deleted
           manually.

>        By  default,  deluser  will  remove  the user without removing the home
       directory, the mail spool  or any other files on the  system  owned  by
       the  user.  Removing  the home directory and mail spool can be achieved
       using the --remove-home option.

       The --remove-all-files option removes all files on the system owned  by
       the  user.  Note  that  if you activate both options --remove-home will
       have no effect because all files including the home directory and  mail
       spool are already covered by the --remove-all-files option.

---

### Post by Rog3236 on 2009-04-22
My thanks to all of you who responded to and solved my problem.

Roger

---

### Post by mathmom on 2009-04-24
I have a XP system that I set up to dual-boot with Ubuntu 8.04 about 7 months ago but
then never really used Ubuntu. Then I unintentionally deleted part of my Ubuntu files.
Now I have re-installed Ubuntu 8.04 but I have old home folders from the previous installation.  There are no users connected with them.  How do I delete them?
They have no data I want to save.

---

### Post by durand on 2009-04-24
You can just use:

```

sudo rm -rf /home/{user1,user2}

```

[COLOR="Red"]BE CAREFUL ABOUT WHAT YOU TYPE IN! IF YOU'RE NOT SURE, ASK FIRST.[/COLOR]

---

### Post by mathmom on 2009-04-27
> **durand said:**
> You can just use:

```

sudo rm -rf /home/{user1,user2}

```

[COLOR="Red"]BE CAREFUL ABOUT WHAT YOU TYPE IN! IF YOU'RE NOT SURE, ASK FIRST.[/COLOR]
I tried this and the two folders in home are still there.  The associated users were not reinstalled when
I reinstalled Ubuntu 8.04

---

### Post by durand on 2009-04-27
Hmm, you can't have done it right :S That command literally deletes the folders. You need to replace user1 and user2 with the usernames that you want to delete.

---


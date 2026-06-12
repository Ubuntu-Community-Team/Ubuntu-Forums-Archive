---
title: "User Privileges Mix up"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-16
I have installed Ubuntu on several PCs at work.  On each of them, when initially asked what user name I wanted to use, I said 

smd_staff

I then checked the "Log in automatically" checkbox and proceeded with the install.  I then installed Skype under the smd_staff user account.  Now I want to make lockable screen savers on all the Ubuntu machines, but I don't want my staff to know the "Power User" (smd_staff) password, because I don't want them installing software on Ubuntu.

Simple solution I thought, just make another user account (called "doc"), with a different password.  A few snags arose:

1) When I make the "doc" user account, the computer still logs into smd_staff automatically. I want the computer to default password protected login on the "doc" account, and password protected screen saver under the "doc" user.

2) Under the "doc" account, Skype is not installed.  I guess I have to re-install Skype in all the "doc" accounts, right?  No way to "share" the Skype installed under the "smd_staff" account?

3)  While playing arond with creating and deleting accounts, I discovered that when a user account is deleted, the "home directory" is not deleted, meaning, even though the user account is deleted, you can never use that user account name, on that PC ever again.  I tried manually deleting the old "home" directories (named according to the user account name) but, Ubuntu wouldn't allow it (I suspect for some very good reason that I'm not aware of).

How do I get rid of the old home directories of deleted user accounts?

How do I make Ubuntu automatically log into the "doc" account?  (I'll make a password protected screen saver for protection during clinic hours)

Must I re-install Skype under the "doc" account?

Thanks in advance.

---

### Post by bodhi.zazen on 2010-02-16
> **RedOctober said:**
> I have installed Ubuntu on several PCs at work.  On each of them, when initially asked what user name I wanted to use, I said 

smd_staff

I then checked the "Log in automatically" checkbox and proceeded with the install.  I then installed Skype under the smd_staff user account.  Now I want to make lockable screen savers on all the Ubuntu machines, but I don't want my staff to know the "Power User" (smd_staff) password, because I don't want them installing software on Ubuntu.

Simple solution I thought, just make another user account (called "doc"), with a different password.  A few snags arose:

1) When I make the "doc" user account, the computer still logs into smd_staff automatically. I want the computer to default password protected login on the "doc" account, and password protected screen saver under the "doc" user.

2) Under the "doc" account, Skype is not installed.  I guess I have to re-install Skype in all the "doc" accounts, right?  No way to "share" the Skype installed under the "smd_staff" account?

3)  While playing arond with creating and deleting accounts, I discovered that when a user account is deleted, the "home directory" is not deleted, meaning, even though the user account is deleted, you can never use that user account name, on that PC ever again.  I tried manually deleting the old "home" directories (named according to the user account name) but, Ubuntu wouldn't allow it (I suspect for some very good reason that I'm not aware of).

How do I get rid of the old home directories of deleted user accounts?

How do I make Ubuntu automatically log into the "doc" account?  (I'll make a password protected screen saver for protection during clinic hours)

Must I re-install Skype under the "doc" account?

Thanks in advance.

If you want multiple users to use Skype, install it to a shared location, such as /usr/local. Make the files owned by root, and rx by everyone.

In terms of removing users, how did you do that ? See man userdel, in particular the -r option.

To remove additional files, use find.

To add a user, and specify a home directory, see man useradd, in particular the -d option.

For you auto log in, change the auto login profile.

[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

---

### Post by ibuclaw on 2010-02-16
Furthermore, there is an official Skype repository: [http://forum.skype.com/index.php?showtopic=29679](http://forum.skype.com/index.php?showtopic=29679)

Installing Skype via that method will make it a system-wide installation.

Regards
Iain

---


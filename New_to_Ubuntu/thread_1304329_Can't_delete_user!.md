---
title: "Can't delete user!"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-29
EDIT: I found my answer in [this thread.]("http://ubuntuforums.org/showthread.php?t=211063") So, howcome the GUI Users and Groups button to delete a user doesn't work?

----------

Hmm well this is odd!

I created a new user called "newuser" so I could customize my guest session by setting up newuser's account how I wanted it, then copying over his home directory to /etc/skel.

This works great, my guest account now saves my settings... but, I want to delete newuser now as i'm finished with him... but he refuses to go!!

I go to users and groups and unlock, then delete, but when I close the window and re-open it, he's back again!

I even completely removed his home directory, but he still keeps appearing... wtf!

Any ideas?

---

### Post by PorkyPie on 2009-10-29
> **humphreybc said:**
> EDIT: I found my answer in [this thread.]("http://ubuntuforums.org/showthread.php?t=211063") So, howcome the GUI Users and Groups button to delete a user doesn't work?

----------

Hmm well this is odd!

I created a new user called "newuser" so I could customize my guest session by setting up newuser's account how I wanted it, then copying over his home directory to /etc/skel.

This works great, my guest account now saves my settings... but, I want to delete newuser now as i'm finished with him... but he refuses to go!!

I go to users and groups and unlock, then delete, but when I close the window and re-open it, he's back again!

I even completely removed his home directory, but he still keeps appearing... wtf!

Any ideas?

------------
Edit:
You can also do all this in one by using
```
sudo userdel -r username
```Replace "username" with the username.
------------


Well... I don't think that link in your edit is going to help you. That's using an older version of ubuntu, so it probably wouldn't be accurate. Try this:

```
sudo userdel
```Replace "userdel" with the user.

Now, try to delete his home directory:

```
sudo rm -r /home//USERNAME
```Replace "USERNAME" with the user, again.

---

### Post by soumava on 2010-03-03
thnx a ton :-)):KS

---

### Post by felixvah on 2010-06-02
> **PorkyPie said:**
> ------------
Edit:
You can also do all this in one by using
```
sudo userdel -r username
```Replace "username" with the username.
------------


Well... I don't think that link in your edit is going to help you. That's using an older version of ubuntu, so it probably wouldn't be accurate. Try this:

```
sudo userdel
```Replace "userdel" with the user.

Now, try to delete his home directory:

```
sudo rm -r /home//USERNAME
```Replace "USERNAME" with the user, again.

I encountered the same problem and tried the command as you've suggested but this is what I got:
user thinclient6 is currently logged in

How would I kill the client or log off the user.  I can not log on as thinclien6 anymore.  when I tried I'll get an error saying could not update ICEauthority files and there'll be a blank desktop so I can't logout or do anything.  I'll have to switch into command line and restart gdm and log on as other users.  When I tried to delete thinclient6 the above errors is what I got.  this us ubuntu 9.10.. please help..

thanks

---


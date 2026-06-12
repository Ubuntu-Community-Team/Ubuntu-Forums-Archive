---
title: "Making a user a su"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by mikeybinec on 2011-01-23
Running ubuntu server 10.10. I created a user, joeblow. joeblow logs in and I was trying to make him a su with the su - command. It asked for the password, which I assumed was the root password and I entered it, but it came back with authentication failure. I got this su - command from my SLES9 school book, but it ain't happening for joeblow today.
 
Any comments from anybody?  
 
Thanks.

---

### Post by TeoBigusGeekus on 2011-01-23
su with a username doesn't make the username a superuser.
```
su joeblow
```
would ask for joeblow's password so you can run things as joeblow.
If you want to give administrative rights to joeblow, add him to sudoers or log on to his account and 
```
su
```
to become superuser.

PS:
```
man su
```
for more info.

---

### Post by Rocket2DMn on 2011-01-23
To give a user "root" privileges in Ubuntu, we use a sudo rather than granting access to a root account.  For background and more information on how to set this up, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Let us know if you have any specific questions.

---

### Post by wojox on 2011-01-23
You could change his group as well:

```
sudo useradd -G admin joeblow
```

---

### Post by Paqman on 2011-01-23
> **wojox said:**
> You could change his group as well:

```
sudo useradd -G admins joeblow
```

I believe it's "admin" rather than "admins".

---

### Post by wojox on 2011-01-23
> **Paqman said:**
> I believe it's "admin" rather than "admins".

Your right, thanks. Changed it. ;)

---

### Post by mikeybinec on 2011-01-23
Thanks to all for replies and links

---


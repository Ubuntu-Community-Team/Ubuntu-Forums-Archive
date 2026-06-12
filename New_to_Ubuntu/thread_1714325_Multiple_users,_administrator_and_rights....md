---
title: "Multiple users, administrator and rights..."
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Z80A on 2011-03-25
This is a fairly basic question, but I would like to know how you guys handle this in real life.

When installing Ubuntu on my daughters laptop, I have so far installed it with myself as primary user (administrator) and then afterwards added my daughter as a normal user user. This is a good setup as only I will do the more tricky configuration things, but the drawback is that she will only receive software updates when I log in and check for updates.

The same thing on the PC hooked up on my TV - the "TV" account should not be an administrator.

How do you deal with such a scenario? Any rule of thumbs on how to assign right to various users?

Z80A

---

### Post by Smart Viking on 2011-03-25
What do you mean by "administrator account"? Do you mean root, or do you mean a user that is part of the wheel group(can use sudo)?

I would probably make her a part of the wheel group and let her use sudo to install updates and new programs. It is not a problem for the TV user to be part of the wheel group really as it wont use sudo all by itself, only the user, so it's not like anything that is run is runned with super-privileges, only if you tell it to and then you gotta write your password.

---

### Post by Ghost_Mazal on 2011-03-25
I add users that needs sudo access with

```
sudo addgroup username admin
```

This adds username to the admin group and can then use sudo with is/her own username and password.

---

### Post by tarps87 on 2011-03-25
Have a look at:
[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

In your case I would set up the second account on the laptop (in this case your daughters) with sudo rights for apt-get, aptitude and also the GUI install application and the GUI update application (I can't remember the names, I will updated this when I get access to a Ubuntu install)

If you don't want your daughter installing other programs you can limit the rights to apt-get update, aptitude update and GUI update application

You can apply the same style setting to the TV setup

GUI install application = /usr/bin/software-center
GUI update application = /usr/bin/update-manager

---


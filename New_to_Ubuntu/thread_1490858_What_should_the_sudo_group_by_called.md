---
title: "What should the sudo group by called?"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Xeoncross on 2010-05-22
When starting with a fresh install most people create a "wheel" group and add each sudo user to that. However, I see a group already setup with sudo rights called "sudo". 

Should I go against the flow and add users to that or keep using the wheel group?

```
/usr/sbin/groupadd wheel
/usr/sbin/visudo

...

## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL

...

/usr/sbin/adduser demo
/usr/sbin/usermod -a -G wheel demo
```

---

### Post by Iowan on 2010-05-22
I've never had to add a sudo group to my Ubuntu systems. My */etc/sudoers* file uses %admin rather than %wheel.

---

### Post by Xeoncross on 2010-05-22
My empty 10.04 server install came with a group called "sudo" already set with sudo permissions. That is why I was wondering.

Personally, "admin" makes the most sense since they are full "server admins" at that point.

---

### Post by marshmallow1304 on 2010-05-22
I thought wheel was more commonly used to designate those users who are allowed to su to root, obviously on distros in which the root account is not locked.  Whenever I set up Debian and add sudo, I make a group called admin for sudoers.

---

### Post by Xeoncross on 2010-05-23
Well, I see a group called "admin" also pre-created in the list of groups... although it doesn't seem to have sudo permissions yets. Again I personally like the term "admin" so perhaps I'll remove the wheel group.

---

### Post by Xeoncross on 2010-06-06
After more research [the manual says]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html") to add the user to the group "admin". However, only the group "sudo" is setup in visudo with sudo permissions.

So for right now on my VPS I'm just creating my user and putting it in the "sudo" group since that group is already setup and has sudo permissions.

However, it seems that the desktop version adds the user to the "admin" group automatically and creates an entry in the **/etc/sudoers** file.

Any more thoughts on this?

---


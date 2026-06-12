---
title: "Giving a user sudo permissions"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by nick_nik on 2009-07-02
Hi, 

i would like to set up a group of users called [FONT=Century Gothic]accesscontrol [/FONT]which is able to access the users-admin command.

i have set up a user call john who is a member of the accesscontrol group

i have used the visudo command to add the following to my sudoers file:

```
%accesscontrol ALL=/usr/bin/users-admin
```Now logged in as john I have a couple of questions:


[LIST=1]
[*]when i issue the command ```
sudo users-admin
```. the user admin dialog box which opens cannot be unlocked allow john to add a user
[*]When you go to ```
System > Admin > user and groups
``` its says john doesn't have sufficient privilages.
[/LIST]
Any hints in the right direction would be most appreciated.


Thanks, 

Nick

---

### Post by RealPSL on 2009-07-03
I keep thinking that entry should be ```
%accesscontrol ALL=(ALL)  /usr/bin/users-admin
``` but I am a little rusty. Either way you can test this with sudo -l as the user to see exactly what he can run.

---


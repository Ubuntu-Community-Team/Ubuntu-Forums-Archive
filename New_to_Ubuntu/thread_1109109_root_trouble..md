---
title: "root trouble."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Adarshkl on 2009-03-28
i installed ubuntu within vista. but  i didnt get any prompt regarding the root user or the root password. the profile i created later was actually the privilaged one. but i accidently deleted that user. now im in trouble as i dont know the default root password, or how to create a privilaged user.please someone help me..i just began loving ubundu.

---

### Post by sisco311 on 2009-03-28
Boot in the Recovery Mode and add your user to the *admin* group:
```
adduser **username** admin
```

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

EDIT: if you need you can first create a new user, then add it to the admin group:
```
adduser username
adduser username admin
```

---

### Post by 123456789123456789123456 on 2009-03-28
the last reply is a good one.  This is what actually happens, I don't know why, but ubuntu does not automatically give Root a password, but it will not allow you to use nothing for the password.

*EDIT (HymnToLife): This is because Ubuntu's policy is to not use the root account at all for interactive sessions and use [font="monospace"]sudo[/font] instead. Moreover, it is against [forum policy](http://ubuntuforums.org/showthread.php?t=716201") to give advice about unlocking the root account.*

---


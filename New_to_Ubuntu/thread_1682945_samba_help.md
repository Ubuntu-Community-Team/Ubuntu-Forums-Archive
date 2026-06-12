---
title: "samba help"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by dd1313 on 2011-02-06
Hi GUys

I am a newbie to ubuntu having tried it on and off for years
Ok I want to share files with windows user, so I have setup samba with the instructions from here

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

What I want is to have 2 shared folders.owners and users and usernames with the same value.

I want owners to have access  to both folders but users to the users folder only, here is my sample samba file

[owners]
    path = /home/owners/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = owners
   
[users]
    path = /home/users/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = users

How can I have owners access both at one login.
Also I want to be able to get them to login on the windows
machine each time I restart samba but that does not happen.

Please help
DD

---

### Post by robsoles on 2011-02-12
'force user' doesn't control who has access, it sets it so that the system will allow a 'valid user' to login and when they access that resource the system with samba will treat their actions as being from the 'forced user' rather than whatever Linux user the valid login relates to.


I think you want more like (assuming 'owners' and 'users' are both groups - let me know if they are actually users)```
[owners]
    path = /home/owners/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    valid users = @owners
   
[users]
    path = /home/users/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
valid users = @users
```
Here is a snippet from my Samba config file - I have it setup as [quote="Snippet of output from testparm"]Server role: ROLE_DOMAIN_PDC[/code]

```
[music]
    comment = Family's Music
    path = /home/family/Music
    read list = @users
    write list = rob
```

This actually doesn't seem to list all the directives I am used to being able to use in Samba but it's better than nothing: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---


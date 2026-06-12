---
title: "restricting access on ubuntu server"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-04
I got a minimal install ubuntu on a virtual server.  

There is only one user that is 'root'

I have created a few more user under /home

I want to disable root login, and password authentiation on sshd_config, and allow only one user to be able sudo. So that user has root access through sudo.  

How would I go about allowing a user to be sudoer?

---

### Post by bodhi.zazen on 2011-08-05
> **007casper said:**
> I got a minimal install ubuntu on a virtual server.  

There is only one user that is 'root'

I have created a few more user under /home

I want to disable root login, and password authentiation on sshd_config, and allow only one user to be able sudo. So that user has root access through sudo.  

How would I go about allowing a user to be sudoer?

Add the user to the admin group and make sure sudo and ssh both work before you disable ssh and the root account.

sudo is configured in the /etc/sudoers file and you should see a line :

```
# Members of the admin group may gain root priviliges
%admin ALL=(ALL) ALL
```

If not, add it in (the second line)

---

### Post by 007casper on 2011-08-05
I did
> adduser username groupname

it works.

Thank you so much.

I was wondering...

How can I list the groups the user belongs to?

And how can I delete the user from a specific group? 
> deluser username groupname
 
~is that correct?

---

### Post by bodhi.zazen on 2011-08-05
> **007casper said:**
> I did


it works.

Thank you so much.

I was wondering...

How can I list the groups the user belongs to?

And how can I delete the user from a specific group? 

 
~is that correct?

You can either directly edit /etc/group or use id and usermod

id user_name

see man usermod ( -g and -G )

---


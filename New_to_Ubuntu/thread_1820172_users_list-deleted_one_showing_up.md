---
title: "users list-deleted one showing up?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by ub newb on 2011-08-07
I ran this command  to create a user list.

cat /etc/passwd | grep /home | cut -d: -f1

all current users showed up but also one that I thought I deleted the desktop for.

Do I just delete the whole folder in /home? for this deleted desktop? It doesn't show up in the listed users on sign on so I thought it was gone. 

Also came up as users were syslog and klog. 
Who or what are these users? 

thanks

---

### Post by hailtothethief on 2011-08-07
```
sudo deluser --remove-home username
```

Will delete user 'username' and the /home directory associated with it. Hope this helps

---

### Post by bodhi.zazen on 2011-08-07
> **ub newb said:**
> Also came up as users were syslog and klog. 
Who or what are these users? 

thanks

From your post I take it you are very new to Ubuntu.

Why then are you deleting things you do not understand ? This is a good way to break your installation.

Use google to search for those user names and read up on Ubuntu before you go deleting things.

Or be prepared to re-install.

---


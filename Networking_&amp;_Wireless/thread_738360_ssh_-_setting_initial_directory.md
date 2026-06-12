---
title: "ssh - setting initial directory"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by JimJey on 2008-03-28
I would like to know how I can specify the directory I am placed in when I connect via ssh to one of my computers. Normally you are placed into the home directory. However I would like to start in a subdirectory of $HOME. How can I achieve this?

---

### Post by fmartinez on 2008-03-29
> **JimJey said:**
> I would like to know how I can specify the directory I am placed in when I connect via ssh to one of my computers. Normally you are placed into the home directory. However I would like to start in a subdirectory of $HOME. How can I achieve this?

#usermod -d /path/to/new/home/directory

You can use this command to specify a new home directory for a specific user. 

#man usermod
in a terminal to get more info. 
GOOD LUCK!

---

### Post by JimJey on 2008-03-29
This will work. However I want to be placed into a subdirectory of home, not in a new home directory.

---

### Post by qpieus on 2008-03-29
try this:```
ssh -t *IP address* "cd ~/whatever ; bash"
```

This will put you in a non-login shell however. So, after you are done working on the remote pc and you type "logout', instead of logging out, you'll get a message > bash: logout: not login shell: use `exit

so then you have to type exit, then logout.

---


---
title: "lsmod on Ubuntu 8.04 Server (V-Server)"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by mastertom on 2009-07-19
Hi Ubuntu comunity,

I am an new ubuntu server user. I use Ubuntu "workstation" on my desktop many month.

Now my  aim is to install al VM-Ware-Server on a ubuntu 8.04 server.

After starting setup the script ask for the path of the lsmod files... but no lsmod is installed on the system!

How can I install the right package on my server (only with putty-support / winscp-support).:confused:


Thanks for your support 

Mastertom ;-)

---

### Post by yeats on 2009-07-19
What is the output of 

```
locate lsmod
```

?

---

### Post by The Tronyx on 2009-07-19
If locate lsmod outputs too much data, please let us know what the outputted from the below:

```

whereis lsmod
which lsmod

```

I am guessing which lsmod won't return anything since you are getting command not found but it can't hurt. :)

---


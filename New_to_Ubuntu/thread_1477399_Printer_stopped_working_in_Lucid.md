---
title: "Printer stopped working in Lucid"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by rf9rider on 2010-05-08
As per title, my printer has stopped working.

Tried to reinstall drivers, i get a box asking me for root password, which won`t accept my password.

Used the help button on my printer config, says CUPS spool not running?

Help says go to System>Admin>Services to check if cups is running? Services not an option i have in my list.

Worked fine yesterday, haven`t altered/changed anything.

Help! :confused:

---

### Post by cariboo on 2010-05-08
Open a terminal and type:

```
sudo service cups restart
```

Paste whatever error you get in your next post.

It usually helps if you mention what type of printer your are having problems with.

---

### Post by rf9rider on 2010-05-08
Heres what happened

mark@mark-desktop:~$ sudo service cups restart
[sudo] password for mark: 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
mark@mark-desktop:~$ 

That seemed to get it working, Thanks.

---

### Post by TheNerdAL on 2010-05-08
> **rf9rider said:**
> Heres what happened

mark@mark-desktop:~$ sudo service cups restart
[sudo] password for mark: 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
mark@mark-desktop:~$ 

That seemed to get it working, Thanks.

Does it work now after you did that?

---

### Post by rf9rider on 2010-05-08
Yup, all working fine, just rebooted and tried it, Thanks.

By the way, its a Lexmark 2600 series printer. :D

---

### Post by TheNerdAL on 2010-05-08
Please mark this thread as solved if your problem is solved. :)

---

### Post by rf9rider on 2010-05-08
> **TheNerdAL said:**
> Please mark this thread as solved if your problem is solved. :)

Too late, i already did. ;)

---


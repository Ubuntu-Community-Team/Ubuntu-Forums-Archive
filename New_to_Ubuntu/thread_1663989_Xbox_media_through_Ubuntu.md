---
title: "Xbox media through Ubuntu?"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2011-01-10
Is there an easy way to get Xbox 360 to work through Ubuntu? or any recomended media centres please?

---

### Post by cheekymonky2010 on 2011-01-26
Any help please???

---

### Post by cheekymonky2010 on 2011-02-02
After configuring Ushare, it worked! needed to have an open terminal that had started Ushare and the Xbox could see the media. all.  Music doe,snt play but the films work fine!  thanks

---

### Post by Ditchdoc7893 on 2011-02-21
I feel really dumb right now.  I have no idea how to "configure" ushare.  I assume one would configure it in terminal.  Can you give me some instruction?  Thanks!  

Ryan

---

### Post by tjwoosta on 2011-02-22
Edit the config file. Not sure where it is on ubuntu, I think its usually /etc/ushare/ushare.conf. Youll probably need to have root privelages to edit the file.

if its not there you might try the locate command to find it

First update the search database
```
sudo updatedb
```

then locate
```
locate ushare
```

It should return a list of all the files and directories with ushare in the name.

---


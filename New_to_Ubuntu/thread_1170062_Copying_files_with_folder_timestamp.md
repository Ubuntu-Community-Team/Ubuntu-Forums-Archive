---
title: "Copying files with folder timestamp"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by mistypotato on 2009-05-25
Can someone look at this string.... 
**sudo cp -R /var/www/shoes/ /media/disk/htdocs/date +':%m/%d/%y%n-:%H:%M:%S**'

and tell me why I get an error saying......
**cp: target `+:%m/%d/%y%n-:%H:%M:%S' is not a directory**


What I'm trying to do here is backup files on a server from the www directory to an external USB hard drive.   I'm wanting to create a new folder each time (timestamped so I get a unique folder every time I run the backup).

If I use a line like this it works......
**sudo cp -R /var/www/shoes/ /media/disk/htdocs/**
as long as the directory /media/disk/htdocs/ already exists on the external drive, it works.  But that's not what I want.

Thanks!

---

### Post by Boondoklife on 2009-05-25
I think you are missing a few things in that script: first they %variables are used in the date app and the %n would give you a newline character, not sure how that would even qualify as valid.

Try this instead```
cp examples examples-`date +'%m.%d.%y-%H.%M.%S'`
```

> **mistypotato said:**
> Can someone look at this string.... 
**sudo cp -R /var/www/shoes/ /media/disk/htdocs/date +':%m/%d/%y%n-:%H:%M:%S**'

and tell me why I get an error saying......
**cp: target `+:%m/%d/%y%n-:%H:%M:%S' is not a directory**


What I'm trying to do here is backup files on a server from the www directory to an external USB hard drive.   I'm wanting to create a new folder each time (timestamped so I get a unique folder every time I run the backup).

If I use a line like this it works......
**sudo cp -R /var/www/shoes/ /media/disk/htdocs/**
as long as the directory /media/disk/htdocs/ already exists on the external drive, it works.  But that's not what I want.

Thanks!

---

### Post by mistypotato on 2009-05-25
Thank you VERY much :KS

Your reply helped me quickly get it working.

---

### Post by Boondoklife on 2009-05-26
> **mistypotato said:**
> Thank you VERY much :KS

Your reply helped me quickly get it working.

No prob, you might want to consider taring up the backup, just makes it easier to manage.

---


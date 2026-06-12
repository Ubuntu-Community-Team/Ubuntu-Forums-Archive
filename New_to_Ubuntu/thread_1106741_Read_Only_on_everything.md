---
title: "Read Only on everything"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Bri0 on 2009-03-26
I just did a reinstall of ubuntu and have all my stuff on a DVD, now everything has a lock icon on every folder and files within them when I put them all back on my comp.

I'm not about to right click on every stinkin' file to put it back to the way they where.

You know how annoying this is??!! ](*,)

Thanks

---

### Post by Bri0 on 2009-03-26
I got it now. Its been awhile... #-o

sudo chmod +w -R /folder

---

### Post by KIAaze on 2009-03-26
Command-line to the rescue!
```
chown -R $USER:$USER DIRECTORY
chmod -R u+w DIRECTORY

```

Just so you can tweak this according to your needs:
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)
[http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml)

edit: Ah, I see you are already experienced. :)

---


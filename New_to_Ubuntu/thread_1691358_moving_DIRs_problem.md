---
title: "moving DIRs problem"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by nhtrader on 2011-02-19
I'm trying to move a DIR and I can't do it.

Basically, I would like to move the DIR: /var/lib/mythtv and its subfolders to a new location. I want to move it to an existing DIR: /home/mythtv

here's what I did...

 mv /var/lib/mythtv/  /home/
mv: cannot move `/var/lib/mythtv/' to `/home/mythtv': Directory not empty


If I execute this command...
 mv /var/lib/mythtv   /home/mythtv
or
 mv /var/lib/mythtv/  /home/mythtv/

the result is that the move produces this DIR:  /home/mythtv/mythtv which is not what I want.

How do I move /var/lib/mythtv to /home/mythtv?

---

### Post by cjhabs on 2011-02-19
It is complaining that there is already a "mythtv" folder under /home and that folder contains files.
Remove - or move - the /home/mythtv folder and you should be good to go.

---

### Post by nhtrader on 2011-02-19
> **cjhabs said:**
> It is complaining that there is already a "mythtv" folder under /home and that folder contains files.
Remove - or move - the /home/mythtv folder and you should be good to go.

I can't. This DIR is necessary b/c it contains many hidden config files. That's the problem.

---

### Post by cjhabs on 2011-02-19
> **nhtrader said:**
> I can't. This DIR is necessary b/c it contains many hidden config files. That's the problem.

Ok, so if you want the files from /var/lib/mythtv moved into /home/mythtv you need:

mv /var/lib/mythtv/*   /home/mythtv

However this won't pick up hidden files or copy links correctly, so a better option is:
cd /var/lib/mythtv; tar cvf - * | (cd /home/myth; tar xvf -)

This does not move the files, it copies them, so you can then remove the source folder with:
rm -r /var/lib/mythtv

---

### Post by nhtrader on 2011-02-20
Thanks. It's not what I want to do, b/c I don't have enough HDD space to copy.

I guess I'll have to move them the old fashion way - manually.

---

### Post by cjhabs on 2011-02-20
You can move the hidden files by using "..*" instead of just "*".
Check if there are any links with:
```
ls -F /var/lib/mythtv | grep @
```
If there aren't any then you are good to go with the mv command.

---

### Post by nhtrader on 2011-02-20
> **cjhabs said:**
> You can move the hidden files by using "..*" instead of just "*".
Check if there are any links with:
```
ls -F /var/lib/mythtv | grep @
```If there aren't any then you are good to go with the mv command.

Excellent. Thank you. This will work.

Solved.

---


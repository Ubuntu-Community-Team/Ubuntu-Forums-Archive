---
title: "Terminal (rm) problem..."
date: 2009-05-16
forum: New to Ubuntu
---

### Post by goldblattster on 2009-05-16
Hi! ):P Basically, I found this thread:
[http://ubuntuforums.org/showthread.php?t=57821&highlight=%2Ftmp](http://ubuntuforums.org/showthread.php?t=57821&highlight=%2Ftmp)
and doclivingston said that ".debs that have been downloaded get put in /var/cache/apt/archive, you can remove everything from this directory but "lock" and "partial" safely." And to remove the debs I used
```
sudo rm /var/cache/apt/archive/*.deb
```
When I hit enter after entering the command (andentering my password for temporary root/sudo power), I get
```
rm: cannot remove `/var/cache/apt/archive/*.deb': No such file or directory
```
Then a new line is started:
```
ariel@ariel-laptop:~$
```
I am wondering why the rm app is giving me this error, since i can open that directory in natilus with
```
nautilus ~/var/cache/apt/archives
```
Help would be greatly appreaciated. thanks! :)

---

### Post by KCormier on 2009-05-16
archives is plural.

```

correct:
sudo rm /var/cache/apt/archives/*.deb
wrong:
sudo rm /var/cache/apt/archive/*.deb

```

missing the s :)

---

### Post by x33a on 2009-05-16
try, 

```
rm /var/cache/apt/archives/*.deb
```

ps: i am not sure how safe it is to delete these debs though. investigate it thoroughly first.

---

### Post by goldblattster on 2009-05-16
That worked! man, that was a weird mistake.
EDIT: To be safe, I just deleted .debs of apps I uninstalled.

---

### Post by StOoZ on 2009-05-16
you could as easily just used the apt-get clean to do that

---


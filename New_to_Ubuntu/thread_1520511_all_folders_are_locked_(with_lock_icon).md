---
title: "all folders are locked (with lock icon)"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by 4chan on 2010-06-29
hello.

i just moved files from another HDD, and now all folders are locked (with lock icon).
this thread ( [http://ubuntuforums.org/showthread.php?t=929483](http://ubuntuforums.org/showthread.php?t=929483) ) only show how to change permissions per folder. for example if i write :

cd /home/charlotte/Videos

and then :

sudo chown charlotte *

it only change the permissions for Videos folder, but all folders inside video folders still locked.

my question is how can i change permissions for all folders in /home directory.

my username is charlotte, please write the complete command line so i don't get confuse. thank you in advanced

---

### Post by Veikk0 on 2010-06-29
I checked the manual page for chown and found this:
> -R, --recursive
              operate on files and directories recursively

So you could try *sudo -R chown charlotte **. I hope that helps :)

---

### Post by nothingspecial on 2010-06-29
```
sudo chown -R charlotte:charlotte /home/charlotte
```

should fix all your problems.

---

### Post by Sir Jasper on 2010-06-29
Hi,

Recently I copied from another drive and I used -hR (not -R ).  

Just a thought for further advice and consideration if your problem should remain unsolved.

My regards

---

### Post by 4chan on 2010-06-29
thank you very much guys. it is working.

---


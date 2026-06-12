---
title: "How to get wget to do what I want"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by ptn107 on 2011-03-03
I'm simply trying to get all the files at [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/).

However using:
```
wget -cb -t 0 -r http://releases.ubuntu.com/maverick/
```
seems to want and grab all the files from http://releases.ubuntu.com/{dapper,hardy,karmic,lucid,maverick}/.

Ha, I came home from work and had a mirror image of releases.ubuntu.com.  I don't need the other versions.

---

### Post by TeoBigusGeekus on 2011-03-03
Use the -np (no parent) option.

---

### Post by maqtanim on 2011-03-03
Well... I am not sure whether I understand your problem. Try the download with the graphical front end of WGET. The graphical front end is much more easier to handle. Go to Ubuntu Software Center and install Gwget.

---

### Post by ptn107 on 2011-03-03
I think -nH is the option I was looking for.

Taken from 'man wget'
>        -nH
       --no-host-directories
           Disable generation of host-prefixed directories.  By default,
           invoking Wget with -r [http://fly.srk.fer.hr/](http://fly.srk.fer.hr/) will create a
           structure of directories beginning with fly.srk.fer.hr/.  This
           option disables such behavior.

** -np worked as well. Thanks.

---

### Post by ptn107 on 2011-03-03
The command in it's final form seemed to work better with the options combined:

```
wget -c -nc -r -nH -nd -np http://releases.ubuntu.com/maverick/

```

---


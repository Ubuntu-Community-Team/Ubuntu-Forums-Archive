---
title: "fade up...."
date: 2009-06-02
forum: New to Ubuntu
---

### Post by chayanmann on 2009-06-02
guys,i'm fade up.i'm using 8.10..in it firefox has become extremely slow only for specifec sites...facebook,ubuntuforum..facebook is taking 3-4 mins to appear..i've installed an update today (can't remember the name)....what can i do????

---

### Post by Cypher on 2009-06-02
Tell us more about your PC, what are the specs? Has Ubuntu always been slow, or only recently??

---

### Post by chayanmann on 2009-06-02
processor-intel pentium D (2.66 GHz)
board-gigabyte 945
ram-512gb
disk-80 gb

its just from today afternoon..everything was going fine before that,especially facobook is taking too much time to load.....i fond this problem once before in my previously installed ubuntu-8.10.i've installed an update though i can't remember its name....i've tried XP,its ok in there.....

---

### Post by Bios Element on 2009-06-02
> **chayanmann said:**
> processor-intel pentium D (2.66 GHz)
board-gigabyte 945
ram-512gb
disk-80 gb

its just from today afternoon..everything was going fine before that,especially facobook is taking too much time to load.....i fond this problem once before in my previously installed ubuntu-8.10.i've installed an update though i can't remember its name....i've tried XP,its ok in there.....

Facebook has been having major problems recently with loading for many people. I'd suggest doing a reboot and seeing if that helps at all. If it doesn't you and you don't mind losing any firefox data you can purge/re-install firefox which might help.

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

You can always backup your /home/username/.firefox folder if you want to restore your firefox settings.

---

### Post by chayanmann on 2009-06-02
it does not work....any more ideas?       (thnx for helping)

---


---
title: "Pipe results of locate into rm?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-02-19
Hi, I'm trying to figure out a way to get rid of all these thumbs.db and desktop.ini files that windows left all over my hard drive. 

I planned on running "locate -i thumbs.db | rm". After some googling, I found out about xargs, so I thought "locate -i thumbs.db | xargs --interactive rm".

Before trying it out for real, I decided to run a test case, I made a file, and named it "test.test". I've tried "locate test.test | rm -i" as well as "locate test.test | xargs --interactive rm". If I simply do "locate test.test" it shows the file, and when I use xargs, it shows the correct command, but the file isn't removed. Any ideas?

---

### Post by yknivag on 2010-02-19
Try

```

find -iwholename '/*/test.test' -exec rm '{}' \;

```

However, try find on it's own first! (find -iwholename '/*/test.test'). Then you won't delete anything you don't want to!

```
man find
``` will give you all the other various permutations of this useful command.

---

### Post by kaibob on 2010-02-19
You can also have find prompt before removing a file. You need to change /target/directory and *.ext

```
find /target/directory -name '*.ext' -type f -ok rm '{}' ';'
```

For example,

> $ find /home/kaibob -name 'desktop.ini' -type f -ok rm '{}' ';'
< rm ... /home/kaibob/temp/desktop.ini > ? y
< rm ... /home/kaibob/downloads/desktop.ini > ? y

---

### Post by falconindy on 2010-02-19
Warning: This might kick your dog.
```
rm -i $(locate filename)
```

---

### Post by Dies on 2010-02-19
May not be as fast as using locate but
```

find . -name ?humbs.db -type f -exec rm -f '{}' \;
```
would recursively delete those files in whatever folder you're in. ;)

---

### Post by Ozymandias_117 on 2010-02-19
Thanks guys!

---


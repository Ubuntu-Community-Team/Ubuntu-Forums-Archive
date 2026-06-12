---
title: "delete locked file"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by asmodeuzz on 2009-01-24
How could i delete this locked file? it seems window xp's virus, i can't delete it,the file is protected

[IMG]http://i41.tinypic.com/21jdspd.jpg[/IMG]

---

### Post by Crandom on 2009-01-24
That's not a virus, that's the recycle bin's folder. A virus may be stored within the recycle bin directory ("RECYCLER") but you should use windows based anti virus software to remove it. If you have none, try [http://www.avast.com/eng/avast_4_home.html](http://www.avast.com/eng/avast_4_home.html)

---

### Post by fuser312 on 2009-01-24
become root using su
then go to that directory using cd
and tthen use this command
rm -rf recycler
replace recycler with the file you want to delete.

---

### Post by mister_pink on 2009-01-24
Press Alt+F2 and type 
```

gksudo nautilus

```
Using this you will be able to delete it, but be very careful where you click, one missed click and you can ruin your system. When you're done close that file browser window.

---

### Post by asmodeuzz on 2009-01-25
ok thx u very much, i will try it

---

### Post by searayman on 2009-04-07
you need to unlock it first. I wrote a good articel about this [here]("http://www.associatedcontent.com/article/1588637/changing_permissions_of_locked_folders.html?cat=59").

---


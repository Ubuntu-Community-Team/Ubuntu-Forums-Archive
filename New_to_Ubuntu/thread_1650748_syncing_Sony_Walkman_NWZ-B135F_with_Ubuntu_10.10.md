---
title: "syncing Sony Walkman NWZ-B135F with Ubuntu 10.10"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by astrob0t on 2010-12-22
I am having problem syncing my sony walkman NWZ-B135F with my ubuntu ..

i tried jsymphonic but in vain..

my pc simply doesnt recognise my walkman and no devices can be seen in /media

rythmbox player however detects it but crashes everytime i try to access the files.

plz help!!

:(

---

### Post by astrob0t on 2010-12-22
bump !!!!

---

### Post by Koffeehaus on 2011-02-15
I have a similar problem, except when I connect my Walkman nothing happens at all....

---

### Post by heyho on 2011-02-15
I used to have trouble with my NWZ walkman, although with 10.04 it works fine.

I had to use:

```
killall gvfs-gphoto2-volume-monitor
```

Before plugging it in.  Worth a shot.

---

### Post by Koffeehaus on 2011-03-03
You need to download 'pmount' from the software centre and restart.

---


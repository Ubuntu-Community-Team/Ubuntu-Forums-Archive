---
title: "Mount external drive to home directory?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by dragonpimpsta on 2010-08-19
mount /dev/sda1 /home/*username*/External

Is doing that bad or is it even possible? I'm too scared to try it. T

I'm trying to make external hard drive files appear in the home folder obviously.

I'm a noob for life

---

### Post by silverglade00 on 2010-08-19
Make sure you create the External folder first. And you might need to sudo the mount command.

```
mkdir /home/username/External
```

Also, I don't think that sda1 is your external drive. Make sure you have the right one. If that is your main Ubuntu partition, then weird things could happen.

---

### Post by brettg on 2010-08-19
There is nothing wrong with doing that, but alternatively you could simply mount it to the usual* place and then make a symlink to it in your home directory.

* For whatever value of usual floats your boat.

---

### Post by dragonpimpsta on 2010-08-19
is there a terminal command to make that type of link? im doing this remotely

---

### Post by silverglade00 on 2010-08-19
```

cd ~
ln -s /media/external ~/external
```

It should be mounted under /media if it is an external disk.

---


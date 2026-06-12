---
title: "Format partition"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by shahmish on 2011-04-07
Hello all,

I just resized one primary partition using gparted and created another one to try out Natty. Everything worked fine, but for some reason, 2.5GB of space on the new partition is taken up by something, whatever it is. I know it might be the journaling system. I used ext4, so 2,5GB seems pretty big the whole partition is about 80 gigs.

I was wondering what is the safe way to format the partition without risking to format the whole drive by accident.
Oh, and I am aware this can be done through gparted, but GUI seems rather boring. How would I do that through the terminal?
Thanks.

PS: talking of formatting, how can I format a flash drive through the terminal? fdisk or rm? or something else? :)
Thanks again

---

### Post by Paqman on 2011-04-07
You can use the command [mkfs](http://en.wikipedia.org/wiki/Mkfs) to format partitions through the command line. Check out:
```
man mkfs
```
for more info. It'll work on any kind of device (eg: hard drive, flash drive...)

I would still advise using Gparted if you're worried about formatting the wrong thing. You're much more likely to make a mistake doing this in a terminal.

---

### Post by seawolf167 on 2011-04-08
ext formatting keeps 5% for root overhead when formatted - you can turn it off with tunefs (yes I know 5% of 80GB != 2.5GB). Using GParted is a good suggestion if you are concerned about using the correct commands.

---


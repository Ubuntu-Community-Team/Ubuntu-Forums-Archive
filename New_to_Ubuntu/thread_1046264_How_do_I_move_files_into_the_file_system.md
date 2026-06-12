---
title: "How do I move files into the file system?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Limerick on 2009-01-21
It isn't a major issue but I'm trying to install a skin to amsn but the entire amsn is in the file system because I installed it as a package.

My question is: How do I gain permissions to move the files by graphical means?

I know that there is a terminal command to move files but I'm still a bit newbish and I'm not sure how to do that.


If it helps, I'm running Ubuntu 8.10

-Advanced gratitude,
        Limerick

---

### Post by Michael.Godawski on 2009-01-21
hi
graphical way:
```
gksudo nautilus
```
terminal way:
copy:
```
sudo cp /path/to/file /path/to/new/location
```
move:
```
sudo mv /path/to/file /path/to/new/location
```

---


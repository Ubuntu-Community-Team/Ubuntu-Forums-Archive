---
title: "help with Conky"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by tim1970 on 2010-11-30
I am having problems displaying the correct disk usage.  The % used is wrong.  Here is my config file.  Can anybody tell me what I am doing wrong?

---

### Post by mobilediesel on 2010-11-30
> **tim1970 said:**
> I am having problems displaying the correct disk usage.  The % used is wrong.  Here is my config file.  Can anybody tell me what I am doing wrong?

The system monitor and conky are using different numbers to figure the space used. In the help for the system monitor it shows:
```
**Free**
Amount of space not in use
**Available**
Amount of space which can be used
```
The system monitor figures the percent of space used by subtracting free space from total space. Conky figures it by subtracting available space from total space.

Apparently the difference between "free" and "available" are because some space is reserved for root. "Available" is how much space the non-root user can use while "free" is the total that root can use. Conky is calculating the percent used by including the amount reserved for root.

Found a bit of info about it here: [http://ubuntuforums.org/showpost.php?p=5121593&postcount=14](http://ubuntuforums.org/showpost.php?p=5121593&postcount=14)

---


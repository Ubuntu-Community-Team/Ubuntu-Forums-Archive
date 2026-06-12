---
title: "Help Saving in Terminal"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by zenawenliang on 2011-03-27
Ok so I want to reduce my swappiness to 10 and it says to do it permanently I have to open a file in terminal and add a line, but after that how do I save?:KS

---

### Post by howefield on 2011-03-27
> **zenawenliang said:**
> Ok so I want to reduce my swappiness to 10 and it says to do it permanently I have to open a file in terminal and add a line, but after that how do I save?:KS

What/where is "it"

Do you have a link to the instructions that you are following ?

---

### Post by zenawenliang on 2011-03-27
[http://ubuntuforums.org/showthread.php?t=856485](http://ubuntuforums.org/showthread.php?t=856485)

---

### Post by howefield on 2011-03-27
Try Ctrl O

```
man nano 
```

For more nano options

---

### Post by philinux on 2011-03-27
> **zenawenliang said:**
> Ok so I want to reduce my swappiness to 10 and it says to do it permanently I have to open a file in terminal and add a line, but after that how do I save?:KS

Or:-

```
gksu gedit /etc/sysctl.conf
```

---


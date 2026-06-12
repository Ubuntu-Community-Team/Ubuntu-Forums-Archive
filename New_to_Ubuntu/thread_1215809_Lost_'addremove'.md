---
title: "Lost 'add/remove'"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by raysa on 2009-07-17
The 'add/remove' tag at the top of the drop-down Applications menu has disappeared. It's been replaced by a 'Run programs' tag instead. 
What could have caused this, and how can I get it back?

Thanks, Ray

---

### Post by Tholley on 2009-07-17
You might check out this link, I had a similar problem and was able to fix it.
 
[http://ubuntuforums.org/showthread.php?t=1180356](http://ubuntuforums.org/showthread.php?t=1180356)

---

### Post by master_kernel on 2009-07-17
I don't use Xubuntu, but I know Ubuntu uses Synaptic:
```
sudo apt-get install synaptic
```

You could also try:
```
adduser $USER admin
```
as root where $USER is your username.

---

### Post by sisco311 on 2009-07-17
> **raysa said:**
> The 'add/remove' tag at the top of the drop-down Applications menu has disappeared. It's been replaced by a 'Run programs' tag instead. 
What could have caused this, and how can I get it back?

Thanks, Ray

can you run Add/Remove from a terminal?
```
gnome-app-install
```

what's the output of:
```
cat /usr/share/applications/gnome-app-install.desktop
```

---


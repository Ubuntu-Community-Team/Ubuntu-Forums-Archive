---
title: "Copying files to root folder"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-14
Hi,


           I need to copy some images to /usr/share/backgrounds for setting up wallpapers, but the permission in the folder says only root user can do it. I believe I am also a root user since I am using the account that was first created in Ubuntu. Pls help me..

---

### Post by Michael.Godawski on 2009-01-14
hi,

just slip a sudo in front of the command:

```
sudo cp etc etc
```

[http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)

---

### Post by Jeyaganeshdj on 2009-01-14
Is there any way other than typing the command... I mean copy and paste options???

---

### Post by Paqman on 2009-01-14
> **Jeyaganeshdj said:**
> 
I believe I am also a root user since I am using the account that was first created in Ubuntu.

Sort of.

You have the right to take on root privileges temporarily by prefixing terminal commands with sudo. For graphical apps like the file manager (which is called Nautilus), you'll need to launch them with the prefix gksu. For example:
```
gksu nautilus
```

---

### Post by Tibuda on 2009-01-14
> **Jeyaganeshdj said:**
> Is there any way other than typing the command... I mean copy and paste options???

You can open the file browser with root privilegies. Press Alt+F2 and run ```
gksudo nautilus
```

Edit: paqman was faster

---


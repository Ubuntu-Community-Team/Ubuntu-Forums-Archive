---
title: "How to uninstall Python 2.7 and install 3.2.1"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Udavid on 2011-08-14
Hello forum,
I just checked Ubuntu software center that Python 2.7 is preinstalled with Ubuntu. I just to remove it but it prompted that "failed to download pack files". Is there any thing I can do to get rid of Python 2.7? 
Thanks.
[IMG]http://farm7.static.flickr.com/6080/6041049799_55215ac385_z.jpg[/IMG]
[IMG]http://farm7.static.flickr.com/6082/6041049851_eb9e40f981_z.jpg[/IMG]

---

### Post by babakott on 2011-08-14
You don't want to get rid of 2.7. It will break your system. Just install 3.2.1 along side it.
In your scripts just call it as #!/usr/bin/python3.2

---

### Post by Anonymous is Incognito on 2011-08-14
> **Udavid said:**
> Is there any thing I can do to get rid of Python 2.7? 

Get to a terminal and type the following followed by enter.

- removed -

> **babakott said:**
> You don't want to get rid of 2.7. It will break your system. Just install 3.2.1 along side it.
In your scripts just call it as #!/usr/bin/python3.2

EDIT: Thanks for pointing that out.

---

### Post by Udavid on 2011-08-14
> **babakott said:**
> You don't want to get rid of 2.7. It will break your system. Just install 3.2.1 along side it.
In your scripts just call it as #!/usr/bin/python3.2
Thanks. But I just want to know how to install 3.2.1 along with Python 2.7. Can I just open the software center and choose Python 3.2 to install and then it will be okay.

---

### Post by babakott on 2011-08-14
If I am understanding you correctly, open the terminal and type
```
sudo apt-get install python3.2
```

**edit** Reread your post. Yes you can install it along side 2.7 with no problems.

---


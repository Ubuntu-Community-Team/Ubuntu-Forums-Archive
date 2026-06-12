---
title: "File Sharing"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by djmac on 2010-02-22
I was wondering if there was any alternatives to Samba for networking between ubuntu machines? (I have just a small home network with three ubuntu PC's).

I haven't had any problems with Samba, it just seems a little convoluted, connecting ubuntu machines to each other through a Windows network. Just a curiosity. (And my understanding of networking is very limited)

Thankyou.

---

### Post by nothingspecial on 2010-02-22
Sharing between ubuntu machines is very straight forward.

```
sudo apt-get install openssh-server openssh-client
```

Then in your menu, go places > connect to server

In the first box choose ssh

in the second box put the username and ipaddress of the other machine eg ```
bob@192.168.1.2
```

You can find the ipaddress of the other machine by right clicking on the network icon and choosing connection information.

You can add a bookmark so that you can connect by clicking on an entry in your places menu.

---

### Post by djmac on 2010-02-22
Thanks alot!! That is exactly what I was after!

---

### Post by netopalis45 on 2010-03-11
is there any way of sharing this with Windows computers as well?

---

### Post by marshmallow1304 on 2010-03-11
> **netopalis45 said:**
> is there any way of sharing this with Windows computers as well?

[http://ubuntuforums.org/showthread.php?t=1027820](http://ubuntuforums.org/showthread.php?t=1027820)

---


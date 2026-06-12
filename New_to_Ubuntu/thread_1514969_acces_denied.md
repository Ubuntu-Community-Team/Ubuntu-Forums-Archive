---
title: "acces denied"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by andyhart on 2010-06-21
I tried to configure a file and it came up acces denied  /etc/network/interfaces can you tell me how to get into the file thanks.
I'm using server 10.4

---

### Post by lolzwut on 2010-06-21
use sudo

example:

sudo gedit /etc/network/interfaces

i don't know what editor you want though.

---

### Post by -humanaut- on 2010-06-21
If your going to use a graphical editor like gedit your should use gksu instead of sudo.

---

### Post by bodhi.zazen on 2010-06-21
Well, on a server one generally does not have X , so gedit and gksu are not the best of options.

```
sudo -e  /etc/network/interfaces
```

In Ubuntu 10.04 the editor should be nano.

Earlier versions were vim

---

### Post by andyhart on 2010-06-22
> **bodhi.zazen said:**
> Well, on a server one generally does not have X , so gedit and gksu are not the best of options.

```
sudo -e  /etc/network/interfaces
```

In Ubuntu 10.04 the editor should be nano.

Earlier versions were vim

thank you that worked

---


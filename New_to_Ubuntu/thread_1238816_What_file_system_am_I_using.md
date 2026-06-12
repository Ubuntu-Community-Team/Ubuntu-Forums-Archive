---
title: "What file system am I using?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by triplesick on 2009-08-12
How can I check whether my partition is ext3, ext4, etc?

I'm using Ubuntu 9.04.

---

### Post by miwaypet on 2009-08-12
```
sudo gedit /etc/fstab
```

---

### Post by Bachstelze on 2009-08-12
> **miwaypet said:**
> ```
sudo gedit /etc/fstab
```

A simple [font=monospace]cat /etc/fstab[/font] will do. No need to run a text editor as root.

---

### Post by zeroseven0183 on 2009-08-12
Go to **System** > **Administration** > **System Monitor** > then click on **File Systems **tab.
You'll see there under the Type column which file system you're using.

---

### Post by triplesick on 2009-08-12
> **zeroseven0183 said:**
> Go to **System** > **Administration** > **System Monitor** > then click on **File Systems **tab.
You'll see there under the Type column which file system you're using.
Thank you, sir!  An easy GUI approach!

---


---
title: "sudo error"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by node2network on 2011-04-29
When I type "sudo apt-get update", gnome-terminal shows "sudo: unable to resolve host foofoo".

How to fix this ?

--/etc/hosts--

127.0.0.1	localhost
127.0.0.1	foofoo

--/etc/hostname--

foofoo

---

### Post by mikewhatever on 2011-04-29
Have you changed it or something?

---

### Post by Elfy on 2011-04-29
Try editing the file and changing foofoo to the name of your machine. Mine is called hobgoblin and has a line 

127.0.0.1		localhost.localdomain hobgoblin localhost

Back up the file from a terminal

```
sudo cp /etc/hosts /etc/hosts.2904
gksudo gedit /etc/hosts
```

Make the file read 

127.0.0.1 *yourname* localhost

If you're not sure of the name of your machine it'll be in the terminal eg

[hobgoblin@hobgoblin ~]$

---

### Post by sikander3786 on 2011-04-29
Try

```
gksudo gedit /etc/hosts
```

And replace 127.0.0.1 for foofoo with 127.0.1.1.

```
127.0.0.1 localhost
127.0.1.1 foofoo
```

Save and close and try again.

---


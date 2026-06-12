---
title: "[SOLVED] running Deb command?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Ant68 on 2008-12-08
Hi,
I am having troubles with NetworkManager Applet 0.7.0. I have been advised to set up wicd which I have the intention to do. I am booting in a recovery mode (option Root) because every time I boot and log in Gnome, I have the NetworkManager to freeze Gnome. 

It then need to run:
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

but I am getting:
-bash: deb: command not found.


the Deb command does not seems to work. 

How should I do?

---

### Post by lovelyvik293 on 2008-12-08
I think you have to add these lines in the software source file.
Not have to run this deb thing.
```

sudo vim /etc/apt/sources.list

```
And add the  lines.
```

deb http://apt.wicd.net intrepid extras

```

---

### Post by handydan918 on 2008-12-08
> sudo gedit /etc/apt/sources.list

vim? For someone who thinks deb is a command?

---

### Post by lovelyvik293 on 2008-12-08
@handydan918 :lolflag:
First of all read the post from Ant68 :)
He doesn't have the GUI,so what option he have...
He can only use vim or the nano.He don't have the gedit.

---

### Post by Ant68 on 2008-12-08
thanks, I do not have access to gnome...

vim:

How will I save and quit?

:q!

or what?

---

### Post by lovelyvik293 on 2008-12-08
use the :wq

---


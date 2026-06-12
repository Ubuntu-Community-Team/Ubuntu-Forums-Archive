---
title: "Sound preference does not open"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by ssdt on 2010-08-09
Why does not the sound preference open when I click on it from the sound icon in the top menu? I am using Ubuntu 10.0, does anyone know any bug like this?

---

### Post by MCVenom on 2010-08-09
Does it run if you click Sound under System>Preferences?

---

### Post by ssdt on 2010-08-10
It does not exist in the preference.

---

### Post by MCVenom on 2010-08-10
> **ssdt said:**
> It does not exist in the preference.
Thanks ssdt, can you run

```
gnome-volume-control
```

In the terminal? If Sound Preferences is installed, it should start up; if not, you'll probably get a command not found error. If so, run this command:

```
sudo apt-get install gnome-media
```

That should install Sound Preferences.

---

### Post by ssdt on 2010-08-10
Thank you. I mistakenly uninstalled gnome-media and after reinstalling it it works. Thank you again for the help.

---

### Post by MCVenom on 2010-08-10
> **ssdt said:**
> Thank you. I mistakenly uninstalled gnome-media and after reinstalling it it works. Thank you again for the help.
No problem man :D

---

### Post by Anoopsmohan on 2011-09-24
I did the same mistake, this information is very useful for me. Thank you very much for the information...

---

### Post by technosysind on 2011-09-24
please mark this thread as Solved ( thread tools)

---


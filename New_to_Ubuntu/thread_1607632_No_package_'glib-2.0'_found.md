---
title: "No package 'glib-2.0' found?"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Flynsarmy on 2010-10-28
I'm trying to compile kildclient 2.10.0 on 32-bit Ubuntu 10.10. When i type ./configure I get the following error:
```
checking for GTK... no
configure: error: Package requirements (glib-2.0 >= 2.14.0
                       gthread-2.0 >= 2.10.0
                       gtk+-2.0 >= 2.18.0) were not met:

No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gtk+-2.0' found
```

What do I need to install to fix this? I've got ubuntu-dev-tools installed.

EDIT: Solved - had to install libgtk2.0-dev

---

### Post by Cajhne on 2011-06-13
That produced one further error for me, after a lot of searching, I found another thing that was missing (compiling for Ubuntu 10.10)

The following additional two commands worked for me:

sudo apt-get install libperl-dev
sudo apt-get install libgtk2.0-dev

Hope this helps someone.

---

### Post by omghahalol on 2011-12-03
> **Cajhne said:**
> That produced one further error for me, after a lot of searching, I found another thing that was missing (compiling for Ubuntu 10.10)

The following additional two commands worked for me:

sudo apt-get install libperl-dev
sudo apt-get install libgtk2.0-dev

Hope this helps someone.

That worked, thanks a lot.

---

### Post by Anarchj on 2012-08-05
Thank you!

---


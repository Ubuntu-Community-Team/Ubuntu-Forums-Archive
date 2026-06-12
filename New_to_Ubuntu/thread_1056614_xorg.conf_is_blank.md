---
title: "xorg.conf is blank??"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by risingpowers on 2009-01-31
I need to check my xorg.conf for something but the file is a blank page. D: sudo dpkg-reconfigure xserver-xorg or variant of that command does nothing. Help?

---

### Post by taurus on 2009-01-31
Are you looking at the right file?  Yes, it is small but should not be blank.

```
cat /etc/X11/xorg.conf
```

---

### Post by vikramaditya on 2009-01-31
Make sure you capitalise the "X11" part, hence...
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by risingpowers on 2009-01-31
> **taurus said:**
> Are you looking at the right file?  Yes, it is small but should not be blank.

```
cat /etc/X11/xorg.conf
```

Yes, it is the correct file, and unfortunately it is blank.

---

### Post by taurus on 2009-02-01
Can you post the output of this command from a terminal?

```
ls -la /etc/X11
```

---

### Post by vikramaditya on 2009-02-01
I remember reading somewhere that 8.10 (Intrepid) integrates hardware info differently.  Are you using 8.10?

---

### Post by anjilslaire on 2009-02-01
Intrepid does manage xorg.conf differently, but it does exist, and iis pretty sparse but not empty. The OP is not reading /etc/X11/xorg.conf

---

### Post by risingpowers on 2009-02-01
> **anjilslaire said:**
> Intrepid does manage xorg.conf differently, but it does exist, and iis pretty sparse but not empty. The OP is not reading /etc/X11/xorg.conf

OP is reading xorg.conf. I might be a Linux noob but I'm not stupid.

```
zachary@zachary-laptop:~$ ls -la /etc/X11
total 72
drwxr-xr-x   9 root root  4096 2009-01-31 18:15 .
drwxr-xr-x 122 root root 12288 2009-01-31 18:12 ..
drwxr-xr-x   2 root root  4096 2009-01-31 15:02 app-defaults
drwxr-xr-x   2 root root  4096 2008-10-29 11:25 cursors
-rw-r--r--   1 root root    14 2008-10-29 11:22 default-display-manager
drwxr-xr-x   6 root root  4096 2008-10-29 11:16 fonts
lrwxrwxrwx   1 root root    13 2009-01-31 04:27 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2008-10-29 11:17 xinit
drwxr-xr-x   2 root root  4096 2009-01-31 15:00 xkb
-rw-r--r--   1 root root  1053 2009-01-31 04:25 xorg.conf
-rw-r--r--   1 root root  1053 2009-01-31 18:10 xorg.conf.20090131181025
-rw-r--r--   1 root root  1053 2009-01-31 18:15 xorg.conf.20090131181517
drwxr-xr-x   2 root root  4096 2008-10-29 11:09 Xresources
-rwxr-xr-x   1 root root  3730 2008-10-23 03:40 Xsession
drwxr-xr-x   2 root root  4096 2009-01-31 15:02 Xsession.d
-rw-r--r--   1 root root   265 2008-10-23 03:40 Xsession.options
-rw-------   1 root root   614 2008-10-29 11:09 Xwrapper.config

```

---

### Post by taurus on 2009-02-01
> **risingpowers said:**
> OP is reading xorg.conf. I might be a Linux noob but I'm not stupid.

```
zachary@zachary-laptop:~$ ls -la /etc/X11
total 72
drwxr-xr-x   9 root root  4096 2009-01-31 18:15 .
drwxr-xr-x 122 root root 12288 2009-01-31 18:12 ..
drwxr-xr-x   2 root root  4096 2009-01-31 15:02 app-defaults
drwxr-xr-x   2 root root  4096 2008-10-29 11:25 cursors
-rw-r--r--   1 root root    14 2008-10-29 11:22 default-display-manager
drwxr-xr-x   6 root root  4096 2008-10-29 11:16 fonts
lrwxrwxrwx   1 root root    13 2009-01-31 04:27 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2008-10-29 11:17 xinit
drwxr-xr-x   2 root root  4096 2009-01-31 15:00 xkb
**[COLOR="Blue"]-rw-r--r--   1 root root  [SIZE="5"]1053[/SIZE] 2009-01-31 04:25 xorg.conf[/COLOR]**
-rw-r--r--   1 root root  1053 2009-01-31 18:10 xorg.conf.20090131181025
-rw-r--r--   1 root root  1053 2009-01-31 18:15 xorg.conf.20090131181517
drwxr-xr-x   2 root root  4096 2008-10-29 11:09 Xresources
-rwxr-xr-x   1 root root  3730 2008-10-23 03:40 Xsession
drwxr-xr-x   2 root root  4096 2009-01-31 15:02 Xsession.d
-rw-r--r--   1 root root   265 2008-10-23 03:40 Xsession.options
-rw-------   1 root root   614 2008-10-29 11:09 Xwrapper.config

```

As you can see, it's not empty.  Again, maybe there is not a whole lot in there but there should be something in it.

```
cat /etc/X11/xorg.conf
```

---

### Post by risingpowers on 2009-02-01
> **taurus said:**
> As you can see, it's not empty.  Again, maybe there is not a whole lot in there but there should be something in it.

```
cat /etc/X11/xorg.conf
```

Why isn't anything displayed in nano or gedit? The cat command shows what I should see in those programs...

---

### Post by taurus on 2009-02-01
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by risingpowers on 2009-02-01
I must be stupid. D: I was typing /ect/ rather than /etc/. How embarrassing...

Thanks all for your effort, I finally have my display working correctly. :D

---


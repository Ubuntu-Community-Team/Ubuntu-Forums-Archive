---
title: "Folders don't open &amp; no icons on desktop"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by adobrakic on 2009-05-29
I have Ubuntu 9.04 64bit, and I can't see any icons on my desktop. I can't highlight anything on my desktop, nor can I right-click on it. I've tried going to nautlius > preferences through 'gksudo-editor', but that didn't fix it.

I now realized that I can't open folders either. When I go to Places -> Home Folder, nothing happens. I've also tried opening a mounted folder, and nothing happens.

Any ideas?

---

### Post by SunnyRabbiera on 2009-05-29
Sounds like an issue with nautilus, nautilus controls stuff like desktop icons.

---

### Post by Volt9000 on 2009-05-29
Sounds like something really broke in your installation.

Have you added or changed anything lately? Perhaps got a bit too curious with some commands? ;)

---

### Post by adobrakic on 2009-05-31
Nah, I haven't done anything. I used wubi to install it though, so that may be it. I didn't really do anything other than install the basics (ubuntu-restricted-extras, etc.) and enabled compiz/emerald.

---

### Post by adobrakic on 2009-06-07
bump

---

### Post by jrox717 on 2009-06-07
I would try simply reinstalling Nautilus. 

In the terminal:
```
 sudo apt-get install -reinstall nautilus 
```

---

### Post by mrbiggbrain on 2009-06-07
i used wubi + 9.04 (upgraded from 8.10) + 64-bit and have had not a hitch... so it works in theory

---

### Post by adobrakic on 2009-06-07
Actually, I just went into terminal and did "sudo nautilus" and that command fixed it, heh.

Now everything works, however when I save things, they don't show. For example, if I save a picture on my desktop from Firefox, it doesn't show up. But If I go to imageshack to upload a picture, and go to 'Desktop,' the picture's there.

Bah.

---

### Post by ad_267 on 2009-06-07
That's because you ran "sudo nautilus". You should have just run "nautilus". Running sudo nautilus will show the root users desktop. Try restarting or logging out and in again and it should fix things.

Using sudo runs a command as root, you just want to run nautilus with your own user account.

---

### Post by ethoxyethaan on 2009-06-07
Ok, open a terminal and give me the output of:

ls -al ~/ | grep Desktop

it should display:

drwxr-xr-x  2 user group   4096 2009-06-08 03:27 Desktop

(755) your user and your group.

also check your home directory:

ls -l /home/

it should be 755 aswell

**Do not run nautilus as root, everything that forks from nautilus will run under root permissions and this is insecure**

---

### Post by adobrakic on 2009-06-07
ad_267, just doing 'nautilus' gives me:

```
ado@ubuntu:~$ nautilus
/home/ado/.themes/Truth+/gtk-2.0/gtkrc:196: error: invalid string constant "theme-combo", expected valid string constant
**
Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted
ado@ubuntu:~$ 

```

ethoxyethaan,

```
ado@ubuntu:~$ ls -al ~/ | grep Desktop
drwxr-xr-x  3 ado  ado     4096 2009-06-07 22:24 Desktop
ado@ubuntu:~$ 

```

```
ado@ubuntu:~$ ls -l /home/
total 4
drwxr-xr-x 37 ado ado 4096 2009-06-07 22:25 ado
ado@ubuntu:~$ 

```

---

### Post by adobrakic on 2009-06-08
bizzump

---

### Post by yajnas on 2009-06-11
Try this :

open Configuration Editor (Applications > System tools > Configuration editor)
In the left side pane apps > nautilus > desktop.

Now in the right side pane, look for a key named "trash_icon_name". Double click on it and in the pop-up box, change type to String and value to "Trash" (without quotes).

Below trash_icon_name, double click on trash_icon_visible. In the pop up window that opens, make sure that the value is set to true. If it is change it to false and then to true. Save and exit.

open a terminal and type nautilus.

---

### Post by adobrakic on 2009-06-12
Trash_icon_name can't be changed to letters, it's a 1 by default.

---


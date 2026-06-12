---
title: "changing writing permission onto /var/www folder"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-18
just installed LAMP on my ubuntu desktop... but i can't add or change anything on the /var/www folder...

what's the easiest way of making it writable to? or how can i set my self to root user so i can modify or add stuff to the folder (on GUI mode)

---

### Post by xjcannonx on 2008-12-18
GUI ```
gksudo nautilus
```

---

### Post by talsemgeest on 2008-12-18
> **manuleka said:**
> just installed LAMP on my ubuntu desktop... but i can't add or change anything on the /var/www folder...

what's the easiest way of making it writable to? or how can i set my self to root user so i can modify or add stuff to the folder (on GUI mode)
To open the folder in GUI mode, you can type this into a terminal (or run it using alt-F2): ```
gksudo nautilus
```
To open a text file in GUI mode with root privileges, you type: ```
gksudo gedit <file>
``` Where <file> is the name of the file that you want to open.

Hope this helps :)

---

### Post by manuleka on 2008-12-18
what's gksudo? can't i just type in sudo gedit?

---

### Post by xjcannonx on 2008-12-18
yes you can

---

### Post by the_hardy_kid on 2008-12-18
You could try:

```
sudo chown your-user-name /var/www/
```

---

### Post by manuleka on 2008-12-18
so what's the diff between gksudo and sudo?

---

### Post by talsemgeest on 2008-12-18
gksudo is for use with GUI programs, sudo for command line. It is safer to use gksudo than sudo for GUI applications.

---

### Post by nothingspecial on 2008-12-18
gksudo is for guis sudo is for the shell.

---

### Post by randlieb on 2008-12-29
To take this a step further, is there a way to copy the var/www directory to my home directory and make it writable? I seem to remember seeing a thread to that effect somewhere but can't find it now.

---

### Post by talsemgeest on 2008-12-29
> **randlieb said:**
> To take this a step further, is there a way to copy the var/www directory to my home directory and make it writable? I seem to remember seeing a thread to that effect somewhere but can't find it now.
Take a look [here.](http://ubuntuforums.org/showthread.php?t=346337)

---


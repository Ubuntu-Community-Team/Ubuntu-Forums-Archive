---
title: "auto script from home directory"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by akkad on 2009-04-23
i have a script in my directory "/home/myuser/folder/script.sh", how can let this script to run on boot automatically.

---

### Post by .nedberg on 2009-04-23
If you want it to run when you log in, you can go to System -> Sessions and add it to "Startup programs".

If you want to run it at boot you can add a line in /etc/rc.local before "exit 0"

---

### Post by akkad on 2009-04-23
am using ubuntu server, so i want to be on boot but using command line ??

---

### Post by .nedberg on 2009-04-23
You can use nano to edit the file:
```

sudo nano /etc/rc.local

```
Add a line with
```

/home/myuser/folder/script.sh

```
before "exit 0" at the bottom. Save with Ctrl+o (the hit enter), exit with Ctrl+x.

If your script is something that goes into a loop, or doesn't return in any other way, use this in rc.local
```

/home/myuser/folder/script.sh &

```

---

### Post by MOBIDON1 on 2011-01-30
I am using ubuntu 10.04 and i want to make "autoupdate" script at home and schedule it to run at 2:15am.
Command line plz...?

---

### Post by EkiLibRiuM on 2012-09-27
I am using ubuntu 10.04 too nd i try to execute some command's but the answer is not  a located file ...i don' know what is wrong but i have some probel mto be root too...

---


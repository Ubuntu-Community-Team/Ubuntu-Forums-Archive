---
title: "ftp help"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by lad3391 on 2009-01-12
im just messing around trying to create a small ftp server to transfer stuff with my friends and i need some help, so thanks in advance ;)

so i installed gadmin-proftpd with

```
sudo apt-get install proftpd gproftpd
```

but when i go to applications->system tools-> gadmin-proftpd i get "failed to execute child process "su-to-root" (no such file or directory)"

if i go to edit menus, and check the command it says "su-to-root -X -c /usr/sbin/gadmin-proftpd"

when i go to terminal and type sudo gadmin-proftpd i get "segmentation fault"

dell inspiron 6000 ubuntu 8.10

ive been reading here:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Bachstelze on 2009-01-12
Try:

```
gksudo /usr/sbin/gadmin-proftpd
```

---

### Post by omg3969 on 2009-01-12
Easter Day in childhood

Do you remember the egg and candy you [ buy wow gold ](http://www.mmoinn.com) on Easter Day in childhood?  [ cheap wow gold ](http://www.mmoinn.com) are always fresh on our minds. Why not prepare some gifts now to refresh those sweat memories? Bring home the bunny, colored eggs and [ wow gold](http://www.mmoinn.com) to celebrate the Easter Day! MMOinn wishes you a good Easter Day. [ wow power leveling ](http://www.mmoinn.com/mmoinn_pl/)

---

### Post by lad3391 on 2009-01-12
it looked like it tried to start (a window flashed up for less than a second) then went away. i was left with a new line in terminal, no errors or anything

---

### Post by Bachstelze on 2009-01-12
Then it is most likely a bug in the application in question. You can go see on Launchpad if this bug has already been reported, and if not, file it yourself. ;)

---

### Post by lad3391 on 2009-01-12
okay will do. i wish it was the usual case where my lack of ubuntu knowledge is the problem, this forum seems to remedy that pretty quick ;)

---


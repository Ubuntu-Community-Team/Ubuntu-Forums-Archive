---
title: "Rsync commands"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by krisrae675 on 2010-01-19
I am using Rsync within a local network of 46 computers.
Our main server has an IP of 192.168.1.60:8010 and our 46 clients range from 192.168.1.1 to 192.168.1.46.
They are all taking there updates from the main server but i need the 46 clients to send there log reports back to the main server.
I can run an update from the main server which currently uses the command 192.168.1.(client number)::ccobex/
which pulls all data from that folder.
Is there a way of adding the range of ip's so that it will round robin through them all.
i.e a command string i can use to make it look at all the ip's from 1 to 46

---

### Post by KeLa on 2010-01-19
I shell script you can use this:

```
for ((  i = 1 ;  i <= 46;  i++  ))
 do
   "rsync ... 192.168.1.$i:ccobex"
 done
```

That will do all ip's from 1 to 46

---

### Post by J V on 2010-01-19
That has nothing to do with rsync?

You can add cronjobs on every client computer to email (or samba) their logs once a day or so...

---

### Post by krisrae675 on 2010-01-19
> **KeLa said:**
> I shell script you can use this:

```
for ((  i = 1 ;  i <= 46;  i++  ))
 do
   "rsync ... 192.168.1.$i:ccobex"
 done
```

That will do all ip's from 1 to 46

Thx for your reply
the code ((  i = 1 ;  i <= 46;  i++  )) do i enter this in the rsyncd.config folder?

---

### Post by KeLa on 2010-01-19
No, you do shell script file and put it there and run it
between lines do and done are the rsync command you want to run.

---


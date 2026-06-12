---
title: "Can't replace the httpd.conf file"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by alfuego on 2011-04-28
I am trying to configure the ubuntu server and coulnd't edit the httpd.conf file at first then I copied it into a text editor and saved it on desktop. I cannot replace the new conf file I created with the one in the etc folder. Any suggestions?

---

### Post by fdrake on 2011-04-28
> **alfuego said:**
> I am trying to configure the ubuntu server and coulnd't edit the httpd.conf file at first then I copied it into a text editor and saved it on desktop. I cannot replace the new conf file I created with the one in the etc folder. Any suggestions?
on the terminal(if your server edition has a GUI installed):
```

sudo su
<create backup>
cp /etc/httpd.conf.bak
gedit /etc/httpd.conf
<change and save>
```

---

### Post by alfuego on 2011-04-28
thanks drake,
I got the bak file in the same folder as the original but I can't replace the original conf file with it.  I can't rename anything or delete anything those options are grayed out.  Any suggestions?

---

### Post by fdrake on 2011-04-28
> **alfuego said:**
> thanks drake,
I got the bak file in the same folder as the original but I can't replace the original conf file with it.  I can't rename anything or delete anything those options are grayed out.  Any suggestions?

with sudo u have full access rights to the system. the only reason that prevents you from not being able to change that file is that is already running or being used by another program.. do you know witch one may be using it? can you stop it and restart later.

---

### Post by fdrake on 2011-04-28
do you have a program called httpd runniing?
type:
```
ps -e|less
```
and post here the output

---


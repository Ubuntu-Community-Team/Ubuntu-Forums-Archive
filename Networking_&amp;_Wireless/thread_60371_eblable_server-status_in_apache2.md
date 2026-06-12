---
title: "eblable server-status in apache2"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by -DarkMind- on 2005-08-27
i edit the apache2.conf and appear this:

```
<Location /server-status>
    SetHandler server-status
    Order allow,deny
    Allow from 127.0.0.1
</Location>
``` 

i go to [http://myserversdir/server-status](http://myserversdir/server-status) and says:


```
Forbidden

You don't have permission to access /server-status on this server.
``` 


why?  :???:

---

### Post by -DarkMind- on 2005-08-29
someone?

---

### Post by hfranco on 2006-04-16
I have the same problem.  Did you ever figure this out?

---

### Post by fdoving on 2006-04-17
Did you try to go to [http://127.0.0.1/server-status](http://127.0.0.1/server-status) ?

---

### Post by hfranco on 2006-04-17
That's exactly what I did but I'm getting: Forbidden

You don't have permission to access /server-status on this server.

I tried [http://localhost/server-status](http://localhost/server-status) just in case but it still doesn't work.

---

### Post by fdoving on 2006-04-18
Are you sure the IP of localhost is 127.0.0.1 in your /etc/hosts file?

Is the loopback interface up? (ifconfig) 

- Frode

---

### Post by xcomm on 2008-02-22
Hi Forum,

You have to remove the ` localhost.localdomain` part from your /etc/hosts file created during installation.

vi /etc/hosts
#from
 127.0.0.1 localhost.localdomain localhost servername
#to
 127.0.0.1 localhost servername

/etc/init.d/apache2 restart

Regards, xcomm

---


---
title: "No Samba in init.d?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by HBE66 on 2010-11-09
ok next problem :popcorn:

eventhough ive installed ubuntu server 10.10 i took the liberty to use the following guide:
[https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html)

now i have a problem: when i get to step 8 of PDC[B]

sudo /etc/init.d/samba restart[/B]
i find out, that there is no samba in init.d :confused:

and yep, i performed step 1

has anyone got a clue how i can get my dc running soon?
thank you!

---

### Post by Morbius1 on 2010-11-09
A couple of things have happened sine that howto:

The samba service has been replaced by it's component parts: smbd and nmbd. And samba is now controlled by upstart.

Todays equivalent command is:
```
sudo service smbd restart
```

---

### Post by HBE66 on 2010-11-09
aah alright thanx!

---


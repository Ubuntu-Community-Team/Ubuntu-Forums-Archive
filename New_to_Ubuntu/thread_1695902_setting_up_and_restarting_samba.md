---
title: "setting up and restarting samba"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by jonneymendoza on 2011-02-26
Hi. i am trying to get samba working on my ubuntu server box and i am having issues trying to restart the samba server.

what happens is that when  i type "sudo /etc/init.d/samba restart"  i get an error saying this:

sudo: /etc/init.d/samba: command not found


i followed teh exact guide from here [https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html)

i then browsed in the  /etc/init.d/ location and could not find samba there! however, there is a /etc/samba/smb.conf file as i was able to edit it fine.

---

### Post by roninbv on 2011-02-26
the service name for samba is smbd
try the following command:

sudo service smbd restart

that should do it for you. You can also stop or start the service by replacing restart with stop or start respectively.

good luck!

---

### Post by CharlesA on 2011-02-26
Samba has two parts in Ubuntu - smbd and nmbd.

You can manage them with this command:

```
sudo service smbd start|stop|restart
sudo service nmbd start|stop|restart
```

---


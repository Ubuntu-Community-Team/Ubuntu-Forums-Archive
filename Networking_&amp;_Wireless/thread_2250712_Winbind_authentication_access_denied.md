---
title: "Winbind authentication access denied"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by 7tupel on 2014-10-30
Hi,

i have the following problem. In our network we have about 200 Clients, mostly windows 7 and Ubuntu 14.04. The school just got new maschines and we migrated from an old Linux Mint to Ubuntu. We use a central user management via Samba/Winbind server hosted on a Debian Wheezy maschine. Now while authentication works fine in windows 7 it does not work in Ubuntu. Winbind does not use Kerberos/AD yet to have one error source less.

I set the client machines up according to this [guide]("http://wiki.ubuntuusers.de/Samba_Winbind") (german). When i try to login as a domain user i get an ```
access denied
``` error. Running ```
getent passwd
``` works fine and returns a full list of all my domain users.

After i installed and configured the client maschine the first time after restarting winbind domain login worked just fine. After rebooting the maschine i got the access denied error (getent passwd still works). 

I figured out running
```

net rpc join -U user%password
service winbind restart

```
domain login will work again. But just until i reboot.

As a quick and dirty solution i put those commands in a script getting executed on startup/reboot. According to my log the script runs without errors. But still, domain login does not work. But if i run the script manually over command line after the startup/reboot then i can login with my domain user. Again, after shutting down the maschine i still have the same problem. 

My samba/winbind logs give me no clue to what might be the problem. I hope that you have an idea what might cause the problems and how to solve it. I'm a bit in a hurry because it must be fixed before monday when school starts again.

Hope you can help me, cheers sieben

---


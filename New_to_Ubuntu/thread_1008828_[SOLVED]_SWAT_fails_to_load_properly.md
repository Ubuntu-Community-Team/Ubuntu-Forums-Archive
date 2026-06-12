---
title: "[SOLVED] SWAT fails to load properly"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2008-12-11
Hi, my new server system has been on line about two weeks. I currently have ALL my MUSIC and PHOTOS moved over to the system. (Ubuntu 8.10 server edition, SAMBA ver. 3.2.3
 loaded on an Athlon 1800+ system with 1 meg memory).

I have what I believe to be a problem?? that I cannot resolve nor find help with and I need suggestions/help from this fantastic linux community.


I have SWAT loaded and accessible BUT I evidently received the VOLKSWAGON VERSION instead of the CADILLAC VERSION.

I have tabs for:
HOME
STATUS
VIEW
PASSWORD

I **DO NOT** HAVE TABS FOR:
GLOBAL
SHARES
PRINTERS and
WIZARD.

Not much of a tool (as is) without the ability to create a SHARES.
What do I need to do to get these 4 tabs to appear on my SWAT screen?

Removal and re-installation made no difference.


THANKS in advance for your help.

CarolinaGuy

---

### Post by cariboo on 2008-12-12
You have to access SWAT as root in order to get the full menu. You could try:

```
sudo -i
```

and start then firefox as root. I find the latest version of /etc/samba/smb.conf is so well commented, that it is easily edited in a text editor.

Jim

---

### Post by CarolinaGuy on 2008-12-12
cariboo907,

THANKS for your help. Sudo -i made no difference.

I'm accessing the server for startup & log-on with putty from a Win Xp client. Firefox is on the Win XP client.

CarolinaGuy

---

### Post by CarolinaGuy on 2008-12-12
If I enter these hyperlinks into my browser I can access the pages.

But, the icons to access them are still missing from the initial SWAT pages @ [http://ubuntu8:901/](http://ubuntu8:901/)

[http://ubuntu8:901/wizard](http://ubuntu8:901/wizard)
[http://ubuntu8:901/shares](http://ubuntu8:901/shares)
[http://ubuntu8:901/printers](http://ubuntu8:901/printers)

CarolinaGuy

---

### Post by hyper_ch on 2008-12-12
from what I remember swat really needs an activated root account to login. is there a reason why you don't write the config to the /etc/samba/smb.conf file but are using swat?

---


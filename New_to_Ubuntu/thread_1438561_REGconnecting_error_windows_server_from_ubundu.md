---
title: "REG:connecting error windows server from ubundu"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by vaskbtech on 2010-03-25
Hi,
When i connect windows server 2003 from ubuntu these error displayed .

[FONT=Verdana]When i installing the tsclient, by executing these following command from a Terminal window:[/FONT]
 [FONT=Verdana]*sudo apt-get install tsclient*[/FONT]


[FONT=Verdana][I]When i run these command the following error displayed.
[/I][/FONT]

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?:popcorn:

---

### Post by jimv on 2010-03-25
Make sure that you have all software installing programs (like Synaptic, Add/Remove Applications, Update-Manager, etc) closed.  They will lock dpkg if they are open.  If you can't tell if they are open, try rebooting.

---


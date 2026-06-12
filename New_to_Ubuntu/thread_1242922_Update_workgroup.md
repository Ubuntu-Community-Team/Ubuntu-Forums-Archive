---
title: "Update workgroup"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2009-08-17
I have built a new system computer with WIN 7 as the operating system.

The work group on the New Computer is --- WORKGROUP
On my ubuntu 8.04 server the work group is ---MSHOME.

I want to change MSHOME over to WORKGROUP. What do I need to change on my server to enable these 2 machines to talk to each other?

THANKS in advance for your help.

CarolinaGuy

---

### Post by coggins on 2009-08-17
edit the samba configuration file on the server
```
sudo pico /etc/samba/smb.conf
```
after all the preamble, the first setting under [global] should be workgroup=MSHOME - change that to WORKGROUP.
CTRL-O to save, CTRL-X to exit
restart samba
```
sudo /etc/init.d/samba restart
```

---

### Post by CarolinaGuy on 2009-08-17
coggins,

A very BIG THANK YOU. I'm up and running.

CarolinaGuy

---


---
title: "Samba help please"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by timbim on 2009-07-07
I've got an XP desktop, with a folder shared.  I have a laptop running ubuntu 9.04 with the latest samba installed.  It needs to see the share on the desktop.  If I look in places > Network > Windows Network, I can see MSHOME and WORKGROUP, MSHOME being the domain I'm using.  If I try to open it, I get an error.

Sorry for being a noob, but the instructions on the ubuntu help page are a bit confusing.

Many thanks
Tim

---

### Post by LowSky on 2009-07-07
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)
that should help with set up

find out the Routers IP address for the windows PC, something like 192.168.0.2 

take that address and open file manager and type smb://192.168.0.2 (or what ever the win PC address is)

---

### Post by cariboo on 2009-07-07
You need  to change the workgroup in /etc/samb/smb.conf to match MSHOME. Press Alt-F2 and type:

```
gksu gedit /etc/smaba/smb.conf
```

After you have changed the workgroup you need to restart samba in order for the change to take place. Open an Applications-->Accessories-->Terminal and type:

```
sudo /etc/init.d/samba restart
```

---

### Post by timbim on 2009-07-07
Thanks.  I'm an linux idiot, but it really is brilliant.

Is there any way to map the shared folder as a place on its own like in Windows?

---


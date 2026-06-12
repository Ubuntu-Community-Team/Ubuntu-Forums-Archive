---
title: "CLI to enable tsclient services?"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2008-03-15
using SSH, How do I enable tsclient connections?

I can SSH into an ubuntu box. I would like to enable tsclient connections on it.

Thanks

---

### Post by jimjawn on 2008-03-16
There isn't a 'Terminal Services' for linux per se.  What you should be looking at is is VNC'ing to your linux box.  Do a search on the forums for turning on VNC.  Or an 'ubuntu vnc tutorial' on google.

Good luck and if you get stuck, I'll post some links.

---

### Post by ant2ne on 2008-03-18
What I'm referring to...

Applications->Internet->Terminal Server Client

Maybe I have my vocabulary wrong.

---

### Post by lsutiger on 2008-03-19
What jimjawn was referring to is that you can not setup a linux box to be a host using Terminal Services Client. You can set up VNC on the host and use TSC to dial into the host.

---

### Post by ant2ne on 2008-03-19
> ant2ne@2ne-buntu:~$ man vnc
No manual entry for vnc
ant2ne@2ne-buntu:~$ vnc --help
bash: vnc: command not found
ant2ne@2ne-buntu:~$ 


linky me to info on VNC?

---

### Post by lsutiger on 2008-03-19
sudo apt-get install vncserver

---


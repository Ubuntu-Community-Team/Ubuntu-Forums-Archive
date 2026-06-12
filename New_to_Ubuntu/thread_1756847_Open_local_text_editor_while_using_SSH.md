---
title: "Open local text editor while using SSH"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by The_Don5891 on 2011-05-12
Hello and thank you in advanced.

I am on my ubuntu box (10.04) and am connected to another linux box (CentOS I believe) via SSH. There is a file on the remote system that I am connected to that I want to edit. I want to be able to use a text editor that is on my local machine, say gedit, on that remote file with out transferring. 

Is this possible? Any ideas welcome. 

Thanks

---

### Post by Vaphell on 2011-05-12
you can try using sftp in nautilus (press ctrl+L to be able to type the address and enter sftp://user@server/location/), if you manage to mount remote location that way you'll be able to edit files as if they were local.

---

### Post by lmarmisa on 2011-05-12
Welcome to the forums.

Try to use the option **-X** (or **-Y**; check details with **man ssh**) when you type the command **ssh**:

```

ssh -X user@remote_host

```

Then you will be able to edit the remote file using gedit:

```

gedit remotefile

```

---

### Post by sweetleaf on 2011-05-12
> **The_Don5891 said:**
> I want to be able to use a text editor that is on my local machine,

> **lmarmisa said:**
> ```

ssh -X user@remote_host
gedit remotefile

```

Wouldn't this launch gedit from *remote_host*, rather than from the local machine? The result would look the same (gedit window appears on local machine), but it would fail if gedit isn't installed on remote_host.

---

### Post by jperelli on 2011-05-12
You could mount the remote filesystem using 'sshfs' and then navigate to the mounted directory, and edit the file with your text editor gedit nano vi etc.

---

### Post by lmarmisa on 2011-05-12
> **sweetleaf said:**
> Wouldn't this launch gedit from *remote_host*, rather than from the local machine? The result would look the same (gedit window appears on local machine), but it would fail if gedit isn't installed on remote_host.

You are right. My proposal uses a remote editor but I consider that, in many cases, this is not a limitation. In the other hand, my proposal is valid not only for gedit but also for any other program which uses a X11 graphical user interface.

---

### Post by collisionystm on 2011-05-12
> **The_Don5891 said:**
> Hello and thank you in advanced.

I am on my ubuntu box (10.04) and am connected to another linux box (CentOS I believe) via SSH. There is a file on the remote system that I am connected to that I want to edit. I want to be able to use a text editor that is on my local machine, say gedit, on that remote file with out transferring. 

Is this possible? Any ideas welcome. 

Thanks



Just use 

```

nano filename

```

---

### Post by SpeedyGonsales on 2012-06-28
Old topic, but there is no real suggestion for slow networks (where X forwarding is too slow) and editor only solutions.

If you want hard core solution, you have Komodo Edit from ActiveState (Free Code Editor for Windows, Mac and Linux). Only thing to remember is that remote editing in this lite version of Komodo IDE seems to be limited to only one remote site.

Second editor only solution is jEdit with FTP plugin, which gives you sFTP option if you have Java 1.5 or higher installed (which in 2012 is reasonable assumption).

I would repeat ```
sftp://user@server/location/
``` solution as I use it often although I installed Komodo Edit waaaaaaaaay back. :D

---


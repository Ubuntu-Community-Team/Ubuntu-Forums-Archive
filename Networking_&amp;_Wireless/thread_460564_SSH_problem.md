---
title: "SSH problem"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-05-31
I can access my two computers, from either one, in a terminal using

ssh username@ipaddress

But when I do this from Places/Connect to Server, it craps out, so I can never get to nautilus.

I re-set both with

```

sudo /etc/init.d/ssh restart

```

to no avail.

Help appreciated!

Thanks....

-merlin

---

### Post by x64Jimbo on 2007-05-31
How exactly are you setting it up in connect to server? There are some options that I believe you need to specify to get it to work correctly.

---

### Post by merlinus on 2007-05-31
Service type: SSH
Server: IP address (they are static on both machines)
Name to use for connection: userid

It sometimes will work if I reboot, but this is obviously a PITA.

Thanks!

-merlin

---

### Post by x64Jimbo on 2007-05-31
The name to use for the connection is a nickname - a name for the shortcut that will be placed on your desktop. Just use an easy to remember name for the computer you're connecting to, not the username.

---

### Post by merlinus on 2007-05-31
Thanks!  Looks like this is going to work.

-merlin

---


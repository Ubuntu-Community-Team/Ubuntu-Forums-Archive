---
title: "connection to windows network blocked by iptables firewall"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by steve101101 on 2009-05-05
I am trying to connect to my window's netowrk comupters on my home network. If iptable is enabled it cant connect. However using firestarter to disable it, it connects without an issue. How do allow connects to be made on my local network?

Thanks

---

### Post by steve101101 on 2009-05-05
i have set up firestarter to allow ports 137-139 and 445 (ie samba and microsoft-ds) through b/c this is what seems to get connected when the firewall is off. however this doesn't help.

---

### Post by ptn107 on 2009-05-05
I got frustrated with Firestarter a while ago when trying to set up a samba server.  My advice is to ditch Firestarter and go with ufw (it has a gui frontend called gufw but the command line is just as easy).  All you need is a few commands to set up ufw the way you want (must be running Ubuntu 8.04, 8.10, or 9.04).

1. Remove firestarter:
```
sudo aptitude purge firestarter
```

2. Enable ufw and set the default policy to deny incoming traffic:
```
sudo ufw enable && sudo ufw default deny
```

3. Allow all local network connections through:
```
sudo ufw allow from 192.168.1.0/24
```

That's it.  You can substitute 192.168.1.0 for whatever your LANs address is.

More Information:
```
man ufw
```

---

### Post by steve101101 on 2009-05-05
will that allow all local networks connects access???

b/c thats what i want

---

### Post by steve101101 on 2009-05-05
worked like a charm. thanks. i am glad i can actually connect to my other widows shares now. :) :KS

---

### Post by ptn107 on 2009-05-05
The last line:
```
sudo ufw allow from 192.168.1.0/24
```
will allow _any_ connection from the local network through the firewall.  Just make sure you use the correct address for your LAN.  192.168.1.0 may or may not be what you use.

If you ever forget what rules you added type:
```
sudo ufw status verbose
```
to view the list.

---

### Post by steve101101 on 2009-05-05
okay. thanks for all the help. its working great now.

---

### Post by steve101101 on 2009-06-28
this thread is also useful for setting up samba correctly.

---


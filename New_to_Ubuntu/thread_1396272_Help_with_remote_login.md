---
title: "Help with remote login"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-02-01
I have followed every tutorial it seems like to learn how to login into my ubuntu desktop from my windows xp laptop, both on the same network.  the connection on the windows end keeps timing out.  I am using VNC viewer 4. 

Any ideas?

Thanks

---

### Post by switch10 on 2010-02-01
Go to system>Preferences>Remote Desktop

Make sure the first 2 boxes are checked, "allow others to view your desktop", and "allow others to control your desktop"  you should also setup a password.

Good luck.

---

### Post by baddnady23 on 2010-02-01
> **switch10 said:**
> Go to system>Preferences>Remote Desktop

Make sure the first 2 boxes are checked, "allow others to view your desktop", and "allow others to control your desktop"  you should also setup a password.

Good luck.

Already done it... no luck.  Would it have anything to do with opening certain ports on the firewall?

---

### Post by baddnady23 on 2010-02-02
Everything i read seems to mention something about port 5900...

---

### Post by superprash2003 on 2010-02-02
absolutely right , you need port 5900 open to remote control your vnc machine over the internet . you need to open this port on your router.. what is th model no of your router?

---

### Post by baddnady23 on 2010-02-02
> **superprash2003 said:**
> absolutely right , you need port 5900 open to remote control your vnc machine over the internet . you need to open this port on your router.. what is th model no of your router?


AT&T 3800HGV-B Gateway

---

### Post by superprash2003 on 2010-02-04
here is a guide [http://www.portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm](http://www.portforward.com/english/routers/port_forwarding/2wire/3800HGV-B/default.htm)

---

### Post by porchrat on 2010-02-04
> **superprash2003 said:**
> absolutely right , you need port 5900 open to remote control your vnc machine over the internet . you need to open this port on your router.. what is th model no of your router?

The OP said "on the same network". I assume he/she means LAN. Why would one need to open ports on the router if the machine is local?

Could always do a remote login with X through SSH... seems a little excessive but then the same setup is easy to replicate across the net?

Just a thought.

---


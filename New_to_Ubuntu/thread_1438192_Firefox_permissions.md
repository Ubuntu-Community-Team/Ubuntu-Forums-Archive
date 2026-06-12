---
title: "Firefox permissions"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by frank cox on 2010-03-24
When I played around with the user permissions I somehow managed to set firefox were it will only display my bookmarks or let me surf if I open it with sudo.
Help!

---

### Post by wojox on 2010-03-24
Here you go [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Scroll down to Troubleshooting.

---

### Post by sisco311 on 2010-03-24
for GUI apps use *gksu* or *sudo -i*: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
(oh and never run your web browser as root)

run:
```
sudo chown -R $USER: ~/.mozilla
```

---

### Post by frank cox on 2010-03-25
Thanks guys!

I guess I spoke to soon as far *** being solved.. I still have the same problem. my bookmarks are gone and I cannot browse except in sudo.  I copied the command and and switched my user name where you typed user and it went back to a prompt so I thought it had worked.

---


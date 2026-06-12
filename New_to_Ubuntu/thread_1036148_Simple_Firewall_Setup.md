---
title: "Simple Firewall Setup"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by sam-c on 2009-01-10
[SIZE="2"]a-Please compare ufw Firestarter and Shorewall .
b-Which is easiest to setup and use.
c-Is it OK to have all three or should I uninstall one of them.
d-Any other Suggestions?[/SIZE]

---

### Post by cerealtx on 2009-01-10
a-Firestarter ive heard good things about it 
b-unsure havn't tried them all
c-no point having more than one and can acctually be more harm than protection
d-this is old info, but should be able to get ya started [http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

---

### Post by handydan918 on 2009-01-10
> c-no point having more than one and can acctually be more harm than protection

Common misconception from the windows world. There is no harm to running all the different firewall configuration tools you want. They are all only frontends for iptables, and as such, do not conflict with each other like windows firewall apps would.

---

### Post by crjackson on 2009-01-10
> **sam-c said:**
> [SIZE="2"]a-Please compare ufw Firestarter and Shorewall .
b-Which is easiest to setup and use.
c-Is it OK to have all three or should I uninstall one of them.
d-Any other Suggestions?[/SIZE]

a - I like first gufw then firestarter
b - gufw IMHO
c - Yes - They aren't really firewalls. They are different configuration tools for the same firewall (iptables)
d - ```
sudo apt-get install gufw
```

---

### Post by minsf on 2009-01-10
sam, you will probably be interested in reading the sticky on the security forum: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
especially the firewall part.
also [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604) will give the newbie-paranoid something to work on :)

and explaining handydan's post a little bit: ubuntu comes with a firewall called iptables by default. firestarter and the rest are normally just cool graphical interfaces that help you play with the settings of the complicated iptables. they are not firewalls by themselves.

and one more word about firestarter: it sometimes has problems starting up. if you read my last paragraph and handydan's post, you may be asking "but why do we need firestarter to start on boot, when you said we have iptables?" and you are right. the only problem is that iptables tends to go to its default settings after boot, rather than the settings that you configured via the firestarter before the boot. those default iptables setting are good. but if you want iptables to start with your "firestarter settings" you may be interested in the following: [http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)
(especially that step about commenting out the relevant lines).

---

### Post by Norm24 on 2009-01-10
I also prefer gufw over firestarter.

---


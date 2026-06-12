---
title: "Hostname doesn't work, IP does?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Depressed Man on 2007-07-10
I'm trying to use shares and I've noticied that when I use hostname such as smb://vendetta/MyFiles it doesn't work. But if I use the ip smb://192.168.1.4/MyFiles it does work. Why?

---

### Post by CheShA on 2007-07-10
do you have a firewall installed?

Check [this thread]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+firestarter")

---

### Post by Depressed Man on 2007-07-10
I do have IPtables (didn't bother configuring it though). But that would explain why hostnames randomly stop working. THANK YOU! You've resolved a serious headache. :)

---

### Post by CheShA on 2007-07-10
NP :)

FWIW Firestarter is a really easy to configure - well  recommended!

---

### Post by Depressed Man on 2007-07-10
aww.. it's back to not working again. >.<

*sighs* I'll just have to do it by IP again.

---

### Post by kevdog on 2007-07-10
Do a search on the forums for winbind.  You will need this package installed and configured properly (easy to do), in order to use hostnames rather than IP addresses.  Its fairly easy to do. Sorry I dont have the link.

---


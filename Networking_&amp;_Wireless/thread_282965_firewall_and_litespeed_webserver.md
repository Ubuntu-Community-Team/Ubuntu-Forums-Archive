---
title: "firewall and litespeed webserver"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by markster23 on 2006-10-23
i have firestarter firewall and ubuntu 6.10 edgy eft with lsws webserver running and i'm wondering how to add an exception to allow for incomming connections ?? would it be to add a rule for HTTP on port 80?

---

### Post by bswilson on 2006-10-23
Just issue this command, but replace **ethX** with whatever your interface's real name is.

```
sudo iptables -N -i ethX -p tcp --dport 80 ACCEPT
```

---

### Post by markster23 on 2006-10-23
okay well i added the rule thru the gui to allow HTTP connections on 80 and it supposedly worked cuz i had someone try it.. but is there a command that lets me manually edit the ip tables ?

---

### Post by bswilson on 2006-10-23
That is exactly what I provided to you.  *Firestarter* is just a GUI that controls the *iptables* rules.  Try looking at the man pages for iptables, or run this command to show your running rules:

```
sudo iptables -L
```

---

### Post by mips on 2006-10-23
> **markster23 said:**
> okay well i added the rule thru the gui to allow HTTP connections on 80 and it supposedly worked cuz i had someone try it.. but is there a command that lets me manually edit the ip tables ?

Define manually edit ?

You can edit the file with a text editor use a gui like firewall builder etc.

---

### Post by markster23 on 2006-10-24
manually edit i meant as in using gedit... umm.. i'm actually new to iptables and the iptables -l output was a bit confusing to me.. i'm using firestarter firewall and i have litespeed webserver and mysql running but i've been encountering a few problems like people being able to connect, but i recently put an exception for HTTP on port 80 in my firestarter config and i guess people are able to connect now, you can try yourself, [http://markster23.servepics.com](http://markster23.servepics.com) let me know if ur able to connect... umm, aswell i dunt know if you know much about mysql, but when i setup any php app that tries to connect to it, it wont allow me to connect... i read in one of the forums to try using 127.0.0.1 instead of localhost because of the socket being broken, and that worked in some cases, but i'm not sure how to fix the socket so that localhost links to 127.0.0.1... ?? any ideas ?

---


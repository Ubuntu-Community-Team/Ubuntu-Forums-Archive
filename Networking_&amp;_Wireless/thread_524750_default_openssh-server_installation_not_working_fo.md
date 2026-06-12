---
title: "default openssh-server installation not working for me"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by girard on 2007-08-13
i managed to install openssh-server from synaptic quite well. i was able to establish a connection between ubuntu and xp via crossover cables. everything went perfect. but when i tried what was supposed to be the main use of ssh, remote access, my client could not get a connection.

he said something about the port being filtered. well i don't know really. but the point is that he couldn't get remote access. i'm not sure what ssh client he was using (if that matters). but the successful connection in xp was under winscp.

i already set policies in firestarter (i'm not really a fan of the terminal so i try to do as much using GUI) to allow service for ssh with the default port (22) "when the source is" anyone. to make sure, i also allowed FTP service to everyone on the default ports also (20-21), but still nothing. 

i haven't touched anything aside from those.

this is not really an urgent need as i have a successful p2p samba setup between the same xp notebook mentioned above and this linux desktop. it works well for my needs. this is just something i want to figure out and understand - and maybe later on, have an actual use for it.

any ideas?

EDIT: according to the client who is testing my server, he gets "no route to host" error or something.

---

### Post by djgrandmarquis on 2007-08-13
> **girard said:**
> i was able to establish a connection between ubuntu and xp via crossover cables.

How is the server machine connected to the Internet? I had to forward port 22 on my wireless router to gain SSH access.

---

### Post by girard on 2007-08-13
i don't have a router. they are connected directly to the LAN, so that only one system is connected at a time.

---

### Post by girard on 2007-08-14
we spent a good number of hours trying to figure out what we're doing wrong. apparently, my internet subscription does not support public ip address. i have a private one, so it's impossible for me to setup this system as a server.

meaning? a firewall is actually useless for me, since i own all pc's and no one can get into my system? i don't have a LAN and only connect my notebook via cross overs, unless i have to protect myself from.. well ... myself? man!

---


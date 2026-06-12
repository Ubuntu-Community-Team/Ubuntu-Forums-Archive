---
title: "Network access"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Garthhh on 2009-11-22
I'd like to be able to access the files on my 8.04 build [here], from 2 other computers on the same home network, one vista, one XP?
I can see both the other computers from here & they can see each other, so sharing is working

---

### Post by danill2008 on 2009-11-22
Try Samba: sudo apt-get install samba. [Here]("http://en.wikipedia.org/wiki/Samba_%28software%29") is a link to what it is.

---

### Post by Garthhh on 2009-11-22
Thanks 
Found it & am installing
just getting the hang of synaptic, nice...

---

### Post by Garthhh on 2009-11-22
I installed it 
What do I do with it?
on a windows machine I would do things like make sure all the machines are in the same group & enable the files I wanted to share:D

---

### Post by sandyd on 2009-11-22
then install system-config-samba

run this in the terminal
```

gksudo system-config-samba

```
then go to prefrences -> Server Settings

enter the workgroup.
go to the "security" tab

flip "authentication mode" to user

flip guest account to your own username

click "ok"

click the "+" sign
on the access tab -> accessable to everybody

then you can fill in everything else for your shared folder.

when your finished, samba sometimes requires a little kick to get it chugging'
so
```

sudo /etc/init.d/samba restart

```

---

### Post by Garthhh on 2009-11-22
I entered the command in terminal & didn't get an error, must have worked then?
I don't see a server settings
on 
system>preferences

do I need to configure as server?

---

### Post by Garthhh on 2009-11-25
I going to do a fresh install as a server,
Thanks for the help

---

### Post by Iowan on 2009-11-25
Any linux box that will share files with Windows machines will need Samba-server installed (OK, there's nautilus...). Stock Ubuntu server install is a CLI environment (no GUI). You can add one, but it'll end up being about as hard to install a desktop on a server as installing Samba on a workstation (you'll still need to configure Samba on the server).

---

### Post by Garthhh on 2009-11-25
Any chance of getting that translated into beginner?
A link, Tutorial, terms that would give me meaningful search results...:D
I'm gonna do a fresh install, since I've changed hard ware
see my other thread
[http://ubuntuforums.org/showthread.php?t=1337336](http://ubuntuforums.org/showthread.php?t=1337336)

---

### Post by Iowan on 2009-11-26
[Here]("http://ubuntuforums.org/showthread.php?t=202605") is the "classic" Samba setup How-To.
What part of my crystal-clear ( :rolleyes: ) technobabble needs translation? :)
[This]("https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html") is some Window's (Samba) server information.

---

### Post by Garthhh on 2009-11-26
perfect thanks
I'm trying to figure out exactly how my fresh install is going to go.
I'll get back to this once I'm through

I see you've stuck w/HH [8.04] & have been doing this awhile, gives me hope that my similar choice is good.

---


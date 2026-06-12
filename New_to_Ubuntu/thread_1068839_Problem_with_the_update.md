---
title: "Problem with the update"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Share_The_Pain on 2009-02-13
Hello all, i made a clean install of ubuntu 8.10 stable and when i go to update (gui) or apt one, i have these errors, can someone help me out ?

[http://fdhdgshhd.googlepages.com/dfsdfsdf](http://fdhdgshhd.googlepages.com/dfsdfsdf)

Kind regards

---

### Post by overdrank on 2009-02-13
> **Share_The_Pain said:**
> Hello all, i made a clean install of ubuntu 8.10 stable and when i go to update (gui) or apt one, i have these errors, can someone help me out ?

[http://fdhdgshhd.googlepages.com/dfsdfsdf](http://fdhdgshhd.googlepages.com/dfsdfsdf)

Kind regards

Hi and welcome, I am assuming you have a internet connection. You may try and change the location of the server, under system, administration, software sources. Under download from.

---

### Post by Share_The_Pain on 2009-02-13
Hey thanks for the help, but it still dont work

i did tryed to change it but :( the same, even if i press the select best server

i get --> [http://img101.imageshack.us/my.php?image=sad2zw4.jpg](http://img101.imageshack.us/my.php?image=sad2zw4.jpg)

And these is a crap because my connection is fine :( 

please help

---

### Post by Share_The_Pain on 2009-02-13
Is there somebody that can help me out ?

Thanks in advance

---

### Post by drs305 on 2009-02-13
Check System, Preferences, Network Proxy, Proxy configuration tab. Is it set to Direct Internet Connection?

PS Welcome to the ubuntu forums. 
I know you are anxious to get an answer but starting another post isn't encouraged on these forums.

---

### Post by Share_The_Pain on 2009-02-13
Omg... Thanks for the help

Yep sry for that second post, but i saw soo many people online and no one sayd nothing so i... -.-'''

I manage to do it, sorry for all the trouble... 

Stay fine drs305

---

### Post by drs305 on 2009-02-13
Sometimes the ability to update via synaptic/update manager is due to a corrupted *hosts* file.

If you enter "cat /etc/hosts" in terminal the response should be something like 
> me@**mycomputer**:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	**mycomputer**


If your computer name has changed to something like "yourcomputername.something-added-here" you should change it back.
For example: 
127.0.0.1	localhost
127.0.1.1       mycomputer.ubuntu 
to
127.0.0.1	localhost
127.0.1.1       mycomputer

```

sudo cp /etc/hosts /etc/hosts.backup
gksudo gedit /etc/hosts		

```

---


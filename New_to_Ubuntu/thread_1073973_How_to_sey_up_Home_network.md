---
title: "How to sey up Home network"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by articwolf939 on 2009-02-18
Any one know where i can find a "how to" set up a home network on ubuntu im just tring to enable fileshareing between them all

---

### Post by Kain000 on 2009-02-18
> **articwolf939 said:**
> Any one know where i can find a "how to" set up a home network on ubuntu im just tring to enable fileshareing between them all

sure, first tho are these all linux/unix machines or are we talking windows and linux and macs?


for networks with a mixed bunch (windows talking to linux or Mac)

YOu will want SAMBA, a handy protocol that windows will play nice with, and linux/Mac can talk to.

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

if you are looking for somthing between linux/unix machines, then NFS is your man...or er, protocol.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

---

### Post by Kain000 on 2009-02-18
Also you may want to consider the program  Giver if it is between workstations that will have people at them, it's like an instant message file transfer, a notify window pops up and says so and so wants to give you this file where do you want to save it?

drop copy is also a good solution for linux to mac transfers.

[http://www.jupiterbroadcasting.com/?p=485]("http://www.jupiterbroadcasting.com/?p=485")

---

### Post by articwolf939 on 2009-02-18
> **Kain000 said:**
> sure, first tho are these all linux/unix machines or are we talking windows and linux and macs?


for networks with a mixed bunch (windows talking to linux or Mac)

YOu will want SAMBA, a handy protocol that windows will play nice with, and linux/Mac can talk to.

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

if you are looking for somthing between linux/unix machines, then NFS is your man...or er, protocol.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")


Well basicly i have 2 ubuntu machines, and my ps3 dual booted with ubuntu and sonys XMB, one of the machine that run ubuntu is an old desktop im turning into a server, i just want to be able to run and\or start programs from it and save files on it. the other ubuntu machine is a laptop dual booted with vista and ubuntu but i meanly uses linux, so whatever is easyer and will meet thoses need ive tried samba but havent been very sucsess ful yet

---

### Post by Kain000 on 2009-02-18
> **articwolf939 said:**
> Well basicly i have 2 ubuntu machines, and my ps3 dual booted with ubuntu and sonys XMB, one of the machine that run ubuntu is an old desktop im turning into a server, i just want to be able to run and\or start programs from it and save files on it. the other ubuntu machine is a laptop dual booted with vista and ubuntu but i meanly uses linux, so whatever is easyer and will meet thoses need ive tried samba but havent been very sucsess ful yet


Hum well I dont know much abotu ubuntu on the ps3 is it just a port of the full system?    

If you want to stream media to the ps3's original system you can use Ushare, or any other UPNP app.

If you want windows support you will need to use samba, unless you dont care about shareing to your vista boot, in which case NFS is (at least in my opnion) alot easier to set up.

I had quite a headache seting up samba.

if you want some samba help look into a program called GADMIN --samba

just go to applications > add/remove > and search for gadmin   there are like 5 of them just a graphial way to set up many common server daemons such as samba.   

I used the FTP one to set up my servers FTP protocol with user accounts and whatnot.

---


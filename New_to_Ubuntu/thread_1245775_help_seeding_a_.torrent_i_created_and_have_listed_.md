---
title: "help seeding a .torrent i created and have listed w/ tracker..."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by earthpigg on 2009-08-20
what i have done:

1. created the torrent.
2. uploaded the torrent to a tracker website.
3. downloaded the torrent from that tracker.
4. moved the contents of the torrent to where it needs to be for the two torrent clients i have tried to check the file and recognize it as 'downloaded' immediately.
5. set both to seed. both claim to be seeding. no, i am not using both simultaneously :D

clients: transmission and vuze

error message vuze's tester is giving me:

```
Testing port 26541 ... 
NAT Error - Connection to 69.107.89.208:26541 (your computer) refused.
```

my networking knowledge is fairly weak. i have never changed any of ubuntu's defaults. normally, when i download a torrent it starts uploading while it is downloading and continues after. i would *think* it would be the same when i "download" the contents of the torrent by the method i did above, but apparently not.

tracker: tpb [http://thepiratebay.org/torrent/5063553](http://thepiratebay.org/torrent/5063553)
project info, if you are curious: [http://sites.google.com/site/masonux/](http://sites.google.com/site/masonux/)

---

### Post by sandyd on 2009-08-20
if you haven't changed ubuntu's firewall, the port is open on your computer and should be accepting connections.
however, are you behind a router?
if you are, you will either have to
1. configure port forewarding
2. enable dmz
3. enable PnP

---

### Post by sandyd on 2009-08-20
p.s. why are't you hosting it at sourceforge?
you don't need to seed that way.

---

### Post by earthpigg on 2009-08-20
> **carlee said:**
> p.s. why are't you hosting it at sourceforge?
you don't need to seed that way.

sourceforge wants source code, which i have never even seen, and seems exceptionally above and out of the scope of this project. :D

i respect the GPL immensely, and address source code concerns at the project's page above.

> you will either have to
1. configure port forewarding
2. enable dmz
3. enable PnP 

either? hrm.... could you tell me which is easiest, perhaps?

this entire project is more of a proof-of-concept and learning experience than a "my distro will take over teh world!!one!" type project. this is my last hurdle.

---

### Post by sandyd on 2009-08-21
I guess since your asking me which one, your behind a router.
it would be nice to know your router model so i can pull the docs off the net.
(most routers are capable of all of them, but the instructions for each router are diferent.)

---

### Post by earthpigg on 2009-08-21
i got it, thanks carlee! 

just had to find the key word that applied. in this case, it was 'port forwarding'.

---

### Post by sandyd on 2009-08-21
your welcome.

---


---
title: "my ubuntu router gets slooow"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by vaalbygaardsvej on 2008-03-16
my ubuntu server running NAT, samba wireless acces point and so on goes SLOOOOW after some hours. it also runs deluge and seeding a couple torrent files. it seems to have something to do with deluge because it takes many hours to go slow when deluge is not running. but relatively few when it is. the temporarely cure for the issue is downning the NIC connected to the internet and upping it again. then everything runs smooth again fore some time.

deluge is set at max 200 connections, but when it becomes slow deluge is usally only got less than 10 connections.

it would be nice to have some sort od fix that just makes the server fly with no regard for how long it has run.

i believe deluge maybe don't drop the conections when they are no longer active. i  also suspect that changing to another torrent client will help the problem, but i don't want to do this if it does not help..

---

### Post by vaalbygaardsvej on 2008-03-31
bump. problem still there, and it does in fact seem to be torrents that cause the problem. and furthermore it is not limited to the server, i was downloading linux MCE on one of the peers. this has same effect on the server. after approx half an hour of downloading with 1 meg/s the connection almost dies and seizes to operate.

does anybody have a clue to what i can do about this. it is quite annoying to have to restart ones server every day :-(:confused:

---

### Post by vaalbygaardsvej on 2008-04-03
weeel. seems like it was just an IPv6 issue.. it has been working splendid at full speed for a few hours now :guitar:

---

### Post by vaalbygaardsvej on 2008-04-06
well latest update is that after i disabled ipv6 it got alot better, but it still slows down grinding to a halt.. sometimes after only a few hours, and sometimes after a couple of days

---


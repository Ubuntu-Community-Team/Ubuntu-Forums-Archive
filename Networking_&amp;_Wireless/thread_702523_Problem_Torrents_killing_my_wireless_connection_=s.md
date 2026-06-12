---
title: "Problem: Torrents killing my wireless connection? =s"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by E-Mike on 2008-02-20
When i run a torrent, it seems to kill my connection. My connection is wireless and im using a Dell M1330 with the iwl3945 (the ipw3945 doesn't work past 30kb/s lol) the iwl3945 works fine apart from this little bug. it also doesn't matter which bittorrent client i use. the connection still drops.

Any ideas whats causing this? and maybe a solution?
Thanks
Mike :)

---

### Post by Rogers on 2008-02-20
Low end hardware can be crushed by torrents.... My linksys old Network card would cause me to lose my network and hard locks if I ran more than 1-2 torrents.

I would try to 
> sudo apt-get update
then
> sudo apt-get upgrade
and maybe there is an updated driver available... if not try throttling and decreasing connections in the torrent client.

---

### Post by E-Mike on 2008-02-20
It can't be the low end hardware.

I have an 2.2 dual core intel with 4gb of ram, the nvidia 8400m gs 128mb and a 200gb hard drive.

running the commands didnt update anything :( it's all up to date. im using the best drvers for my wireless card.

i will try to limit the torrent and see if that works.

---

### Post by rustybronco on 2008-02-20
I believe on launchpad there is a post/thread about wireless disconnecting under load.
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=iwl3945&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=iwl3945&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

I'd look again but my eyes hurt from looking to find  answers on that chipset.

****oops, I see you changed to the iwl3945 drivers so it may not apply.

---

### Post by E-Mike on 2008-02-20
yeah i couldn't find anything on the lauchpad :( i hope it's something i can fix, i really LOVE ubuntu and have gone as far as removing windows totally :)

---

### Post by sojusnik on 2008-05-04
Same problem here with nearly the same hardware.

Link to hardware: [http://www.box.net/shared/d0rfuonkck](http://www.box.net/shared/d0rfuonkck)


Especially at high speed my wireless connection gets killed. Strange and very annoying bug.

Anyone found a solution to this?

---


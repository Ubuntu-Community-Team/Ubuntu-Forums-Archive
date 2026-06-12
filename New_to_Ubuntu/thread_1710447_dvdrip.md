---
title: "dvd::rip"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-19
ok im using DVD::rip is there anyway to have it shrink files while it rips?

---

### Post by SuperFreak on 2011-03-19
Have a look at K9Copy (in software center). It will shrink dvds to ISO, Folder or a DVD

---

### Post by mushroom08 on 2011-03-19
i tried K9copy it crashed and got this message

Executable: k9copy PID: 11860 Signal: 11 (Segmentation fault)

---

### Post by gofurygo on 2011-03-20
I assume you are talking about shrinking DVD9 to DVD5? At this point, it cant be done with DVD::rip... See the ToDo section on the developers website: [http://www.exit1.org/dvdrip/todo.cipp](http://www.exit1.org/dvdrip/todo.cipp)
However, there is a program called DVD95 in the repositiories you could try, shrinking DVD9 to DVD5.
While ripping DVD9 with dvd::rip I experienced several problems like "only 150000 of 210000 frames could be read", or dvd::rip shortening the movie although it showed fine in the clip&zoom screen. I believe all these problems were related to the fact I ripped DVD9.

Another way of "shrinking" DVD9 is using DVDshrink under wine (it works very well). I shrinked DVD9 to DVD5 with it, then used the output to run it through dvd::rip for transcoding to a 700MB .avi file.

Hope that helps

---

### Post by MartyBuntu on 2011-03-20
> **gofurygo said:**
> 

Another way of "shrinking" DVD9 is using DVDshrink under wine (it works very well).

I'm glad someone mentioned it. People tend to freak out when the subject of WINE as a solution comes up.

Yes, DVD Shrink works nicely.

---

### Post by mushroom08 on 2011-03-20
ya i used that back when i had windows it wont read the disk what about k9copy i tried opening it in terminal and got this 


Error: "/var/tmp/kdecache-mushroomstamp" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-mushroomstamp" is owned by uid 1000 instead of uid 0.
KCrash: Application 'k9copy' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/mushroomstamp/.kde/socket-MushroomEmpire/kdeinit4__0

---

### Post by gofurygo on 2011-03-20
what do you mean, "it wont read the disk"? Wont read it with DVDshrink under windows? So the disk is damaged, a disc type ur DVD drive doesnt support (blueray?) or its copy protected...? Please clearify "it wont read"... I never had any issues with dvdshrink and wine on ubuntu, neither with dvd:rip - beyond the DVD9 --> DVD5 limitation.

---

### Post by mushroom08 on 2011-03-20
its the copy protection it only reads 19 mins from the middle of the movie

---

### Post by stmiller on 2011-03-20
Have you tried handbrake? - [http://handbrake.fr](http://handbrake.fr)

---

### Post by mushroom08 on 2011-03-23
gave up on dvd::rip switched to K9copy

---


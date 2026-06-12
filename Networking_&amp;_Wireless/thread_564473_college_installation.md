---
title: "college installation"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Tuge on 2007-10-01
hello!

i'm setting up a edubuntu to be our secondary(hopefully primary in a near future) o/s on our campus. currently we are running ~100 windows computers for our students (and as our former it-person was a big fan of ms) we are also running 2 server 2003:s

i'm making plans and tests so that we would be able to change around 40 student computers to edubuntu before end of this year. (because this is very new thing to our school, bigger implementation is virtually impossible) currently i'm running edubuntu on a server and i have done test drives with thin clients -> it works like a charm.

question 1:
i have changed so that edubuntu uses our server 2003 ad for authentication which works also very nicely. the current problem is that i would need to setup centralized place for "user profiles" (what are these called in linux?) so that if our student changes for example background image, it would follow him/her to a next computer (which isn't propably behind the same server)... i know it works currently like this, but after putting up couple of edubuntu servers to serve edubuntu it won't automatically work so. do i need to mount a new network place on server and set user profiles to load from this share or what is a proper approach??

question 2:
currently students have shared folders on our ad server where they can save files and stuff. i would need to make this folder to be users home folder on linux. is it proper approach, if i am to change template homedir setting in /etc/samba/smb.conf to match the user network share somehow. so that it would point to everyones windows share. if this is the proper way of doing this, how am i able to keep track of user credientials so that only john.doe would be able to enter windows share folder named john.doe?

i want to apologize for long post and i appreciate hugely all replies to these problems.

---


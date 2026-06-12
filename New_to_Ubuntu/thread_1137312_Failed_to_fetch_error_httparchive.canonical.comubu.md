---
title: "Failed to fetch error http://archive.canonical.com/ubuntu/dists/jaunty-commercial"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by capnthommo on 2009-04-25
hi.  Dont know if this is a real problem but when i try to update with update manager i get the following
> Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty-commercial/main/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/jaunty-commercial/main/binary-amd64/Packages)  404 Not Found

Some index files failed to download, they have been ignored, or old ones used instead.

the third party software sources i have enabled in aptitude are as follows
> (checked)        [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
(not checked)  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (Source Code)
(checked)        [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-commercial main
(checked)        [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
(not checked)  [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free (Source Code)
i am running 9.04 on 64 bit
it is now 3 days since my system has downloaded any updates, according to update manager whenever i try.
what happens is i try to check for updates, get the "failed to fetch" error, continue and then the system seems to go through the process of checking and says, basically, you are up to date.  is it too early for updates?
i wouldn't worry but for the failed to fetch error, 
otherwise jaunty is running really well, i am pretty impressed (computer bursts into flame)
cheers everyone
nigel

---

### Post by cariboo on 2009-04-25
I don't know where the jaunty-commercial came from, I would just comment it out in /etc/apt/sources.list and you shouldn't have any problems.

---

### Post by capnthommo on 2009-04-26
Thanks cariboo
that seems to have fixed it, no error mssge and it just downloaded and installed 15 updates.
thanks a lot.  i got the "commercial" sources by following the complete multimedia howto but i may well have messed it up cos i tried a couple of other things of my own devising.  i probably 'invented' it.
anyway, excellent as ever
cheers
nigel

---


---
title: "Downloading entire repositorie for off-line purpose"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by obscur156 on 2009-02-18
Hi all.i wan't to know if it is possible to download entire repositorie for further use without internet connection or slower connection.

I would like to have like : main, universe,restricted,multiverse.

Thanks,regards.

---

### Post by albandy on 2009-02-18
sudo apt-get install apt-mirror

---

### Post by JKyleOKC on 2009-02-18
It's possible, if you have enough storage space and can stay connected for a long enough time. However I suspect that you're not aware of just how huge the repositories are. Since they contain tens of thousands of packages, you'd need thousands of DVDs to hold them and the connection time would be measured in weeks or even months.

Also, you'd lose the updating feature that the repositories provide automatically. By the time you had downloaded the last package, the first ones would be several versions out of date.

In general, not a good idea...

---

### Post by mcduck on 2009-02-18
Be prepared for buying a couple of extra hard disks if you really intend downloading everything available in Ubuntu's repositories (about 30 000 packages..) ;)

---

### Post by obscur156 on 2009-02-18
OUCHHHH,ok i did not think that was so big.Said to my self it maybe a couple of dvd lolll.Maybe i will just install all i need and make APTONCD.

Or is there something better?
Thanks for your quick reply guys.

---

### Post by JustANewb on 2009-02-18
AptOnCD is great!  I use it every time I have to reinstall my OS.  The only problem I have had is that when I updated to the next release, some of the packages don't ever update through the update manager (although I think that maybe these were proggies I downloaded from the net).

---

### Post by Pikestaff on 2009-02-18
Ubuntu in general is kind of heavily internet-update-based, there may be some distros better suited to a lack of an internet connection.  Just thought I'd toss that out there, good luck, regardless :)

---


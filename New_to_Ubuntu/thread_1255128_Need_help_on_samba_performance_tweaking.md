---
title: "Need help on samba performance tweaking"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by palmboy5 on 2009-09-01
Ever since I changed my server's OS drive to a 4GB flash drive (nothing fast), there has been a LOT of lag trying to access my server's SATA HDDs over the network. It takes 2-6 seconds for it to navigate into any folder or to do any other type of data access. 

Now, I would understand that it could lag if I were accessing that flash drive, but I'm only trying to access the storage HDDs connected to that system. Even if the OS drive were slow, there should be no reason for the SATA HDDs to have to be laggy as well. 

I'm guessing the lag is coming from some sort of caching samba is doing on the OS drive? Whatever it may be, how can I stop the lag? My sanity is counting on you. Thanks in advance!

---

### Post by palmboy5 on 2009-09-02
Bump!

---

### Post by palmboy5 on 2009-09-04
.. Bump :-\"

---

### Post by bear24rw on 2009-09-05
My guess would be caching or log writing.. you can try mounting /var/log on a ram disk and see if that helps? I'll have to google around some more

---

### Post by palmboy5 on 2009-09-07
I could try copying /var/log contents all to a folder on one of the storage HDDs and redirect to that, that should be possible, right? I don't remember what command(s) to use to change the symbolic link(?) though. What other directories can be moved in such a way? Or I suppose a better question is, what can't be moved in such a way?

I have no problem with the majority of the OS residing on a storage HDD. What I have a problem with is the OS taking up its own partition on the storage HDD, and making the _storage_ HDD become a bootable drive as a result.

---


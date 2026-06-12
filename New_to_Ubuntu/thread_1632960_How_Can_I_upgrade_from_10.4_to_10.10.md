---
title: "How Can I upgrade from 10.4 to 10.10"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Mindswap1 on 2010-11-28
Hi guys I'm really new to Ubuntu ( 3 days of total experience ) And I was hoping to get Ubuntu 10.10 onto my desktop. I really don't want to have to back everything up to a hard drive or flash drive and then freshly install, because I don't have anything I can back it up into ( my usb broke.)How can I safely upgrade to 10.10 or other future releases without making Ubuntu system files a mess. ( for example Windows had the option to just upgrade to the new OS without deleting things on the hard drive, but however caused it to bug a lot, and have a really fragmented registry.) I was hoping Ubuntu had a way to upgrade without causing something like that to happen.

---

### Post by lobralleo on 2010-11-28
Hi and welcome to Ubuntu! :)

You can upgrade to 10.10 via Software Updates: go to System -> Administration -> Software Updates and you will find an active button saying "New Release Avaliable" or something similar (I can't check right now, sorry about that). It should be enough to click on it and the upgrade will start and complete automatically.

As always, backup all your important data before upgrading: it's safe enough, but the occasional glitch in the process is possible.

The whole process will take a while (possibly several hours, depending on your connection and computer specs).

Hope this helps!

---

### Post by Autodave on 2010-11-28
> **Mindswap1 said:**
> Hi guys I'm really new to Ubuntu ( 3 days of total experience ) And I was hoping to get Ubuntu 10.10 onto my desktop. I really don't want to have to back everything up to a hard drive or flash drive and then freshly install, because I don't have anything I can back it up into ( my usb broke.)How can I safely upgrade to 10.10 or other future releases without making Ubuntu system files a mess. ( for example Windows had the option to just upgrade to the new OS without deleting things on the hard drive, but however caused it to bug a lot, and have a really fragmented registry.) I was hoping Ubuntu had a way to upgrade without causing something like that to happen.


SYSTEM > ADMINISTRATION > UPDATE MANAGER
Once there, you may have to click on "CHECK" to make sure the latest update list is shown.  You should see the 10.04 update there and can just update.

HOWEVER: it is ALWAYS recommended that you back up important files before doing an update!!!!!

---

### Post by garvinrick4 on 2010-11-28
#I do not know of anyway to dist-upgrade any OS that you should not back up your /home
#You are always at risk. 

```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```

---

### Post by lobralleo on 2010-11-28
Apologies, I somehow missed the part where you say that you don't have an available backup medium.
Have you considered using an online backup solution? For instance, if you don't have a huge amount of data on your computer, you could try Dropbox: I've never used it myself, but I am being told it works quite well, the only drawback being the limited space available.
There are several more free possibilities available; here is a comparison list:

[http://en.wikipedia.org/wiki/Comparison_of_online_backup_services](http://en.wikipedia.org/wiki/Comparison_of_online_backup_services)

Good luck!

---

### Post by wojox on 2010-11-28
> **garvinrick4 said:**
> #I do not know of anyway to dist-upgrade any OS that you should not back up your /home
#You are always at risk. 

```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 
```

LOL and here is the PERL way

```
perl -p -i.lucid -e 's/lucid/maverick/' /etc/apt/sources.list
```

---

### Post by EJI on 2010-11-29
Thanks garvinrick4

Worked Well!

---

